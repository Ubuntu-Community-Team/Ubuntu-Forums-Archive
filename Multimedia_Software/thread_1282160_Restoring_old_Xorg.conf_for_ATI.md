---
title: "Restoring old Xorg.conf for ATI"
date: 2009-10-04
forum: Multimedia Software
---

### Post by jperez on 2009-10-04
Hi all

My girlfriend is currently in a fix and I for the life of me can't remember how to go about fixing this.  See, here's the deal.  She installed Ubuntu using her laptop (with an ATI chip) on an external drive.  Simple enough and it worked for the most part.  She then took it to her PC with an nVidia card and installed the restricted drivers for it, thus making any use of the ATI drivers, moot.

So, I would like some help to get her old conf back so her laptops ATI card will be recognized again.  As it stands, she's getting the low-graphics mode error due to this situation.

Any help would be greatly appreciated.  Thanks! :)

Jesse~

---

### Post by inobe on 2009-10-04
```
sudo dpkg-reconfigure xserver-xorg
```

that should do it, you will need to restart.

edit: that's not it !


sec

---

### Post by jperez on 2009-10-04
EDIT:
lol Good thing she stopped when it asked for her keyboard.

Jesse~

---

### Post by inobe on 2009-10-04
make the backup

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

restore it

```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

visa versa

---

### Post by jperez on 2009-10-04
That sounds about right.  Thanks again! :D

Jesse~

---

### Post by inobe on 2009-10-04
> **jperez said:**
> EDIT:
lol Good thing she stopped when it asked for her keyboard.

Jesse~


i hope you caught my edit ?

that first command will reconfigure xserver to use nvidia and i think you should backup the conf file first prior to running that command.

---

### Post by jperez on 2009-10-04
We caught the edit, but a little too late.  I think it did go over the old config, so I'm going to edit the xorg.conf to fix her card on my laptop.

Thanks for the help though.  I'll have to put those commands in a safe place so I can recall them if I ever need them. :p

Jesse~

---

### Post by inobe on 2009-10-04
ubuntu will re-detect the hardware however don't forget to activate the nvidia driver.

---

### Post by BulletTheBlueU2 on 2009-10-04
[COLOR=DarkRed]I've been forced to post here.

Yes I am Jesse's girlfriend, he can confirm it.

What's going on is, I have Ubuntu on an external HDD that I use solely for my Laptop. 
Laptop = ATI Graphics Chipset. Everything worked.
I switched my External HDD to my Desktop and booted up Ubuntu to try out some Animation Effects. But I needed to Install the NVIDIA drivers in order to even get the Effects.

After testing out to see which ones I liked best, I shut down my desktop and switched my External HDD back to my laptop and booted Ubuntu back to my laptop. But, then it went into Low-Graphics mode and I can't use any effects.

I don't want to use Linux on my desktop because that is my main platform for my schoolwork and graphical work. But it startled me since I can no longer use any Graphical additions that came with Compiz Fusion.

Laptop = ATI Chipset. My main platform that I use Linux on.
Desktop = NVIDIA. I only used it to test them out. I don't want to use Linux on my Desktop Computer.

This was just to make some things clearer.
[/COLOR]

---

### Post by inobe on 2009-10-04
okay

me again

restore the previous xorg.conf from backup


```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

if you haven't made a backup reconfigure xserver

```
sudo dpkg-reconfigure xserver-xorg
```

activate driver


note: i don't think it's a great idea to swap hardware on a regular basis due to problems you may encounter.

---

### Post by jperez on 2009-10-04
Well, here's the thing.  It didn't show restricted drivers when she installed Ubuntu the first time on the ATI chipset laptop.  So, enabling the drivers wouldn't happen.  What I did was change one of the xorg.conf backups she had to look for the fglrx module and access "ati" under device.  While that didn't crash the xserver, it didn't allow for compositing still.

Perhaps reconfiguring would be the key, so we'll try that.  If not, my only other thought would be to have her remove anything ATI and just reinstall the xserver-xorg-ati/radeon drivers that came pre-installed for good measure.

What do you think?

Jesse~

---

### Post by inobe on 2009-10-04
> **jperez said:**
> 

Perhaps reconfiguring would be the key, so we'll try that.  If not, my only other thought would be to have her remove anything ATI and just reinstall the xserver-xorg-ati/radeon drivers that came pre-installed for good measure.

What do you think?

Jesse~

sounds like a plan

---

### Post by jperez on 2009-10-04
The future Mrs figured it out before me! :lolflag:

She removed the nvidia drivers (as an added measure) and reinstalled the ati drivers.  Success!  I swear she'll supersede me in Linux knowledge and she'll be teaching me instead.

Anyway, thanks for your help nonetheless **inobe**.  Much appreciated. :mrgreen:

Jesse~

---

