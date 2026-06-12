---
title: "Video Card Upgrade"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by j.thunes on 2006-07-12
Hopefully an easy question:

I have just upgraded my video card on my secondary computer.  When booting, there is now an error message saying that X cannot be started.

I have tried downloading the (I think) correct video drivers using apt-get and have also tried using Xorg -configure.

Using Xorg -configure I get an error message saying that there is a problem with the output driver.

As I am new to linux I have no idea what else to try.  Any suggestions would be apperciated.

System Information:
   ubuntu breezy badger
   128 mb ram
   pentium II processor
   Nvidia GeForceFX 5200 128mb

***This should obviously be in the breezy badget section
   a mistake on my first post :( ***

---

### Post by tseliot on 2006-07-12
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

The Xserver should work fine and you should then be able to install the Nvidia Driver (see my guide)

---

### Post by j.thunes on 2006-07-12
Thanks it worked

---

