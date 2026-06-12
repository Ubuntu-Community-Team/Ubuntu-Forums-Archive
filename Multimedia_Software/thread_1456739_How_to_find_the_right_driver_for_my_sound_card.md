---
title: "How to find the right driver for my sound card"
date: 2010-04-17
forum: Multimedia Software
---

### Post by mjsilverstri on 2010-04-17
Hi,

I have a HP Pavilion dv7 laptop. Can you please tell me how can I find the right driver for my sound card? When I play a mp3 via vlc in ubuntu 9.10, there is sound, but the quality is bad. And I play the same on Windows7. It plays fine.

Thank you.

---

### Post by Yellow Pasque on 2010-04-17
The driver (snd-hda-intel) is pre-installed. To update it, see: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
If you decide to try that, make sure to edit the version section of the script like this before you run it:
```
PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17
}
```

---

### Post by mjsilverstri on 2010-04-17
I tried. But I get this error:

> 

--2010-04-17 19:03:02--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)
  (try: 3) => `alsa-driver-1.0.22.1.tar.bz2'
Connecting to ftp.alsa-project.org|63.251.171.80|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|66.150.161.141|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|69.25.27.170|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|66.150.161.140|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|69.25.27.173|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|63.251.171.81|:21... failed: Connection timed out.



---

### Post by Yellow Pasque on 2010-04-17
You should modify the script to build ALSA 1.0.23 like I posted.

---

### Post by mjsilverstri on 2010-04-17
Thank you for your response.  I have updated and retried. I still get these connection timeout error.

> --2010-04-17 20:03:10--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2)
           => `alsa-driver-1.0.23.tar.bz2'
Resolving ftp.alsa-project.org... 69.25.27.173, 63.251.171.80, 63.251.171.81, ...
Connecting to ftp.alsa-project.org|69.25.27.173|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|63.251.171.80|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|63.251.171.81|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|66.150.161.140|:21... failed: Connection timed out.
Connecting to ftp.alsa-project.org|66.150.161.141|:21... failed: Connection refused.
Connecting to ftp.alsa-project.org|69.25.27.170|:21... failed: Connection timed out.
Retrying.





---

### Post by ekoerner on 2010-04-18
I tried to upgrade to Alsa 1.0.23 too. However it seems the website [www.alsa-project.org](www.alsa-project.org) is not available. This could explain the failure.

Ewald Koerner

---

### Post by mjsilverstri on 2010-04-18
Any other way to install the right driver for my sound card?

---

### Post by lidex on 2010-04-18
Unfortunately alsa-project.org is down. Can you supply some info? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Yellow Pasque on 2010-04-19
The ALSA site is back up now.

---

### Post by ekoerner on 2010-04-19
I successfully ran the upgrade scripts this morning. "cat /proc/asound/version" shows version 23. "aplay -l" lists my card, XONAR DS, and I am getting sound out of my stereo speakers (they are connected to the XONAR DS card!).

Ewald Koerner

---

### Post by mjsilverstri on 2010-04-19
I have sound only play via my laptop speakers. But when I connect my stereo speakers  to my laptop, the sound still play via laptop speakers.

---

### Post by lidex on 2010-04-19
What is the output of this command:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by mjsilverstri on 2010-04-20
Here is the output:
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT220 HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT220 HDMI

---

### Post by lidex on 2010-04-20
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version

```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by mjsilverstri on 2010-04-21
Thank you.
> 
$ uname -a
Linux home 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



---

### Post by lidex on 2010-04-21
And...
```
cat /proc/asound/version
```

---

### Post by lidex on 2010-04-23
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=1  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

