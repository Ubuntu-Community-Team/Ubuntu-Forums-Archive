---
title: "Lenovo 3000 N100 Sound Problem"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by timhaughton on 2006-08-04
I know there are problems with this laptop and sound under dapper, I've followed the most common workaround:

[http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1101974&postcount=10)

And I've been through this:

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

But I still have zero sound. The sound card is found by the system, and the module is loaded. The only significant thing I've changed in the system is the kernel (now 686).

Anyone have any other suggestions before I log it as a bug?

Cheers,

Tim

---

### Post by xp_newbie on 2006-08-28
> **timhaughton said:**
> Anyone have any other suggestions before I log it as a bug?

It may indeed be a bug (merely the fact that it doesn't work out of the box), but I have managed to solve all sounds problems, including using the special silver-colored keys for volume and mute. Here is a concise summary of what I did:

> admin@lenovo3000:/$ lsmod|grep snd
snd_hda_intel          18964  1
snd_hda_codec         142640  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

typed: alsamixer
 > received a cursors-like GUI with sliders as follows:
   Playback: Headphone, PCM, Front, Surround*, Center*, LFE*, Line*, CD, 
             Mic*, IEC958**, PC Speaker*, Aux*, Mono*, Stereo Downmix**
   Capture:  Line, CD, Mic, Phone, Aux, Mono, Capture!, Mix
   (card: HDA Intel, chip: AD1986A)

*  = Off, but sliders responding to up/down arrow keys,
** = Off, no full slider
!  = The only "Capture" control that has slider

Unmuting various combination (including *nothing* muted) did not help. 
Then:
  > sudo gedit /etc/modprobe.d/options
  > Add the line:
     options snd-hda-intel model=laptop-eapd
  > Reboot.

That's it. :)

---

### Post by chrismyers on 2007-11-11
This works on my 3000 N200:

[FONT=Tahoma]Try adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo[/FONT]

---

