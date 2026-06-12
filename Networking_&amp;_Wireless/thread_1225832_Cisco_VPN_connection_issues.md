---
title: "Cisco VPN connection issues"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Zuke24 on 2009-07-29
I'm having issues connecting to my VPN at work.  I'm using the 64bit Jaunty on my laptop.  I've installed the VPNC and KVPNC, and every time I connect I get "failed to connect to VPN because there are no vaild VPN secrets".  Now, I've heard this is an issue with the Gnome keychain not interfacing with the VPN module correctly.  I even tried it on Karmic and it worked.

However, Karmic seemed to be having crashes all the time, so I went back down to Jaunty and now I'm stuck not being able to connect to work again. 

Any ideas on what to do?

Thanks in advance!

---

### Post by Zuke24 on 2009-07-31
OK, here's where I get frustrated:

I have a Dell Mini9 running 9.04-32bit and a Netbook Remix on top of it.  It can connect to our Cisco VPN just fine.  I'm not sure how, since when I first installed it, it couldn't.  I'm assuming some update has happened where it now can (gave the "No Valid VPN Secrets Error").

I also have a Lenovo X61 running 9.04-64bit.  It can't connect to the VPN.  At first it gave the same "No Valid Secrets" error, but then it suddenly worked.  Then it stopped.  Now it says it cannot start the VPN service.  What gives with the network manager in Ubuntu?  What do I need to do to fix this and get it to just work?

---

### Post by jonobr on 2009-07-31
No real solution for you, just to say I use my system here and at home for connecting to a cisco vpn by importing a pcf file through kvpnc.
I use 32 bit systems running 9.04 on both and have difference type of hardware and have not seen the issues you have 

I have seen others of timeouts and inactivity etc. but no errors like those you mention.

---

### Post by Zuke24 on 2009-07-31
Could it be the difference between 32 to 64 bit?  If so, that'd suck, since 32bit can't see all 4GB of my RAM.

---

### Post by jonobr on 2009-07-31
I dont want to jump to conclusions but given your experience and mine and thinking it may have something to do with it.

When your connecting did you try looking at your logs to see if anything jumps out?
You should have entries in kern.log, syslog and messages
Aslo, are you importing a pcf file or setting this up yourself?

Im thinking is its pcf then all things being equal its either hardware or bitOS.
Im thinking its not hardware related

---

