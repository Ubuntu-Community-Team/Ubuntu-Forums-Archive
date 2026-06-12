---
title: "EVGA GTX 670 Linux overclock Law Base clock. Coolbits doesn't work"
date: 2013-03-19
forum: Multimedia Software
---

### Post by Artpen on 2013-03-19
Hi All,

I have installed a new graphics card EVGA GTX 670 SC and its specs are:

Base Clock = 967
Boost Clock = 1046
Memory clock = 6008

But I am using linux and after installing Nvidia drivers 310.40 in Nvidia settings I get this :

Perfomance Level 0
Graphics Clock = 324
Memory Clock = 324


Perfomance Level 3
Graphics Clock = 705
Memory Clock = 3004

Yes, its much smaller that says EVGA specs of this card.

So I am trying to overclock it to EVGA specs. I edited my xorg.conf by adding :

Option "Coolbits" "1"

And it doesn't work. I do not get overclock options in Nvidia settings.

I tried Option "Coolbits" "4" for the fan control and it works!

1. How can I get overclocking option work?
2. Is it possible in Linux make Graphics card dynamically adjust clock and fan speeds?
3. What software to use in linux ti test stability of Graphics card?

Thanks guys.

---

### Post by Artpen on 2013-03-23
up :)   It looks like Linux NVIDIA drivers doesnt' support overclocking ?

---

### Post by FunkyPresident on 2013-03-28
You are correct about the lack of overclocking though the NVIDIA binary driver. It hasn't been supported since Fermi. Also, your card is functioning at it's factory clock speeds, but nvidia-settings is not showing the highest clock correctly. This is a known bug. I'm not sure why it hasn't been fixed. I confirmed that my GTX 670 is running at the correct clock speed when I profiled a CUDA application. It reported the 980 Mhz boost clock of my card (Vanilla GTX 670). Your memory clock really is 3004 Mhz. The advertised 6008 Mhz refers to the effective memory clock. Here is a link that discusses this a bit. [http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx680&num=3](http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx680&num=3)

---

