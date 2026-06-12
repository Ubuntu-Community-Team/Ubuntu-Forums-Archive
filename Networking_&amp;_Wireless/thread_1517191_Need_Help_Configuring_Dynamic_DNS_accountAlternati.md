---
title: "Need Help Configuring Dynamic DNS account/Alternatives"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Serpher on 2010-06-24
I have a computer in my home connected via Ethernet cable through a router running Fedora 13, and a laptop running Ubuntu 9.04 (Broadcom WiFi card issue). I would like to be able to SSH, and use the sftp and/or scp commands to transfer files from my computer to my laptop when at another location. I've tried making a dynamic DNS account but I've haven't been successful in getting it to work. Would somebody be so kind to give me a step by step guide on how to accomplish this?

Also I know SSH uses TCP port 21 or 22, and FTP uses 21 or 22 as well but I'm not sure if it's the same as SSH. Would I have to port forward my router to allow SSH access to my computer, and would I have to open a port to use SFTP or scp?

Thanks!

---

### Post by pricetech on 2010-06-24
You'll probably find your best help at whatever site you're getting your dynamic DNS from.

Yes you will have to forward a port in your router to be able to connect to your computer from outside your LAN.

SSH uses 22, FTP uses 21.  You probably don't want to open a port for FTP since you can transfer files over SSH just fine.

Install fail2ban (in the repositories) before you open the port.

---

### Post by Serpher on 2010-06-24
Thanks for the help and that program defiantly looks useful. Also if the command sftp uses the FTP or SFTP protocol, I really want to open that port because sftp is just so much easier than opening 2 terminal windows and typing in long commands to transfer a file using scp. Not to mention I could just run my PC at home as an FTP server and transfer files through gFTP.

If anybody on this website could give me ah and though with dynamic DNS or any other way I could go about solving my problem. It would be appreciated.

---

### Post by pricetech on 2010-06-25
> **Serpher said:**
> I really want to open that port because sftp is just so much easier than opening 2 terminal windows and typing in long commands to transfer a file using scp.

Places - Connect to Server.  Choose SSH as the service type.  Piece of cake.

What dynamic DNS service are you using, or trying to use ??

---

