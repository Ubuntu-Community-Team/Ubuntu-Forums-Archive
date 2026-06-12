---
title: "no HDMI sound output"
date: 2013-05-07
forum: Multimedia Software
---

### Post by jingo811 on 2013-05-07
Hi,

I have tried to watch videos on the TV by using a HDMI cable.  It didn't work very well when I first tried it on Mint 14 Nadia only video no audio on the TV.
Then I tried AMD-xbmcbuntu Frodo and I only managed to get sound from the Netbook only at two separate occassions, I didn't remember what procedures I did to get sound from Netbook speakers because I tried a lot of procedures.

So now I ended up with Lubuntu 13.04 Raring, and sound was working on Netbook right away without any fixing just like it did on Mint 14.  But the same problem only video no audio on the TV.  What else can I do to get HDMI sound output on the TV?


**1.)  Is ALSA present in your kernel?** - [http://www.seehuhn.de/pages/alsa](http://www.seehuhn.de/pages/alsa)
```
bruce@lee:/proc/asound$ ls
card0  cards    Generic  modules  SB   timers
card1  devices  hwdep    pcm      seq  version
```

**2.)  What sound cards are known to the system?**
```
bruce@lee:/proc/asound$ cat cards 
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeb44000 irq 40
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb40000 irq 16
```

**3.)  How do I set the default device?**
So I created this file like seehuhn wrote on their webpage.  Because some other command told me that card 0 have the text HDMI and not card 1 but I have already tried them both in this file.  Still no sound on TV.
```
bruce@lee:/etc$ cat asound.conf 
defaults.ctl.card 0
defaults.pcm.card 0
defaults.timer.card 0

```

**4.)  SPDIF unmute**  - [https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_7](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_7)
> If HDMI output has stopped working, muting and then unmuting the SPDIF output in alsamixer can cause the sound to start working again 
I pressed M to mute and unmute SPDIF but no difference.



[SIZE=4]GRAPHICS info[/SIZE]

**5.)**
Since [COLOR="#DAA520"]"cat /proc/asound/cards"[/COLOR] seemed to mention ATI I figured you might want some graphics info on my Netbook.
```

bruce@lee:~$ lspci -vvnn | grep "VGA compatible"
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250] [1002:9804] (prog-if 00 [VGA controller])

```

**6.)**
```
bruce@lee:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6250 Graphics
OpenGL version string: 4.2.11986 Compatibility Profile Context

```

**7.) Using AMD proprietary drivers**
Software & Updates > Additional Drivers
> * Using Video driver for the AMD graphics accelerators from fglrx (proprietary) 

What else can I do to get HDMI sound output on the TV?

---

