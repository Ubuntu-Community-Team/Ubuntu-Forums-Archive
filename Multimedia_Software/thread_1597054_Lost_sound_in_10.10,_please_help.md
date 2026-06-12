---
title: "Lost sound in 10.10, please help"
date: 2010-10-14
forum: Multimedia Software
---

### Post by ProcyonSJJ on 2010-10-14
OK, here's my situation.  I have a Qosmio X505 Q887.  I installed Ubuntu 10.04.  Sound worked out of the box, but I had to install the realtek linux audio pack to enable audio out through the HDMI port.  It also fixed an issue I was having with the built in microphone.

Fast forward to this week, and I upgrade to Ubuntu 10.10.  Everything went well, audio out still worked, but the microphone died again.  So... what do I do?  I try installing the realtek linux audio pack again, and poof... no more sound.

I have tried umpteen things, including all the steps in the troubleshooting guide, all the way down to compiling the driver myself.  For one thing, the ALSA Project does not seem to know about the Intel 5 Series/3400 Series chipset.  I couldn't find anything about it on their wiki.  For another thing, when I try to compile the 1.0.23 Alsa driver, I get:

```

/home/procyon/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/home/procyon/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/home/procyon/src/alsa/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/home/procyon/src/alsa/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/home/procyon/src/alsa/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/home/procyon/src/alsa/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2

```

Can _anyone_ please point me in the right direction before I give up and reinstall?  I would appreciate it.  Here is all the pertinent info you might need to know:

uname -a
```

Linux procyon-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```

aplay -a
```

aplay: device_list:235: no soundcards found...

```

sudo lshw -c sound
```

  *-multimedia UNCLAIMED  
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:cdefc000-cdefffff
  *-multimedia UNCLAIMED
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f0900000-f0903fff

```

---

### Post by fouadatmeh on 2010-10-15
Hello,
I am having the same problem. 
** the Readme.txt file in the realtek driver has some instructions for Ubuntu so I guess you should try them. (didn't work for me BTW).

Hope it works for you or someone comes back with an answer for both of us

---

### Post by robertsclark on 2010-10-15
Don't know if it will help you, but I had a similar problem on by Acer Aspire One AOA150 under Ubuntu 10.10.

I had to download and install pavucontrol.  When I ran this, the sound profile is set to Analog Stereo Duplex.  I had to go to the Output tab and set the volume slider on either the left or right channel to Silence and then suddenly the microphone would burst into life.

Robert

---

### Post by lidex on 2010-10-17
*ProcyonSJJ:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

