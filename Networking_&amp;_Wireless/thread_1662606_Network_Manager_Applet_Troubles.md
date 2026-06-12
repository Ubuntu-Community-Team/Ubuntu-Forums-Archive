---
title: "Network Manager Applet Troubles"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by hilight on 2011-01-08
Hi Guys,

I'm struggling to get the Network Manager applet to appear after I've installed Ubuntu.

I used a minimal CD image to install Ubuntu and the optional xfce4 package. After that I installed another package called network-manager-gnome. 

What I'm not sure of is why I can't see two little computer icons in the bottom right of the desktop! :confused:

Any help would be much appreciated. I'm a little new to this so go easy... :)

---

### Post by PatchesTheCaveman on 2011-01-08
You should use the WICD network manager with Xfce, unless you need to use a mobile broadband card or PPP over Ethernet (PPoE).  It doesn't have any GNOME dependencies and is designed for lightweight desktop environments like Xfce.

It's available as a package called *wicd*

---

### Post by hilight on 2011-01-09
> **PatchesTheCaveman said:**
> You should use the WICD network manager with Xfce, unless you need to use a mobile broadband card or PPP over Ethernet (PPoE).  It doesn't have any GNOME dependencies and is designed for lightweight desktop environments like Xfce.

It's available as a package called *wicd*

Hi Patches,

Thanks for your reply. wicd did the trick - the icon appears in the system tray and I can successfully connect to my wireless.

My main aim here is to share the wireless on this Ubuntu laptop to a desktop PC. Using the instructions here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) I realised that I can't use the Network Manager method and instead used the more complicated Ubuntu Internet Gateway Method. Unfortunately this doesn't seem to play nicely with wicd. Every time I bring up the wired interface using the command ```
sudo ifconfig eth1 192.168.0.1
``` I get a message from wicd telling me that it's disconnecting the wireless network that I'm trying to share!

What would be the best way to get sharing working with wicd? This was dead easy to do in Windows XP with the Internet Connection Sharing :(

---

### Post by PatchesTheCaveman on 2011-01-09
Try the method I explained in this thread:
[http://ubuntuforums.org/showthread.php?t=1655454](http://ubuntuforums.org/showthread.php?t=1655454)

---

### Post by hilight on 2011-01-10
Hi Patches,

I installed the Firestarter package but can't get past the issue where wicd only allows one network interface to be connected at any one time.

When I try to start the firewall in Firestarter I'll get an error that eth0 is not ready if the wireless is enabled. If I enable the wired networking in wicd this leads to Firestarter telling me that the device wlan0 isn't ready!:confused:

Thank for your help so far.

---

### Post by PatchesTheCaveman on 2011-01-10
Unfortunately there's no way to make wicd support two connections at the moment.  You'll have to rename the wired connection to something weird in wicd and manually configure the wired Ethernet connection via /etc/network/interfaces.

Adding this to your /etc/network/interfaces file should be sufficient for your purposes:
```
auto eth0
iface eth0
    address 192.168.1.1
    netmask 255.255.255.0
```

---

### Post by hilight on 2011-01-10
Hi Patches,

Ah I didn't realise I could make wicd ignore an interface like that. It's all set up now and working like a charm. :D

You've been very helpful; thanks for your time.

---

