---
title: "Wonky sound on realtek alc662"
date: 2008-08-05
forum: Multimedia Software
---

### Post by haxwithaxe on 2008-08-05
Okay here it goes,
I just built a system about a week ago, I hooked up some speakers and the audio was messed up.  Specifically it stuttered and hissed.  I thought it might be the cord i was using so i hooked up some headphones and it was identical. I went through the guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449). Doing so unfotunately seems to have made my problem worse.  
Motherboard: Biostar TF720A2+ AM2+ (nvidia chipsets)
CPU:AMD Phenom 9550 Quad-core
RAM:4GB Dual Channel DDR2-1066
HDD:80GB & 750GB SATA II
OS: Ubuntu Hardy Heron 8.04.1 LTS 32-bit & **WinXP Pro SP2 (sound works fine, so thankfully it's not the mother board)**

###output of "aplay -l"###
# Before the guide it looked something like this:
NVidia (HDA NVidia) device 0: realtek alc662 analog
   (stuff I can't remember)
NVidia (HDA NVidia) device 1: realtek alc662 digital
   (stuff I can't remember)
   
# After the guide
aplay: device_list:205: no soundcards found...
   
###end output###

###relevent output of "lspci -v"###
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Unknown device 820f
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fcf78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
###end of output###

###output of modinfo soundcore###
filename:       /lib/modules/2.6.24-20-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-20-generic SMP mod_unload 586 
###end output###

BIOS has been explored and checked audio now set to "External" drivers that's the only way I can get any sound out of it.

I've tried using OSS, ALSA, and Pulse audio.

I've tried building and rebuilding the alsa modules from source. Even building all of them not just the ones that looked like what I needed.

I have made sure that my user profile and root are part of the audio group.

Thanks in advance.

PS: I was double checking that I had covered all bases and possibly found the drivers direct from realtek.  I don't know why I couldn't find them a week ago.  I will repost when I have the results.

_**Update: **_realtek drivers failed also tried alsa v1.0.17 also failed also tried adding "option snd-hda-intel model=3stack-6ch-dig" to /etc/modprobe.d/alsa-base ... failed also alsaconf failed. Now trying fresh install -- will update when done.

_**Update2:**_ fresh install was no good same problem only now alsa can see my card I've also found the alsa wiki says the nvidia built realtek alc662 is supposed to use the snd-intel8x0 kernel module.
[http://alsa.opensrc.org/index.php/RealtekALC](http://alsa.opensrc.org/index.php/RealtekALC)

---

### Post by Qchan on 2008-08-05
[b][color=darkred]
You must be using onboard sound. The hissing could be due to the lack of ground those sound chipsets have.

The studdering would have more to do with the buffering. There's a way to increase the buffer size, I hear, but it's complicated. What I'd suggest is testing other applications and seeing if they suffer from the same thing.
[/b][/color]

---

### Post by haxwithaxe on 2008-08-05
Update: realtek drivers failed also tried alsa v1.0.17 also failed also tried adding "option snd-hda-intel model=3stack-6ch-dig" to /etc/modprobe.d/alsa-base ... failed also alsaconf failed.  Now trying fresh install -- will update when done.

reply: I tried all sorts of media players(vlc, totem, mplayer, xine, alsaplayergui) for each sound system and it's not the hardware causing any of the problems.  I have windows installed on the same machine and the audio is pristine. Also I'm playing local media as well as streams, none come through at all right.  This is not your standard poor audio quality this is completely unrecognizable.  The standard alsa test.wav sounds like a random tone (as apposed to the normal one) played over and over even when it's played only once in a media player.  It will go for as long as I let it without the track repeating in the player.

Thanks for the quick reply though.

---

### Post by DerOli on 2008-08-11
Hi 

I've very similar problems with my onboard sound on a Gigabyte GA-M750SLI-DS4. 
It's a Realtec ALC885 codec.

The Onboard Sound usually is stuttering while playing any kind of audio.
While playing videos it's stuttering a bit too but not so intense. 

I've tried to pull down all Audichanels with alsamixer below 80%,
tried the "option snd-hda-intel model=several options" in alsa-base but there where no improvements.

Under System > Settings > Audio all Options are set to ALSA

But i figured out something really strange. Whihle heavy CPU load (i.e. 100% using Boinc on all processors) the sound works mostly perfect. (Every 30 to 40 seconds there is a short single scrath in the sound) When you stop Boinc the stuttering immediately starts again. When contiuing Boinc the sound again works perfectly.

I also have searched through a lot of forums but didn't found any solution yet.

---

### Post by markbuntu on 2008-08-12
If your sound is suttering you can try this link, part C should fix you up:


[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by haxwithaxe on 2008-08-14
Sorry,
I didn't post about that yet.  I've tried that thread, no dice so far.  I got a little improvement by fiddling with the daemon.conf settings, but there is still a lot of stuttering.

---

