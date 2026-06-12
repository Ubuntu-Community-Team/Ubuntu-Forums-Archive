---
title: "HowTo install Network Driver for Intel Pro10, Pro100 and Pro1000 Adapters"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by ACarib on 2006-04-14
Hi,

Can anyone advise how to install the appropriate driver? I just installed Ubuntu on my system. During the installation Ubuntu informed that it did not detect my network adapter.

How can I attempt to detect the Adapter? How do I install the appropriate driver of an Intel Pro10, Pro100 and Pro1000 Adapter?

If anyone can give me some direction on howto proceed, appreciate it greatly....

Tks.

---

### Post by cilynx on 2006-04-14
Check 'lspci' or the graphical device manager to make sure your net card is seen at all.  My lspci output gives me this:
```

0000:02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)

```
among a bunch of other stuff.

Gigabit Intel is handled by the e1000 module.  You might want to check lsmod to see if it loaded.  (This card should be detected out of the box, just FYI)  If it didn't load, you can 'modprobe e1000'.  I believe the Intel 10/100 cards are handled by the e100 module, but don't quote me on that.

Good Luck

---

### Post by EriK76 on 2006-04-14
This works 

[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

---

### Post by s.mcclatchie on 2006-04-25
Hello 

I have recently installed breezy badger version of ubuntu on a Toshiba
Satellite pro 100 with an Intel Pro 1000 gigabit ethernet card. As
reported before in this forum, the network adaptor was not found
during instllation. I followed the instructions in
<http://www.ubuntuforums.org/showthread.php?p=741687> to install the
appropriate driver. Modprobe e1000 seemed to be accepted, but the card
is still not detected on reboot.

sudo pppoeconf gives
... no working ethernet card can be found. ...

The /system/administration/networking gui does not show an ethernet card.

lspci gives ... Ethernet controller: Intel corp: unknown device 109a

My /ect/modules is
#...
#...
#..

lp
mousedev
psmouse
sbp2
e1000

My /etc/interfaces is
 #...
auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider dsl-provider

auto eth0
iface eth0 inet dhcp
name Ethernet LAN card

Connection properties: lo is receiving and sending packets

I'm stuck -- why is the ethernet not being detected or activated, please?

Best fishes

Sam

---

