---
title: "rtl8187b, monitor mode?"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Desolator64 on 2009-05-05
Hello!
I'm trying to get Kismet to work with my rtl8187b card. I successfully configured kismet.conf to work with my card (source=rt8180,wlan0,Realtek) and am now at a halt because it's telling me it is unable to enter monitor mode.
```
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (Realtek): Enabling monitor mode for rt8180 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Device or resource busy.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.

```I'm under the impression that my card does not support monitor mode with the default driver supplied by the current version of Ubuntu. I've read many threads and blogs about getting this specific card to work with Linux but few to none mentioned its capabilities of entering monitor mode. Does anybody know where I can get a driver that will allow me to use Kismet?

Thanks

---

### Post by Desolator64 on 2009-05-05
I found a cracked driver floating around that was made by a guy named Cuervo but after reading the readme (which doesn't list Ubuntu) and trying for a couple hours to get it to build I gave up. The blog it was hosted on says it works in Ubuntu so I'm kinda lost on this one. Help?

---

### Post by Desolator64 on 2009-05-07
[IMG]http://www.w3bbo.com/forums/Bump-Head_injury.jpg[/IMG]

---

### Post by Desolator64 on 2009-05-08
I refuse to give up. Somebody has the answer to my question.

---

### Post by Desolator64 on 2009-05-09
After doing more reading, I began following these steps: ([https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b))

I'm at the part in which you load the driver with:
sudo ./wlan0up


Unfortunately, I get 6 errors saying "insmod: can't read 'filename': No such file or directory" Obviously, it is trying to copy these modules to the kernel. I change directories to the location with these files and try to insmod manually but I get an error "Operation not permitted." I try with sudo and I get "invalid module format."

I read from 'man insmod' something about hyphens being a problem or whatever and all of these files have hyphens. I dunno.

---

### Post by Desolator64 on 2009-05-09
Apparently, the patch for this driver is for kernel 2.6.24 and I think I have 2.6.27. I wouldn't know how to find out if that is the case though.

(edit) I found that yes I do have 2.6.27. I guess I'll either have to revert or wait until someone supports the driver in the newer kernel.

Thanks for the help ubuntuforums.org! You provided me with a great place to blog about my problems and recieve zero help!  :D

---

### Post by mr_skater99 on 2009-07-15
I've got a similar card, and set up similar to yours - but kismet just works for me - no errors about not being able to get into monitor mode.

I am wondering if the default rt8180 driver supports monitor mode and injection???

Anyone got any idea?

---

