---
title: "Wireshark Monitor Mode"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by ctbuzzy on 2013-04-26
I debated posting this because it has been addressed already at some level, probably more than once. But I've scoured as best I could & didn't find a discussion that solved my problem. So any help would be appreciated. 

Anyway, I can't seem to get Wireshark into monitor mode on Ubuntu. I'm using it on 12.04 in a Virtualbox VM (with a Win7 host). I've got kernel 3.5.0 & Wireshark v. 1.6.7. I'm using an Alfa AWUS036H adapter with an 82540 gb ethernet controller driver. The adapter is 802.11bg.

So I put the adapter into monitor mode using the following commands:

sudo ifconfig wlan0
down sudo iwconfig wlan0 mode monitor

Yet when I go to capture, "capture packets in monitor mode" is still grayed out.

Here's what the Wireshark wiki has to say:  "If it is grayed out . . . if it is an 802.11 adapter, either the adapter does not support monitor mode, the adapter's driver does not support monitor mode, or there's a bug in libpcap causing it not to think the adapter and driver support monitor mode."

I know the adapter supports monitor mode. I'm not familiar with the driver, but I'm able to put the adapter into monitor mode using command line, so that would seem to be compatible, too. All that's left is a bug in libpcap - but that seems unlikely. I keep another Ubuntu VM for testing various issues, & I have the same problem there.

Am I missing something? Are my commands wrong? If there is a bug in libcap, are there any suggestions for debugging? Apologies if I've missed something obvious. Thanks!

---

### Post by erik-vrf on 2014-04-14
[FONT=arial black]I have the same question and cannot find an answer anywhere[/FONT]

---

### Post by wildmanne39 on 2014-04-14
Thread closed. Please do not post in old threads.

---

