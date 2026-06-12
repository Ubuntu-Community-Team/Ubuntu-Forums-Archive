---
title: "Just a little question [NVIDIA]"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by leveliv on 2007-08-23
Alright I made the jump to ubuntu 7.04 from XP MCE last night once again...and this time I plan on staying. but I used Automatix2 to instlal all my programs including Nvidia drivers...but when I restarted it crashed and I had to do the sudo dpkg-reconfigure xserver-xorg thing but it didn't work..once I got to the part where you pick either 16 or 24 bit it wouldn't go any farther it said something about a backup or something being overwritten I can get it exactly when I go home. but I am sure someone has had this problem before.

---

### Post by tseliot on 2007-08-23
I have edited the title of the thread.

You can follow this steps:
Boot in Recovery Mode (select it from the GRUB menu)

type:
```
dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:
```
reboot 
```

and boot as usual

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by leveliv on 2007-08-23
alright thanks tseliot I will try that when I get home :) thanks again.

---

### Post by leveliv on 2007-08-23
also I have heard a lot of good things about Envy..what exactly is it? Why are people having such good luck with installing the drivers with that other than an well detailed guide..

---

### Post by tseliot on 2007-08-23
> **leveliv said:**
> also I have heard a lot of good things about Envy..what exactly is it? Why are people having such good luck with installing the drivers with that other than an well detailed guide..
Here you will find a brief explanation of what it is:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

