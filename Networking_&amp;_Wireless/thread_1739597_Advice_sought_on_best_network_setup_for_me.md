---
title: "Advice sought on best network setup for me"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by drew boardman on 2011-04-26
Hi 

I would like to setup a home network.  Ideally to save my files, including 000's of photos, to stream my music, to have backups. 

So I am looking for some advice given my setup and equipment I have on the general idea on how to go about it.  Installing server software etc I'm sure I'll find on separate questions and answers in the forum. 

I would like to access it from Linux netbook, my old Windows machine, my wife's windows machine and my Iphone (if possible) and to be able login remotely. Is this SSH Putty?  Mail is not  important as I get it via Google mail.

At present I have a combined router/wifi/ADSL box (for those of you in France its a Sagem BBox) to which we connect wirelessly or via Ethernet depending where we are in the house.  It has 2 USB ports and 4 Ethernet ports. 1 to the Ethernet cable in the study where we work,  1 to a VOIP phone, 1 to the television and 1 spare.

At present I backup via USB to a 600GB HDD. It takes ages!

I have another 500GB USB HDD, a spare 80GB mini computer designed to be a server but its been wiped of software, kindly donated, and a spare Netgear Wireless ADSL Router (DG834G v2)

Thanks in advance for the comments and advice.

Drew

---

### Post by headvampyre@hotmail.co.uk on 2011-04-26
You could use an old box as a Server :) youd be able to access the content from the iPhone if you used HTTP/WebDAV, but thats pointless.

Look around for an old computer or an older server, there powerhouses at low prices :)

Then you wanna install Samba, bump up the RAM to around 2Gigs if the macghines capable, and use reliable hard disks. 

For remote file access, you could use ssh, you could just use that altogether in fact, but im not sure SSH plays that well with windows.

If you go for Samba, and want SSO (Single Sign On), you could always use Samba4 and a VPN server, theres guides to that here:

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

Hope this helps :)

---

### Post by Lars Noodén on 2011-04-26
> **drew boardman said:**
> 
I would like to access it from Linux netbook, my old Windows machine, my wife's windows machine and my Iphone (if possible) and to be able login remotely. Is this SSH Putty?  Mail is not  important as I get it via Google mail.

Samba would be the way to go for that.

---

