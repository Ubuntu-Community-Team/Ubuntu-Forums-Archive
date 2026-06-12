---
title: "Epson DX8400 Scanner Driver trouble with Ubuntu 9.10"
date: 2010-01-15
forum: Multimedia Software
---

### Post by mo7ard on 2010-01-15
Ok, installing the Epson DX8400 printer driver was easy... I just turned it on, and Ubuntu searched and installed the printer itself.

But scanning... that's another story. In Ubuntu 9.04 the trick was as simple as installing libsane-extras in Synaptic, but this doesn't work in Ubuntu 9.10 :( !! When I try to run XSane, it simply replies that there is no available device... can anyone help me, please?

Thank you all... best regards! ;)


**[SIZE=1]ubuntu 9.10 32-bit[/SIZE]**

---

### Post by xc3RnbFO8P on 2010-01-16
Turn on your scanner,
in Terminal show the output of:
> sudo sane-find-scanner

---

### Post by ellgor on 2010-01-16
Hi,

Go to the "Avasys" site, its for Epson's, and get the Imagescan package, works after a reboot.

Regards, Ellgor.

---

### Post by mo7ard on 2010-01-18
> **ellgor said:**
> Hi,

Go to the "Avasys" site, its for Epson's, and get the Imagescan package, works after a reboot.

Regards, Ellgor.

Thanks a lot!! It really worked :D!!

---

### Post by Kenneth CAB on 2010-01-21
Avasys' drivers worked great for my TX330F too, thanks for the tip.

---

### Post by 4gsl on 2010-02-24
I can print, but still can't scan after downloading the Avasys driver, installing (via debian installer), and rebooting.

I'm using Ubuntu 9.10 with an Epson Stylus Photo RX580.

PLEASE HELP!

---

