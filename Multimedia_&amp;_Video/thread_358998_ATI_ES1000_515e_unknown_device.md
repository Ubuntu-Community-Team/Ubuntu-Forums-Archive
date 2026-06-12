---
title: "ATI ES1000 515e unknown device"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by gian on 2007-02-11
Hello,

my video card in unrecognized:

gian@oggy:~$ lspci -n | grep 0300
0000:04:04.0 0300: 1002:515e (rev 02)
gian@oggy:~$ lspci | grep VGA 
0000:04:04.0 VGA compatible controller: ATI Technologies Inc: Unknown device 515e (rev 02)

When I log out, the screen does not go to sleep and I have to switch it out.

How can I fix that ?
Could not find a driver for that card....

regards,
-Gian

---

### Post by The Foz on 2007-09-05
The open source driver "ati" sort of works for the ES1000.

What that means is that it will drive the card, but there is no support currently for any hardware graphics acceleration, so rendering will be done in software and will be slow.

You need to put the word "ati" into your xorg.conf file, as below:

```

Section "Device"
	Identifier	"ATI Technologies Inc ES1000"
	Driver		"ati"
	BusID		"PCI:8:9:0" # or whatever is correct for your hardware - it should already be in the file
EndSection

```

I am waiting for a new release of this open source driver, in the hope that it will properly support the ES1000 - it's not as if the chip is that new anymore.

I have tried the proprietary driver (fglrx), but it doesn't support the ES1000 either - it doesn't work at all. There is a new release, which I haven't yet tried, but the release notes on the ATI web-site don't mention the ES1000 so I don't have high hopes.

---

