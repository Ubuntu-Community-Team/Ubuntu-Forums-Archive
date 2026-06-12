---
title: "Ralink rt3060 chipset support?"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by MikeB23930 on 2010-04-29
Does anyone know if Ubuntu supports the Ralink rt3060 chipset or will support it in the upcoming 10.04 release?

Thanks,

Mike

---

### Post by malcmail on 2010-12-08
Did you get anywhere with this? I've been trying the same myself. Did find some code to put in the Kconfig file for rt2x00 but no idea what to do after I've changed the file itself.  The file seems to be  /drivers/net/wireless/rt2x00/Kconfig. 2.6.36 has it but I'm only on 2.6.32-26 so I had to make the manualk changes. But now stuck :-s

---

### Post by TBABill on 2010-12-08
Ralink has drivers for Linux and mine is a rt2860 and works well. It is probably a matter of getting the firmware and following the notes on installing from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

---

### Post by malcmail on 2010-12-08
Thanks for that. I did find that but I'll be utterly honest to say the instructions at the start did nothing but confuse me! 
 
I unzipped it and went into Makefile. The first line in mine is "RT28xx_MODE = STA" Am I supposed to change it? If so, what to?
 
I think I might manage the linux kernel - well we will see lol.  If you have any idea what I'm actually supposed to do I'd be eternally grateful.

---

### Post by loftkilla on 2011-03-22
The README is for Redhat  not UBUNTU....can someone help out a tad here with some Ubuntu specific instructions?\

The included readme is terrible, rlly.  Worst instructions EVER.

---

### Post by xinxu36 on 2011-05-28
I'm also having the same problem, running 11.04.  Step by step instructions to install the rt2860 drivers would be amazing.

---

### Post by chili555 on 2011-05-28
> running 11.04. Step by step instructions to install the rt2860 drivers would be amazing.I believe rt2860sta is included by default. Is it not driving your device? May we see:```
lspci -nn
```Feel free to trim away everything that's not a Ralink wireless device.

---

