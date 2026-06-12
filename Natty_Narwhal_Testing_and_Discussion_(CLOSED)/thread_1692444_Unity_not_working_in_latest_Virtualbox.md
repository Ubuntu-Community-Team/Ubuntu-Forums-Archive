---
title: "Unity not working in latest Virtualbox"
date: 2011-02-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MechaMechanism on 2011-02-21
I'm trying to try out Natty in Virtualbox.  I'm not seeing Unity, just the fall back regular Gnome desktop.  Does anyone have Unity working in Virtualbox and if yes how are you getting it to work.

Host 10.04.2
Nvidia 8800GT with 3D drivers
Latests Virtualbox

---

### Post by Quadunit404 on 2011-02-21
Did you install the Guest Additions in the Natty guest and enable 3D Acceleration? That's important for Unity to actually work in a VM.

---

### Post by MechaMechanism on 2011-02-21
> **Quadunit404 said:**
> Did you install the Guest Additions in the Natty guest and enable 3D Acceleration? That's important for Unity to actually work in a VM.
I did what you said to do.  The guest additions install just fine.  But when I log out it goes to a black screen and if I restart, it hangs in the boot process.  I assume it does not work because maybe Natty has moved along and Virtualbox 4 is getting old.  Oh well.

---

### Post by Quadunit404 on 2011-02-21
VirtualBox 4.0.4 was released four days ago...

---

### Post by lucazade on 2011-02-22
> **MechaMechanism said:**
> I did what you said to do.  The guest additions install just fine.  But when I log out it goes to a black screen and if I restart, it hangs in the boot process.  I assume it does not work because maybe Natty has moved along and Virtualbox 4 is getting old.  Oh well.

I have the same issue with Vbox 4.0.4 and guest additions.. it hangs in the boot process..
I believe it is related to the latest natty kernel (2.6.38-4) which is not supported yet.

---

### Post by MechaMechanism on 2011-02-22
> **lucazade said:**
> I have the same issue with Vbox 4.0.4 and guest additions.. it hangs in the boot process..
I believe it is related to the latest natty kernel (2.6.38-4) which is not supported yet.
Ah, I see.  Ok.

---

### Post by grubdude on 2011-02-22
Same problem here. Gets stuck in the boot process. I have a brand new install so cannot roll it back to the previous kernel.....Besides I want to use the latest and greatest. I hope they fix it soon...
 
:-(

---

### Post by Derspankster on 2011-02-22
Same here. I reinstalled the latest daily build but have not installed guest additions for fear of failing to boot.  

Interestingly, I cannot install even the 2d panel which isn't supposed to require 3d acceleration.

---

### Post by slamhound on 2011-02-23
Seems to work again after this morning's updates.  I booted into recovery mode, then ran updates, then rebooted. Had to reinstall guest additions again, but then things worked after another reboot.

---

### Post by lucazade on 2011-02-23
> **slamhound said:**
> Seems to work again after this morning's updates.  I booted into recovery mode, then ran updates, then rebooted. Had to reinstall guest additions again, but then things worked after another reboot.

I can confirm it is working properly now!

---

