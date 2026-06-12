---
title: "Cannot hear music/videos"
date: 2009-07-23
forum: Multimedia Software
---

### Post by magh-87 on 2009-07-23
I apologize if my specific question has been answered but I have been searching for the forums and have not been able to determine why I cannot hear audio from my laptop anymore. I can play the same files on my Windows partition so I know that it's not the sound card. I've check my alsamixer and followed the steps in [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") but to no avail so far.

Any suggestions or ideas to why this has happened and what I could do to fix it would be greatly appreciated.

Thanks!

---

### Post by magh-87 on 2009-07-24
I'm sure that I'm missing something simple here but I can't seem to figure out what it is. When I initially installed 9.04, everything was working great. It seems like after an update, I lost my sound but I'm not sure if I can pinpoint it to an update or not. Can anyone point me in the right direction?

magh

---

### Post by igorzwx on 2009-07-24
aplay -l

---

### Post by magh-87 on 2009-07-24
```
magnus@magnus-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
magnus@magnus-laptop:~$ 
```

---

### Post by igorzwx on 2009-07-24
Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)

---

### Post by magh-87 on 2009-07-24
> **igorzwx said:**
> Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://www.opensound.com/osshw.html](http://www.opensound.com/osshw.html)

```
110    oss_ich	pci8086,266e	Intel AC97 (ICH6)
```

Both sites list my hardware.

---

### Post by igorzwx on 2009-07-24
Install another Ubuntu 9.04 in dual boot
and try OSS4

---

### Post by magh-87 on 2009-07-24
Alright, I'll give that a shot now.

---

### Post by magh-87 on 2009-07-24
Weird, it looks like I have 2 versions of 9.04 on this laptop already. The beta and the official release. I'm not entirely certain which one I've been using recently :confused:

---

### Post by igorzwx on 2009-07-24
You boot the first, perhaps?

---

### Post by magh-87 on 2009-07-24
I just loaded the Live CD and it plays sound. Yes, I load the first one but I'm not sure if it's the beta or release.

I have 
2.6.28-13-generic
2.6.28-11-generic

---

### Post by igorzwx on 2009-07-24
You may find your Ubuntus in this file:

/boot/grub/menu.lst

Copy the boot entries

---

### Post by igorzwx on 2009-07-24
If you just free some space on a disk.
You can install to the largerst available free space (option in menu)

free means without partitions

---

### Post by magh-87 on 2009-07-24
> **igorzwx said:**
> You may find your Ubuntus in this file:

/boot/grub/menu.lst

Copy the boot entries
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		59d3be75-58dc-45cb-a62f-6b83baeb4142
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=59d3be75-58dc-45cb-a62f-6b83baeb4142 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		59d3be75-58dc-45cb-a62f-6b83baeb4142
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=59d3be75-58dc-45cb-a62f-6b83baeb4142 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		59d3be75-58dc-45cb-a62f-6b83baeb4142
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=59d3be75-58dc-45cb-a62f-6b83baeb4142 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		59d3be75-58dc-45cb-a62f-6b83baeb4142
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=59d3be75-58dc-45cb-a62f-6b83baeb4142 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		59d3be75-58dc-45cb-a62f-6b83baeb4142
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by igorzwx on 2009-07-24
I have one normal Ubuntu 9.04

and I have this:

/boot/grub/menu.lst

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8359e1ff-bc60-4f8e-a7e9-90e1d8c37383
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8359e1ff-bc60-4f8e-a7e9-90e1d8c37383 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8359e1ff-bc60-4f8e-a7e9-90e1d8c37383
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8359e1ff-bc60-4f8e-a7e9-90e1d8c37383 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8359e1ff-bc60-4f8e-a7e9-90e1d8c37383
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8359e1ff-bc60-4f8e-a7e9-90e1d8c37383 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8359e1ff-bc60-4f8e-a7e9-90e1d8c37383
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8359e1ff-bc60-4f8e-a7e9-90e1d8c37383 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8359e1ff-bc60-4f8e-a7e9-90e1d8c37383
kernel        /boot/memtest86+.bin
quiet

---

### Post by magh-87 on 2009-07-24
> **igorzwx said:**
> If you just free some space on a disk.
You can install to the largerst available free space (option in menu)

free means without partitions

I've been working on making some free space recently. However since most of my external hard drives are tied up I've resulted in having to transfer the files via wifi through my network. A painfully slow process. I'll still if I can't find a usb stick though

---

### Post by igorzwx on 2009-07-24
You have one Ubuntu and I too.
It was update of the kernel

---

### Post by igorzwx on 2009-07-24
make free space
reboot
select install to hard disk
select install to the largest available free space.
it will go automatically

---

### Post by igorzwx on 2009-07-24
here, in Germany, is 02:30
I will be in the forum for 30 minutes or so
We may continue tomorrow

---

### Post by magh-87 on 2009-07-24
> **igorzwx said:**
> here, in Germany, is 02:30
I will be in the forum for 30 minutes or so
We may continue tomorrow

That works for me, I need to go to work (over night shift). My girlfriend is going to Germany in September for 11 months.

Talk to you tomorrow, thanks for all the help :)

---

### Post by igorzwx on 2009-07-24
You are well come
bis Morgen

---

### Post by martinbaselier on 2009-07-24
just FYI: If you have the same applications installed there will be no difference between the beta and the final, since both of them update. Only settings and installed applications would make a difference.

---

### Post by magh-87 on 2009-07-25
> **martinbaselier said:**
> just FYI: If you have the same applications installed there will be no difference between the beta and the final, since both of them update. Only settings and installed applications would make a difference.

Yeah I'm aware of that, since I'm going to do a clean install and just save my files over, I'll have to be more specific with what I choose to update.

I'm curious about OSS4. Where do I find it? It seems that my laptop is compatible with it so how could I make a change to it? Hopefully the answer isn't right under my nose :wink:

---

### Post by igorzwx on 2009-07-25
You should try to follow this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Carefully!!!

If you have questions, you can ask me (or better Martin)

---

### Post by magh-87 on 2009-07-26
> **igorzwx said:**
> You should try to follow this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Carefully!!!

If you have questions, you can ask me (or better Martin)

Success!

Sorry about the long delay. I got injured at work and had to look after myself for once instead of my computer. Thank you both for the help. Hopefully now I can help others with their sound issues =)

---

### Post by martinbaselier on 2009-07-26
Check the links in my signature for a tutorial.

---

### Post by igorzwx on 2009-07-26
Great!!!

You can try Skype and Ekiga with OSS4
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

Best,
Igor

---

### Post by igorzwx on 2009-07-26
This might be useful too:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

** 	[COLOR=#008C00][B][all variants]**[/COLOR] Comprehensive Multimedia & Video Howto  
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

[/B][COLOR=DarkRed]**Reason for Howto:**[/COLOR] This howto, guide, tutorial, or whatever you wish to call it, was written to help those who struggle to, and/or become frustrated while trying to get streaming media, Java, DVD playback (and so on) to work properly, and those who are having general multimedia and video issues. Please keep in mind, however, that Ubuntu has a helpful feature, where if you click on a certain file, or try to view Flash videos, a dialog should pop-up and ask if you want to install proprietary packages that are neccessary to play those formats. This howto is for users who are still having issues, or simply want as many different formats working as possible with just a few commands.

---

