---
title: "drivers for ATI Radeon R250 [Mobility FireGL 9000]?"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by nold-i-spolen on 2007-10-04
Hi!

I'v had problems finding information about drivers for my card.

This site says i can only use the guide if my card is 9500 or higher
([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI))

I was trying to install via Envy, but after instaling it told me to restart, and then right befor i would normaly get the log-in screen, it went to "blue-screen" where it told me somthing like the Xserver didnt find a screen.
And sins i'm a "rookie" at LINUX i couldn't work out what to do, i couldn't even boot in "safe graphic mode".........so i reinstalled, and am now a bit afraid to **** it up again. 

I'm using Feisty Fawn 7.04 installed from Ubuntu Ultimate Edition 1.4

Hope i can get som help in here

Regards
Thomas

---

### Post by elliotjreed on 2007-10-05
You could use the xorg command: reconfigure it if it goes bad - 

```
sudo dpkg-reconfigure xserver-xorg
```

Just look in repositries (synaptic) for fglrx

---

### Post by w4ett on 2007-10-05
The Wiki instructions are correct:  ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) The fglrx driver only support the 9500 card and ABOVE.  The legacy fglrx driver is not supported by the current Xorg 7.2.

The proper driver for your card is the xorg-driver-ati which should be installed when your card is autodetected when you installed ubuntu.  This driver does provide 3d capability with support for Compiz-Fusion, GoogleEarth and the like, but it is not sufficient for gaming unfortunately.

---

### Post by nold-i-spolen on 2007-10-13
Thank you for the answers!

I guess il'l just have to live with the current driver. I don't play that many games anyway, but wher is the best place to read about driver updates ect?

Thank's

Thomas

---

### Post by kshane on 2007-10-13
> **nold-i-spolen said:**
> Thank you for the answers!

I guess il'l just have to live with the current driver. I don't play that many games anyway, but wher is the best place to read about driver updates ect?

Thank's

Thomas

ATI has a driver RSS feed that you can get the info for off their site.  I have it set up for "MyYahoo" where I get all my morning news feeds.

*I could be mistaken*, but I think ATI is no longer updating the earlier card's drivers.  You'd have to check their site to be sure, though.  [ati.amd.com](ati.amd.com)

Kevin

---

