---
title: "No Sound in Dell Dimension 4600"
date: 2009-01-14
forum: Multimedia Software
---

### Post by pieisgood4589 on 2009-01-14
I just did a clean install on a Dell, but it has no sound after the installation.

I get sound fine in Windows XP.

:confused:

---

### Post by pieisgood4589 on 2009-01-14
> **pieisgood4589 said:**
> I just did a clean install on a Dell, but it has no sound after the installation.

I get sound fine in Windows XP.

:confused:

Bumpity bump bump bump. I need this solved ASAP because I have to watch a video for school, but I can't 'cuz I have no sound... Help? :(

---

### Post by originalsynthesis on 2009-01-14
might not be much of a reply, but are you sure your drivers are working and up to date? i did not have this problem with audio, but i did have to dig for better drivers for my video card since the one i have is fairly unique to the laptop im using.

---

### Post by pieisgood4589 on 2009-01-14
In all honesty, I got this computer for free, just like my laptop, (yes, I'm poor) and I have no idea what sound chip it uses. I'm assuming it's using a SoundBlaster card, as used in many Dells. Could anyone point me towards what sound card I have, where to get drivers, and how to configure them? Thanks xD

---

### Post by pieisgood4589 on 2009-01-15
> **pieisgood4589 said:**
> In all honesty, I got this computer for free, just like my laptop, (yes, I'm poor) and I have no idea what sound chip it uses. I'm assuming it's using a SoundBlaster card, as used in many Dells. Could anyone point me towards what sound card I have, where to get drivers, and how to configure them? Thanks xD

Bump Bumpity Bump Bump Bump

Cmon, has the community gotten lazy over the years? :guitar:

---

### Post by originalsynthesis on 2009-01-15
you might not actually have a soundblaster card, i dont use a dell, but i googled a couple specs on them. some have sb audigy 2, one i saw was listed as having an intel integrated soundcard. why dont you log back into windows and check in device manager. no one can tell you what you have in front of you, which is what anyone is going to need to know to help out.  or how about, checking on your pulseaudio/alsa/oss. you may have a conflict from two of them running at the same time. just shots in the dark.  you just might get more help if you post what you do know/ what you are doing to figure this out.

---

### Post by pieisgood4589 on 2009-01-15
> **originalsynthesis said:**
> you might not actually have a soundblaster card, i dont use a dell, but i googled a couple specs on them. some have sb audigy 2, one i saw was listed as having an intel integrated soundcard. why dont you log back into windows and check in device manager. no one can tell you what you have in front of you, which is what anyone is going to need to know to help out.  or how about, checking on your pulseaudio/alsa/oss. you may have a conflict from two of them running at the same time. just shots in the dark.  you just might get more help if you post what you do know/ what you are doing to figure this out.

Well, I just contacted Dell support, and they told me the Windows drivers that I would need are as follows-

ADI 198x Integrated Audio
Soundblaster Audigy 2
Soudblaster Live!

---

### Post by pieisgood4589 on 2009-01-15
> **pieisgood4589 said:**
> Well, I just contacted Dell support, and they told me the Windows drivers that I would need are as follows-

ADI 198x Integrated Audio
Soundblaster Audigy 2
Soudblaster Live!

If it makes any difference, here is the output from the command aplay -l

```
george@george-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by pieisgood4589 on 2009-01-15
> **pieisgood4589 said:**
> If it makes any difference, here is the output from the command aplay -l

```
george@george-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/Bump

---

### Post by pieisgood4589 on 2009-01-15
OK, community, this is getting serious. Unless I get sound on my computer ASAP, I'm messed for this school project.

---

### Post by pieisgood4589 on 2009-01-15
Bumpity.

---

### Post by RJARRRPCGP on 2009-01-16
> **pieisgood4589 said:**
> If it makes any difference, here is the output from the command aplay -l

```
george@george-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

More likely it has an onboard ADI 198xx. The Dimension 4600 I was using temporarily did. I couldn't recall any problems.

Also, this:

Warning, if your SoundBlaster Live! model code is SB0200, it's likely unsupported! 

!-Warning-!, it was suspected on the internet that the SB0200 is a corrupted version of a SoundBlaster Live, it was suspected that Creative conspired to make an Emu 10K1 that only is accessible by Dell!

---

### Post by pieisgood4589 on 2009-01-16
So what you're telling me is  that my sound card simply isn't supported by Ubuntu at all?

Well this is just greeeat... Is there any way to get sound on this machine, or will I have to re-install Windows? T_T

---

### Post by RJARRRPCGP on 2009-01-16
> **pieisgood4589 said:**
> So what you're telling me is  that my sound card simply isn't supported by Ubuntu at all?

Well this is just greeeat... Is there any way to get sound on this machine, or will I have to re-install Windows? T_T


Which model of SoundBlaster Live do you have? Did you look at the card?

---

### Post by throke on 2009-02-05
[comment redacted]

---

### Post by pieisgood4589 on 2009-02-09
> **RJARRRPCGP said:**
> Which model of SoundBlaster Live do you have? Did you look at the card?

According to the forum user who posted above, more likely it has an onboard ADI 198xx. 

But again, here's the output from aplay -l, apparently it tells experts a lot-

```
george@george-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by pieisgood4589 on 2009-02-09
bahump

---

### Post by pieisgood4589 on 2009-02-11
What happened to the old Ubuntu community? Posts were answered in 1 minute... Cmon, guys T_T

---

### Post by pieisgood4589 on 2009-02-27
Bump

---

### Post by pieisgood4589 on 2009-02-28
Bump

---

### Post by SwayMeOneWay on 2009-02-28
[http://support.creative.com/downloads/welcome.aspx?nLanguageLocale=1033&nDriverType=1#type_1]("http://support.creative.com/downloads/welcome.aspx?nLanguageLocale=1033&nDriverType=1#type_1")try the first download for the driver i had the exact same problem earlier and came across your post, this driver worked for me, i have the exact same computer so it should work for you

---

