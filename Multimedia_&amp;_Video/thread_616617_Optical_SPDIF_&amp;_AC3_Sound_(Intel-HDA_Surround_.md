---
title: "Optical SPDIF &amp; AC3 Sound (Intel-HDA Surround Sound?)"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by Skerit on 2007-11-18
I just bought an optical spdif cable, thinking it would make my quest for true surround sound (not just "pro logic" false surround) a lot easier ...

A shame that it's not, my amplifier only sees it as a stereo channel, which makes it rather useless ...

I mean; the motherboard HAS digital out, which works in linux, but I can only get a stereo signal? I can't be fated to use the 6 ANALOG jacks, can I?

---

### Post by bksunday on 2007-12-21
Man, i know this post is old but.. have you ever got that working? =)

or anyone else?

---

### Post by jamesntse on 2008-01-02
I was able to get my Intel HDA to produce Dolby Digital 5.1 Surround Sound (video file with AC3 -> SPDIF optical adaptor), thanks to this Wiki:

[http://mythtv.org/wiki/index.php/Configuring_Digital_Sound#But_I_want_to_have_all_my_sound_go_to_the_S.2FPDIF_connector.2C_how_do_I_do_that.3F](http://mythtv.org/wiki/index.php/Configuring_Digital_Sound#But_I_want_to_have_all_my_sound_go_to_the_S.2FPDIF_connector.2C_how_do_I_do_that.3F)

To summarize:

1. sudo edit your /etc/asound.conf
2. Add or edit the following entry:
```

pcm.!default { 
type hw 
card 0 
device 1 
} 

```

(My Intel HDA digital was registered as card 0 and device 1. Do an 'aplay -l' to determine the actual card # and digital device # for your sound card.)

3. Restart alsa-utils
```

sudo /etc/init.d/alsa-utils restart

```

I'm by no means a expert with alsa but this seems to work with mplayer. If you have a video with Dolby Digital 5.1, you can test it with the following:
```

mplayer -ao alsa [path_to_video_file]

```

Hope this helps.

Jim

---

### Post by Skerit on 2008-01-31
Man, this thread is not nearly as old then as it is now :P

I had the concept of "true surround sound" wrong though!

I had to rig up all my software to send out a surround sound, but still nothing changed on my receiver...

UNTIL I actually loaded a movie with surround sound (lol). My receiver somehow saw it was a surround sound signal and made sure it was treated as such.

Real wonderful stuff, those digital signals :D

However, I went back to regular analog sound. Every media player needed different settings and it became a bit too confusing (and my alsamixer also got terribly confused... My volume buttons, though I "told" them to arange the volume of my digital sound, kept changing the volume of the regular pcm sound and... what-ever, I'll bother with it next time.)

---

