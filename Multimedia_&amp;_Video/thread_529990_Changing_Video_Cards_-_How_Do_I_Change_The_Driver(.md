---
title: "Changing Video Cards - How Do I Change The Driver(s)?"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by theyain on 2007-08-19
(SOLVED)


I am going to be changing my video card soon.  But before I do so, I want to know if it is possible to install the correct drivers for my other card before I change them out/ go back to my integrated card.  That way i don't have to worry about Xorg X server.  Help?

---

### Post by w4ett on 2007-08-19
Easiest  way is to:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

and select 'vesa' as your driver.  Install your new card, reboot then select or enable the new proprietary or open source driver.

---

### Post by southernman on 2007-08-19
It would be a really BIG help if you could enlighten us on what card your going to put in... Most cards just shut down you computer, put on your wrist strap (or not if your feeling lucky), install the card and power up your system. X should see it and load the module for it. A handful of cards you'll need to work with to get working right.

---

### Post by RomeReactor on 2007-08-20
If you're changing from ATI to Nvidia, install the **nv** driver:
```
sudo apt-get install xserver-xorg-video-nv
```
if your going from Nvidia to ATI, then it's:
```
sudo apt-get install xserver-xorg-video-ati
```
After either of these, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose the driver you just installed. If you're not changing brands, then just revert to the open source driver in each case (**nv** for Nvidia, **ati** for ATI) when doing the **dpkg** command. Shut down your computer after that.

Then open your case and change the cards.

---

### Post by w4ett on 2007-08-20
> **RomeReactor said:**
> If you're changing from ATI to Nvidia, install the **nv** driver:
```
sudo apt-get install xserver-xorg-video-nv
```
if your going from Nvidia to ATI, then it's:
```
sudo apt-get install xserver-xorg-video-ati
```
After either of these, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose the driver you just installed. If you're not changing brands, then just revert to the open source driver in each case (**nv** for Nvidia, **ati** for ATI) when doing the **dpkg** command. Shut down your computer after that.

Then open your case and change the cards.

Both the nv and the ati driver are already available within xorg. a simple:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

will make either of those drivers avaiable for use and reconfiguation of xorg.conf.  But there is no mention what particular card the op is installing......might well be an SIS, Hercules or Matrox as far as we know.  :)  Enabling the vesa driver will allow booting into a GUI desktop and then further modification of xorg.conf and enabling of restricted drivers or compiling of a new driver from source.

---

### Post by theyain on 2007-08-20
Thank you.  The first person who responded was the most helpful.  :D

Bur anywho,  I was chaning from an old ATI card (really really old) to a somewhat new VIA card.  I didn't say that because I wanted to see if there was just a general way to do what I needed to do.

---

