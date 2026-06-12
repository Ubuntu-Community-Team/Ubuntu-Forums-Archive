---
title: "Netgear WG111T USB - Can't Connect to Router"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by gotlisch on 2009-09-26
Hi there,

Just recently managed installed my **Netgear WG111T USB Wireless Dongle **on my fresh copy of Xubuntu. The dongle works just fine and I can find my wireless network using the GNOME Network  Manager.

What I **can't **do however is to **connect to the router**. When I tried to connect I'm prompted for password (as expected) and Xubuntu then sets about trying to establish a connection but after a minute or so I'm just prompted for the password again.

I am ***100% sure*** I'm using the right password and I've even tried to set my router not even to require a password for connection as well as trying every authentication method supported (WEP, WPA, WAP2, etc.) but ***nothing works!***

I've found many threads on similar topics but non of the tips found there seem to do the trick...I'm getting *really* desperate now as I'm keen to do away with Windows but unless I can get my Wireless Internet to work I'm forever confined to being Microsoft follower.....:(

Help!

/Mika

---

### Post by DFlame on 2009-09-26
I think you should use ndiswrapper to get this working properly. I've used it before so I should be able to walk you through.

Lets get some specific information and prepare the system. Open a Terminal window and enter these commands:

```
sudo apt-get install ndisgtk
lsusb
```

Post the output of lsusb here, so we know exactly what we're dealing with :)

---

### Post by gotlisch on 2009-09-27
Hi there,

Thanks for your reply but that isn't my problem...I've already installed ndisgtk which worked like a charm. I've also manged to install the drivers and they run every time a start the computer. My problem is that I can't connect to my router...I find it, but just doesn't connect.. :-(

---

### Post by DFlame on 2009-09-27
Aha, that fast forwards things somewhat. Did you use the same drivers as the ones located [here](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WG111T)? There's two sets to load apparently.

In the meantime, lets see what

```
lsusb
```
and
```
sudo ndiswrapper -l
```

give us :)

---

### Post by Gordaen on 2009-09-29
Same problem with a slightly different Netgear USB adapter (WNDA3100).  It worked fine in Ubuntu 8.10; now it can show the wireless networks that are available and attempt connection, but it never succeeds.

Output of lsusb shows this for the device:
Bus 001 Device 004: ID 0846:9010 NetGear, Inc.

And ndiswrapper -l is:
arusb_xp : driver installed
        device (0846:9010) present

---

