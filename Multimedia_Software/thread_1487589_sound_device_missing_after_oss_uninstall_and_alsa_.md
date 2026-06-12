---
title: "sound device missing after oss uninstall and alsa reinstall"
date: 2010-05-19
forum: Multimedia Software
---

### Post by iofu on 2010-05-19
Hello,

I was having issues with the mic or line in on my onboard sound card, while trying to get my tvtuner patched in, later I gave OSS a try, I could not get it to work and decided to go back to Alsa, now my soundcard is not functioning.

I have followed quite a few different guides, one of which is the sticky, please forgive me for not remembering which guides. I'm going nuts over this.

As you can see below it looks like it is still using the oss driver.

Thanks for your help.


uname -a
Linux freekbox 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:56 UTC 2010 i686 GNU/Linux

aplay -l
aplay: device_list:223: no soundcards found...

cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory


00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
06:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Gateway 2000 Device 4037
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: oss_hdaudio
        Kernel modules: snd-hda-intel

sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=oss_hdaudio latency=0
       resources: irq:16 memory:febfc000-febfffff
  *-multimedia:0
       description: Multimedia video controller
       product: Bt878 Video Capture
       vendor: Brooktree Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
       resources: irq:22 memory:dfefe000-dfefefff(prefetchable)
  *-multimedia:1 UNCLAIMED
       description: Multimedia controller
       product: Bt878 Audio Capture
       vendor: Brooktree Corporation
       physical id: 1.1
       bus info: pci@0000:06:01.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32 maxlatency=255 mingnt=4
       resources: memory:dfeff000-dfefffff(prefetchable)

[http://www.alsa-project.org/db/?f=11951351c9e0f4f934da0b8aa07f4f10a946aecc](http://www.alsa-project.org/db/?f=11951351c9e0f4f934da0b8aa07f4f10a946aecc)

---

### Post by lidex on 2010-05-20
For now, remove the custom entry in alsa-base.conf:
```
options snd-hda-intel: model=gateway

```

Run this command:
```
sudo apt-get remove oss4-base oss4-gtk
```
Now this:
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```

---

