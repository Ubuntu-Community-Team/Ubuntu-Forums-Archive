---
title: "no sound in wine under different user"
date: 2012-11-23
forum: Multimedia Software
---

### Post by virx on 2012-11-23
Dear Ubuntu users,

Since some windows games need modification for playing under wine I do not trust them. I run all games as different user using program SUX for X redirection.

When I log into Ubuntu Unity with my gaming account and start wine then sound works, but when I log into Unity with my regular account and from terminal with SUX to gaming account, there is no sound in wine.

Terminal output:
```
 $winecfg
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
err:pulse:pulse_contextcallback Context failed: Connection refused
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 23 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0

```


$ aplay -l
aplay: device_list:252: no soundcards found...

Few years ago it was working. Probably it has something to do with pulseaudio.

Do I need somehow redirect sound also from one user to other?

---

### Post by virx on 2012-11-24
Just in case somebody with the same problem, then solution came from [SoundTroubleshootingProcedure Step 10]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_10")
When I added my gaming account into group "audio", logged out and in, sound worked as expected

---

