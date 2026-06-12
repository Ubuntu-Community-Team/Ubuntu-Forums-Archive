---
title: "X server"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Vehendi on 2006-09-04
Hi,

I'm trying to install Ubuntu on my system, but the X graphics server doesn't work. I use an ATI Radeon X800GTO card, and I altready tried the sudo dpkg-reconfigure etc. command, but it did not work.

Thank you in advance,

Vehendi.

---

### Post by meng on 2006-09-04
A few more details please, like exactly what are you trying to do? Boot the Live CD, boot from a hard disk installation? What error message are you getting? What did you select during dpkg-reconfigure: ati, vesa or other? What are your system specifications, RAM etc.

---

### Post by tseliot on 2006-09-05
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by Vehendi on 2006-09-05
That doesn't work either.

I use a live boot CD which I got with a LinuxFormat Special Edition and I'm not that technically experienced.

Also, the x server crashes before I can install Ubuntu.

---

### Post by tseliot on 2006-09-05
> **Vehendi said:**
> That doesn't work either.

I use a live boot CD which I got with a LinuxFormat Special Edition and I'm not that technically experienced.

Also, the x server crashes before I can install Ubuntu.

The alternate installation can be performed from a separate cd (not the livecd).


In your case the only thing I can suggest is that of booting the livecd in Safe Mode.

---

