---
title: "Skype and Cheese not working with 11.10"
date: 2011-10-27
forum: Multimedia Software
---

### Post by smi402 on 2011-10-27
I have installed Ubuntu 11.10 from the **Ubuntu-11.10-alternate-amd64** disc and it is working properly. My webcam is a **Logitech Pro 9000** and I have used that webcam with both *cheese* and *skype* in Ubuntu 11.04 without any problems. *lsusb* indicates the webcam has been found under Ubuntu 11.10 and the webcam application *guvcview* displays video and seems to work fine.

The Canonical Partners repository was added and *skype:i386* and *cheese* were installed. But, running *cheese* from a terminal results in "Segmentation error". Running *cheese* from the dashboard launcher causes the launcher icon to pulse a few times and then disappear. Skype put a launcher icon on the launcher bar, but it does nothing when pressed. Running *skype* from a terminal launches the application and I can log into Skype. When going through the Skype Test Call I can hear all the responses from the test call (so my audio is working) but my microphone is not picking up my voice and playing it back.

I have been through other threads related to similar issues with Ubuntu 11.10 but many of the suggested fixes seemed to apply to alpha and beta releases rather than the final Official Release which I am using. I also get the feeling that part of this problem may be specific to certain webcam models as some have reported these applications working on 11.10 installations with other webcam models.

