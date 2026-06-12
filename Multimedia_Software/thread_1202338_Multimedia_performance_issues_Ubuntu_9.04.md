---
title: "Multimedia performance issues Ubuntu 9.04"
date: 2009-07-02
forum: Multimedia Software
---

### Post by g003y on 2009-07-02
I have installed en upgraded my ASUS Pundit Barebone AMD64-X2 4800+ with Ubuntu 9.04 and there are some performance issues. And although I've got acquainted with the administration procedures I consider myself to be a newbie when it comes to Ubuntu.

I'm not impressed by the performance of video playback using players such as VLC or mplayer. I read on the sticky that Intel Chipset users have this problem but my system is no Intel and the GPU comes from nVidia (GeForce 6150, nForce 3 chipset).

The audio works but the speakers are hissing as if the volume was set to max (which it isn't) regardless of what the actual volume is set to. When booting into WinXP-x64 the speakers are silent, even when the volume *is* set to max. When muting the sound the speakers give off crackling noise as if there was some loose connection somewhere. I don't have this issue in WinXP either.

XBMC which I find to be quite impressive although I miss media library features such as those found in software such as Songbird or Amarok, is very sluggish on my system. Amarok refuses to play, and if I struggle with the playback long enough, the program crashes.

---

### Post by Th3_uN1Qu3 on 2009-07-02
First install the restricted nvidia drivers if you haven't yet, they'll help a great deal.

As for the sound:

```
sudo apt-get remove pulseaudio
sudo apt-get remove alsa
sudo apt-get install alsa
```

Then go into Sound Preferences and set everything to ALSA. It should be much better. I could never get PulseAudio to work without crackling and popping all the time, by letting ALSA do the software mixing things are much much better.

---

### Post by g003y on 2009-07-02
Thanks for your quick reply.

I tried what you suggested but I still hear a hissing sound from the speakers, and Amarok still crashes.

Regarding nVidias proprietary drivers I think that's what is installed by default actually. I'm not quite sure how to check it but I got that notification during the upgrade progress and I also have NVIDIA X Server Settings in the administration menu.

---

### Post by HavocXphere on 2009-07-02
Pulse didn't work right on installation for me either. Unlike Th3_uN1Qu3 I choose the opposite route and installed more pulse stuff.

Do what this guy says...he knows what he's talking about:
[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
More complicated stuff by same author:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by g003y on 2009-07-02
I took the other route and installed further packages as you suggested. I still have the hissing sound in my speakers but I have managed to get rid of the crackles when muting.

I chose HDA Nvidia - Realaudio ... (PulseAudio) instead of the HDA Nvidia - ALSA .. as main volume control.
None of these different volume controls take away the hiss though.

---

### Post by g003y on 2009-07-02
I have now found the source of the noise. It was the CD volume control. By muting it the noise is gone and I can keep this permanent as I don't have any CD or DVD player on the computer.

It seems that the video playback is a little bit better now but I'm not entirely satisfied with it. XBMC is still very sluggish and it seems that the programs get confused about the volume controls. When in the desktop; the volume control that I have on my keyboard (Logitech diNovo edge) controls whatever I have chosen to control in the sound settings (now set to "HDA NVidia (ALSA Mixer)"). If say that I mute the volume with the ALSA Mixer (through my keyboard) and then start XMBC, I lose control of that mixer since XBMC "hijacks" the volume control I have on my keyboard and the sound stays mute regardless of what I do in XBMC.

Amarok still refuses to play and crashes but I guess it's no big deal when there are other players around such as aTunes or Songbird.

---

### Post by Th3_uN1Qu3 on 2009-07-02
Try Audacious. ;) Also Rhythmbox (the default audio player) isn't that bad.

The mixer issues you are experiencing with XBMC is probably related to pulseaudio. And yes i had read that thread too, and no it did not help me at all. Pulse is just too laggy and crackly and whatnot.

Let me put it this way: Pulse is an extra layer of bloat over the already bad ALSA driver. To quote PulseAudio devs, "PulseAudio is in some cases uncovering bugs in ALSA", in other words they're blaiming it on ALSA, while ALSA alone works just fine. However ALSA does have some decent software mixing nowadays, it's still not the best thing since sliced bread however it is continuously improving and it is certainly better than last year.

What Pulse does is add latency and eat up CPU cycles for no reason. It has a built-in CPU limiter that strangulates it when it thinks it's using too much CPU time (all the time that is), which produces these "nice" crackles and pops in the audio. Disabling the limiter usually results in PulseAudio crashing. If you can finally manage to get it NOT to crackle (which i have never succeeded), your audio will have a latency of a few seconds. Way cool. If you are not using it for its ability to send sound over a network, then you should not need it at all.

I wonder, is this realtime audio thing really THAT hard to get working? Coz it sure does work on 'doze, AND with open-source drivers too (ASIO4ALL).

---

