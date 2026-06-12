---
title: "wrong screen resolution at start up screen blank"
date: 2008-09-29
forum: Multimedia Software
---

### Post by reddragons13 on 2008-09-29
after i installed the restricted drivers my screen resolution changed and now i cant login. i see grub loading and ubuntu loading but at login it goes blank and tells me the resolution is wrong please help

---

### Post by overdrank on 2008-09-29
> **reddragons13 said:**
> after i installed the restricted drivers my screen resolution changed and now i cant login. i see grub loading and ubuntu loading but at login it goes blank and tells me the resolution is wrong please help

Hi and can you boot into recovery mode and use the xfix option and hopefully this will correct the issue.
What is the model of the graphics card?

---

### Post by reddragons13 on 2008-09-29
perfect that was it . thank you for the help

---

### Post by reddragons13 on 2008-09-29
sorry i spoke to soon.i did that and i can see it in recovery but when i enable the driver and then reset i get the same thing.i get out of range on my monitor.it goes back into a resolution that my monitor cant display.

---

### Post by overdrank on 2008-09-29
Ok what is the model of the graphics card?

---

### Post by reddragons13 on 2008-09-29
sorry the card is a xfx gforce 7900gt. evga motherboard 2 gig xms ddr.amd 4800 x2

---

### Post by overdrank on 2008-09-29
> **reddragons13 said:**
> sorry the card is a xfx gforce 7900gt. evga motherboard 2 gig xms ddr.amd 4800 x2

Ok you can try Envy to install the driver, of course after disabling the restricted driver. Or you can try and install the nvidia driver from nvidia sites.

---

### Post by reddragons13 on 2008-09-30
didnt work. i installed envy ng for the drivers in recovery mode then on reboot the resolution at log in is still out of range. is there a way to change the log in resolution?it works on  my other monitor. but thats for my work pc.

---

### Post by Knuxyl on 2008-09-30
try looking at your xorg file. u can access it by going to recovery mode, choosing go to shell (or w/e command prompt for linux, im a windows person :p) and typing this
sudo nano /etc/X11/xorg.conf

look through that and see if the resolution and refresh rate are there and if so make sure they match what ur monitor can handle. btw i dont know how to add it to there, i just remember seeing it once. im having the exact same problem as u but with the 8500 card. if u get it to work tell me what u did plz :p

---

