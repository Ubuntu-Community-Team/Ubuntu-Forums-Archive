---
title: "ndiswrapper and Airgo MIMO"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by Lambert on 2006-02-09
Just recently a new version of ndiswrapper was released (v1.9)

One of the changes is added support for the airgo MIMO chipset. If you don't know what this is, it's the latest technology that's coming. It's actually a pre-release (802.11 pre-n) of the newest protocol which extends the range of wireless signal and improves transfer rates. Current 802.11g speeds max out at 108Mbs on specific dual channel cards (54Mbps on most) and the 802.11n protocol is expected to reach 300+Mbps when it is finalized.

there have already been many devices released into the market under this pre-n protocol and you may have one.

I won't recommend to rush out and buy a pre-n adaptor but if you are one that has bought one already and would like to use it on your GNU/linux pc, here's your chance to roll up your sleeves, compile the latest ndiswrapper release and see if you can get it working.

Don't believe you will get a lot of help here but you can ask and look at the ndiswrapper site or other support channels.

Change log:
* Added support for real-time preempt (RT) patch. * Added support for TNETW1450 (TI's USB chipset). * Added support for latest Windows Broadcom driver. * Added support for Airgo Networks MIMO Pre-N driver. * Added support for Intel PRO/Wireless 3945ABG driver; this driver needs 16KB   stacks in kernel. * Bug fixes.

This link will take you to a wiki page which has instructions for compiling ndiswrapper. These have not been verified as of yet with the newer version but they should work.
[https://wiki.ubuntu.com/WifiDocs/Ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Ndiswrapper")

---

