---
title: "3G modem with ICS, router and samba file sharing, HELP!"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by r2ramos on 2010-08-17
Hello everyone, I need your help with the following:

I recently bought a 3G usb modem to access internet at my house (no wired services where I live).  I connected the modem in my computer with ubuntu lucid, and to share the  internet with another PC in the house (which has windows 7) connected a  wireless router. The ethernet connection from the ubuntu pc goes to the wan socket of the router. This works great for internet access from any machine in my house.

The problem is that now I have no idea how to share files between computers. Before I was doing well when I could connect the modem (cable) directly to  the router and we were all on the same LAN and samba, but now my PC is the WAN,  then there is the router, then the LAN. I can not even share the printer.

Thank you give me a hand with this!

---

### Post by r2ramos on 2010-08-22
Digging around I found out that what i want is to share files with samba between subnets. The one before the router 192.168.0. ; and the one behind the router 192.168.1.

Somebody knows how to do that?

I've tried the "host allow" option in the smb.conf file, but still nothing; maybe im not doing right

here is what i added to the smb.conf

   "hosts allow = 192.168.0. 192.168.1."

Please help

---

### Post by r2ramos on 2010-08-24
I finally did it!
 
Don´t know if is the best solution, but it worked for me:
 
turned the ubuntu pc into a router, and the router into a switch. That way all the pc´s are in the same LAN, and they share internet connection and files (through samba).

---

