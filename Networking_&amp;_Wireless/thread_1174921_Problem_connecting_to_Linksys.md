---
title: "Problem connecting to Linksys"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by smalljaws on 2009-05-31
I am not real computer savy. I am trying to "hardwire" a gateway (ELP 500s) running Ubuntu 9.04 to a an existing Linksys WRT54GS. I am new to Linux and the computer is running on a brand new harddrive with nothing, but Ubuntu 9.04 installed. I would think I could just connet the ethernet cable from the computer to one of the Linksys ports, but that does not seem to work.
 
The computer seems to think it has a connection, but I can't get online, nor can a connect directly to the WRT54GS by typing 192.168.1.1 into the browser.
 
Thanks

---

### Post by expelledboy on 2009-06-01
Is the Linksys running as a DHCP server or is there one on the network?

If there is right click the network-manager applet, edit connections, and remove all the existing connections.. restart.

It should automatically pick up all the relevant information for a connection. If you still have problems follow [[COLOR="MediumTurquoise"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1167304")..

Also make sure you havent plugged your pc into the WAN port on the linksys.. #-o

---

