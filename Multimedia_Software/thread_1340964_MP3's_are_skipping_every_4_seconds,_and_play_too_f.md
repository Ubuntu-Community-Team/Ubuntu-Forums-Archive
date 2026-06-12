---
title: "MP3's are skipping every 4 seconds, and play too fast (Amarok)"
date: 2009-11-29
forum: Multimedia Software
---

### Post by stephanelefou on 2009-11-29
Hi,

On a newly, fully patched 9.10 installation of Kubuntu, the issue I got is that Amarok is playing songs way too fast -about 10% faster than normal-, also, every 4 seconds, it "chugs" or "lag" for about half a second.  

I did try the alsa driver but no luck.  The soundcard is an old on-board Intel.  I've been searching other forums and it looks like there are NO Linux drivers for my system:
[http://fixunix.com/ubuntu/555161-sound-can-anyone-explain-please.html](http://fixunix.com/ubuntu/555161-sound-can-anyone-explain-please.html)


Well, just in case you'd like to suggest me something, here is some info on my system:

Computer PIII 1Gzh,  Dell GX150 (slim or mini)
Audio type	Sound Blaster emulation
Audio controller	Analog Devices AD1885 AC97 Codec

stephane@gx150:~$ uname -a
Linux gx150 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

stephane@gx150:~$ lsmod |grep snd
snd_intel8x0           30168  2
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
stephane@gx150:~$

stephane@gx150:~$ cat /proc/asound/modules
 0 snd_intel8x0


Thanks!

---

### Post by Newvin on 2009-12-15
I have the same issue here.  Any mp3 skips 4 seconds at a time in any player I choose rhythmbox, amarok, banshee, and several others.  I haven't tried any other types of audio files.  Everything was fine in Jaunty; the problem began directly after upgrading to Karmic.

---

### Post by Newvin on 2009-12-17
It's fixed! After trying many different solutions, I think what did the trick was this:

```
# first a simple line to select your sound card from a drop down
sudo apt-get install asoundconf-gtk && asoundconf-gtk

# next forcing the reloading of alsa
sudo /sbin/alsa force-reload
```

I found it here:

[http://ubuntuforums.org/showthread.php?t=1243064&page=2](http://ubuntuforums.org/showthread.php?t=1243064&page=2)

---

