---
title: "Wireless connecting, but no webpages load"
date: 2011-02-22
forum: Networking &amp; Wireless
---

### Post by PokeTehPenguin on 2011-02-22
Hi everyone...
So last night I decided to install Ubuntu 10.10 using the WUBI installer, everything went well and it installed, but there was one problem. I didn't have any wireless networking options, so I scavenged this forum using google and came across on how to fix it using System -> Adminstrator -> Additional Drivers. I reset my laptop(Dell Inspiron 14R N4010 I believe) and to my success, I was able to join my network. So I took out the cable(The wired connection has worked since fresh install) and it didn't work... I updated using Synaptic Package Manager and restarted, hoping it would work, but it didn't.
Could someone help me figure out what is wrong with my wireless? I would prefer to have it working rather than restarting my system and using Windows 7 just to go on the Internet... Any help is appreciated!

EDIT: I also turned off the Wireless hotkey or whatever it was called in the BIOS, but that didn't do any good either.

---

### Post by uncaspi on 2011-02-23
Open a terminal and issue this command

sudo iwlist scan

See if you have any networks available. Also try 

sudo rfkill unblock

---

### Post by PokeTehPenguin on 2011-02-23
> **uncaspi said:**
> Open a terminal and issue this command

sudo iwlist scan

See if you have any networks available. Also try 

sudo rfkill unblock

Okay, so I went with a fresh install of Ubuntu and installed the proper drivers, in the network applet it scans, but the problem is it will not connect! I tried just iwlist scan, but I'll try sudo iwlist scan, because iwlist scan showed no results for anything, it said scanning was not supported.

EDIT: Alright! I got wifi able to connect and load web pages! But of course one problem after another, the web pages take a God awful amount of time to load, Google took a few minutes to load up, any way to fix this?

---

