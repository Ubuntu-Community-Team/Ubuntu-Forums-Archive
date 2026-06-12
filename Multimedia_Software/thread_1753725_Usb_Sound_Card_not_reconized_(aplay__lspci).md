---
title: "Usb Sound Card not reconized (aplay / lspci)"
date: 2011-05-09
forum: Multimedia Software
---

### Post by floboss07 on 2011-05-09
Hello,

Since I reinstalled PulseAudio and Alsa (I don't remember why I removed them), my Creative Xmod isn't reconized anymore.
It isn't in **aplay -l**, and in **lspci -v** neither !

Have you got any idea to solve my problem ?



P.S. Maybe I should say I had to add snd-hda-intel in /etc/modules to make my intern chipset audio work.

P.S.² I'm using a HP Compaq 8510p

---

### Post by lidex on 2011-05-11
OK, not sure why you would want to mess with /etc/modules. Why don't you remove that and reboot. 
Next use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by floboss07 on 2011-05-13
Thank you for you help !

Well, if I remove the driver from my modules, I have no sound at all (it was for the internal chipset, without that he doesn't load the module..). But I did it !

Here are my ALSA informations : [http://www.alsa-project.org/db/?f=f542f56dca62511b9e359beaf92bbd435f048dbe](http://www.alsa-project.org/db/?f=f542f56dca62511b9e359beaf92bbd435f048dbe)

And here with the module added :
[http://www.alsa-project.org/db/?f=ab4da871bf9af09b9588cbcf9382f68c15f399a6](http://www.alsa-project.org/db/?f=ab4da871bf9af09b9588cbcf9382f68c15f399a6)

---

### Post by lidex on 2011-05-13
I see you have an asoundrc file. What is the purpose of that?
Humor me and rename ~/.asoundrc to asound.old for now. Next update:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo update-grub
```
**Reboot**

Now reinstall alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by floboss07 on 2011-05-17
Thank you. I did that.

Here are my problems :

- No alsa-utils already installed, so I just "sudo aptitude install alsa-utils"

- Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.32-31-generic"

- After these manipulations, withouth the /etc/modules file modified, still no sound on the mainboard (and no creative xmod detected).


Here are my (new?) ALSA informations :
[http://www.alsa-project.org/db/?f=93054dc757ee0966c0f7811ec6613c8ff356f018](http://www.alsa-project.org/db/?f=93054dc757ee0966c0f7811ec6613c8ff356f018)


Thank you for your help.

---

### Post by lidex on 2011-05-17
If you boot into a previous kernel, does it work?
This output please:
```
dpkg -l | grep "alsa"
```

---

### Post by floboss07 on 2011-05-19
No, it doesn't work with a previous kernel.

My *dpkg -l | grep "alsa"* Output :

```
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  alsaplayer-common                         0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                            0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                            0.99.80-5                                       PCM player designed for ALSA (OSS output mod
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
```

---

### Post by lidex on 2011-05-19
Try upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by floboss07 on 2011-05-20
Ok, I did that, but..
Still no sound.

And..
> After reboot you can type:

cat /proc/asound/version

This will let you know if you're running the new version.
**But I don't have any "asound" in /proc/.**

And..
```
aplay -l
aplay: device_list:240: no soundcards found...

```

And..
```
dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                     1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                               1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                            1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  alsaplayer-common                         0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                            0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                            0.99.80-5                                       PCM player designed for ALSA (OSS output mod
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA

```

(Shouldn't I have the 1.0.24 version ?! I had no error with the script..)



EDIT : If you want the log of the script, I don't have it. I did "sudo script -a -c "./AlsaUpgrade-1.0.24-2.sh -i" /tmp/Alsa_1.0.24-2_upgrade_download.log", but I think after rebooting my /tmp/ folder has been emptying.

---

### Post by lidex on 2011-05-22
Let's see a new alsa-info output.

---

### Post by floboss07 on 2011-05-23
Okay.

Here is my alsa-info :

[http://www.alsa-project.org/db/?f=defeef26c0083ab4d55bdf6608d05527f83b66ee](http://www.alsa-project.org/db/?f=defeef26c0083ab4d55bdf6608d05527f83b66ee)


I'm not sure that's better.. :/

---

### Post by lidex on 2011-05-24
> **floboss07 said:**
> Okay.

Here is my alsa-info :

[http://www.alsa-project.org/db/?f=defeef26c0083ab4d55bdf6608d05527f83b66ee](http://www.alsa-project.org/db/?f=defeef26c0083ab4d55bdf6608d05527f83b66ee)


I'm not sure that's better.. :/

It's not. Can you boot into a previous kernel and see if that works?

---

### Post by floboss07 on 2011-05-26
I already tried. :/

> **floboss07 said:**
> No, it doesn't work with a previous kernel.

My *dpkg -l | grep "alsa"* Output :

```
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  alsaplayer-common                         0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-gtk                            0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-oss                            0.99.80-5                                       PCM player designed for ALSA (OSS output mod
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
```

---

