---
title: "ATI RADEON 9250 Driver Issue on Ubuntu 7.04"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by dannyreign on 2007-05-30
Hi guys. 

I have 0 experience with Linux. I don't know anything about it, so bare with me :p

Anyway, the problem is that I can't seem to make the driver work for my Ati card, on Ubuntu.
I searched the net far and wide, and tried a lot of methods that where supposed to make the driver work.. and did more trouble than good, causing Ubuntu to fail at starting, more than once.
The best progress I got from one of them is the increase of my resolution (not the refresh rate though), but if I "fglrxinfo" in the terminal, it kept showing me the whole "Mesa" thing.
From what I understand, if the driver was working properly, it should show some Ati specs. Or am I wrong?

And before anyone bothers to offer me any method in which the xorg.conf needs to be tempered with, know, that It won't save, no matter what I try.

If anyone can offer a solution to this and has the patience to guide me through this, I would be more than grateful :D

---

### Post by eye208 on 2007-05-30
Did you use Ubuntu's restricted drivers manager to install the driver? This is usually the easiest and safest method. You can also test this method from the Live CD without changing your working system.

---

### Post by dannyreign on 2007-05-30
The Restricted Drivers Manager gives me "You hardware does not need any restricted drivers".
Don't know what thats supposed  to mean..

---

### Post by pebo on 2007-05-30
I wouldn't recommend the restricted driver unless you absolutely have to have high end 3D performance  - and if you did you would probably want a better card anyway ;). I use the open source  ati driver that comes with xorg and my Radeon 9200 pro runs 3D ok. Install it from the terminal with```
sudo apt-get install xserver-xorg-video-ati
```Back up your existing xorg.conf:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Then you can edit your xorg.conf file like this:```
gksudo gedit /etc/X11/xorg.conf
```. Find the Section "Device" and edit the Driver line to read```
Driver		"ati"
```save and restart the xserver with ctrl-alt-bksp.
If it goes horribly wrong you can restore your original xorg.conf with```
sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```
Good luck!

---

### Post by eye208 on 2007-05-30
It seems your card is not supported by Ubuntu's version of fglrx. Of course you could compile and install an older version, but I wouldn't recommend it. Older versions of fglrx are well-known for being unstable and crash-prone. It's probably best to stick with the open source ati driver or replace the card.

---

### Post by dannyreign on 2007-05-30
Pebo, your method seems great, except, there is one thing that i don't quite get.. 


```
Driver		"ati"
```


Are you sure it's supposed to be "ati" in there?

> It seems your card is not supported by Ubuntu's version of fglrx.

I see. Well, thanks for the help anyway.

---

### Post by eye208 on 2007-05-30
> **dannyreign said:**
> Are you sure it's supposed to be "ati" in there?
Yes, that's correct.

---

### Post by pebo on 2007-05-30
"ati" is the open source driver

---

### Post by dannyreign on 2007-05-31
Ok, so I tried Pebo's method. Nothing changed. Resolution, the same. Refresh rate, still low.
Other ideas?

> I wouldn't recommend the restricted driver unless you absolutely have to have high end 3D performance - and if you did you would probably want a better card anyway

Actually, to get back to you, thats exactly what I want.
The 9250 is just fitting for what I want to do.

---

### Post by eye208 on 2007-05-31
> **dannyreign said:**
> Ok, so I tried Pebo's method. Nothing changed. Resolution, the same. Refresh rate, still low.
Other ideas?
You were asking how to get fglrx running, not how to change resolution and refresh rate. To configure the latter, enter "sudo dpkg-reconfigure xserver-xorg" into a terminal, follow the steps, then restart X. No driver change is required for this.

---

### Post by dannyreign on 2007-05-31
Guess I misunderstood something then.
I actually care for the 3d acceleration to work, *but*, from what I understood, if the method would've worked, there should be some change to the resolution and refresh rate also. So, I take it that I'm wrong?

Remember, I'm a newbie..

---

### Post by eye208 on 2007-05-31
The open source driver "ati" also offers some level of 3D acceleration. It's sufficient to run Beryl but too slow for games.

During a fresh install on a system with ATI graphics, the open source driver is usually chosen by default. The restricted drivers manager can be used to install the proprietary "fglrx" driver if there is a supported card in the system. Support for the Radeon 9250 has been dropped from fglrx a while ago.

Changing resolution and refresh rate is an entirely separate thing. It's true that fglrx, once it is installed, automatically detects the highest possible resolution and refresh rate of the monitor. With the open source driver you have to specify it manually by editing the xorg.conf configuration file.

Because xorg.conf is quite complex, the preferred method to modify it is to run "sudo dpkg-reconfigure xserver-xorg". This allows reconfiguration of the X window system without editing the file by hand.

---

### Post by dannyreign on 2007-05-31
> The restricted drivers manager can be used to install the proprietary "fglrx" driver if there is a supported card in the system. Support for the Radeon 9250 has been dropped from fglrx a while ago.

So, thats it? There's no way to go around that?

Such a shame. I really liked Ubuntu so far, but, seems like I'll have to stick to crappy win. instead..

Thanks for the help, anyway.

---

### Post by dodgydavec on 2007-06-07
I had this problem. Some "vesa" driver was in there. I changed it to "ati" thanks to you. Thank you very much.

---

### Post by cleopete on 2007-06-08
> **eye208 said:**
> Did you use Ubuntu's restricted drivers manager to install the driver? This is usually the easiest and safest method. You can also test this method from the Live CD without changing your working system.

Installing from the live cd provokes a reboot.  Isn't that kind of an oxymoron?  How can you boot the driver without either putting it on the HD or burning a new CD?

---

### Post by pebo on 2007-06-08
Well you can try just restarting the X server with Ctrl-Alt-Bksp - no reboot required

---

### Post by cleopete on 2007-06-09
> **pebo said:**
> Well you can try just restarting the X server with Ctrl-Alt-Bksp - no reboot required

Hadn't thought of that, thanks.

---

