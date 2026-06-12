---
title: "setpci not work on soundcard"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by wilso027 on 2006-08-02
I am having problems with crackling audio when watching HD on my breezy box. I read an article that talked about pci latency. Sure enough I checked my sound card and it was set to 0. I have tried to up it using setpci and it takes my command but does not make a change. I have tried sudo the command also. Any ideas?

sudo setpci -v -s 00:1f.5 latency_timer=40

and lspci -v still showed me

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC
'97 Audio Controller (rev 02)
        Subsystem: Asustek Computer, Inc. P4P800 Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e800 [size=256]
        I/O ports at ee80 [size=64]
        Memory at f7fff800 (32-bit, non-prefetchable) [size=512]

Allan

---

