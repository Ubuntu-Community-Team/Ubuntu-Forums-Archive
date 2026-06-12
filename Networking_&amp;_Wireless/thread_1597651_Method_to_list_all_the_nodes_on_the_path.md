---
title: "Method to list all the nodes on the path"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Like2Learn on 2010-10-15
I am thinking about an application, and I am not sure if Ethernet can support it.
 
I have a dozen of devices, which has a distinct IP address each and two ethernet jacks, one for "In", the other for "out". Of course the devices have processors inside to perform the network functionalities. I would like to call my device "node" although it might sound informal to some experts.
 
Now I want to connect the nodes one by one with ethernet cable. The "Out" jack of node X will be connected to "In" jack of node (X+1). This way they are all hooked. I would like an application, that list all the nodes between node M and node N in terms of their connectivity sequence. For example, between Node 3 and Node 6, there are Node 4 then Node 5 in between. This way if one node sends out a message, I can easily trace the node and physically located it. BTW, the nodes are connected randomly and typically reshuffled the order quite often except of the first node, so possibly I won't be able to physically locate the node just by their IPs (and I don't want to label the node with its IP). However, If the application runs at the first node, and tell me how many nodes between the first node and the node "beeping", then I can locate the "beeping" node.
 
This application sounds similar to PathPing or MTR, but are actually different.
 
Anybody is aware of this type of application/utility, or let me know if there is a simple solution to develop one?
 
Thank you!

---

