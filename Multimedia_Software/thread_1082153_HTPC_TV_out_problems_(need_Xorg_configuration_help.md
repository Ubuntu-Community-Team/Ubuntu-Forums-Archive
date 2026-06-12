---
title: "HTPC TV out problems (need Xorg configuration help)"
date: 2009-02-27
forum: Multimedia Software
---

### Post by sis on 2009-02-27
Hello,
I have some problems setting up an HTPC.
**The hardware:**
The mainboard is a [D945GCLF2]("http://www.intel.com/products/desktop/motherboards/D945gclf2/D945gclf2-overview.htm") Intel Atom dual core with integrated video card. This setup is for my living room and will be connected to an european PAL CRT via a [s-video]("http://en.wikipedia.org/wiki/S-Video") cable.
The first probably problem might be that the TV image input from the PC has to be done with an euroconector s-video adapter like [this]("http://www.scannerplace.com.au/0allothers/SCART_SVideo_100.gif") (there is no S-video entry in the TV. Yes! an old box). Is it possible that autoconfiguration of Xorg is not possible through this device?

**The software:**
I installed a minimal Ubuntu 8.04 command line version on which runs [XBMC]("http://xbmc.org/"). On my PC monitor it works perfect, but on the TV I can "see" the booting until the user is connected (actually, not very well, just in black & white). From that moment on (starting XBMC) nothing. Black TV screen.
The onboard driver is here:
```
ccb@xbmc:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

Any ideas? they would be highly appreciated.
Thanks in advance.

---

