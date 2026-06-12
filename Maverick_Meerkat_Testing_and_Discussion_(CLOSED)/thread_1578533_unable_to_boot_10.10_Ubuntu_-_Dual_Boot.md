---
title: "unable to boot 10.10 Ubuntu - Dual Boot"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jakeyyoyo on 2010-09-20
Hi,

I had one 1TB hard drive running Windows 7 pro and Ubuntu 10.04 side by side with no issues and two extra 1TB drives.

today I upgraded Ubuntu to 10.10 using the "press Alt+F2 and type in "update-manager -d"" path from within 10.04 and the update ran with no issues.

It asked to reboot, which I did but now when I select any of the Ubuntu options from the grub loader, I get taken to like a dos prompt where i enter my login info and thats it - I dont seem to be able to access the desktop at all.

I can boot into Windows 7 with no problems.

I have tried "startx", "gnome-session" and "gnome3-session" - none of which have any effect.

There doesnt appear to be any errors I can see.

I have tried installing latest grub from ubuntu recovery menu.

Any help would be much appreciated - even if it is just to allow me to roll back to 10.04.

Thanks

J

P.S. graphics card is ATI Radeon HD4350

---

### Post by Iowan on 2010-09-20
Moved to Maverick Meerkat Testing and Discussion

---

### Post by kansasnoob on 2010-09-20
> Any help would be much appreciated - even if it is just to allow me to roll back to 10.04.

Sadly it's not possible to "roll back". I'm having some trouble with Intel graphics as well.

This is why I multi-boot and always keep a stable version of Ubuntu/Debian on my box :)

Also this Beta has been more unstable than usual for me but after looking at the changes I think it's worth the trouble.

---

### Post by NightwishFan on 2010-09-21
Try running:
```
sudo apt-get update && sudo apt-get -f install && sudo apt-get install ubuntu-desktop
```

Then reboot. No desktop? Then:

Hold shift while booting; you will get a menu that lists kernels. You can try an older kernel if you have one to see if it helps. If not, then press E to edit the first kernel. Find the line that starts with **Kernel** or **Linux** I forget which. Press END to go to the end of the line, add a space and type:
```
nomodeset
```

Then push ctrl+x to boot. Does that help? If not for the future record. Please install only stable supported editions of Ubuntu if you do not ONLY wish to bugfix or develop. Also testing with a live CD first is always a good idea.

---

### Post by sdowney717 on 2010-09-21
>  I get taken to like a dos prompt where i enter my login info and thats it 

I was getting the same exact thing.
I was able to boot into an earlier kernel 2.6.32-14

The problem for me was the video driver. 
boot into recovery mode 
install the nvidia driver from the nvidia site
run it as ./nameoffile.run in recovery console
then it worked for me.

---

### Post by garvinrick4 on 2010-09-21
I have seen threads with this problem and they have had to remove gdm and clean and reinstall.

---

### Post by garvinrick4 on 2010-09-21
```
sudo apt-get remove gdm
```
```
sudo apt-get clean
```
```
sudo apt-get install gdm
```
```
sudo apt-get reboot
```

---

### Post by jakeyyoyo on 2010-09-21
A huge thank you to everyone who has posted suggestions - I will try them as soon as I get back from work tonight and let you know how I get on.
Thanks _very_ much.
J

---

