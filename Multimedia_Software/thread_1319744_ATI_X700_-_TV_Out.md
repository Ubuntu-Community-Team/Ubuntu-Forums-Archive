---
title: "ATI X700 - TV Out"
date: 2009-11-08
forum: Multimedia Software
---

### Post by driesv on 2009-11-08
Hello,

I'm using Ubuntu 9.10 and I have an *ATI Radeon X700 Mobility* as video card. I'm using the Ubuntu-standard driver, but I haven't the /etc/X11/xorg.conf file.

But tv out doesn't work. Is there a solution?
(Installing atitvout or using envyng doesn't work)

Thank You!

---

### Post by driesv on 2009-11-09
I have tried this suggestion: [http://ubuntuforums.org/showpost.php?p=7271915&postcount=18](http://ubuntuforums.org/showpost.php?p=7271915&postcount=18)

But it doesn't work and I get

```
dries@dries-laptop:~$ tvon
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  24
  Current serial number in output stream:  24
dries@dries-laptop:~$ 

```

Do I have to change Xorg.conf?

---

### Post by aotf01 on 2009-11-21
When you reboot your computer do you see the bios and boot screen on the TV?  If not you may have a different problem.

I have a Compaq Armada E500 with an ATI Rage Mobility P/M AGP 2x and this worked for me.

```
sudo apt-get install atitvout
sudo atitvout l #This turns on only the LCD and stops the out of sync image on the TV.
sudo atitvout lt #This turns on both the LCD and TV. If you do this first it may crash.
```

---

