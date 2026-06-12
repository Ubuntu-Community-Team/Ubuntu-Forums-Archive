---
title: "Prolink Pixelview BT878 (Rev. 11)"
date: 2008-05-16
forum: Multimedia Software
---

### Post by jeffimperial on 2008-05-16
I just plugged in my Pixelview BT878 and installed TVtime. I did sudo modprobe bttv, and still nothing.

I already added "bttv" in /etc/modules

and I already created a file called "bttv" in /etc/modprobe.d the contents of which are:

# i2c
alias char-major-89 i2c-devb
options i2c-algo-bit bit_test=1
# bttv
alias char-major-81 videodev
alias char-major-81-0 bttv
# My TV Card
options bttv card=23 tuner=18 radio=0 pll=1 adc_crush=0

Any help will be appreciated!

---

