---
title: "How to suspend network interface r8169"
date: 2012-07-09
forum: Networking &amp; Wireless
---

### Post by ppgus on 2012-07-09
Hi everyone, im using a Toshiba Satellite M645 with powertop to save energy, when i'm using the wireless network the eth0 network interface (wired) is on too and I see it consumes 9 Watts according to Powertop.

How can I turn off the NIC or what can I do to save energy and decrease the discharge rate of the battery?

Thanx

I'm using Ubuntu 12.04 and here is my screen capture

---

### Post by alex008 on 2012-09-01
I have the same problem on my hp-dm1 laptop. Powertop reports that the r8169 card consumes 730mw even though the interface is not in use (and the cable is unplugged). I can disable the card manually by running: 'sudo ifconfig eth0 down'. 

Unfortunately, I still haven't figured out how to do it automatically. The system is able to detect the link status correctly ('sudo ethtool eth0'), however for some reason is not putting the card into power saving state...

---

### Post by ppgus on 2012-09-03
Thankyou so much, it worked for me, searching on internet I found this to do it automatically:

[http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html](http://www.upubuntu.com/2012/01/how-to-disable-your-network-adapter.html)

---

