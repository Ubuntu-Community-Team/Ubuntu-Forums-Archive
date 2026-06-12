---
title: "Help with proper commands for NAT?"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by wakkawakka on 2010-12-13
Hello!  I'm really, really hoping someone can help me with this...

First of all, I'm running Linux Mint 10.

I have one ethernet card in the machine (eth0) and a Linksys wpc 11 wireless card (wlan0).

Using this card and hostapd, I'm trying to use my laptop as a wireless hotspot (yes, I'm 100% certain I want to do this).

So the setup I hope to have in the end is 
router--->linux box--->wireless devices

I'm able to put the card in master mode and assign it an ssid just fine,  so that it's visible to devices wishing to connect to it.  

However, I'm having a lot of trouble making wlan0 and eth0 talk to each  other, so that traffic from wlan0 is passed through eth0 and to the  internet.  

Bridging (using brctl) between wired and wireless interfaces doesn't  work by all (most?) accounts, and it hasn't worked in my case. 

I've tried using Firestarter to bridge the connections.  But trying to  share the connection between eth0 and wlan0 kills my connection to the  internet just as well as brctl does.  

So that brings me to setting up NAT, which appears to be the recommended solution.  

I've found A LOT of variance in the commands used to do this, and I haven't gotten it to work yet.

If someone could tell me what the proper commands would be to make it so  that data from wireless devices connecting to wlan0 goes to the  internet and back through eth0, that would be wonderful.  

What would be doubly wonderful is if someone could tell me what  commands/method I could use afterward to determine if the commands were  applied successfully and to see if they're working properly.   

I'd really appreciate help with this.  I'm very new to linux, and I've  been struggling with this for days, and I'm on my third linux reinstall  now.  

Thanks a lot in advance.

---

