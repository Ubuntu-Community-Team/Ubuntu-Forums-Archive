---
title: "Koala vs Broadcom"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by DaleFarrell on 2009-11-22
Well I searched and tried different tutorials and no luck.
I may have enabled fwcutter and ndiswrapper.
Card is bcm4306 rev 03, in an old emachine laptop.
WICD will find all nearby routers.
I can login to mine, and get past the validation phase, but it hangs on 
getting an IP.
This is farther than I could get with Jaunty, so I am hoping someone can
help. Dale in Seattle

---

### Post by VraiChevalier on 2009-11-22
Did you see this on the Wicd site?
<quote>Troubleshooting
If Wicd fails to connect after you install it, make sure that the only entry in your /etc/network/interfaces file is

    auto lo
    iface lo inet loopback 

You can change the contents of this file by pressing alt + f2, then typing

    gksudo gedit /etc/network/interfaces

if you are using Gnome, or replace gedit with kate if you are using KDE. This will allow you to view and edit the /etc/network/interfaces.You can ignore lines that start with #. </quote>

I just now installed Wicd on an Acer Aspire One with the Broadcom BCM4312 802.11b/g and it worked very well after I managed to type in the correct passkey.

---

### Post by DaleFarrell on 2009-11-22
Read out is as you suggest. thanks. still no ip.

---

