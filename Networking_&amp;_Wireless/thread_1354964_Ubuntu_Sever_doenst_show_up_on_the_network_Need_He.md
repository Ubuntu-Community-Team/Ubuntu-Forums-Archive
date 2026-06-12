---
title: "Ubuntu Sever doenst show up on the network Need Help"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by CheresZabor on 2009-12-14
Hello,
i'm having some issues with my file server that runs Ubuntu Server 9.10. 
So problem is this, i can access the thing by manually entering the IP address into windows explorer, however, it is not discoverable by any of my computers. Furthermore when i try to access it through its "name" or computer alias it also does not respond. 

Is there a way to fix that?

Thanks

---

### Post by MaindotC on 2009-12-14
What do you mean when you say "it is not discoverable"?  As for the name of the machine - you'll only be able to acces it via IP address unless you are running a WINS or WinBIND server, or if you have some host configuration file on Winblows that tells the winblows machine what IP address is associated with the name of the Ubuntu machine.

---

### Post by CheresZabor on 2009-12-15
Im sorry i dont really understand, 
the WinBIND server is supposed to run on the Linux machine or the windows machine. if its the linux machine could u explain how to start it and configure it.

Tnanks

---

### Post by Iowan on 2009-12-15
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To is more directed at mounting Windows shares on an Ubuntu box, but Problem 2 - Part 2, and Problem 3 cover netbios names and Winbind/nsswitch.conf.

---

