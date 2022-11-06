# singly_linkedlist_py

````py
class Node:
  def __init__(self, value):
    self.data = value
    self.next = None

class SinglyLinkedList:
  def __init__(self):
    self.head = None
    self.tail = None

  def insert_at_beginning(self, value):
    newNode = Node(value)
    if self.head == None:
      self.head = self.tail = newNode
      return
    newNode.next = self.head
    self.head = newNode

  def insert_at_middle(self, afterValue, insertValue):
    current_node = self.head
    while current_node and current_node.data != afterValue:
      current_node = current_node.next
    newNode = Node(insertValue)
    if current_node:
      current_node.next, newNode.next = newNode, current_node.next

  def insert_at_end(self, value):
    current_node = self.head
    newNode = Node(value)
    if current_node == None:
      self.head = self.tail = newNode
      return
    while current_node.next:
      current_node = current_node.next
    current_node.next = newNode
    self.tail = newNode


  # def delete(self, value):
  #   pass
  
  def print(self):
    current_node = self.head
    flag = 0
    while current_node:
      print(" -> "*flag  + str(current_node.data), end = " ")
      flag = 1
      current_node = current_node.next
    print()

  def delete_from_beginning(self):
    if self.head is None:
      return
    if self.head.next is None:
      self.head = self.tail = None
      return
    self.head = self.head.next

  def delete_from_end(self):
    if self.head is None:
      # no nodes in linkedlist
      return
    if self.head.next is None:
      # only one node in linkedlist
      self.head = self.tail = None
      return

    prev, cur = self.head, self.head.next
    while prev and cur:
      if cur.next == None:
        prev.next = None
        self.tail = prev
        return
      else:
        prev = cur
        cur = cur.next

  def delete_from_middle(self, value):
    prev, cur = self.head, self.head.next
    while prev and cur and cur.data != value:
      prev, cur = cur, cur.next
    prev.next = cur.next
    cur.next = None

sll = SinglyLinkedList()
sll.insert_at_beginning(10)
# sll.print()
sll.insert_at_end(20)
# sll.print()
sll.insert_at_end(30)
# sll.print()
sll.insert_at_end(40)
# sll.print()
# sll.insert_at_middle(20,50)
sll.print()
# sll.delete_from_end()
# sll.print()
# sll.delete_from_beginning()
# sll.print()
sll.delete_from_middle(30)
sll.print()
````
