---
title: "I deleted network manager and need help getting it back."
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by goldenboy1 on 2009-08-17
[INDENT]Is there a way to get network manager back when you have deleted network manager and lost you internet connection on your PC? I have a seperate working laptop and a usb stick available running Vista.
 
Cheers, Chris
[/INDENT]

---

### Post by philcamlin on 2009-08-17
```
sudo apt-get install network-manager

```there you go :) just run it in terminal

---

### Post by goldenboy1 on 2009-08-17
Sorry apt get not working as i lost the internet connection.

---

### Post by AlexanderDGreat on 2009-08-17
Have you tried to enable the CDROM from the repository? I read that somewhere here in the forums if you don't have an internet connection.

---

### Post by Rawgers on 2009-08-17
If you can transfer, download Network Manager source (google) and transfer to your pc. Then follow the instructions given to install.

Or else, you can use the ubuntu cd as the above poster mentioned.

---

### Post by goldenboy1 on 2009-08-18
Ok how do I enable the cd

---

### Post by GeorgeVita on 2009-08-18
Hi **goldenboy1**,
try System > Administration > Software Sources and tick "installable from CD/DVD"

Insert CD, run System > Administration > Synaptic Package Manager find Network Manager right click it and "mark for installation"

If this did not work, we will try the 'real offline' method.

>>> What Ubuntu Version are you running?

Regards,
George

---

### Post by goldenboy1 on 2009-08-18
Hi,
 
Running 9.04 yet only have 6.06 on cd.
 
Was able to get the check mark option under 3rd party software ticked as this is the only place I found a check mark.
 
Synapic still wants to download from the net to install but obviously can't.
 
Cheers, Chris

---

### Post by GeorgeVita on 2009-08-18
Hi Chris,
now I am running 9.10 and I need some time to shut down, reboot to 9.04, purge 'network manager', connect install it back ... to check all dependencies maybe need to get it running. finishing I will have the requested info!

00:02 Hold on ...

00:07 booted from 9.04 to get the pppd line from my signature! ...

00:11 purged, installing again to check dependencies
00:12 it says only network-manager & network-manager-gnome (600K good!)

00:19 get the 2 .deb files below (**i386, Ubuntu 9.04**):
[http://packages.ubuntu.com/jaunty/i386/network-manager/download](http://packages.ubuntu.com/jaunty/i386/network-manager/download)
[http://packages.ubuntu.com/jaunty/i386/network-manager-gnome/download](http://packages.ubuntu.com/jaunty/i386/network-manager-gnome/download)

(or get them from my: [http://acomelectronics.com/GeorgeVita/nm0.7.1_U904_i386.zip](http://acomelectronics.com/GeorgeVita/nm0.7.1_U904_i386.zip))

copy them to desktop of the Ubuntu running PC, double click each icon and install them

Regards,
George

---

### Post by goldenboy1 on 2009-08-18
Thanks I will check in again soon.

---

### Post by GeorgeVita on 2009-08-18
... or get it here:
[http://acomelectronics.com/GeorgeVita/nm0.7.1_U904_i386.zip](http://acomelectronics.com/GeorgeVita/nm0.7.1_U904_i386.zip)

contains:
network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb
network-manager_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb
and checksums

---

### Post by goldenboy1 on 2009-08-18
Thanks that worked!  Still need help see next post.
 
Cheers, Chris

---

### Post by goldenboy1 on 2009-08-18
I now have network manager installed with no working wired connection.  I deleted Auto eth0 I don't know what I was thinking yesterday.  Help?

---

### Post by goldenboy1 on 2009-08-18
Tried your method with wicd instead and it worked like a charm.
 
Cheers, Chris

---

### Post by GeorgeVita on 2009-08-19
Hi **goldenboy1**, fine if you finally solve it!

Just for the 'History': I have read a lot of posts about using wicd instead of network manager, but I act like a modem (if something is not working I am trying a 'lower level' method). So from a non working GUI program (network manager) I prefer to try a 'terminal' one (wvdial) and if I cannot (missing from 9.04 .iso) I have the terminal command (pppd). After possible 'removal' of this my last option could be ... typing hex codes with my keyboard!

Regards,
George

---

### Post by AlexanderDGreat on 2009-08-20
Hi just for future reference go here:

/var/cache/apt/archives/

Do you see all those .deb files?

Now, you can use this resource whenver you want to reinstall something.

For example: sudo dpkg -i /var/cache/apt/archives/network-manager_*.deb

---

