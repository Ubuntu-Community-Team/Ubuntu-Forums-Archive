---
title: "mythbuntu installation problem"
date: 2008-10-12
forum: Mythbuntu
---

### Post by 404wanderer on 2008-10-12
Hello all,
apologies if this has already been asked.

Mythbuntu is dropping out to the initramfs prompt when I try to do an install or run the live desktop. How do I turn off the quiet startup or see any logs so I can see where it is dropping out?

Thanks,
wanderer.

---

### Post by nasha on 2008-10-12
This thread may help

[HTML]http://ubuntuforums.org/showthread.php?t=934767&highlight=initramfs[/HTML]

---

### Post by 404wanderer on 2008-10-13
Thanks for the reply.

I downloaded the alternate cd and tried an install from that. I removed the quiet from the command line and it seems that the install is failing because it cannot find the device associated with the CD-drive. I tried using the "all_generic_ide option" but that failed.

I am using a sata connected Pioneer bdc-s02bk blue-ray drive.

How do I find out what device name this would show up as (it is using sata channel 3)?
Do I need a seperate driver? If so, any ideas which I should use?

Sorry for all the questions, I have never used this type of hardware before with Ubuntu.

---

### Post by madman_lxl on 2008-10-13
Have you by any chance tried hooking up an old IDE or Non-bluray SATA drive to install Mythbuntu? Its just I've also had problems with installing linux from blu-ray drives. Found it easier to get installed with an old IDE or SATA DVD first.

---

### Post by nasha on 2008-10-13
At least we got to the bottom of the problem!
Id follow the last posters suggestion. Support for HD content is very limited under linux, so i would imagine the hardware support is also lacking

---

### Post by 404wanderer on 2008-10-18
Ok, so I checked out the motherboard and it has no IDE connectors, so I'm stuck with using my one and only sata cd-drive - the blu-ray one which doesn't get recongised. 

So, I thought I would boot ubuntu off a USB flash drive. No worries and after only a day of messing around I managed to get a bootable mythbuntu usb flash drive. I select the install option and yet again it fails because it can't find a cd drive. I don't even want it to find a cd-drive :mad:, I just want it to install from the USB flash drive.

So, anyone any ideas how I build a system when I can't boot from the CD or from a flash drive and I have no ability to connect an IDE CD and don't have a USB CD-Drive.

The really annoying thing is that MS Vista goes on straight out of the box:mad:

---

### Post by 404wanderer on 2008-10-18
ok, got a bit further. Using instructions here - [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The install now fails at the "load installer components from CD" as it says it failed to copy the file (doesn't say which file). Are the install logs accesible anywhere so I can find out what is going on?

wanderer

---

### Post by 404wanderer on 2008-10-19
Ok, a bit further in the saga of my mythbuntu install.

I fixed my flash boot disk, and I can now boot from it. The first problem was caused by the unebootin application trying to write a symbolic link to a fat filesystem. I manually changed the stable directory to be a copy of the hardy directory and now I get further through the install process :)

I figured out how to get the syslog off the device and copied to the flash disc as well. The error that is now stopping the install is -

```

DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Oct 19 21:50:10 anna[22306]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Oct 19 21:50:10 anna[22306]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored) 
Oct 19 21:50:10 anna[22306]: DEBUG: resolver (efi-modules): package doesn't exist (ignored) 
Oct 19 21:50:11 cdrom-retriever: error: Unable to find 'pool/main/l/linux/fs-secondary-modules-2.6.24-19-generic-di_2.6.24-19.34_amd64.udeb'.
Oct 19 21:50:11 anna[22306]: WARNING **: package retrieval failed 

```

:(

Anyone any ideas?

Cheers,

wanderer.

---

### Post by 404wanderer on 2008-10-25
Ok, fixed. Just gave up and booted from an external USB cdrom.

---

