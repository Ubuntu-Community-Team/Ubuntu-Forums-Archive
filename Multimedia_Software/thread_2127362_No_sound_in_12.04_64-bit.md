---
title: "No sound in 12.04 64-bit"
date: 2013-03-19
forum: Multimedia Software
---

### Post by Curbuntu on 2013-03-19
I have finished upgrading every computer in the house to Ubuntu 12.04.  And, as bad luck would have it, the only machine that's had any issues belongs to my wife.  As worse luck would have it, the only problem with her machine is that the sound doesn't work -- and she listens to a LOT of classical music at her computer.  So, friends, in the interest of keeping a guy out of the digital doghouse, I ask for your help.

I should quickly add that sound on this machine worked fine under Ubuntu 10.10, which was on her machine until about two months ago.  No hardware has changed.  And just to make certain that everything was working properly soundwise, I burned off the Ubuntu 10.04.4 DVD last night and booted from it.  No problems -- everything worked fine.  But boot back into 12.04 and it's doghouse time again.  No, nothing is muted.  No, headphones don't work.  Yes, the speakers are turned on.  Yes, I've tried pavucontrol, alsamixer, made certain  of choosing the right output device.  I've even tried other solutions proffered on other forums, including deleting .pulse, fiddling with alsa-base.conf (I restored the original), etc.

FWIW, the only suggestion that yielded partial success was appending the line
```
options snd-hda-intel model=generic
```

to /etc/modprobe.d/alsa-base.conf.  All that got was rear right and left speakers working in a hardware list that was reduced to one option -- basic analog stereo output.

Hardware involved is detailed in the attached lshw output.  What I assume to be the relevant info in lshw is this:

```
[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]multimedia[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Audio device[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]RS880 HDMI Audio [Radeon HD 4200 Series][/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Hynix Semiconductor (Hyundai Electronics)[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]5.1[/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"]pci@0000:01:05.1[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]00[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]32 bits[/TD]
[/TR]
[TR]
[TD="class: first"]clock:[/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]pm msi bus_master cap_list[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]snd_hda_intel[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]19[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]feae8000-feaebfff[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

The doghouse is cramped and the nights are still cold. Any help would be appreciated!

---

### Post by mike acker on 2013-03-19
general approach to audio bugs
1. open your system settings and select the SOUND control
2. select the output tab and then run the built in TEST

the sound has to go to an amplifier. debugging amplifiers is a little beyond the scope of this forum . fundamentally you need to work with an amp that you know works: test it using another computer with a similar set up . note that amps are now stereo, or surround sound,  where surround sound can be 5.1 or 7.1 format 

once you are connected to an amp you know works then you run the Test Sound option on your System Settings panel . this should allow you to test each channel .

if you can't get any of the output options to work then you probably have a problem on your mother board or a bad device driver .

if the sound worked "OK" with a different O/S then it's probably as device driver issue .  i would get a suitable DAC or Sound Card then from Amazon or NewEgg

---

### Post by Curbuntu on 2013-03-19
> **mike acker said:**
> general approach to audio bugs
if you can't get any of the output options to work then you probably have a problem on your mother board or a bad device driver .

if the sound worked "OK" with a different O/S then it's probably as device driver issue .  i would get a suitable DAC or Sound Card then from Amazon or NewEgg

Thanks for the reply.

I have no doubt that it's a device-driver issue, since the exact same setup works in 10.10 and 10.04.4 on this machine.  The Asus mobo is only two years old; I installed it about the time I moved my wife to Ubuntu originally.  I'm using the built-in sound chip.  What got left out of Ubuntu 12.04 or its Linux kernel that necessitates a non-canonical [pun semi-intentional] driver -- or a sound-hardware upgrade?  Sound drivers never seem to be listed in Ubuntu's "Additional Drivers" like WiFi and video drivers are, so where would I find one?

---

### Post by mike acker on 2013-03-20
> **Curbuntu said:**
> Thanks for the reply.

I have no doubt that it's a device-driver issue, since the exact same setup works in 10.10 and 10.04.4 on this machine.  The Asus mobo is only two years old; I installed it about the time I moved my wife to Ubuntu originally.  I'm using the built-in sound chip.  What got left out of Ubuntu 12.04 or its Linux kernel that necessitates a non-canonical [pun semi-intentional] driver -- or a sound-hardware upgrade?  Sound drivers never seem to be listed in Ubuntu's "Additional Drivers" like WiFi and video drivers are, so where would I find one?

General Approach to Problem Solving

I have found that google is one of the best aids available
doing a little "googling" on this issue I found:

[https://wiki.ubuntu.com/Audio/HDAGeneric](https://wiki.ubuntu.com/Audio/HDAGeneric)

here's what shows on mine:
```

mike:~$ grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC892
/proc/asound/card2/codec#0:Codec: ATI RS690/780 HDMI
mike:~$ 

```

this stuff is the on-board sound. i don't use the on-board stuff: i have a Bheringer USB connected DAC

additional reference

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

*** porceed with caution ***

---

### Post by Curbuntu on 2013-03-30
Sorry for the delayed response.  I tried the suggestions offered in your links, but still couldn't get things to work.  Because of time pressures (I'm going to be away 50 out of the next 53 days, mostly abroad), I opted to add a used SoundBlaster 5.1 sound card in the unit, turning the onboard sound off on the mobo from BIOS.  Everything seems to be working fine now.  But it will always annoy me a bit that I couldn't get the built-in chip to work.

Thanks for all your help and suggestions!

---

