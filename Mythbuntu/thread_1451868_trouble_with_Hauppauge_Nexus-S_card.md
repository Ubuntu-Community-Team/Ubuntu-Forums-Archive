---
title: "trouble with Hauppauge Nexus-S card"
date: 2010-04-11
forum: Mythbuntu
---

### Post by pec99 on 2010-04-11
Hi
I'm trying to use a Hauppauge Nexus-S card with Mythbuntu. Please note that this card already works well with Windows XP (and Hauppauge software from CDROM).

# dmesg | grep dvb
[   12.253755] saa7146: register extension 'dvb'.
[   12.255227] dvb 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.255378] firmware: requesting dvb-ttpci-01.fw
[   16.375986] dvb-ttpci: gpioirq unknown type=0 len=0
[   16.401194] dvb-ttpci: info @ card 0: firm f0240009, rtsl b0250018, vid 71010068, app 80002622
[   16.401212] dvb-ttpci: firmware @ card 0 supports CI link layer interface
[   16.449197] dvb-ttpci: Crystal audio DAC @ card 0 detected
[   16.801301] dvb-ttpci: found av7110-0.

# ls -lR /dev/dvb
/dev/dvb:
total 0
drwxr-xr-x 2 root root 200 2010-04-10 19:11 adapter0
/dev/dvb/adapter0:
total 0
crw-rw----+ 1 root video 212, 1 2010-04-10 19:11 audio0
crw-rw----+ 1 root video 212, 6 2010-04-10 19:11 ca0
crw-rw----+ 1 root video 212, 4 2010-04-10 19:11 demux0
crw-rw----+ 1 root video 212, 5 2010-04-10 19:11 dvr0
crw-rw----+ 1 root video 212, 3 2010-04-10 19:11 frontend0
crw-rw----+ 1 root video 212, 7 2010-04-10 19:11 net0
crw-rw----+ 1 root video 212, 8 2010-04-10 19:11 osd0
crw-rw----+ 1 root video 212, 0 2010-04-10 19:11 video0

# lspci -v
00:0f.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
    Subsystem: Technotrend Systemtechnik GmbH Device 0003
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at e4129000 (32-bit, non-prefetchable) [size=512]
    Kernel driver in use: dvb
    Kernel modules: snd-aw2, dvb-ttpci

# scan -cv
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.

MythTV doesn't work : it can't probe the driver

Sorry I'm a newbie.  I've already searched in Forum but found nothing. Could you help me please ?

Regards

---

### Post by pec99 on 2010-04-15
Nobody could help me ?   [-o<

---

