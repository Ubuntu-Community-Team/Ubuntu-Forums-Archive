---
title: "howto - DRI &amp; Compiz working with open Radeon drivers! (tested on  X300)"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by Turin Turambar on 2007-12-03
I managed to have a working DRI (tested with gl screensavers) and compiz with open source Radeon driver. My card is ATI Radeon X300 RV370.

Prior to that, I had two choices. To have compiz, but choppy DRI support (ssavers not working) or to install fglrx and have a great DRI but no compiz.

This page helped me:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)


I fixed it with just a few options I added in xorg.inf.

```

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"radeon"
	Option "AccelMethod" "XXA"
	Option "AccelDFS"    "1"
	Option "GARTSize" "64"
 	Option "EnablePageFlip" "1"
EndSection

```

You can try EXA instead of XXA, but that restarted the X everytime I wanted to enable 3d effects (compiz). So I returned to XXA.
Also do not use the module "glx" (suggested by the DRI Wiki) - that caused my X to be in low-res mode. I also found that DRI module is not required for DRI function.

Basically, those xorg options I added were only to speed up the DRI, since I already had the compiz working (without EXA, as mentioned above).

I hope this will help others too. :)

---

### Post by sledwich on 2008-01-05
Wow thanks - I used these settings with the "ati" driver and it worked great.

I am using Gutsy with ATI X300. Thanks:)

---

### Post by Redenbacher on 2008-02-07
Which drivers are you using? The newest "fixed" ATI drivers, or the proprietary drivers through the restricted driver manager?


...I said "driver" way too many times...

---

