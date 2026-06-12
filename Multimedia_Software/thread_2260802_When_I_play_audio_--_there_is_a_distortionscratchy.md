---
title: "When I play audio -- there is a distortion/scratchy sound  14.04 ubuntu"
date: 2015-01-14
forum: Multimedia Software
---

### Post by xigen on 2015-01-14
Ubuntu 14.04 
Delta 66  (sound card)

I just updated the kernel ... and changed a parameter   sudo gedit /etc/pulse/default.pa
load-module module-udev-detect =>  load-module module-udev-detect tsched=0

reboot

Unfortunately the scratchy sound remains.

How can I get rid of that distortion/scratchy background?


meow@MeowBatunde:~$ cat /proc/asound/cards
 0 [M66            ]: ICE1712 - M Audio Delta 66
                      M Audio Delta 66 at 0xc040, irq 20
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 17
meow@MeowBatunde:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
meow@MeowBatunde:~$

---

### Post by Jay_Bowles on 2015-01-15
Not sure if this will help but I always edit my daemon.conf file to use Secret Rabbit Code.

If you open with your favourite file editor:

```
/etc/pulse/daemon.conf
```

scroll down to **resample-method** and change that entry to:

```
src-sinc-best-quality
```

you will also probably need to un-hash that line (ie remove the hash in front of resample-method). Then save the file. It's probably best to back up this configuration file before changing things just in case; not that I have ever had issues.

There is no need to reboot although you may want to restart your music app. This certainly improves the sound quality.

---

### Post by xigen on 2015-02-01
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

To the people who created this wiki -- a very sincere thank you!  It worked.

The specific code:
> sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`



---

### Post by xigen on 2015-02-09
I had some remaining scratchy sound ... especially around the highs / trebble.     

I removed the sound card (Delta66) and cleaned all of the contacts, removed dust, and made sure there was no dust.   

Now my system sounds terrific again.

---

