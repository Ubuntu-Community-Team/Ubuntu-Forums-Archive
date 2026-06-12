---
title: "Headphone sound, Intel ICH 7"
date: 2010-05-20
forum: Multimedia Software
---

### Post by kerzane on 2010-05-20
Hi,

I have problems getting sound to come out of my headphone jack properly.

In previous versions of Ubuntu alsa did not seem to recognize my headphone jack.

Now in 10.04, it does, and produces sound, but the mix is wrong, half the track is suppressed. 

The speakers are now working well.
```

eoin@eoins-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


```
eoin@eoins-laptop:~$ lspci -v
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
        Subsystem: Samsung Electronics Co Ltd Device ca00
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
```

```
eoin@eoins-laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.32-22-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     51925557ECF0F2838930862
depends:        
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           preclaim_oss:int
```


Does anybody have an idea of what could be the problem?
Am I doomed to have crap headphone sound with this machine?

Thanks very much,
Kerzane.

---

### Post by lidex on 2010-05-20
Install the alsa-backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot.

Now this please: Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
*_Also helpful is the make/model of your PC/Laptop._*
Please post text output using code tags (the # in toolbar)

---

### Post by kerzane on 2010-05-20
> **lidex said:**
> 
*_Also helpful is the make/model of your PC/Laptop._*


Samsung NC10

> **lidex said:**
> 
Install the alsa-backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot.


Done. No change.

> **lidex said:**
> 
Now this please: Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"


```
eoin@eoins-netbook:~$ uname -a
Linux eoins-netbook 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```


```
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

```


```
eoin@eoins-netbook:~$ head -n 1 /proc/asound/card*/codec#* 
Codec: Realtek ALC272

```

Thanks for your help,
Kerzane.

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=samsung-nc10 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by kerzane on 2010-05-20
> Open this file for editing:
Code:

 gksudo gedit /etc/modprobe.d/alsa-base.conf

Insert this line at the bottom:
Code:

 options snd-hda-intel model=samsung-nc10

Save. Close. Reboot.

Done.

> Check your levels in alsamixer.

The only card visible in alsamixer is HDA Intel, which appears to be the default. The levels look and work fine.

> Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default. 

I'm not seeing anything about sound cards in this dialog. Nothing in this seems to be relevant to alsamixer.

Still no improvement on the sound.

Are the wrong drivers being used? Do you see a possible cause?

Thanks again,
Eoin.

---

### Post by kerzane on 2010-05-20
In the hardware tab of the Sound dialog, only one item:

Internal Audio

is listed. 

There doesn't seem to be any option to configure it or anything. I'm not sure how relevant this is. But possibly my sound card, the HDA INTEL should appear there?

Thanks again,
Eoin.

---

### Post by lidex on 2010-05-20
The next step is an alsa upgrade. You can follow the alsa-upgrade link in my sig to accomplish that.

---

### Post by kerzane on 2010-05-20
Having followed the steps of the upgrade, -d > -c > -i , reboot, etc, I still seem to be using the old alsa
```

eoin@eoins-netbook:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).

```

Have I missed something?

Thanks.

---

### Post by lidex on 2010-05-20
Sorry, you'll need to uninstall the alsa-backports, just found that out.

---

### Post by kerzane on 2010-05-20
Ok,

I am now using the updated version.

Unfortunately the problem persists. I'm on the point of admitting defeat and concluding that it's a hardware issue.

So unless you have any further suggestions, or advice on how I might do a simple overview of the headphone hardware connection, I'll leave you be.

Many thanks for your help though,
Cheers,
Eoin.

---

### Post by lidex on 2010-05-20
To clarify, you now have alsa 1.0.23 and the line
```
options snd-hda-intel model=samsung-nc10
```
added to alsa-base.conf, correct?

---

### Post by kerzane on 2010-05-20
Yeah.

---

### Post by lidex on 2010-05-20
OK, replace that line with:
```
options snd-hda-intel model=laptop
```
Reboot.
Another possible option:
```
options snd-hda-intel model=auto
```

---

### Post by kerzane on 2010-05-20
No luck there either.

Keep 'em coming though!! :)

---

### Post by lidex on 2010-05-20
These are the options listed for that codec:
```
 3stack-dig	3-stack (2-channel) with SPDIF
  3stack-6ch	 3-stack (6-channel)
  3stack-6ch-dig 3-stack (6-channel) with SPDIF
  6stack-dig	 6-stack with SPDIF
  lenovo-101e	 Lenovo laptop
  eeepc-p701	ASUS Eeepc P701
  eeepc-ep20	ASUS Eeepc EP20
  ecs		ECS/Foxconn mobo
  m51va		ASUS M51VA
  g71v		ASUS G71V
  h13		ASUS H13
  g50v		ASUS G50V
  asus-mode1	ASUS
  asus-mode2	ASUS
  asus-mode3	ASUS
  asus-mode4	ASUS
  asus-mode5	ASUS
  asus-mode6	ASUS
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

```

I'm a little confused that the first one didn't work (samsung-nc100). These are from another source:
[http://ubuntuforums.org/showthread.php?t=1043568]("http://ubuntuforums.org/showthread.php?t=1043568")
```
Samsung model=laptop
M50 model=laptop
R65 model=laptop-eapd
Ultra tablet pc model=ultra
```

You may want to play around with this also:
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by kerzane on 2010-05-20
Ok,

So I installed gnome-alsamixer and started playing with things.

Experimenting with the balance in the headphone channel is interesting.

The default position (which I presume is in the centre, there must be a way to verify this) produces a really bad sound. The mix is all wrong, the vocals are way back in the back somewhere. 

The extreme left and right positions are better, the vocals mix with most of the channels better, but comparing the two extreme positions shows that there are elementing missing in both.

The most satisfactory result comes from some position moderately to the side of the centre, with all channels appearing present and mixing reasonably well.

This is pretty satisfactory and definitely a step in the right direction.

It would be good to understand why this is happening, and to find some better way of getting the optimum sound.

Have you come across anything like this before? Does it bring anything to mind?

Is there any way to visualise what should be coming through each channel (left, right (and centre if there is one))?

Many thanks,
Eoin.

---

### Post by lidex on 2010-05-20
The only thing that comes to mind is perhaps you're getting rear channels. What is the sound configuration? Stereo, six channels? How many analog jacks are present? Digital? If, for example, you have six-channel sound with three jacks and no spdif, try the option: ```
options snd-hda-intel model=3stack-6ch
``` in alsa-base.

---

