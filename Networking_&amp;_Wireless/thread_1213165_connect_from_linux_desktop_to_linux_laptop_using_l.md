---
title: "connect from linux desktop to linux laptop using lan cable"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by kmaster228 on 2009-07-14
hello all
i just bought a new laptop and i want to move my files from my desktop to my laptop and it will take me ages using a usb so i want to use a lan cable, so basically i have one ethernet connection coming from a router spliting the connection between my brothers desktop and mine. so i have one ethernet connection that can be plugged into either my laptop or my desktop and i also have a lan cable and i want to be able to transfer files from my desktop to my laptop (which has internet), so how will i be able to do this?

---

### Post by kmaster228 on 2009-08-21
bump ( come doesnt any body have any answers?)

---

### Post by Iowan on 2009-08-21
:oops: 
Oops... must have been a busy day. Does you router have any extra connections? Reason for asking: If you do a direct connection, you will probably need a crossover cable (some new cards can figure it out by themselves). Secondly, you will need to configure a static address on each machine (unless **avahi** kicks in - like it should) - in the same subnet. Then you'll need to install a server of some kind on your desktop - what kind depends on how you want to transfer the files.  You have options of [SSH/SSHFS]("https://help.ubuntu.com/community/SSHFS"), [NFS]("http://ubuntuforums.org/showthread.php?t=249889"), Samba, and [FTP]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html") - to name a few. The laptop probably already has the client for all of the above. Samba is a bit complex, but I can provide links if you choose to go that way. [Here]("http://ubuntuforums.org/showthread.php?t=218630") is another FTP How-To.

---

### Post by kmaster228 on 2009-08-23
thank you iowan you are very helpful and have helped me on alot of my other treads, im not quite sure whether i am using a crossover cable or not but i know it is a lan cable, umm yes my router has an extra port but my laptop has a port for and ethernet cable and a lan cable so basically is there a way to plug in the ethernet cable in to my laptop and then use the lan cable to plug into my desktop, and i could ftp, but which is the easiest and what about the application giver, and how would i go about making static ips on each computer? 
btw thanks again

---

### Post by Iowan on 2009-08-23
[Here]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable") is a picture of crossover cable - in brief, if you look at ends, the colors will match on standard ethernet cable, they are different on a crossover.
> **kmaster228 said:**
> ... my laptop has a port for and ethernet cable and a lan cable so basically is there a way to plug in the ethernet cable in to my laptop and then use the lan cable to plug into my desktop,  One of us may be confused about the difference between an ethernet cable and a LAN cable. Is one of them a modem connection (4 pins rather than 8 )?

---

### Post by general_fault on 2009-08-31
get a crossover cable  then 


pc 1 : 
 
 sudo ifconfig eth0  192.168.1.1 netmask 255.255.255.0 up 
 
install vsftpd... (check [http://ubuntuforums.org/showthread.php?t=91887](http://ubuntuforums.org/showthread.php?t=91887)) 

 
 sudo /etc/init.d/vsftpd restart 
 
 
pc2 :  
 
run filezilla, enter address 192.168.1.1, username and password so we can access pc1... 
_________________

have a nice day :popcorn:

---

