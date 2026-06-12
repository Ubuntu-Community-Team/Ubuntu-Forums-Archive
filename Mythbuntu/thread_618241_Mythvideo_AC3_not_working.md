---
title: "Mythvideo AC3 not working"
date: 2007-11-20
forum: Mythbuntu
---

### Post by Lester_Burnham on 2007-11-20
Hi,

I'm trying to get audio working properly in Mythvideo. I'm running Mythbuntu 7.10 using SPDIF on an Intel board ALC880 with iec958 unmuted.

I've tested a DVD inside MythDVD and 5.1 is fine.
I've played an ac3 encoded xvid outside mythtv using mplayer and ac3 is fine.
If I play the same file inside MythVideo it is only 2 channel.
If I add the alsa:device=hwac3 to the player path inside MythVideo setup, ac3 works fine, but then stereo encoded files have no audio.

Something must've changed some where, because I have it working on other machines with Ubuntu 7.04.

Thanks,
Lester

---

### Post by foxbuntu on 2007-11-20
I would suggest trying to chang e your player from internal to an external one such as mplayer/xine.


Xine:
```
xine -pfhq --no-splash %s
```

MPlayer
```
mplayer -fs -zoom -quiet -vo xv -playlist %s
```

---

### Post by Lester_Burnham on 2007-11-20
Hi foxbuntu,

It is the Mythvideo player which already uses mplayer out of the box.
I can get it to work using "alsa:device=hwac3" tacked on the end as below, but I then lose stereo.

mplayer -fs -zoom -quiet -vo xv -playlist %s alsa:device=hwac3

I might use xine and see how I go too.

For interest sake MythDVD uses the internal command, yet it plays AC3 fine. I have also loaded the w32 codecs, as well and was thinking it could be a config issue in ffdshow maybe. How do I "really" tell what codec is being used.

Thanks,
Lester

---

### Post by superm1 on 2007-11-21
> **Lester_Burnham said:**
> Hi foxbuntu,

It is the Mythvideo player which already uses mplayer out of the box.
I can get it to work using "alsa:device=hwac3" tacked on the end as below, but I then lose stereo.

mplayer -fs -zoom -quiet -vo xv -playlist %s alsa:device=hwac3

I might use xine and see how I go too.

For interest sake MythDVD uses the internal command, yet it plays AC3 fine. I have also loaded the w32 codecs, as well and was thinking it could be a config issue in ffdshow maybe. How do I "really" tell what codec is being used.

Thanks,
Lester

ffdshow is not used in Linux. Its parent project, ffmpeg . For ac3 files I personally always use xine.

---

### Post by Lester_Burnham on 2007-11-21
Hi & thanks for the reply superm1.

I will give it a try with xine and see how I go. The reason I left it as mplayer, was I thought .mkv was better supported.

More info on audio setup:
Audio output device = ALSA:default
Passthrough output device = ALSA:iec958:{AESO 0x02}
Pass through AC3 & DTS checked
Mixer device = default
Mixer controls = master

Thanks for your continued efforts in helping get Mythtv this far in Ubuntu, too superm1!

Lester

EDIT: Tried xine and it played stereo without previous configuration. I then changed the audio in xine to spdif passthrough and ran it again. I got a pink screen and AC3 working for a few seconds till the box froze. Something to do with the AC3 I fear. Any ideas?

---

### Post by joe_newbie on 2008-04-14
I have the same problem. If I specify -ac hwac3 for the mplayer command,  ac3 pass through works fine. But then 2 channel files don't have sound. Is there anyway to have it automatically detect which output to use?

---

### Post by joe_newbie on 2008-04-15
solved my problem. This is the command line used in player settings for mythvideo:

mplayer -fs -zoom -afm hwac3 -quiet -vo xv %s 

the mplayer online documentation was very clear about the -afm option allowing for falling back to other codecs.

---

