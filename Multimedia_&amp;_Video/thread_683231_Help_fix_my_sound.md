---
title: "Help fix my sound"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by RayDeCampo on 2008-01-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/185811](https://bugs.launchpad.net/bugs/185811) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A longtime Fedora/RedHat user, I'm trying Ubuntu for the first time.  Unfortunately, sound is not working on my system.  I filed a bug at [https://bugs.launchpad.net/bugs/185811]("https://bugs.launchpad.net/bugs/185811") with the various debugging outputs.

The short version is that I had no sound at all until I configured System->Preferences->Sound to use USB Audio instead of Autodetect.  Now I have sound for most applications but not all.  The biggest issue is the lack of sound in flash or java plugins in Firefox.  Also, programs like mpg321 have no sound:

[HTML]ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
No default libao driver available.[/HTML]

I've tried various workarounds from these forums, but I suspect the issue is more fundamental.  E.g., I have a /dev/snd/controlC1 but no /dev/snd/controlC0.  This strikes me as odd.

Ray

---

