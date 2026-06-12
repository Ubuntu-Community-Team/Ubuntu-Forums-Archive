---
title: "[SOLVED] No sound for emu10k1x on Hardy"
date: 2008-07-01
forum: Multimedia Software
---

### Post by vrdabomb5717 on 2008-07-01
I recently switched from Windows XP SP2 to Ubuntu 8.04 Hardy Heron, and so far, it's been working fine. I've begun learning how to use the command line, though I'm still pretty unfamiliar with it. I've installed most of the programs I need and migrated most of my Windows data to Ubuntu, like my Firefox profile and my Pidgin accounts.

So far, my only major issue has been the lack of sound. I've checked to see if the sound was muted, even going so far as to enable all the columns on the Volume Control and raising their volumes to the limit, but I still don't get any sound. I followed the preliminary directions on the *Comprehensive Sound Solutions Guide*, but I haven't been able to deduce much other than that the problem is a software problem, since the hardware itself works on Windows. Here are the results from the few commands that I ran:

```
user@user-desktop:~$ aplay -l
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
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```and the other command:

```
lspci -v

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
    Subsystem: Dell Unknown device 0155
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at ee00 [size=256]
    I/O ports at edc0 [size=64]
    Memory at febffa00 (32-bit, non-prefetchable) [size=512]
    Memory at febff900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
    Subsystem: Creative Labs Unknown device 1003
    Flags: bus master, medium devsel, latency 64, IRQ 22
    I/O ports at df20 [size=32]
    Capabilities: <access denied>

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
    Subsystem: Creative Labs Unknown device 1003
    Flags: bus master, medium devsel, latency 64
    I/O ports at df08 [size=8]
    Capabilities: <access denied>
```So far, I've deduced that Hardy recognizes my sound card, but that the driver may not be loaded correctly. Alsa seems to have a driver for my sound card, so that's not a problem. I got up to **General Help Step 4** and found that the command sudo modprobe snd-emu10k1x would not work. I next downloaded the latest development sound drivers, and then compiled them with no error using the directions I found in the _**[SIZE=1]ALSA driver Compilation[/SIZE]**_ directions. I did that without any trouble, and was able to install the drivers without any errors. However, when I went back to **General Help Step 4** and tried to run sudo modprobe snd-emu10k1x again, I found that nothing came up, even though I just installed the drivers from alsa-project. What should I do now? Any help would be greatly appreciated.

I am running the latest kernel,  2.6.24-19-generic, if that helps at all.

---

### Post by NoobieDoobieDo on 2008-07-03
For gods sakes people.

My sound worked *perfectly* until I ran an 'update' last night and got the latest linux images, etc.

Well smashing job on the 'update' because now I have no sound what so ever.

So now, as usual with Ubuntu, I'll have to tool around on the net for a few hours trying to find a fix for this _*latest*_ thing you've broken.

These are the exact types of reasons I always end up **REMOVING** Ubuntu and replacing it with **_*DEBIAN*_**.

Do please stop breaking things when you roll out 'updates'.

With kind regards,
Your entire customer base.

---

### Post by vrdabomb5717 on 2008-07-04
Can no one help me? It's rather hard to avoid going back to Windows if I don't have any sound...

---

### Post by StaticIp on 2008-07-08
Same problem here.. only it stopped seeing my card HELP...

---

### Post by vrdabomb5717 on 2008-07-23
So, still no replies? Does nobody here have any idea of how to fix this problem? I've gone back to Windows for a while simply because a home operating system is useless without sound.

---

### Post by Ixonal on 2008-08-04
I'm having this problem. for a quick fix, you can get your audio from the on-board audio jacks (IE, the ones on your motherboard). I'd really love to know why my card is detected but not working though... 

actually, I have heard sound out of it. for instance, if I go into system->preferences->sound and set any of the sound playback options to emu10k1x front, it will play the sound, but just that sound. nothing else. and that's the only one of the three that makes any sound (possibly because my system only has stereo output). also of note, when I try to test alsa in there, it gives me the following error
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
I hope someone knows what's goin on with this, cause it's quite vexing.

PS. pardon the capitalization, bad habit of forgetting it and all

---

### Post by vrdabomb5717 on 2008-08-27
Yeah, I had that too. I finally got tired of the problems and updated my installation to the latest daily build of Intrepid Ibex, and lo and behold, that fixed the problem! The hardware recognition definitely got screwed up somewhere along the line, but a full reinstallation fixed that. Now I have music playing in Rhythmbox and I can finally move along to Ubuntu fulltime!

---

### Post by wooikok on 2008-08-28
i am also using Creative SB Live! as my soundcard and just came form Win XP SP2, care to share how u enabled the sound again?...regarding build of Intrepid Ibex...now dual booting ..would really love it if can switch fully once my sound card problem solved..thanks

---

