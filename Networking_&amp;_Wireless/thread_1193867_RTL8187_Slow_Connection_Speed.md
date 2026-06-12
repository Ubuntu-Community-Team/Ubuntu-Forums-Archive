---
title: "RTL8187 Slow Connection Speed"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by grock215 on 2009-06-22
I am trying to install the a wireless USB dongle.  It is the Rosewill RNX-G1W and is uses the RTL8187 wireless chip.

It initially worked very poorly (Very low signal strength and speed).  I installed the Jaunty backport modules and and it is performing much better.  I have full signal strength and faster speeds.

According to iwconfig, the bitrate is at a healthy 54mbps.  However, when transfering files over the network, i am only seeing about 1 MByte/s (which is 8 Mbps).  This speed is acceptable when surfing the internet, but it sucks for streaming DVDs (which needs about 16 mbps to stream comfortably). 

Is this issue with the driver i have installed?  Or is 1MByte/s all i can hope for when dealing with a wireless g network?

Thanks
Gerald

P.S. I am running Mythbuntu 9.04 (I am trying to setup a new frontend)

---

### Post by Miwers on 2009-06-27
Hi,

I read another thread about some other guy/gal having the exact same problem as you. Turned out, that it was a problem with his/her USB port not being a USB 2.0 port, and thus, his/her max. speed was theoretically 12 Mbps. That's one place to start :)

---

### Post by jurelex on 2009-08-09
Hi, I'm having the same problem, but mine is an internal wireless card in a Gateway W-350i.
When using the wireless connection, it behaves like I'm using a 1Mb/s connection but when I use the ethernet port, I get 10Mb/s

---

