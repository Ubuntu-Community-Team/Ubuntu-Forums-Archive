---
title: "headphone jack not working"
date: 2016-12-20
forum: Multimedia Software
---

### Post by adhityaravi on 2016-12-20
Hello,

I installed ubuntu 16.10 on my alienware 15 r2. The laptop speakers are working fine. But i am not able to get the headphone jack to work. I tried pavucontrol, it was of no help. Can anyone help me in resolving this issue?

Thank you.

---

### Post by Yellow Pasque on 2016-12-20
Try this:
```
echo "model=alienware" | sudo tee /etc/modprobe.d/alienwarequirk.conf
```
Do the headphones work after rebooting the system?

Reference: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133)

---

### Post by adhityaravi on 2016-12-22
Hey Thanks for the reply. I tried the code  and rebooted my system. But  the headphones are still not working and my laptop speakers stopped  working now too. I do not know much about linux, but the alienwarequirk.conf in modprobe.d is an empty file. Is it supposed to have any code in it?. I tried many things to revert the settings so that I could at least hear the sound through my speakers but I had no success so far. Is there anything I can do?

---

### Post by Yellow Pasque on 2016-12-22
> I do not know much about linux, but the alienwarequirk.conf in modprobe.d is an empty file.
I'm sorry. I botched the command. The file /etc/modprobe.d/alienwarequirk.conf should contain:
```
options snd-hda-intel model=alienware
```

---

### Post by adhityaravi on 2016-12-22
So can i use this code now

echo "options snd-hda-intel model=alienware" | sudo tee /etc/modprobe.d/alienwarequirk.conf

and reboot my system?

---

### Post by Yellow Pasque on 2016-12-22
^Yes. If it's still not working after reboot, please give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by adhityaravi on 2016-12-23
The headphone jack is still not working. My alsa information is in the below link

[http://www.alsa-project.org/db/?f=6d10ac9475bda962fac93fb834965ccbbc79a4a0](http://www.alsa-project.org/db/?f=6d10ac9475bda962fac93fb834965ccbbc79a4a0)

Thank You.

---

### Post by Yellow Pasque on 2016-12-24
I can see that you have entered the quirk correctly:
```
snd_hda_intel: model=alienware
```

But for some reason, the quirk is not being applied, or pin 0xf would be recognized as a headphone out.
```
snd_hda_codec_ca0132 hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
```

Normally, I would point you to this page and tell you to install the appropriate package. Unfortunately, they don't offer packages for Ubuntu 16.10 (yet?): [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

Other options:
1. Wait for kernel 4.10-rc1 and use that when it comes out.
2. You can try tasking pin 0xf manually:
```
sudo apt-get get install alsa-tools-gui
sudo hdajackretask
```
3. Report a bug and request that the fix be backported to Ubuntu 16.10 kernel.

---

### Post by adhityaravi on 2016-12-26
I tried retasking the pin manually. pin 0xf in the creative codec (i think creative is the sound card) is already tasked as headphones. and if i try to override any settings i get the following message

tee:/sys/class/sound/hwC0Do/reconfig: Device or resource busy

and the following message in the terminal

E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied
E: [pulseaudio] main.c: Failed to kill daemon: No such file or directory
0x0b 0x01014010
0x0c 0x014580f0
0x0d 0x014570f0
0x0e 0x01c530f0
0x0f 0x0321403f
0x10 0x02216011
0x11 0x02012014
0x12 0x37a791f0
0x13 0x908700f0
0x18 0x500000f0
1

---

### Post by Yellow Pasque on 2016-12-28
Since the alienware quirk did not apply, remove it.
```
sudo rm /etc/modprobe.d/alienwarequirk.conf
```

Next, try the 4.10-rc1 kernel. The fix I linked to was included in that kernel.

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc1/)

---

