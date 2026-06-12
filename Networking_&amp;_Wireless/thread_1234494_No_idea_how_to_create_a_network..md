---
title: "No idea how to create a network."
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Sashin on 2009-08-07
I've heard to network windows and ubuntu you are supposed to use samba, but I have no idea how to network two ubuntu only computers.

I have two ubuntu computers connected to one router and share internet, I can't transfer files, I can't share the printer.

I've searched google but to no avail.

I'd appreciate a way that was quick, simple and left terminal use to a minimum.

---

### Post by starcannon on 2009-08-08
You can use samba when networking in linux as well; though I use [sftp]("http://www.mylinuxinstaller.com/guide_ssh_fileshare.shtml").

GL and HF

---

### Post by Sashin on 2009-08-08
Does this share printers as well as files?

---

### Post by starcannon on 2009-08-08
Not sure, I have a printer with built in wifi, so its already on my network with its own IP address, indeed there is no computer actually attached to it. I'll have to go to the basement and grab up an old usb printer and check out print sharing.

Perhaps someone could answer before I go experimenting :)

---

### Post by Iowan on 2009-08-08
[NFS]("http://ubuntuforums.org/showthread.php?t=249889") is another option... dunno about printer sharing, though.

---

### Post by amac777 on 2009-08-08
About sharing a folder on the network, I think you can right-click on the folder you want to share in nautilis and select "Sharing Options" to set it up.

Also, for sharing a printer, I was able to share my printer by going to System->Administration->Printing, and then right clicking on my printer and checking the "Shared" checkbox. Also there are more details availabe in the properties for the printer.

---

### Post by superprash2003 on 2009-08-08
hope this helps [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by ladasky on 2009-08-08
I am working on solving very similar problems right now, in this thread:
 
[http://ubuntuforums.org/showthread.php?t=1234422](http://ubuntuforums.org/showthread.php?t=1234422)
 
Maybe someone will post an answer that helps you too? :)

---

### Post by swerdna on 2009-08-08
Have a look at [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by ladasky on 2009-08-08
Sashin:
 
For me, configuring Samba turned out to be the answer.  Above, superprash2003 and swerdna provided you with links to articles which helped me solve my problems.
 
Samba MAY not be installed on your Ubuntu computer right out of the box.  It wasn't in my installation of 8.04.  But if you go to Nautilus and select a folder that you want to share on your LAN (by right-clicking the folder, then selecting "Sharing Options", then clicking the "Share this folder" checkbox), you will be prompted to download the relevant software.
 
After you do that, and you restart your computer, you should be able to see the folder you made public from another computer which is running Samba.  Since you have two Ubuntu machines, obviously you should install Samba on both.
 
Now you need to turn on printer sharing.  By default, printer sharing is off.  The first part of the article linked by superprash2003 shows you exactly how -- assuming that you are using the CUPS printing protocol, and with two Ubuntu machines that seems like a good choice.

---

