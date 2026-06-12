---
title: "LAN with all ubuntu computers"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by sgian on 2009-07-09
Right now I have a network with three ubuntu 9.04 computers.  Two have a dual boot with windows xp, one is just ubuntu.  Two of the computers are at least 4 years old, one is a dell I bought a year and a half ago.  

The dell opens "windows network" fine but only shows another computer if it is running windows.  The older computers get an error box saying "Unable to mount location; failed to receive share list from server" when I open the windows network icon.  They all connect to the internet fine, and they can all ping each other.

So how do I fix the error box on the two older computers, and how do I get the dell to see the other computers running ubuntu?

---

### Post by lisati on 2009-07-09
Have a look here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting)

---

### Post by sgian on 2009-07-09
> **lisati said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+troubleshooting)
thank you for the response, but my problem is between the ubuntu computers.  My limited knowledge makes me think that the link is for networking with windows.

---

### Post by lisati on 2009-07-09
> **sgian said:**
> thank you for the response, but my problem is between the ubuntu computers.  My limited knowledge makes me think that the link is for networking with windows.

It can be used for all-Linux networks too.

---

### Post by sgian on 2009-07-09
I followed the instructions using my dell, but there has been no change.  The dell can open windows network but sees nobody, and the older two computers get the error message when trying to open windows network.

On a related issue while I still had windows running on one of the computers, somebody told me to use smb://x.x.x.x in Nautilus, and that worked to access the windows machine.  Is there a similar command in Nautilus for connecting to ubuntu machines?

---

### Post by sgian on 2009-07-09
I've been wondering if the two older computers are so old that they they aren't supported anymore by ubuntu.

---

### Post by sgian on 2009-07-09
just got one of them to work, had to use the shares-admin command to share the files and load something, then use the smb:// command to get access.

---

### Post by ptn107 on 2009-07-09
If all your computers on the network are Ubuntu, then I wouldn't use samba.  In your case I would use NFS[1].

[1]http://nfs.sourceforge.net/nfs-howto/

---

