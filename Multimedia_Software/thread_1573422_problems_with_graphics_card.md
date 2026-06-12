---
title: "problems with graphics card?"
date: 2010-09-12
forum: Multimedia Software
---

### Post by owners4life5 on 2010-09-12
okay.....so

i have a graphics card, obviously. but i have no clue what kind, or how to update.

all i know is that it is SORRY.

could anyone please tell me how i can update it, or anything?

thanks in advance.

---

### Post by owners4life5 on 2010-09-13
*bump*

¿por favor?

---

### Post by gordintoronto on 2010-09-13
Open Accessories/Terminal and type the command: lspci

Just over a dozen lines will display, one will include the word "VGA". That's your video adapter.

If you run Administration/Hardware Drivers, it might offer to install a driver for your video.

---

### Post by owners4life5 on 2010-09-16
> **gordintoronto said:**
> Open Accessories/Terminal and type the command: lspci

Just over a dozen lines will display, one will include the word "VGA". That's your video adapter.

If you run Administration/Hardware Drivers, it might offer to install a driver for your video.

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03)

```

it didn.t offer anything.. ):

---

### Post by xenorecor on 2010-09-16
> **owners4life5 said:**
> it didn.t offer anything.. ):

Look closer, its there I promise :p

---

### Post by owners4life5 on 2010-09-17
> **xenorecor said:**
> Look closer, its there I promise :p

haha i could catch your humor any other time...but unfortunately, not this session ):

---

### Post by Yellow Pasque on 2010-09-17
Not another poor soul stuck with a SiS GPU...
Well, you can try this driver with 2D acceleration (but no 3D):
[http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671-0.9.1.tar.gz](http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671-0.9.1.tar.gz)

> it didn.t offer anything.. ):
.. because there's no binary/proprietary driver for it. The open-source one is installed and used by default.

---

### Post by Yellow Pasque on 2010-09-17
Actually, here's a better link: [http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb](http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9_i386.deb)

---

### Post by owners4life5 on 2010-09-29
thank you so much for the link...but when i go to install it, the package installer displays this in a terminal:

```
dpkg: regarding .../xorg-driver-sis671_0.9_i386.deb containing xorg-driver-sis671:
xserver-xorg-core conflicts with xserver-xorg-video-5

```

then goes on to say they are conflicting packages...what do i do now?

---

### Post by owners4life5 on 2010-10-03
*bump*

---

### Post by Yellow Pasque on 2010-10-04
You might have to uninstall the ubuntu sis driver or you could try a force install:
```
sudo dpkg install -f xorg-driver-sis671_0.9_i386.deb
```

---

### Post by owners4life5 on 2010-10-06
> **Temüjin said:**
> You might have to uninstall the ubuntu sis driver or you could try a force install:
```
sudo dpkg install -f xorg-driver-sis671_0.9_i386.deb
```

see this: [http://ubuntuforums.org/showthread.php?t=1587683](http://ubuntuforums.org/showthread.php?t=1587683)

after this suggestion, i tried this.

but i still can.t enable compiz. do you think i should still try out the force install?

---

### Post by Yellow Pasque on 2010-10-06
The driver I linked to doesn't have 3D accel, so it isn't going to let you run compiz.

---

### Post by owners4life5 on 2010-10-07
> **Temüjin said:**
> The driver I linked to doesn't have 3D accel, so it isn't going to let you run compiz.

okay, well it.s no big deal, i guess. thank you for helping though, it is appreciated (:

marking as solved.

---

