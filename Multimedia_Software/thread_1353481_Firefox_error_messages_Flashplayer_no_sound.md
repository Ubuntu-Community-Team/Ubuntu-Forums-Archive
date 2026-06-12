---
title: "Firefox error messages Flashplayer no sound"
date: 2009-12-12
forum: Multimedia Software
---

### Post by skaramanger on 2009-12-12
Greetings,

Like many of you out there, I am having sound problems with flashplayer. Below is error messages I get when going to a flash site:

```
<I Like Scripting>firefox -ProfileManager --no-remote
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1433:(_snd_pcm_hw_open) Invalid value for card
Killed
```

I followed this thread:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")


I eventually downloaded and compiled the alsa source code from the alsa-project, just to get sound that wasn't scratcy and unintelligble.
So where I stand now is, 

I get system sounds, I get music.  These are both quite satifactory.

I cannot record using microphone. Okay I don't need that at the moment, but it would be nice. 

My problem as stated above is no sound in flash and no sound in my favorite game nexuiz.  I will post error messages from the game if someone would like to see them, but they are very close to the output that I get from flash.  This must be a clue (I hope). 

Here are some compile errors I get:


```
gcc: control/.libs/libcontrol.a: No such file or directory
gcc: mixer/.libs/libmixer.a: No such file or directory
gcc: pcm/.libs/libpcm.a: No such file or directory
gcc: timer/.libs/libtimer.a: No such file or directory
gcc: rawmidi/.libs/librawmidi.a: No such file or directory
gcc: hwdep/.libs/libhwdep.a: No such file or directory
gcc: seq/.libs/libseq.a: No such file or directory
gcc: alisp/.libs/libalisp.a: No such file or directory
make[2]: *** [libasound.la] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.21a/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.21a/src'
make: *** [install-recursive] Error 1
```

Linux myhost 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

Alsa: alsa-1.0.21a

Flashplayer is the 64bit beta version: 10.0 r42

My sound card is a built in C-media 6501.

Thanks in advance,

---

### Post by skaramanger on 2009-12-13
Update,

I decided to remove alsa-source that I downloaded from alsa project and install from repos.  I first used the dpkg-reconfigure method with module-assistant.  With out any luck.  Then I pured the sound all together and reinstalled.  I am back to where I was before.  Systems sounds, music, but no flash and no game sounds. Oh well. I keep reading forum posts and going from there.

---

### Post by skaramanger on 2009-12-16
<Solved> Problem is now solved.  I did a fresh install and all playback sound works.  Havn't tested the microphone yet. But that can be subject for another thread.

---

