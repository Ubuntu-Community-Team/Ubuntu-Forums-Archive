---
title: "Via VT2020 AudioChip not working properly"
date: 2010-04-24
forum: Multimedia Software
---

### Post by md2406 on 2010-04-24
Hi. I have been using ubuntu for over a year and still straggling sound problems. I have Asus P7P55D-Deluxe motherboard with Via VT2020 audiochip(10 channel). I also have 5.1 sorround speaker but I cannot get them work with 9.10 nor 10.04. In "sound preferences", it says "Internal Audio 1output/1 Input Analog Stereo duplex". I have searched about it but it seems no one has this problem with VT2020.

---

### Post by lidex on 2010-04-24
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by md2406 on 2010-06-14
Sorry for my late reply. Here is the information you asked.

uname -a

```
 Linux HUN 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

```

aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT2020 Analog [VT2020 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT2020 Digital [VT2020 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

cat /proc/asound/version
```

Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 14 2010 for kernel 2.6.32-22-generic (SMP).

```

head -n 1 /proc/asound/card*/codec#*
```

Codec: VIA VT2020

```

I built my own desktop so no brand.

---

### Post by lidex on 2010-06-14
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by md2406 on 2010-06-19
Hi,
I accidentally clicked ALSA Upgrade Script and then found SoundTroubleshoting page.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Those pages helped me to understand what my problem was and I fixed it. I upgraded the ALSA to the latest version and added a line in alsa-base.conf.
Thanks for your kind help

---

### Post by lidex on 2010-06-19
What line did you add, if you don't mind sharing? I'm not familiar with this codec and it would help others with the same hardware.

---

### Post by md2406 on 2010-06-21
I added this line. > options snd-hda-intel model=6stack-digoutHowever before adding this, I upgraded my ALSA to the latest version. I hope this helps. I would like to help everybody ,who has the same problem,  as much as I can.

---

### Post by lidex on 2010-06-21
> **md2406 said:**
> I added this line. However before adding this, I upgraded my ALSA to the latest version. I hope this helps. I would like to help everybody ,who has the same problem,  as much as I can.

Thank You! Don't forget to mark the thread solved - 'Thread Tools' up top.
Nice work, BTW.

---

### Post by md2406 on 2010-06-21
Thanks for your help.

---

### Post by M4rv1n on 2011-02-04
Hi
I have a problem with the same audio device on lucid 64 bit. At startup before the sound at logon screen and before the sound after login I ear about two second of crackling noise. I have update manually 
alsa-driver at 10.0.24  
alsa-lib 10.0.24.1 
alsa-utils 10.0.24.2

Motherboard is asus P7F7-E WS Supercomputer and 5.1 speaker configuration

I need to install other package from alsa (firmware or utils)??

With alsamixer I have all the channel and if I test surrond with speaker-test is all ok, if I try alsaconf the card is not recognized.

I try md2406's workaround but with no effect, I have also installed from ppa linux-alsa-driver-modules-2.6.32-28-generic.deb as suggested in another post but nothing...


uname -a
```
Linux axl-desktop 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

```aplay -l
```
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: VT2020 Analog [VT2020 Analog]
  Sottoperiferiche: 2/2
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
scheda 0: Intel [HDA Intel], dispositivo 1: VT2020 Digital [VT2020 Digital]
  Sottoperiferiche: 2/2
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
scheda 2: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 7: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 8: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 2: NVidia [HDA NVidia], dispositivo 9: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Feb  4 2011 for kernel 2.6.32-28-generic (SMP)

```head -n 1 /proc/asound/card*/codec#*
```
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT2020

==> /proc/asound/card2/codec#0 <==
Codec: Nvidia GPU 12 HDMI/DP

==> /proc/asound/card2/codec#1 <==
Codec: Nvidia GPU 12 HDMI/DP

==> /proc/asound/card2/codec#2 <==
Codec: Nvidia GPU 12 HDMI/DP

==> /proc/asound/card2/codec#3 <==
Codec: Nvidia GPU 12 HDMI/DP

```Any suggest???

Thx

---

### Post by M4rv1n on 2011-02-04
Update
I used your script for install latest version 1.0.24 series, I added 

options snd-hda-intel model=auto

But nothing change

---

### Post by lidex on 2011-02-04
> **M4rv1n said:**
> Update
I used your script for install latest version 1.0.24 series, I added 

options snd-hda-intel model=auto

But nothing change
I'm a little unclear as to your problem. You're saying you have no audio at all? Are you using analog or digital out? Have you tried both?
You should not have alsa modules and the alsa upgrade at the same time as the modules will override the update. What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by M4rv1n on 2011-02-05
Thank you for reply!
Sorry for my poor english :)

After two days of test now the situation is:
I have surround audio on my analog 5.1 speaker
If I run alsaconf the audio card is not recognized but in alsamixer is reported correctly
The mayor problem is during startup, I ear two second of crackling noise then the sound at logon screen, after login I ear two second of noise and then the sound at startup

This is the output

```
alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware                                  1.0.20-0medibuntu4.1                            Contains firmware for ALSA devices - Medibuntu package
ii  alsa-firmware-loaders                          1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                     1.0.22-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                   0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  linux-backports-modules-alsa-2.6.32-27-generic 2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA sna


```

---

### Post by M4rv1n on 2011-02-07
I found another problem, no audio on totem!
But I have audio on youtube for example and with vlc if I select alsa for output
:confused:

---

### Post by M4rv1n on 2011-03-11
Clean the package and reinstall with new version of the script did the trick
Thx

---

### Post by md2406 on 2011-03-14
why did u you try adding "auto" at the end of the line?
can you please try the one below and post what happens?

```
 options snd-hda-intel model=6stack-digout 
```

---

