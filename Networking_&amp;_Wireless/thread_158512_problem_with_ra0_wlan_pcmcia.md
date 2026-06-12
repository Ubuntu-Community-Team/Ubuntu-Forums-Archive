---
title: "problem with ra0 wlan pcmcia"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by phyre-x on 2006-04-11
hi i've got little idea what im doing but installed ubuntu 5.10 on my laptop with a pcmcia ralink based wlan card, ubuntu knows its therre (appears in network setting's), i followed these instruction and setup for my wpspsk network

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)

got to the line which says

sudo ifdown ra0 && ifup ra0 , done that and i get an error

ifdown: interface ra0 not configured
ifup: failed to open statefile /etc/network/ifstate: permission denied

as i dont really have much idea about ubuntu yet i was hoping there would be a simple solution so i can get my notebook online.

many thanks in advance for any help, Phyre

---

### Post by phyre-x on 2006-04-11
seems to be working fine now, refollowed instructions but ommited the recent changes from 1996 (me thinks date is slightly out). all seems well and i even got ndiswrapper to work for my integrated card too.

---

