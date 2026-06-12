---
title: "Networking 10 Machines With One External HD?"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-24
I have a 1TB external hard drive. I would like to create in it 10 folders:

 	Code:
 	'folder[B]1'
'[/B]folder**2**'
.......
'folder**10**' 
I would then like to permanently mount each folder to a different machine  (I have 10 machines connected through a switch, so each machine will  have a folder that is mounted to **ONE** of the 10 folders in the external hard drive).

My questions:
(1) Is this a good networking configuration?  are there better ideas to give  individual machines more space without replacing their hard drive?
(2) How do I limit each one of the folders ('folder**1', **'folder**2', ...., **'folder**10'**) so that the size does not increase beyond 100 [GB]? I don't want one folder (say, 'folder**1'**) to grow in size and 'steal' the space designated to the other folders.

How do I achieve this?

---

### Post by grahammechanical on 2010-10-24
I am not an expert. I am not telling you how to do this. I just might help move things along. 

1) The external hard disc would have to be formatted. Is this not right? Can you not also partition this drive? I think that we are limited to 4 partitions. So, one partition has to be what is called Extended Partition. This extended partition can then be partitioned itself. This action if it is correct would limit the size of each of the "folders" that you want.

2) How do you intend to connect the external hard drive to each of the ten computers? I think that the hard drive would be attached to one machine which is networked to the other nine. All these are allowed to share the folders (partitions) of this drive. How you do this I do not know. It is the direction I would examine.

Regards

---

### Post by psusi on 2010-10-24
Use LVM to create 10 different logical volumes and share them, but why do you want to give each machine its own directory in the first place?  It is more typical of a network environment to let the 10 machines boot from their local drive, then have the users all store their files on the server drive in the same place, so it's accessible no matter which of the 10 workstations they log in at.

---

### Post by csharpplus on 2010-10-25
thanks to both of you.

The machines works separately from one another. so I thought it would wiser to designate a directory for each one of the machines.

---

