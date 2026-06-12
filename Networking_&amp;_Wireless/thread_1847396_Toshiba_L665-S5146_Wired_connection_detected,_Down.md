---
title: "Toshiba L665-S5146 Wired connection detected, Downloading , but can't browse"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by gotharious on 2011-09-20
Hello everyone,

I've just bought a Toshiba L655-S5146 laptop, I installed Ubuntu 11.04 and everything was working perfectly, but by the time I started using the wireless connection, the wired connection doesn't work any longer, and I have a problem with that as I need the wired connection at some places.

The weird part is, It detects the wired connection, and also When I open the transmission downloader for torrents it downloads with around 300 kb/s but still nothing else gets connected, I mean no browsing, emails, chats, filezilla, thunderbird emails, nothing... software centre, update manager, everything says I'm not connected, when I run a system testing for network, it says my internet connection is fully established

I tried different solutions on this forum, but nothing worked at all

My ethernet is Atheros ar8152 v1.1

I even tried the compact-wireless2.6 package download and install, and still didn't work

---

### Post by gotharious on 2011-09-21
anyone..???

---

### Post by gotharious on 2011-09-23
Ok, I just solved my problem with the wired connection

And here is what I've done.

1. Open the Network Connections
2. Double click on the wired connection
3. move to IPv4 tab
4. type in your DHCP client ID  ( Mine was 192.168.1.14)

If you can't figure out your DHCP Client ID, then just plug your cable into any windows os pc or laptop, open your status -> advanced (where it lists your gateway and IP) --> details (you will find the DHCP Client ID in the last line)

Sorry, I'm not an expert, but this is how I solved my problem (Caveman approach tho :D ) hope it help you

---

### Post by gotharious on 2011-09-24
Once again my wired connection started not working, I can still download using Transmission for torrents but can't browse... checked one of the computers around me, trying to see if there is any difference between my connection and its, so I found that the other is using Google's public DNS to connect  8.8.8.8
which you can find more info about here [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

I changed my settings to Automatic (addresses only) and changes my DNS settings to 8.8.8.8 and now it's working perfectly

Just thought about pointing that out

---

