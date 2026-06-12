---
title: "IDT audio, no sound @ ubuntu 10.04 64bit"
date: 2010-08-10
forum: Multimedia Software
---

### Post by nate_nightroad on 2010-08-10
hi guys,i'm using ubuntu 10.04 64bit and i have a netbook(model is hp mini 110-3004TU) with an integrated HD audio from IDT...

the problem is that no sound is coming out from the speaker, please help

---

### Post by nate_nightroad on 2010-08-10
apparently people from this link has found a solution:

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

however, it was for xubuntu....i tried to followed but the installation failed

---

### Post by lidex on 2010-08-11
Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by nate_nightroad on 2010-08-11
> **lidex said:**
> Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

```
vincent@Raiden:~$ uname -a
Linux Raiden 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
vincent@Raiden:~$ aplay -l
aplay: device_list:223: no soundcards found...
vincent@Raiden:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
vincent@Raiden:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

my netbook make and model is as follow

HP Mini 110-3004TU

---

### Post by lidex on 2010-08-11
Try re-installing alsa first. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by nate_nightroad on 2010-08-12
> **lidex said:**
> Try re-installing alsa first. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

done and reboot...still no sound :cry:

---

### Post by nate_nightroad on 2010-08-12
```
vincent@Raiden:~$ uname -a
Linux Raiden 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
vincent@Raiden:~$ aplay -l
aplay: device_list:223: no soundcards found...
vincent@Raiden:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
vincent@Raiden:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

---

### Post by lidex on 2010-08-13
Post these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

---

### Post by nate_nightroad on 2010-08-13
> **lidex said:**
> Post these outputs please:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```
```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

```
vincent@Raiden:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for vincent: 
Specified filename /dev/dsp* does not exist.
Specified filename /dev/snd/* does not exist.
Specified filename /dev/seq* does not exist.
vincent@Raiden:~$ dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

after inputting this code :

```
dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel'
```

nothing came out

---

### Post by lidex on 2010-08-13
Boot into a lower numbered kernel and re-install your latest kernel and kernel-header packages and reboot.

---

### Post by nate_nightroad on 2010-08-26
> **lidex said:**
> Boot into a lower numbered kernel and re-install your latest kernel and kernel-header packages and reboot.

done,now the alsa drivers are installed....

```
vincent@Raiden:~$ uname -a
Linux Raiden 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
vincent@Raiden:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
vincent@Raiden:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                             1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
vincent@Raiden:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT ID 7667

```

please continue to guide me :)

---

### Post by lidex on 2010-08-27
I need you to do this, it will help to troubleshoot. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by mike4ubuntu on 2010-09-02
Keep in mind that the last few Ubuntu versions have PulseAudio integrated with it.  It's the preferred sound server.  Using ALSA may not work as well anymore.  If you go to sound preferences (should be a little speaker icon on your main gnome panel) check to see if you can hear any sound effects when you click on them on the effects tab.  If not, you may have to set the output device on the output tab.  If you have a driver problem with that hardware, you may have to get another sound card.  Creative Labs has some good USB Sound Cards that you just plug in and then hook up external speakers or headphones.  Excuse this post if I'm way off base with this.

---

