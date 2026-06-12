---
title: "After fresh install, no internet"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by ganewbie on 2010-09-04
After a fresh Ubuntu 10.04 install, no internet for some reasons.
here is what I have in ECT/network/interfaces
 
auto lo 
iface lo inet loopback 
 
Here is the results of sudo dhclient:
 
gaubuntu@gaubuntu-desktop:~$ sudo dhclient 
[sudo] password for gaubuntu: 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [_[COLOR=#0000ff]https://www.isc.org/software/dhcp/[/COLOR]_]("https://www.isc.org/software/dhcp/") 
Listening on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
No DHCPOFFERS received. 
No working leases in persistent database &#8211; sleeping.
 
What can I do?!!!

---

### Post by ganewbie on 2010-09-04
Can somebody help please,
I have a feeling from reading lots of sites that I need to edit ECT/network/interfaces

from:
auto lo 
iface lo inet loopback 
TO:
auto lo 
iface lo inet loopback 
auto eth0
iface eth0 inet dhcp

 
How do I edit it and save it? I tried but the system does not allow me to save.
Help please!!

---

### Post by UncleClover on 2010-09-05
I didn't see anyone reply, so if they did I apologize for the redundancy. To make the command work, you have to go to the directory in which the interfaces file lives, and type this:

sudo gedit interfaces

Ubuntu doesn't permit persistent "su" privileges, I've found (I'm still somewhat new to it, myself), so you sort of need to get used to prefacing a lot of commands with "sudo". If you're a terminal junkie like me, and you prefer interfacing with your system via a terminal window instead of a gui, you (and I) should probably brush up a bit on sudo, as good understanding of that seems to be the key to "Ubuntu bliss". ;-)

---

### Post by ganewbie on 2010-09-05
Excellent the edit works, thanks a million.
However the interfaces filehas been modified, I am still have no luck.
When I try "sudo ifdown eth0"
I get:
"ifdown: interface eth0 not configured"
Do not know why, it says that as it was configured under Network Connections, but the network connection is empty. Try to edit it but no luck what is the trick to the add function in "Network connection"
Help please!!

---

### Post by Iowan on 2010-09-05
Just a few scattered tidbits:
*Ordinarily*, Network Manager works for DHCP connections. If the machine won't be moved much (like a desktop), some have suggested removing Network Manager and using */etc/network/interfaces* instead. Interfaces configured there *shouldn't* be controlled by Network Manager (by default - but you can tell it to control them). Only interfaces controlled (managed) by Network Manager appear in it's list - although they might still work. After you modify */etc/network/interfaces*, you will need to restart networking (or reboot) for the changes to take effect.

[This]("http://www.psychocats.net/ubuntu/graphicalsudo") article recommends using **gksudo** with a graphical editor (**gedit**).

---

### Post by ganewbie on 2010-09-05
Thanks for the explaination.
If I understood you correct then it is either "Networks manager" or the "interface file", is it correct?
No for desktop you suggest that I remove the Network manager and setup the interface file, what do you suggest as I am down for a while and formated the hard drive just to get this to work but no luck so far.
Please note that during the thousands reboot I had since last night the internet was working in couple of incident but I have no clue how or why?
Help please!
 
@ Iowan: Update 1.
 
You are 100% correct, when I deleted the couple of lines from the interfaces file I got "network manager" to have eth0 as before. Now I am not sure what is the best way to move forward as I have no internet so far.
 
@ Iowan update 2.
 
Here is how I got the internet to work. 
"sudo /etc/init.d/network-manager restart"
 
Now what do I need to do to get this thing to work on its own everytime I reboot?!

---

### Post by Iowan on 2010-09-05
> **ganewbie said:**
> 
Now what do I need to do to get this thing to work on its own everytime I reboot?!I presume the "Auto eth0" connection is set to "Connect automatically"...

---

### Post by ganewbie on 2010-09-06
> **Iowan said:**
> I presume the "Auto eth0" connection is set to "Connect automatically"...
 Thanks for the reply, under Wired:
MTU: automatic
under IPV4 method: automatic DHCP
Is it what you mean or there are other things need to be enabled to automatic?

---

### Post by Iowan on 2010-09-06
There *should* be a checkbox for "Connect automatically".

---

### Post by ganewbie on 2010-09-06
> **Iowan said:**
> There *should* be a checkbox for "Connect automatically".

Thanks for the quick response, the check mark is always there but still no luck.
I noticed that the following read disable and I have edited to enable but still no luck.
I still need help please.

---

### Post by ganewbie on 2010-09-07
I have installed WICD, still does not work automatically after a reboot. The great thing is, I can connect to the router throught a GUI and no need for the sudo command in the terminal as that is never easy for kids who do not even have the privilege for such command.
Any idea how to progress from here.
Thanks in advance,

---

