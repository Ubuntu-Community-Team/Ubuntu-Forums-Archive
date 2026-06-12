---
title: "acer aspire one"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by shane8002 on 2009-03-16
hey guys ive had the acer aspire one for about 4 months now with ubuntu intrepid on it, jus wondering if anyone else has had problems with the wireless card using the madwifi driver. It wont connect to wpa networks and it wont connect at some of the local wifi hot spots which dont even use encryption. Just wanted to know if anyone else was having the same issues.

---

### Post by pjalegria on 2009-03-16
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by albandy on 2009-03-16
use linux4one, it's a distro based on ubuntu but modified to support the acer aspire one netbook

[http://www.linux4one.it/](http://www.linux4one.it/)

---

### Post by shane8002 on 2009-03-16
> **albandy said:**
> use linux4one, it's a distro based on ubuntu but modified to support the acer aspire one netbook

[http://www.linux4one.it/](http://www.linux4one.it/)

How good is it?

---

### Post by albandy on 2009-03-17
> **shane8002 said:**
> How good is it?

I use it in my netbook and all works

---

### Post by shane8002 on 2009-03-17
It looks great but ive read on some forums that everything dosent work out of the box, in particular the wireless.

---

### Post by .:Justus:. on 2009-03-17
> **shane8002 said:**
> It looks great but ive read on some forums that everything dosent work out of the box, in particular the wireless.

The distros main function is to support everything out of the box on the AAO.
So i don´t know where you read that^^

---

### Post by blazemore on 2009-03-17
The best thing to do is simply install the debs from this website, on your existing installation:
[http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

It's brilliant, just remember to disable madwifi before you reboot into the new kernel, or it might get confused.

---

### Post by shane8002 on 2009-03-18
Installed the kernel nothing works at all now as far as networking goes. No wireless at all. Also when i plug my cell phone in it automatically pops up as cdma mobile broadband and i can connect to it, dosent do anything at all now. Tried using my external usb wireless adapter and it works out the box in ubuntu because of the open source rt57 driver, jus plug in and connect, it dosent do anything now so my computer is now offically useless for connecting to the internet. Tried to reinstall the new kernel and it says a package manager is working, and there isnt one working at all. Advice on how to fix this would be great because im going to half to make another bootable usb stick to reinstall ubuntu and thats a real pain, and time consuming and i will lose all updates, compiz, the whole works.

---

### Post by blazemore on 2009-03-19
Sorry, I'm in the UK, so you posted at about 1 in the morning. :P

It's no problem because if it comes to it, you can use your original kernel again.
But this shouldn't be happening.
Try installing using the command-line.
Copy the .deb files to your home directory and run the command
```
sudo dpkg -i *sick*.deb
```

If it moans about overwriting existing files, or stuff already being installed, don't carry on but tell me.

---

### Post by shane8002 on 2009-03-19
Sorry about the time thing im on eastern us time haha.;) I reinstalled the package but it's still doing the same thing. There some error code coming up when grub loads, it's about three lines but it's impossible to read because it only flashes on the screen for about 1 second.

---

### Post by blazemore on 2009-03-19
```
sudo dpkg -P *sick*.deb
```
To purge the package

Then install them again with
```
sudo dpkg -i *image*.deb && sudo dpkg -i *head*.deb
```

---

### Post by shane8002 on 2009-03-20
Well its still not working its saying during reinstallation process that there is a symbolic link but cannot be read, and an error while processing *headers*. I guess ill just revert back to the old kernel. Maybe jaunty will be better on the AA1 when the stable realease is put out. Ill need to know how to get back to the old kernel because I don't know how, havent gotten that far with ubuntu yet.

---

### Post by blazemore on 2009-03-20
So you totally removed the package with -P?
What error is it giving?

---

### Post by shane8002 on 2009-03-20
Its saying the headers package and image package is not available then it gives the commands to examine archive and to list their contents.

---

### Post by sloggerkhan on 2009-03-20
I have an aspire one with fedora 10 that works fine with the wireless, but outside of hardware compatibility, I think fedora sucks, it's package manager is really really really really really really really really really slow.

---

### Post by shane8002 on 2009-03-20
Yeah im not a big fan of fedora. The package manager isnt up to par like you said and it dosent have the good network options like ubuntu. Plus when i did a fresh install, the first thing that pops up is kernel faliure ha. The wireless isn't the only issue on the acer, it just isnt nearly as supported hardware wise as some of the laptops out there. I have converted alot of friends to ubuntu and have never the issues i have had with the acer, and I cant believe the hardware isnt better supported because I read somewhere that the aspire one is in the top ten of most sold for the past couple years.

---

### Post by sloggerkhan on 2009-03-20
While I think that package manager is slow, and there are some other downsides, I haven't had any hardware compatibility issues with my aspire one on fedora 10 and it does boot in 20 seconds easily.

---

### Post by blazemore on 2009-03-22
Okay let's download again
```
sudo su
mkdir aspireone
cd aspireone
wget http://kernelmirror.linxisp.com/releases/linux-image-2.6.28sickboy-kuki_0.4_i386.deb
wget http://kernelmirror.linxisp.com/releases/linux-headers-2.6.28sickboy-kuki_0.4_i386.deb
dpkg -i *.deb

```

---

### Post by shane8002 on 2009-03-23
Blazemore I did everything like you said, and I also unloaded any wireless drivers in use. Again I noticed faster boot times volume seemed louder on startup, but I couldnt connect to the internet through wireless or mobile broadband. Everything downloaded normal in the terminal so I didn't see the need to post but this is the code it gives during installation. By the way the error code popped up again when booting this kernel; same thing, its unreadable because its only up there for 1 sec.

```
root@hahahahahahahahahaha:/home/shane/aspireone# dpkg -i *.deb

(Reading database ... 149930 files and directories currently installed.)

Preparing to replace linux-headers-2.6.28sickboy-kuki 0.4 (using linux-headers-2.6.28sickboy-kuki_0.4_i386.deb) ...

Unpacking replacement linux-headers-2.6.28sickboy-kuki ...

Selecting previously deselected package linux-image-2.6.28sickboy-kuki.

Unpacking linux-image-2.6.28sickboy-kuki (from linux-image-2.6.28sickboy-kuki_0.4_i386.deb) ...

Done.

Setting up linux-headers-2.6.28sickboy-kuki (0.4) ...



Setting up linux-image-2.6.28sickboy-kuki (0.4) ...



 Hmm. There is a symbolic link /lib/modules/2.6.28sickboy-kuki/build

 However, I can not read it: No such file or directory

 Therefore, I am deleting /lib/modules/2.6.28sickboy-kuki/build





 Hmm. The package shipped with a symbolic link /lib/modules/2.6.28sickboy-kuki/source

 However, I can not read the target: No such file or directory

 Therefore, I am deleting /lib/modules/2.6.28sickboy-kuki/source



Running depmod.

Finding valid ramdisk creators.

Using mkinitramfs-kpkg to build the ramdisk.

Running postinst hook script update-grub.

Searching for GRUB installation directory ... found: /boot/grub

Searching for default file ... found: /boot/grub/default

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

Searching for splash image ... none found, skipping ...

Found kernel: /boot/vmlinuz-2.6.28sickboy-kuki

Found kernel: /boot/vmlinuz-2.6.27-11-generic

Found kernel: /boot/vmlinuz-2.6.27-7-generic

Found kernel: /boot/memtest86+.bin

Replacing config file /var/run/grub/menu.lst with new version

Updating /boot/grub/menu.lst ... done



Examining /etc/kernel/postinst.d.

run-parts: executing /etc/kernel/postinst.d/nvidia-common

```

---

### Post by blazemore on 2009-03-23
try
```
wget http://kernelmirror.linxisp.com/releases/madwifi-modules-2.6.28sickboy-kuki_0.9.4+r3772.20080716-1+0.4_i386.deb && sudo dpkg -i madwifi-modules-2.6.28sickboy-kuki_0.9.4+r3772.20080716-1+0.4_i386.deb
```

---

