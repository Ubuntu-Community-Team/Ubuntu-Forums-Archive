---
title: "Home network"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by marcopalla on 2009-07-09
duoble posting after 2 days no answers on beginners forum :-k

at home I have two ubuntu computer connected to an ADSL modem (Pirelli Voice), Internet connection works well for both, but
I'd like to share a folder each to copy files among them.

But I never see any shared folder in the network link on resources (only not working "windows network"):

i try to set on both pc cards  in the networking applet (wired connection)
with classic parameter: IP subnet etc. etc.
but everything I set instead of roaming mode the card doesn't work anymore (no Internet too)

I tried also ifconfig configuration, but nothing seems to happen...
some help my friends?

m.

---

### Post by sgian on 2009-07-09
Sounds similar to my networking problem, but I have internet.  If your internet used to work, can you change the settings back to what they originally were?

---

### Post by marcopalla on 2009-07-09
^^^ yes, yes I set back to roaming mode on both pc and everything works, everything but to view shared folders,

m.

---

### Post by chipppy on 2009-07-09
I'm no guru by a long shot.  The only thing I know about static ip addressing is that the last of the  digit numbers have to be different.
XXX.XXX.XXX.XX2 and XXX.XXX.XXX.XX1
Does this help any

Cheers
chipppy

---

### Post by sgian on 2009-07-09
Try following the instructions here [https://help.ubuntu.com/9.04/internet/C/networking-shares.html](https://help.ubuntu.com/9.04/internet/C/networking-shares.html) to share the folders.

nPing the other computers by opening Terminal and type ping x.x.x.x (the x's are for your ip address).   If you can ping the other computers, then go to places->computer and toggle to the text based location bar.  Type in smb://x.x.x.x for your ip address and see if it opens that way.

---

### Post by alexlafreniere on 2009-07-09
First off, do you know the difference between a modem and a router? Do you know which one you have, or if your hardware works as both, like most models provided by the ISP? If your modem does not work as a router, then you can't make a connection between your two computers because you have no network and are simply sharing the Internet connection between them.

---

### Post by MuddBuddha on 2009-07-09
Have you set up sharing for the folders you want to share?

Just right click the folder, (Public folder in your Home directory works best) and select, "Sharing".  It will install the necessary files and configure each PC to share across the network.  Then you should see, "XXXXX-Desktop, XXXXX-Laptop" opr something similar on the network.  Make sure you select Read/Write access if you want to pass files back and forth.

---

### Post by marcopalla on 2009-07-09
@sgian
nothing on smb://ipaddrs front and ping front
as said if I don't set option "roaming mode" card doesn' work 

@muddbuddha
yes on samba/sharing front is all installed/shared

@alexlafreniere
yes is a router too,
maybe I have to work on modem/router settings, IP intervals of the lan are well setted,
but maybe I have to open ports or other?? like in settings of the image below in the guide??

thanx for every suggestion!
[IMG]http://assistenza.tiscali.it/voce/guide_test/pirelli/configurazione/img/virtual_server.gif[/IMG]

---

### Post by Iowan on 2009-07-09
If you're sharing between Ubuntu machines, you can consider [NFS]("http://ubuntuforums.org/showthread.php?t=249889")

---