Any advice on getting these applications to work on my system would be much appreciated as we have used Skype quite a lot to keep in touch with family members in other countries. :(

---

### Post by smi402 on 2011-10-27
**Update:** I have now managed to get some playback sound during the Skype Test Call by increasing the Input Volume in my Sound Settings up to near the maximum level. My voice is being returned at a low level, but is being played back at twice the rate so is unintelligible. The instructions being provided during the Skype Test Call are being output at the correct rate and volume. It sounds like a sampling rate problem.

It is pretty annoying to go from a working system in 11.04 to a broken system in 11.10!! :(

---

### Post by no2498 on 2011-10-27
look in your system/preferences startup programs turn off anything to do with a cam restart the computer

---

### Post by smi402 on 2011-10-27
Thanks for the suggestion no2498. I am running the Unity desktop at present. However I do not see anything in the /etc/xdg/autostart directory that would start webcam applications at startup, but someone might like to check the list below.
```
frank@server:/etc/xdg/autostart$ ls -l
total 124
-rw-r--r-- 1 root root  306 2011-09-27 13:45 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  422 2011-09-27 02:36 bluetooth-applet.desktop
-rw-r--r-- 1 root root  227 2011-09-27 02:36 bluetooth-applet-unity.desktop
-rw-r--r-- 1 root root  365 2011-09-27 19:04 deja-dup-monitor.desktop
-rw-r--r-- 1 root root  501 2011-08-26 20:15 gdu-notification-daemon.desktop
-rw-r--r-- 1 root root  375 2011-10-05 04:00 gnome-fallback-mount-helper.desktop
-rw-r--r-- 1 root root  461 2011-10-19 11:44 gnome-keyring-gpg.desktop
-rw-r--r-- 1 root root  489 2011-10-19 11:44 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root  482 2011-10-19 11:44 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root  464 2011-10-19 11:44 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root  297 2011-10-05 04:00 gnome-settings-daemon.desktop
-rw-r--r-- 1 root root  538 2011-10-06 20:58 gnome-sound-applet.desktop
-rw-r--r-- 1 root root  309 2011-09-27 03:17 gnome-user-share.desktop
-rw-r--r-- 1 root root  279 2011-09-27 07:25 gsettings-data-convert.desktop
-rw-r--r-- 1 root root  353 2011-10-05 04:49 gwibber.desktop
-rw-r--r-- 1 root root  372 2011-10-06 14:37 jockey-gtk.desktop
-rw-r--r-- 1 root root  210 2011-10-01 00:36 nautilus-autostart.desktop
-rw-r--r-- 1 root root 3872 2011-10-04 07:28 nm-applet.desktop
lrwxrwxrwx 1 root root   59 2011-10-26 09:46 nvidia-autostart.desktop -> /etc/alternatives/x86_64-linux-gnu_nvidia-autostart.desktop
-rw-r--r-- 1 root root  291 2011-09-26 04:35 onboard-autostart.desktop
-rw-r--r-- 1 root root  322 2011-09-27 13:47 orca-autostart.desktop
-rw-r--r-- 1 root root 4676 2011-09-07 15:42 polkit-gnome-authentication-agent-1.desktop
-rw-r--r-- 1 root root  379 2011-09-24 22:30 print-applet.desktop
-rw-r--r-- 1 root root 3920 2011-10-06 19:20 pulseaudio.desktop
-rw-r--r-- 1 root root  256 2011-10-06 19:20 pulseaudio-kde.desktop
-rw-r--r-- 1 root root  378 2011-09-09 22:02 telepathy-indicator.desktop
-rw-r--r-- 1 root root  222 2011-09-28 02:11 ubuntuone-launch.desktop
-rw-r--r-- 1 root root  285 2011-10-06 06:04 update-notifier.desktop
-rw-r--r-- 1 root root  307 2011-07-01 23:29 user-dirs-update-gtk.desktop
-rw-r--r-- 1 root root  372 2011-09-29 18:56 vino-server.desktop
-rw-r--r-- 1 root root  336 2011-09-23 01:13 zeitgeist-datahub.desktop

```

---

### Post by smi402 on 2011-10-27
Some further information that may help someone pinpoint these problems:

***lsusb*** recognises the webcam:
```
frank@server:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 003: ID 1d57:0008  
frank@server:~$
``` 

After rebooting and immediately searching ***dmesg*** for **cheese** nothing is reported. However after running ***cheese*** from a terminal ***dmesg*** provides the following error message related to **libnvidia-glcore.so.280.13**.
```
frank@server:~$ dmesg | grep cheese
frank@server:~$ cheese
Segmentation fault
frank@server:~$ dmesg | grep cheese
[   74.037878] cheese[2486]: segfault at fffffffffffffff8 ip 00007fb51b845b44 sp 00007fff095a42e0 error 4 in libnvidia-glcore.so.280.13[7fb51a843000+15f4000]
frank@server:~$ 
```

---

### Post by smi402 on 2011-10-27
**Progress!!**

I am running Ubuntu 11.10 on a SSD and had installed a **ramdisk** for /tmp as many recommend with Solid State Disks. This was done by adding the following code line to /etc/fstab. 
```
/tmp tmpfs nodev,nosuid,noexec,mode=1777  0  0
```
After noting the error being reported by ***dmesg*** in my previous post I commented this line out in /etc/fstab and rebooted. ***cheese*** now works and the Skype sound input quality problem that I had previously has also been fixed. BUT the video colors and quality are very poor as many have noted on this forum earlier - I note a bug report is current for that problem. Video quality and colors are good with ***guvcview***. The launcher icon for ***cheese*** now works, but the ***skype*** launcher icon still just pulses and does nothing - I still have to start ***skype*** in a terminal.

So, it seems setting up a ramdisk for /tmp is causing some memory conflict that results in ***cheese*** producing a Segmentation Error and Skype sound input problems. This machine has 4Gb of memory.

---

### Post by no2498 on 2011-10-28
? you have 64 bit skype
i think ive seen you need to instal the 32 bit lib's
this is for 32 bit only

in a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype




#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

click enter

---

### Post by smi402 on 2011-10-28
Thanks again no2498. Yes I am running the 64bit version of Ubuntu 11.10 installed from the Final Release alternate-amd64 disc. This final release amd64 is supposed to be set up for using multi-arch so I installed the skype:i386 package as recommended by Ubuntu:

[http://askubuntu.com/questions/7498/how-do-i-install-skype]("http://askubuntu.com/questions/7498/how-do-i-install-skype")

Upon running skype from a terminal (the launcher icon doesn't work) and after removing the ramdisk as explained in an earlier post, the sound input problem I had when running the Skype Test Call disappeared. Video quality in both cheese and skype is very poor though, but I understand this is a different problem and a bug report has been filed. Interestingly however, if I also install the libpulse0:i386 package with its dependencies as suggested in the askubuntu link, the sound sampling rate problem returns even without a ramdisk set up - remove libcurses0:i386 (and then run *sudo apt-get autoremove* to remove unnecessary packages) and the sound input quality is restored again.

So, there appear to be multiple problems that require attention. My Brother MFC-8460N scanner, which worked perfectly under Ubuntu 11.04 64-bit also fails to work under Ubuntu 11.10 64-bit. I note that Brother have put out a note on this problem suggesting that it results from changes made in library directories, but I have yet to get around to sorting that out:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)

It has not been a happy experience upgrading to 11.10 as key pieces of hardware that worked "out of the box" in previous releases no longer work without time consuming "tinkering". I do hope these problems get sorted out soon or I will have to scrub 11.10 and reinstall the last LTS (10.04). I would rather not as there are aspects of the Unity desktop I like. I guess the next LTS should be 12.04 so Canonical will no doubt be doing all it can to ensure that is a very stable release:- but that is still 6 months away.

Sorry for the "ranting", but I sense there is a lot of frustration with 11.10 out there.

---

### Post by ppatalano on 2011-11-07
I've had the same webcam color issues since the 11.10 upgrade. Hopefully this gets fixed soon.

---

### Post by smi402 on 2011-12-01
After installing the recent Ubuntu updates, ***cheese*** is now working correctly in Ubuntu 11.10. (Posted 1 Dec 2011)

:D:D:D

---

### Post by mywinningsmile on 2011-12-16
I'm afraid to say this isn't my experience (new to Ubuntu with 11.10)

The Cheese icon appears in the toolbar for a few seconds and then disappears. When I try and run from a terminal I get

(cheese:3314): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined

Any thoughts?

Best
Alex

---

### Post by nocx on 2011-12-29
I do all my updates and have the same problem.    :(

---

### Post by Lester Paul on 2012-06-10
If your webcam is functioning in Cheese, but not in Skype it is probably that Skype cannot find the libv4l1.so file that it needs. The program is looking for this file in the usr/lib/libv4l/ directory, but in the Ubuntu 11.04 install, the directory is in /usr/lib/i386-linux-gnu/ directory. The fix is to copy this directory (/usr/lib/i386-linux-gnu/libv4l) with all of it's contents and paste it into the /usr/lib/ directory, then run the command
 	env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype  
 


 Everything should work fine after that.
 


 Running this command before doing this mod will result in an error message telling you that the command was ignored, then skype will start.

---

