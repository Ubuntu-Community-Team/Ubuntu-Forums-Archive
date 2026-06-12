---
title: "Can't connect to any Wi-Fi network with USB wireless card"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by thebronx on 2010-06-09
Hello!

At first, I would like to apoligize if my english is little poor.

I'm new in Linux world. I have installed Linux Ubuntu 10.4, because it meets all my needs, so it makes no sense to install Windows on my computer. But until I'll solve the problem, the computer is useless for me.

The problem is that connection to the internet does not work. Specifically, I did step by step what I need. By ndiswrapper I've installed drivers to my wireless card. I stopped at the moment where you see the network in range, but I can't connect to any network. I'm clicking links and entering the password. It's trying to connect for a minute or two, and disconnects. I tried typing the key in hexadecimal, I tried to turn off security - then the same thing. I have read various tutorials in which they say get to the repos for "this or that". However, the problem lies in the fact that this computer hasn't got even ethernet card, so my only way to connect to Internet is the USB card.

System: Ubuntu 10.4
Wireles card: WPN111 - RangeMax Wireless USB 2.0 Adapter.

I do not know what logs or other parameters you would like to see. If you know how to solve this problem, answer, please.
Regards.

---

### Post by 666f6f on 2010-06-09
It seems to be generally difficult to properly setup up the  WPN111 RangeMax Wireless USB 2.0 Adapter.

Have you tried the steps in this thread? : [http://ubuntuforums.org/showthread.php?t=414023](http://ubuntuforums.org/showthread.php?t=414023) they look promising.

Also, make sure you're using Ubuntu 32bit and **not** 64bit. Correct me if I'm wrong someone, but I believe Ubuntu 64bit won't play nicely with ndiswrapper drivers.

---

