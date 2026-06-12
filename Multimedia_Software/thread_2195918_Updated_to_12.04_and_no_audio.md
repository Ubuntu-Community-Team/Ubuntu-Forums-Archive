---
title: "Updated to 12.04 and no audio"
date: 2013-12-27
forum: Multimedia Software
---

### Post by Fidelio1st on 2013-12-27
Computer: Dell Inspiron 1420 Intel Core 2 Duo T5550 (3GB, DDR2, 667mHz)

I recently updated from 8.04 to 10.4 to 12.04 and now I have no audio -- no audio for video files, no audio when viewing youtube etc on internet, and when I burn/backup, video burns fine, but no audio... audio is turned all the way up in the audio icon in the top right (mute is not on).

Any help much appreciated!

---

### Post by Bucky Ball on 2013-12-27
Try checking your setting in Pulseaudio Volume Control (Accessories>Multimedia, but I'm not using Unity so I could be wrong).

Get some audio going and in the playback tab you should see the stream happening through whatever app you're playing it through. If the stream is working, go to the output tab and have a tweak, see if anything is turned down, disabled, of pointing in the wrong direction.

---

### Post by Fidelio1st on 2013-12-27
One of things I don't understand about this new setup is where Accessories is --  in Ubuntu Software Center/Accessories, there is no Multimedia option... but in the Software Center you can't actually access anything to use it...

I went to System Settings/Sound -- see the attached screenshot... wondering if anything to try here?

---

### Post by mikewhatever on 2013-12-27
Please run **alsamixer** in a Terminal window, and make sure the PCM and Speaker sliders are not down or muted. Pressing the 'm' key will mute/unmute a channel.

---

### Post by Fidelio1st on 2013-12-27
Please see attached screenshots. The master was originally all the way down. I turned it up to 100 as well as others. But still no sound. Not sure what setting you mean here when you say "speaker sliders"...

---

### Post by Bucky Ball on 2013-12-27
Erm, bring them out of the red else when sound does work you'll be in for a very loud surprise. ;)

---

### Post by mikewhatever on 2013-12-27
It looks like the first four sliders from the left are relevant, and they are up and not muted. Sometimes there is also a Speakers slider, but let's not worry about it just yet. Presumably, there is no sound out of the laptop buitin speakers, so if you have a set of headphones, do check it too.
Please also post the output of **aplay -l** and **dmesg | grep -i hda** .

---

### Post by Yellow Pasque on 2013-12-27
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Fidelio1st on 2013-12-28
At this point I'm about ready to reinstall Ubuntu, but then I was reading the installation guide and it says that should really be a final last resort as it can create problems. I think if I solve the audio (and the internet -- it's not completely fixed, I have to do the command every time I reboot, will update that posting) then I think I'm good too go.


Here's my alsa info:
[http://www.alsa-project.org/db/?f=69ecc91da4f016a0adfd3e6f3a68a8490edfbb45](http://www.alsa-project.org/db/?f=69ecc91da4f016a0adfd3e6f3a68a8490edfbb45)


And what mikewhatever requested:


fidelio1st@Fidelio1st-1420:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
fidelio1st@Fidelio1st-1420:~$ 


------------------

fidelio1st@Fidelio1st-1420:~$ dmesg | grep -i hda
[ 2350.608161] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 2350.608169] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 2350.608226] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[ 4232.984108] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[ 4233.000091] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 181.935 msecs
[ 4233.992066] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 4233.992090] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xfe9fc004)
[ 4233.992097] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 4233.992105] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 4234.066871] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 4234.066880] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 4234.066938] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[ 8049.764109] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[ 8049.780062] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 181.880 msecs
[ 8050.772148] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 8050.772171] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xfe9fc004)
[ 8050.772178] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8050.772186] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 8050.788787] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 8050.788794] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 8050.788851] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[ 9000.316105] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[ 9000.332063] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 182.770 msecs
[ 9001.219784] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 9001.219808] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xfe9fc004)
[ 9001.219815] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9001.219823] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 9001.237286] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 9001.237294] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 9001.237351] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[ 9007.736234] PM: resume of drv:snd_hda_intel dev:0000:00:1b.0 complete after 6498.950 msecs
[12682.740104] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[12682.756063] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 181.724 msecs
[12683.783978] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
[12683.784016] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xfe9fc004)
[12683.784025] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[12683.784036] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[12683.842755] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[12683.842766] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[12683.842838] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[12691.336231] PM: resume of drv:snd_hda_intel dev:0000:00:1b.0 complete after 7493.479 msecs
fidelio1st@Fidelio1st-1420:~$

---

### Post by Yellow Pasque on 2013-12-28
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by mikewhatever on 2013-12-28
There is a trick of trying various Alsa options for the specific codec and notebook brand, which in your case are SigmaTel STAC9228 and Dell respectively. Here are the options for STAC9228 according to [this page]("http://lxr.linux.no/#linux+v3.2.19/Documentation/sound/alsa/HD-Audio-Models.txt"):
```

STAC9227/9228/9229/927x
 312=======================
 313  ref           Reference board
 314  ref-no-jd     Reference board without HP/Mic jack detection
 315  3stack        D965 3stack
 316  5stack        D965 5stack + SPDIF
 317  5stack-no-fp  D965 5stack without front panel
 318  dell-3stack   Dell Dimension E520
 319  dell-bios     Fixes with Dell BIOS setup
 320  volknob       Fixes with volume-knob widget 0x24
 321  auto          BIOS setup (default)

```

To apply, for example, the first option, run  **gksudo gedit /etc/modprobe.d/alsa-base.conf**, and add the **options snd-hda-intel model=ref** line to the bottom, then save and exit. At this stage, you usually need to reboot to check the effect. Make sure nothing is muted after rebooting. If the 'ref' option doesn't work, try dell-3stac or dell-bios instead.

---

### Post by Bucky Ball on 2013-12-28
Wow, all this and OP still hasn't found the Pulseaudio Volume Control ...

---

### Post by Fidelio1st on 2013-12-29
So the audio has been solved by going to F6 in alsamixer and changing to HDA Intel. It's working now at least on internet and other video files.

The only problem now is, using programs like K9 copy and K3b, I can't burn with audio -- the video burnt fine, but no audio. I backed up the same (home movie) DVD using DVD Shrink in Windows and audio was fine. And K9 and K3b worked fine in Ubuntu 8.04. So not sure if that audio problem is related, or if I need to repost in a software forum?

Also, since audio's working now on internet and other video on computer, could this solve the program audio problem?:
run gksudo gedit /etc/modprobe.d/alsa-base.conf, and add the options snd-hda-intel model=ref l


I would be willing to do a fresh install, but again, my Ubuntu/install skills are limited and I'm having trouble figuring out how to install from CD (and/or it seems very time consuming to figure out the boot stuff, and I don't want to mess anything up further since I seem so close to getting it working)...

---

### Post by mikewhatever on 2013-12-30
AFAIK, alsa options have nothing to do with anything other then ALSA. In other words, not, modifying alsa-base.conf will not affect K9 and K3B.

---

