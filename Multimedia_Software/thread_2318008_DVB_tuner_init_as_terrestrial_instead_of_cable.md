---
title: "DVB tuner init as terrestrial instead of cable"
date: 2016-03-22
forum: Multimedia Software
---

### Post by Gabor_Botzheim on 2016-03-22
Hi all,

I hope someone can help where to fix my issue:
1. I have Ubuntu 14.04.04, kernel 3.19.0-47 with a Technotrend TV-Stick CT2-4400 dual DVB-T/C tuner which I use for DVC-C cable reception
2. The stick is listed, but when I boot ubuntu and start w_scan without parameters, it automatically assumes a TERRESTRIAL tuner. When I start Kaffeine (with already set up channels and card) the reception does not work, probably the same issue.
3. I start "w_scan -fc" to tell it to use CABLE repection, after the initialization I abort the scan. I start Kaffeine and the TV reception works. Probably the tuner is now configured to use cable.

Is there a way to tell Ubuntu to init the tuner with the cable setting, so that I do not have to use this w_scan workaround? Or is this a Kaffeine issue?

Thanks
Gabor

---

### Post by Gabor_Botzheim on 2016-04-26
As there came no reply, i am postin a workaround I use now:
I put this command to be executed at startup:
timeout 10 w_scan -fc -c de

after that the tuner is in DVB-C mode, and works perfectly

---

