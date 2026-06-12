---
title: "Eee Pc 1000 Wireless not working"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by cogier on 2010-02-05
Hi,

I am trying to get the RT2860 card in an Eee PC 1000 to work. I have tried Ubuntu 8.04 and 9.10, all the "fixes" below I can find on the web but nothing seems to work.
 
[https://help.ubuntu.com/community/EeePC/Fixes]("https://help.ubuntu.com/community/EeePC/Fixes")
I downloaded the source code from Ralink and using module-assistant followed the instructions.

I can see the wireless network, it tries to connect but just keeps asking for the security key. I have tried WEP, WPA and no security at all but still no go. All works fine if wired. The F2 toggle seems to work OK, the WLAN is switched on in the BIOS. The "iwconfig" command shows the RT2860 in Ubuntu 9.10 but not in Ubuntu 8.04.

Any help would be appreciated.

---

### Post by cogier on 2010-02-05
SOLVED

Just in case some body need to know how to sort this problem I have had some success.

Firstly I got this to work with Ubuntu 8.04

Here is the link I found that made it happen
[http://www.array.org/ubuntu/setup-hardy.html]("http://www.array.org/ubuntu/setup-hardy.html")

The wireless does not seem to work if security is on but I am able to get it to work without security. I have used "Wireless Station Access List" that uses MAC address security.

:D

---

### Post by walt.smith1960 on 2010-02-06
Glad to hear you were able to solve your problem.  Here's a thought though-try enabling backports in Synaptic. I don't know if there are any downsides, but enabling backports helped me with wireless problems.

---

