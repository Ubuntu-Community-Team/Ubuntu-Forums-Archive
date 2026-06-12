---
title: "QC-USB driver for Logitech Quickcam Web"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by greyfox1 on 2007-12-30
Hi all,

I'm having a problem installing the [QC-USB driver]("http://qce-ga.sourceforge.net/") and I'm running into a problem.  So far I haven't been able to find any existing information about this, so here it goes:

I'm using the script provided with the driver (quickcam.sh) and everything goes smoothly up until the point where the script attempts to load and test the driver.  That step fails-- the last few lines of the output are:

```

[  416.508711] usb 2-2: USB disconnect, address 2
[  420.147332] usb 2-2: new full speed USB device using ohci_hcd and address 6
[  420.332918] usb 2-2: configuration #1 chosen from 1 choice
[  420.536087 ] quickcam: Unknown symbol there_is_no_init_MUTEX_LOCKED_for_RT_semaphores
[  420.602958] quickcam: Unknown symbol there_is_no_init_MUTEX_LOCKED_for_RT_semaphores
[  420.612980] quickcam: Unknown symbol there_is_no_init_MUTEX_LOCKED_for_RT_semaphores
[!] The QuickCam driver failed to load!
```

A little bit about my setup:

    * I'm using Ubuntu Studio 7.10 with the 2.6.22-14 realtime kernel.
    * Version 0.6.6 of qc-usb driver.
    * lsusb info: Bus 002 Device 006: ID 046d:0850 Logitech, Inc. QuickCam Web 
    * Sensor info from system log: [   55.134221] quickcam: Sensor VV6410 detected
    * Running  "$ /sbin/lsmod | grep -i usb" produces:

```
snd_usb_audio          81408  0
snd_pcm                80644  4 snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_usb_lib            18176  1 snd_usb_audio
snd_hwdep              10500  3 snd_emux_synth,snd_usb_audio,snd_emu10k1
snd_rawmidi            25728  4 snd_seq_virmidi,snd_emu10k1,snd_usb_lib,snd_seq_midi
snd                    55172  17 snd_emux_synth,snd_seq_virmidi,snd_usb_audio,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            73536  0
usbhid                 30176  0
hid                    29056  1 usbhid
ide_core              118980  4 usb_storage,ide_cd,ide_disk,amd74xx
libusual               18704  1 usb_storage
scsi_mod              148844  5 sbp2,usb_storage,sg,sd_mod,libata
usbcore               139912  9 snd_usb_audio,snd_usb_lib,xpad,usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd
```

I think the "RT" part of the message may be related to my realtime kernel?  Maybe not.  I'm stumped.



Also, I've gone through [this tutorial]("http://ubuntuforums.org/showthread.php?t=642015") and unfortunately it seems that my webcam is not supported by that driver (I get "Could not connect to video device (/dev/video0)" when I launch camorama).



Help will be greatly appreciated!

---

### Post by papatrpt89 on 2007-12-30
I don't know how much help I can be, but I also own a logitech webcam, and it worked out of the box, with Kopete and a program called cheese (similar to OSXs photobooth).  It might be worth a shot just trying it outwith without worrying about drivers.

If you still have problems, there seems to be a thread here about logitech webcams:

