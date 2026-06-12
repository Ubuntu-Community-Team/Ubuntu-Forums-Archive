---
title: "problem with accessing samba shares from workgroup and domain"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by hspijker on 2010-11-05
Hi,

We have a local network with a windows 2003 server. All users have windows machines (XP, Vista or windows7) and log on in a windows domain (controlled by that server). Recently we installed a linux server and Samba was successfully joined in with Active directory. Users could access(read; write) shared  folders on the linux machine.

However, some users do not login on the domain. They login locally on the windows computer (in the windows workgroup). From that they are able to access the shares on the windows2003 server. The user name and computer is known on the server and in active directory.
Now the problem is that those users (logged in locally) cannot access the samba shares on the linux server. They do get a pop-up asking for a username and password, but their username and password is not accepted.
A similar or the same problem exists when someone is connected to the server via a VPN connection. Also then a user cannot access the samba shares, but has no problem accessing the windows shares.

What we would like is that if users do not login on the domain they should still be able to access the samba shares, and preferably have the same permissions in that folder as configured with active directory.
Can someone help me with this problem? Thank you in advance!

Yours Henri.

---

