---
title: "problem with Sapphire X1650 Pro"
date: 2008-05-11
forum: Multimedia Software
---

### Post by lukasorin on 2008-05-11
hi there. i start to say i'm new in linux...i just buy a new video card Ati Radeon Sapphire X1650 Pro with 512 MB DDR2 on AGP 8x. right now i have fresh Ubuntu 8.04 on my PC. i can't find the corect driver for this card. on web site Ati they have just for X1600 driver..i read a lot of but i can't install corect the driver. please if any one can help me..i don't know were to ask more...every time after i try to set active the driver from Resctricted Drivers, i take restart to my PC and my screen stay black..i think is the 8 time when i install Ubuntu.. i'm afraid to make another install who maybe will not work..thank you so much . cheers

---

### Post by RJARRRPCGP on 2008-05-11
Possibly, because the 1650 is the same thing as a 1600 but clocked higher.

---

### Post by kellemes on 2008-05-13
> **lukasorin said:**
> hi there. i start to say i'm new in linux...i just buy a new video card Ati Radeon Sapphire X1650 Pro with 512 MB DDR2 on AGP 8x. right now i have fresh Ubuntu 8.04 on my PC. i can't find the corect driver for this card. on web site Ati they have just for X1600 driver..i read a lot of but i can't install corect the driver. please if any one can help me..i don't know were to ask more...every time after i try to set active the driver from Resctricted Drivers, i take restart to my PC and my screen stay black..i think is the 8 time when i install Ubuntu.. i'm afraid to make another install who maybe will not work..thank you so much . cheers

I have the same card and never got it working using the restricted drivers above version 8.42.3
So currently I'm using [fglrx 8.42.3]("http://ati.amd.com/support/drivers/linux/previous/linux-r-8-42-3.html") and it works fine.

Since I'm not using Ubuntu full time I can't give you a howto on installing fglrx by hand, so I'm afraid you have too google for this.
One link that may be useful. [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

In order to avoid reinstalling Ubuntu all the time, you can create a backup of your (working) /etc/X11/xorg.conf like so..
from terminal.
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.workingbackup
```

Now, when things go wrong (can't get into your graphical environment) you can put back the backup like so..
```
cd /etc/X11
sudo cp xorg.conf.workingbackup xorg.conf
```

Sorry I can't give any easy answer.

---

### Post by lukasorin on 2008-05-16
so nobody can help me? i can belive i just buy the only video card who don't work with linux..i try 10 different linux..all same problem...i still want to use linux..but what i must do... were to ask? somebody know what linux will run propely with my video card. ple help me :( thank you

---

### Post by abanuelosh on 2008-08-27
i have the same problem with my x1650, but all solutios whoever kindly gave to me only ends with a black screen!!!!

it seems that the owners of the old AGP x1650 are being forgotten, sighs 
:(

Pl3ase helpus!!!!!!!!!!!

---

