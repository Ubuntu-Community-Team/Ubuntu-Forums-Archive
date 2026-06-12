---
title: "patching wireless card"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Hawtsoss on 2010-06-29
i just partitioned my hard drive so i could experiment with ubuntu

i am working with aircrack-ng and i have 0000 experience with ubuntu

first things things first, my friend is letting me test aircrack by following the tutorial on [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack)

before i even start i run into a huge wall.... i have no idea how or what to patch my wireless driver with

this is my current wireless driver - Broadcam STA wireless driver - These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

---

### Post by cjmiller00 on 2010-06-30
im playing with the same thing.  my wn111v2 seems fine with aircrack with the exception of speed.  SLOW IV capture.  

look to youtube for realtime usage of this.  I found a couple of tutorials there useful.  watch and take notes step by step.  

then as i am doing now reverse engineer the process to modify for your own use.

---

### Post by Hawtsoss on 2010-06-30
so if i have my friends network password but it still doesn't let me in because of MAC address filtering, do you know how to get around this?

---

### Post by bkratz on 2010-06-30
> **Hawtsoss said:**
> so if i have my friends network password but it still doesn't let me in because of MAC address filtering, do you know how to get around this?

I know very little about air crack, but I noticed that you mentioned the Broadcom STA driver and remembered seeing  the following found on the air crack website.

```
Users whom use broadcom linux_sta driver (otherwise known as wl) should note that there are no monitor/injection modes with such driver. Broadcom deliberately removed the functionality out of their proprietary binary blob. Read here for more info: http://seclists.org/fulldisclosure/2008/Nov/506. Also b43 supports less than a handful of chipsets, take note on which ones are unsupported and see if yours fall into that category: b43

```

Just for your information, may not even affect what you are doing.

---

### Post by Hawtsoss on 2010-06-30
thanks, that is actually very nice to know

---

