---
title: "Ethernet drops out"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by LaptopU on 2013-06-22
I had a software update this morning (on 13.04), since then I'm having problems connecting to the network.  Every so often the connection will drop saying it is disconnected, then several attempts are made to reconnect without success.  After disabling and re-enabling networking it sometimes fixes the problem, it sometimes does not.

This has only been happening this morning.  It may be a coincidence but one of the things that updated was Wireshark.

Can anyone help me shed light on this problem please?

---

### Post by gordintoronto on 2013-06-22
This is Ethernet, not WiFi?

Perhaps you could mention what your Ethernet adapter is. Copy/paste from lspci.

---

### Post by feardotcom on 2013-06-22
Kind of seems like a driver problem. I could understand also if it was a software problem, like wire shark, but if it was trying to send packets out larger than your router would allow then i think it would make it sense though the internet was disconnecting and reconnecting. Wireshark could also be blocking packets from getting out, and i'm not sure if wireshark has the ability but it could it be sitting there pinging the router over and over and it could be freaking out your router. I'm not real familiar with wireshark. If it was wifi then i would say driver problem. Wifi isn't near flawless like Ethernet is.

If you're using ethernet couple of things you can do real quick is just make sure all of your cables are properly connected and no loose connecting. Anything could loosen your ethernet cable. A cat getting behind your computer for the heat. A rat for the same reason, a dog, a child, anything really.

---

### Post by LaptopU on 2013-06-23
So far it hasn't disconnected me since yesterday so I'll put this issue on ice (hoping it doesn't return).  Nothing has been near my desktop to dislodge a cable but I've re-seated it just in case.  Hoping it's one of those things which is no idea why it happened but it doesn't happen again :D

---

### Post by feardotcom on 2013-06-24
Yeah always check for the simple solutions first, They're quick to check and easy to fix. Sometimes the simplest things are the cause to the biggest problems, in networking anyway.

---

