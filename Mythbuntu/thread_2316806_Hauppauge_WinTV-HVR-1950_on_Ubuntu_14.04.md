---
title: "Hauppauge WinTV-HVR-1950 on Ubuntu 14.04"
date: 2016-03-11
forum: Mythbuntu
---

### Post by insanity54 on 2016-03-11
Hi there. I'm trying to get this HVR working for a mythbuntu setup. I've gone through the [linuxtv.org]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1950") guides on this, and found the [official Hauppauge tutorial]("http://www.hauppauge.com/site/support/linux.html") for setting this up on 14.04. I'm having difficulty patching my kernel, because kernel versions have changed since their guide was created. Here's what I've done so far:

[LIST]
[*] install fresh Ubuntu 14.04.2
[*] run software updater to get ubuntu up-to-date
[*] noticed ubuntu was using linux kernel 3.16.0, which was perfect, because this is what the [hauppauge guide]("http://www.hauppauge.com/site/support/install_ubuntu14_04_2-kernel-3.16.txt") used.
[*] tried to find Hauppauge tuner kernel patch that they used in their guide (hvr-9x5-19x5-22x5-kernel-3.16-2015-05-21.patch.tar.xz)
[*] could not find ^ on their website, could only find tuner kernel patch for 3.19! (hvr-9x5-19x5-22x5-kernel-3.19-2015-07-10-v2.patch.tar.xz)
[*] installed ubuntu kernel 3.19.0-51 using `$ apt-get -y install linux-image-generic-lts-vivid linux-headers-generic-lts-vivid`
[*] reboot
[*] cd to /usr/src
[*] extract tuner kernel patch to /usr/src
[*] apply patch using `sudo patch -p1 < hvr-9x5-19x5-22x5-kernel-3.19-2015-07-10-V2.patch`
[/LIST]


two problems when trying to patch:

[LIST=1]
[*] the patch instructions seem to be trying to overwrite files (I just did the default option 'n')
[*] the patch instructions seem to be looking for files which do not exist
[/LIST]


```
patching file drivers/media/dvb-frontends/Kconfig
patching file drivers/media/dvb-frontends/Makefile
The next patch would create the file drivers/media/dvb-frontends/lgdt3306a.c,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/lgdt3306a.h,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/si2168b.c,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/si2168b.h,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/si2168b_priv.h,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/silg.c,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file drivers/media/dvb-frontends/silg.h,
which already exists!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
1 out of 1 hunk ignored
patching file drivers/media/pci/saa7164/Kconfig
can't find file to patch at input line 14400
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/drivers/media/pci/saa7164/saa7164-api.c b/drivers/media/pci/saa7164/saa7164-api.c
|index 4f3b1dd..8f31afb 100644
|--- a/drivers/media/pci/saa7164/saa7164-api.c
|+++ b/drivers/media/pci/saa7164/saa7164-api.c
--------------------------
File to patch: 

```


I'm a bit out of my league here. I have run very basic patches before, but never a kernel patch or a patch that ran on multiple files. What do I need to do here to get past this? Thanks in advance.

---

### Post by insanity54 on 2016-03-12
Bumping. Is there perhaps a better subforum for this topic?

---

### Post by uteck on 2016-03-13
It is safe to say yes and overwrite the files when applying the patch, that is how the files get patched.
Then you can build the new kernel and new driver you need.

---

### Post by insanity54 on 2016-03-14
Thanks for the reply, uteck. That would address one of two issues, the issue of the overwriting files. The other issue is that the patch is looking for files which do not exist. I don't know what to do about that.

Anyway, I think I got it working without having to patch my kernel. I checked dmesg after plugging in the HVR-1950, and this is what I saw:

```
[132760.270414] usb 2-1.2: new high-speed USB device number 3 using ehci-pci
[132760.366715] usb 2-1.2: New USB device found, idVendor=2040, idProduct=7501
[132760.366720] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[132760.366723] usb 2-1.2: Product: WinTV
[132760.366726] usb 2-1.2: Manufacturer: Hauppauge
[132760.366728] usb 2-1.2: SerialNumber: 7300-00-F06EFF6D
[132760.456404] pvrusb2: Hardware description: WinTV HVR-1950 Model 751xx
[132760.456643] usbcore: registered new interface driver pvrusb2
[132760.456645] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[132760.456647] pvrusb2: Debug mask is 31 (0x1f)
[132761.455769] usb 2-1.2: Direct firmware load for v4l-pvrusb2-73xxx-01.fw failed with error -2
[132761.455782] pvrusb2: ***WARNING*** Device fx2 controller firmware seems to be missing.
[132761.455786] pvrusb2: Did you install the pvrusb2 firmware files in their proper location?
[132761.455790] pvrusb2: request_firmware unable to locate fx2 controller file v4l-pvrusb2-73xxx-01.fw
[132761.455793] pvrusb2: Failure uploading firmware1
[132761.455797] pvrusb2: Device initialization was not successful.
[132761.455800] pvrusb2: Giving up since device microcontroller firmware appears to be missing.
```

dmesg says firmware is missing. I did some googling about that file, v4l-pvrusb2-73xxx-01.fw and I found it available for download.

I'm thinking DVB support is baked into the 3.19 kernel, and all I needed to do was install firmware. I downloaded [v4l-pvrusb2-73xxx-01.fw]("http://www.steventoth.net/linux/hvr1950/v4l-pvrusb2-73xxx-01.fw")(MD5 c6b01cb318b909cc52d2cf643ca269a1), copied it to /lib/firmware, then opened up Kaffeine for testing. I was able to scan for channels, and watch TV.

So unless there's some feature not available in mythtv unless I patch my kernel, I'm golden!

---

