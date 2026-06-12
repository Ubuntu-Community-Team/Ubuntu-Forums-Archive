---
title: "Problem with UVC driver &amp; QuickCam Fusion"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by priegog on 2007-11-10
Hi.
Just compiled and installed the UVC driver. But my dmesg output says something's wrong. Will post only relevant part of dmesg:
```

[ 2767.156000] usb 3-1.4: new high speed USB device using ehci_hcd and address 9
[ 2767.424000] usb 3-1.4: configuration #1 chosen from 1 choice
[ 2767.720000] uvcvideo: disagrees about version of symbol video_devdata
[ 2767.720000] uvcvideo: Unknown symbol video_devdata
[ 2767.724000] uvcvideo: disagrees about version of symbol video_unregister_device
[ 2767.724000] uvcvideo: Unknown symbol video_unregister_device
[ 2767.724000] uvcvideo: disagrees about version of symbol video_device_alloc
[ 2767.724000] uvcvideo: Unknown symbol video_device_alloc
[ 2767.724000] uvcvideo: disagrees about version of symbol video_register_device
[ 2767.724000] uvcvideo: Unknown symbol video_register_device
[ 2767.724000] uvcvideo: disagrees about version of symbol video_device_release
[ 2767.724000] uvcvideo: Unknown symbol video_device_release
[ 2768.424000] 9:3:3: cannot set freq 16000 to ep 0x86
[ 3711.580000] bcm43xx: MAC suspend failed
```

(BTW, someone should make a deb, newbies like me would very much appreciate it)

Now, I'm stuck. I can't uninstall because checkinstall spat out some error (will paste later) so I had to make install, and make uninstall gives out 
```

jerry@jerry-laptop:~/UVC$ sudo make uninstall
[sudo] password for jerry:
make: *** No rule to make target `uninstall'.  Stop.
```

Here's the checkinstall error, in case it's relevant (even tho i suspect not)
```

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../..' with matching i-node
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
rm: `/lib/modules/2.6.22-14-generic/kernel/drivers' changed dev/ino
make[1]: *** [_modinst_] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```

I'm desperate now, Please some help!

EDIT - BTW I'm using gutsy 32-bit with generic kernel

---

### Post by priegog on 2007-11-12
Bump...
Maybe I put this in the wrong category since it's a compilation error, and not strictly a video problem. If a moderator thinks it's appropriate, could he move it to general help please?
Thanks

---

### Post by Ubsl on 2007-11-23
Hi,

Today I have tried myself to install this driver and I got the same error in the "make install" procedure. It seems that Ubuntu 7.10 has already installed the uvc drivers (see [http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC]("http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC")  under " Noob question"). The only think what I've installed from the source is luvcview to test my webcam. After entering ```
luvcview -d /dev/video0 -f jpg -s 640x480
``` the webcam runs out of the box!

---

### Post by priegog on 2007-11-23
> **Ubsl said:**
> Hi,

Today I have tried myself to install this driver and I got the same error in the "make install" procedure. It seems that Ubuntu 7.10 has already installed the uvc drivers (see [http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC]("http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC")  under " Noob question"). The only think what I've installed from the source is luvcview to test my webcam. After entering ```
luvcview -d /dev/video0 -f jpg -s 640x480
``` the webcam runs out of the box!

Hi. I don't understand what that command is supposed to do, but it gives me some error, look.```
~$ luvcview -d /dev/video0 -f jpg -s 640x480
bash: luvcview: command not found
```
I'm a complete noob. You've been warned :).

---

### Post by Ubsl on 2007-11-24
Just follow the instructions at [http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC]("http://openfacts.berlios.de/index-en.phtml?title=Linux_UVC") under "Applications".

In point 2 you have to download with synaptic or apt-get the package "libsdl1.2-dev".

In the directory where you have unpacked the luvcview source files enter ```
make
``` and after it ```
sudo checkinstall
``` or ```
sudo make install
```.

If everything runs fine you should be able to run ```
luvcview -d /dev/video0 -f jpg -s 640x480
```

If the above command doesn't works may take a look in the README in the source directory of luvcview.

---

### Post by rsambuca on 2007-11-24
According to the UVC Developers [website,]("http://linux-uvc.berlios.de/") the earlier Quickcam Fusions can have problems.

---

### Post by priegog on 2007-11-24
> **rsambuca said:**
> According to the UVC Developers [website,]("http://linux-uvc.berlios.de/") the earlier Quickcam Fusions can have problems.
Thanks, I'm giving up now since the above command (after having installed luvcview) gives me some error about /dev/video0 not existing. I'll just come to terms with the fact that This cam will never work with linux.

---

