---
title: "[SOLVED] Disable ATI driver in repair mode"
date: 2008-06-01
forum: Multimedia Software
---

### Post by stickx911 on 2008-06-01
I installed the ati drivers to get compiz to work, but I get the black screen on boot. compiz is not that important, so how can I disable/revert/remove the ati restricted drivers in the repair console. Thanks for any help. I tried to search, but only found help on getting them to work, but I really do not need compiz enough to go through the trouble.

Thanks again

---

### Post by Rocket2DMn on 2008-06-01
Try rebooting into the recovery mode kernel (choose the root terminal), and run
```
apt-get remove --purge xorg-driver-fglrx
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Allow the system to reboot normally and you should be OK.  What is your video card?  We might still be able to get compiz to work.  Please post:
```
lspci | grep VGA
```
If you have an older ATI card, like Radeon 9500 or older, see here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by stickx911 on 2008-06-01
....0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] ...
so x800

---

### Post by stickx911 on 2008-06-01
stickx911@stickx911-desktop:~$ lspci | grep VGA
03:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
stickx911@stickx911-desktop:~$ 

to be complete

---

### Post by Rocket2DMn on 2008-06-01
OK, so you will be using the restricted drivers.  If they don't work from within Ubuntu (System->Administration->Hardware Drivers), you can use EnvyNG to install the restricted drivers from ATI's website.  See: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by stickx911 on 2008-06-01
thanks for the help.

---

### Post by gunnar123 on 2009-04-20
> **Rocket2DMn said:**
> Try rebooting into the recovery mode kernel (choose the root terminal), and run
```
apt-get remove --purge xorg-driver-fglrx
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Allow the system to reboot normally and you should be OK.  What is your video card?  We might still be able to get compiz to work.  Please post:
```
lspci | grep VGA
```
If you have an older ATI card, like Radeon 9500 or older, see here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Thanks this helped me recover my laptop after some clueless messing with Penguin Racer destroyed my driver setup !  Made the rest of my day :)

---