[http://ubuntuforums.org/showthread.php?t=642015&highlight=logitech+webcam](http://ubuntuforums.org/showthread.php?t=642015&highlight=logitech+webcam)

Good luck!

---

### Post by greyfox1 on 2007-12-31
Thanks for the suggestion but that did not help.  My system doesn't really recognize the camera at this point, I believe.  Also the thread you mentioned is the second one I referenced in my original post.

I noticed a lot of references to /dev/video0 in reading about this and so far, /dev/video0 does not exist.  I suppose that's part of the problem.

---

### Post by papatrpt89 on 2007-12-31
Sorry, I'm pretty stumped :-?

---

### Post by greyfox1 on 2008-01-02
That's ok m8, thanks for the suggestion anyway.  

*Bump* Anyone else have suggestions?  TIA.

---

### Post by s4mdf0o1 on 2008-01-04
Hi
I've just also compiled a realtime kernel
I now have the same error
The webcam working before, so we might search for a "realtime" issue... :P

```
kernel: quickcam: Unknown symbol there_is_no_init_MUTEX_LOCKED_for_RT_semaphores
```

My own infos :
Linux 2.6.23.11-rt14 #1 SMP PREEMPT RT x86_64 (amd64)

Just a little up :P

---

### Post by s4mdf0o1 on 2008-01-04
I tried this solution :
[http://search.luky.org/linux-kernel.2005/msg39997.html]("http://search.luky.org/linux-kernel.2005/msg39997.html")

> A quick fix would be changing the 'struct semaphore' to 'struct compat_semaphore'.

no success :'(
... try again ;)

Edit:
Sorry I made an error : it works !
I was compiling using m-a which overwrites my changes

So you just have to change what's told in quickcam.h
and rebuild
That's it ;)
NB: take care using m-a, to create a new modified/compressed qc-usb-modules.tar.gz in /usr/src/ ! :P

---

### Post by greyfox1 on 2008-01-04
Hi, thanks for the reply-- but I'm not clear on what exactly you were doing.  Could you tell me the commands you used?  I don't know what all this m-a stuff you refer to means.  All I've been doing is navigating to the directory I untarred to and running 

./quickcam.sh

I changed "struct semaphore lock" to "struct compat_semaphore lock" in quickcam.h -- both in the directory where I untarred and /usr/src/modules/qc-usb-source/.  However I still get the original "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" error when the quickcam.sh tries to load the driver.  Please help, I would really like to get this working!!

---

### Post by s4mdf0o1 on 2008-01-05
What I've done :
```
cp /usr/src/qc-usb-modules.tar.gz{,.orig} #backup
cp /usr/src/qc-usb-modules.tar.gz /tmp # work copy
cd /tmp
tar xvzf qc-usb-modules.tar.gz
sed -i "s/struct semaphore lock/struct compat_semaphore lock/g" modules/qc-usb-source/quickcam.h
tar cvzf qc-usb-modules.tar.gz modules
mv qc-usb-modules.tar.gz /usr/src #overwrite
cd /usr/src
sudo apt-get install module-assistant
sudo m-a prepare
sudo m-a build qc-usb
dpkg -i qc-usb-modules-[your_version].deb
modprobe quickcam
```
That's it ;)

---

### Post by greyfox1 on 2008-01-05
Thanks again for your detailed instructions.  *However...*

I went through all the steps listed above with no problems or errors, but my cam still doesn't work!

Kopete freezes when I try to access the "video devices" section of the options.

Skype lists my quickcam as an available device, but when I click "test" the green light on the cam blinks on, then off and I never see any picture.

Camorama starts up, but tells me it was unable to capture an image and then crashes.  However the process continues to run in the background and shows up in the System Monitor as "Uninterruptible".  The only way I've found to kill it is to reboot.

Sometimes when trying any of the programs above my system just freezes and I am forced to hard boot.

As always, any help will be appreciated!!

---

### Post by s4mdf0o1 on 2008-01-05
Well at this point I'm affraid it surpasses my knowledge :P
I think I'd try to catch errors by launching apps in xterm
And try to googleize with them ...
Realtime kernels are appearing, so we'll find bugs for some time :'(

---

### Post by greyfox1 on 2008-01-05
Darn, I thought it might come to this.  I'm kinda stuck-- I use the RT kernel for music composition, but now it's creating problems with the webcam driver.  I guess I'll have to stick with XP under VirtualBox for my webcam needs at present :(

Thanks for all your help so far, though.

---

### Post by greyfox1 on 2008-01-08
*bump*  Anyone else want to help me take a swing at this?

---

### Post by greyfox1 on 2008-01-16
*Bump*  Anyone?

---

### Post by milliman on 2008-02-16
I have been fighting with installing my Logitech Quickcam Web with Gutsy (7.10) and my 2.6.22-14 kernel.  The only other strange device driver that I have installed is the em28xx for my TV tuner USB card.  The web cam worked in the previous version of Ubuntu using the native drivers.  It does not work with the native quickcam.ko so I followed the instructions in this thread.  When I load the quickcam driver, I receive the message below.

FATAL: Error inserting quickcam (/lib/modules/2.6.22-14-generic/ubuntu/media/quickcam/quickcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)

**dmesg output:**
[ 1780.336140] quickcam: disagrees about version of symbol video_devdata
[ 1780.336152] quickcam: Unknown symbol video_devdata
[ 1780.336425] quickcam: disagrees about version of symbol video_unregister_device
[ 1780.336429] quickcam: Unknown symbol video_unregister_device
[ 1780.336569] quickcam: disagrees about version of symbol video_register_device
[ 1780.336572] quickcam: Unknown symbol video_register_device

I have tried leaving the structure definition alone, I have changed the structure definition as recommended, I have compiled the package using the shell script, and I have made the deb file as recommended.  Each fail differently.

What is going on here?  Some people have this thing working and other's don't.  Is there a definitive HOWTO or script that will get this thing going.  I would wait for Hardy, but I can't seem to get the alpha or daily to run on this machine yet.

Thanks for your help!

---

### Post by nickrout on 2008-02-18
I too have a problem with the quicktime module and the linux-rt kernel, however it works fine with the normal kernel. 

I don't really have much use for the webcam and it is pretty low quality, so for the times I need it I can switch back to the non realtime kernel if I want to use it.

However it does bother me that ubuntu seem to be shipping a non working driver with the rt kernel, that works fine in the non-rt kernel.

EDIT: bug filed: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/193078](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/193078)

---

### Post by jdogzilla on 2008-02-27
Hello all, I too am having problems with my Quickcam Web device.  This is the current quickcam.ko module that I have on my machine

-rw-r--r-- 1 root root 85296 2007-10-13 00:43 /lib/modules/2.6.22-14-generic/ubuntu/media/quickcam/quickcam.ko

When I follow the instructions in this thread and compile and create a new module, it makes a new quickcam.ko module and puts it in another directory.  

In that case, how do I know which module is loading up when my camera is connected?

How can I determine what package the first quickcam.ko module came from, and uninstall it?

How can I blacklist the quickcam module so that it does not load up when I connect my camera?

Thanks

---

