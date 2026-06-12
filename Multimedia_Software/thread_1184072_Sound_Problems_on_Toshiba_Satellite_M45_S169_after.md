---
title: "Sound Problems on Toshiba Satellite M45 S169 after Update"
date: 2009-06-10
forum: Multimedia Software
---

### Post by Mandala 13 on 2009-06-10
Well, the things is this. After a long time having sound problems since installing Jaunty, I finally had some sound. Yes, certainly after a while, the sound crash but strangely enough, RhythmBox always worked and I was happy; in case I wanted to do something else, I just needed to restarted and I would be able to watch movies, use Youtube, and more. 

For getting to this "Nirvana" state, I had to uninstall PulseAudio and be sure that ALSA did come first. Now, after an Update that I made today, that appear in Notifications, of Linux Headers and Images, I found that I have no sound at tall. There's this bell sound since the second sound of the system while booting up, and not even RhythmBox works.

Tried using on terminal  > wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh, for getting more information about the Driver and all, to see if I could fix it up, but its suppose to give me a link to a page with my sound information and nothing happens, as a matter of fact. I would say that this could make me go over to Hardy, where I had no problems, but sincerely, I like Jaunty way too much and want to fix this problem.

Here's my info:

aplay
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1


lspci
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

Any help? :)

EDIT:

Following this thread [http://ubuntuforums.org/showthread.php?t=1046137&page=11](http://ubuntuforums.org/showthread.php?t=1046137&page=11), I upgraded the ALSA driver to Alsa 1.0.20 (Stable). Reboot and now, I can hear some music in RthythmBox again. But, I can't hear Flash Videos from Youtube and other kind of sites, and I can't watch movies. Basically, only the Rthythm is actually working now, just like before. I know that I should be happy, but I would like to think to have the problem fix completely. Any help? If you need any info, just ask it, :)

---

### Post by Mandala 13 on 2009-06-11
In case you get here, I'm trying to solve the problem with the help of this thread, so this one is no longer necessary. [http://ubuntuforums.org/showthread.php?t=1046137&page=31](http://ubuntuforums.org/showthread.php?t=1046137&page=31)

:)

---

### Post by Mandala 13 on 2009-07-29
Thanks to Chochem, I got my sound working all right, at last.

If you're using ATI IXP SB400, this might be what you're looking for.

[http://ubuntuforums.org/showthread.php?p=7695947#post7695947](http://ubuntuforums.org/showthread.php?p=7695947#post7695947)

---

