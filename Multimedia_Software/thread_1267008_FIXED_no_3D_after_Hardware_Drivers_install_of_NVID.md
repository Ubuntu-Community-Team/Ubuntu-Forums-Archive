---
title: "FIXED no 3D after Hardware Drivers install of NVIDIA 96"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Neobuntu on 2009-09-15
I finally FREAKIN' found this and it fixes direct rendering on Jaunty 9.04 and with my MX420. > 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)


> 1) Work around for Nvidia non-root permissions bug in Ubuntu 9.04(Jaunty)

Bug Details

The permissions of the /dev/nvidia files cause errors when processes are launched with non-root privileges on my 64-bit 9.04 desktop system. **Addendum: ...and my 32bit.**

Workaround

Edit /etc/rc.local file from your terminal

gksudo gedit /etc/rc.local

OR (for **K**ubuntu)

sudo kate /etc/rc.local
(Note: I know, it's supposed to be "kdesu" but apparently "kdesu" doesn't work work here; "sudo" does.)

Add the following **before** &#8220;exit 0&#8243;:

**chmod 666 /dev/nvidia* &**
exit 0
    

Save and exit the file

---

### Post by Neobuntu on 2009-09-17
Hell, I don't know. I only get direct rendering with > sudo glxinfo | grep direct and not just "glxinfo | grep direct".

Desktop effects are not working. ????

---

