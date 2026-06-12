---
title: "Users, Groups, and Networks"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by AlwaysLate on 2010-06-17
Hi,
I am trying to understand the relationship between users and groups on a local network, and to be more specific, to add users from different machines on a network to the same user group.  For example:

machine name.......machine1.................machine2...................machine3
Distro/OS..............Ubuntu 9.10..............Ubuntu 10.04LTS........Windows XP
user name............user1........................user2........................user3
user group user.....user1........................user2.......................                                                              user3
user group new.....user1, user2, user3....user1, user2, user3.....user1, user2, user3

By default, the user on each machine is a member of the users group on that machine.  I want to create a group that includes all three users.
I have the operating systems loaded, a working network, Samba users set up and shares accessible, but when I use System > Administration > Users and Groups > Manage Groups > Add,  (from the Ubuntu machines) only the names of the users on the local machine are listed.  How is a user from a different machine specified?  At this time the Windows machine isn't my focus but I included it to explain why I'm using Samba.

Thanks for help with this.  I know it is a very very basic question, but I haven't been able to find the answer in terms that I have been able to understand.

---

