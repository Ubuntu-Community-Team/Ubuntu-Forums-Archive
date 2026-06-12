---
title: "no saound card found"
date: 2009-09-20
forum: Multimedia Software
---

### Post by Terraman on 2009-09-20
Dear Ubuntu Friends,

I haven't sound in my elderly laptop OS: Ubuntu 8.10

```
herman@laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...

```

It worked fine some years ago with Windows 98.

Can anyone help me?

Thanks in advance.

---

### Post by Yellow Pasque on 2009-09-21
What sound device do you have? Please post output of:
```
lspci
```

---

### Post by Terraman on 2009-09-26
> **Temüjin said:**
> What sound device do you have? Please post output of:
```
lspci
```
Temûjin:

> herman@laptop:~$ lspci
00:00.0 Host bridge: OPTi Inc. 82C701 [FireStar Plus] (rev 32)
00:01.0 ISA bridge: OPTi Inc. 82C700 [FireStar] (rev 31)
00:10.0 USB Controller: Compaq Computer Corporation ZFMicro Chipset USB (rev 06)
00:11.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:11.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:12.0 VGA compatible controller: Chips and Technologies F68554 HiQVision (rev a2)
00:14.0 IDE interface: OPTi Inc. 82C825 [Firebridge 2] (rev 30)
05:00.0 Ethernet controller: 3Com Corporation 3cCFE575BT Megahertz 10/100 LAN CardBus [Cyclone] (rev 01)


---

