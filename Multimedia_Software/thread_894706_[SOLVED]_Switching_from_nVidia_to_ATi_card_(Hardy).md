---
title: "[SOLVED] Switching from nVidia to ATi card (Hardy)"
date: 2008-08-19
forum: Multimedia Software
---

### Post by remicks916 on 2008-08-19
Recently my buddy gave me a ATi Radeon 3850 HD, and I want to put it in my Hardy machine to replace the nVidia 8400 GS that is currently crapping up my system. Being new to linux/Ubuntu I am wondering what steps I will have to take to make this go as smoothly as possible. Any help is greatly appreciated.

-remicks-

[PC INFO]
Ubuntu Hardy (8.04.1)
AMD Athlon64 3500+
2GB DDR 800MHZ RAM
512MB nVidia 8400 GS
Audigy 2 Value
Asus Amberine-M Motherboard (Compaq OEM Board)

---

### Post by remicks916 on 2008-08-20
Wow, this couldn't have been easier! All I did to do the switch was disable the nVidia drivers through the Hardware Drivers applet in System>Administration, power down my PC, removed the nVidia card, dropped in the ATi (after having to move one of my HD's because of this new card's IMMENSE size), booted back in to Ubuntu, went back to the Hardware Drivers applet and enabled the ATi drivers, one last reboot and voila! 

On a side note the ONLY other thing I had to do to get my desktop running smooth was turn off Loose Binding in the Compiz-Fusion options. 

I hope this guide is helpful for anyone else looking to change video card vendors in Ubuntu Hardy :)

---

### Post by tuxxy on 2008-08-20
Glad it was easy, the worst outcome you would of had only to reconfigure the xorg

---

### Post by remicks916 on 2008-08-20
Well I'm glad I didn't even have to do that :)

---

### Post by tuxxy on 2008-08-21
lol its only one command, take a couple of minutes if that :)

Mark your thread solved now too

---

