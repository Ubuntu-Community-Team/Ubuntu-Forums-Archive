---
title: "Absolute beginner noob, wifi help!"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by Crunky944 on 2011-01-08
Hi all, I installed Ubuntu 10.10 64bit on my machine a couple of days ago. The install seemed to go okay, I have a dual boot setup with windows 7(what I'm using to access the forums from).
Anyways, I can see wireless networks fine, but I cannot connect to them. When I try to connect, it just sits there connection forever and nothing happens... If its an encrypted connection, it does the same thing, but eventually asks for the key again. If I re-enter the key, the cycle starts all over again. I am using an Asus PCE-N13 wireless card.

I tried looking through the forums for an answer, but as the title says; I'm a complete noob... This is also my first time using any version of Linux, ever. Thanks for your patience and any assistance.

---

### Post by Crunky944 on 2011-01-08
Back to top :D

---

### Post by Bucky Ball on 2011-01-08
Welcome to the forums!

Right click on the network icon, Edit Connections >Wireless and put your details in there: ESSID, security key (WEP, WPA, whatever) and make sure IPv6 is set to 'Ignore', unless you're using IPv6 of course. 

You will need to get in to the router configuration to get these details if you don't know what they are. Works okay on a wired connections? You have all correct drivers and firmware installed? Plug in a cable and get online, then System >Administration >Synaptics Package Manager, search for and install 'ubuntu-restricted-extras'.

Then System >Administration >Additional Drivers. Anything in there that should be activated?

ps: It is forum etiquette to wait 24 hours before 'bumping' you're thread. ;)

---

