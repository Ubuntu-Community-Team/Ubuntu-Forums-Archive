---
title: "[SOLVED] Realtek ALC889A - No Sound From Multiple Apps"
date: 2008-07-11
forum: Multimedia Software
---

### Post by fastfret79 on 2008-07-11
Well, my old Audigy 4 seems to have died so I am now using my on-board sound which is Realtek ALC889A. I am using Hardy 64 bit and sound works but not from more than one program at once.

Everything seemed to be detected ok, except an 'aplay -l' returns:

> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Also a 'cat /proc/asound/card0/codec#* | grep Codec' returns:

> Codec: Realtek ALC885

Both giving me different and wrong results!? 

Despite this, sound quality is perfect and up-mixing to 5.1 works (I need to get/make a jack converter to get 7.1 working with my creative speakers).

However, only one app can use audio at a time. i.e. if I open Firefox and play a flash video, then open up Amarok I get a 'xine was unable to initialize any audio drivers' error message. If I open Amarok first, music plays perfectly, but if you then try and open a flash video in Firefox, the video just hangs. MythTV works perfectly if opened first, but will only show video and no sound if opened second.

I have made sure that everything is setup to use ALSA, both in 'System > Preferences > Sound' and 'System > Preferences > Multimedia Systems Selector'. All apps are configured to use ALSA (Amarok, MythTV) and I have even made sure that PulseAudio isn't even loaded using BootUp-Manager.

Is this caused by incorrectly detecting the sound card? Would compiling ALSA from source fix the issue? I read on the ALSA website that the latest version supports my sound card chipset but doesn't Hardy use that latest version? 

Any help greatly appreciated :)

---

### Post by forger on 2008-07-11
"However, only one app can use audio at a time."

Try enable System > Preferences > Sound > Sounds > check "enable software sound mixing (ESD)" > Close
If it's checked, uncheck it, click close, go to sound > sounds and check it again, then close again.

Log out and log in. Should work now :\


Try "cat /proc/asound/cards" to see a list of your sound cards

---

### Post by fastfret79 on 2008-07-11
Still the same :(

'cat /proc/asound/cards' returns:

0 [SB             ]: HDA-Intel - HDA ATI SB
                     HDA ATI SB at 0xfe024000 irq 16

---

### Post by fastfret79 on 2008-07-11
Followed the instructions to Part A of [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")  switching everything over to PulseAudio and everything is now working correctly - even upmixing which I couldn't get working before with PulseAudio :D

---

### Post by Roasted on 2008-07-14
I wonder why in the world I get scratchy audio, whether alsa or pulse. XP works perfect so I know the onboard card is okay.

fastfret - do you have any sound quality issues at high volume? Even a little bit?

---

### Post by fastfret79 on 2008-07-14
No quality issues here at all.

I guess you've already checked all speaker connections and muted any inputs?

Also have you tried your speakers with another input (MP3/CD player) to make sure it's not an issue with the speakers themselves?

---

### Post by meejah on 2009-03-26
> **Roasted said:**
> I wonder why in the world I get scratchy audio, whether alsa or pulse. XP works perfect so I know the onboard card is okay.


I have a new mac mini (2009) with Debian "lenny" and get horrible static (codec#0 reports Realtek ALC889a, lspci reports NVidia chips, snd-hda-intel only works if I tell it model=imac24). fix_position=1 solves *some* of the cracle, but not all.

It *sounds* like audio interference on the cable, but an older-gen mac mini (powerpc) with debian plugged into the same equipment works fine. OS X on the same box, same equipment works fine.

Any hints welcome.
Thanks,
mike

---

### Post by markbuntu on 2009-03-27
If your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```

You can play around with these numbers to get the best from your particular sound device.

There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you. 

The nvidia crackling problem is well known but you need a 2.6.27 or newer kernel and ALSA 1.0.17 or better to fix it.

---

### Post by wakslob on 2011-10-19
> **markbuntu said:**
> If your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```You can play around with these numbers to get the best from your particular sound device.

There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you. 

The nvidia crackling problem is well known but you need a 2.6.27 or newer kernel and ALSA 1.0.17 or better to fix it.
Im having the same issue as well. So how do i update ALSA? Why was this marked Solved?

---

