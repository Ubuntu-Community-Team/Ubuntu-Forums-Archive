---
title: "Alsamixer and 5.1 sound only working with 2 speakers"
date: 2006-05-19
forum: Multimedia &amp; Video
---

### Post by tuga on 2006-05-19
Hello,

My PC has a sound system  5.1 (NVidia CK804). It works fine on XP but on ubuntu 6.06 only 2 speakers work.

When I try "alsamixer" I get the errors:
"
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.ctl.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:817:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory
"

Can someone help on this?

Thanks

---

### Post by mrazster on 2006-05-20
Since I'm pretty much a n00b....I'm not sure on whats wrong.

But hve you tried to reinstall alsamixer and/or alsabase and utils ? They can be found with synaptic.

---

### Post by roderikk on 2006-05-28
Hi,

I've the same problem with my NVidia CK804. Even though Alsamixer works fine with me I cannot get center/rear boxes to work. Does anyone else have the same problem?

Thanks!

---

### Post by d0rift0 on 2006-06-14
I have a AC97 onboard soundcard that's recognised by kubuntu as NVidia CK804. Finally got the rear speakers to work using the 'Duplicate front' option under the switches tab in Kmix. Middle speaker still doesn't work though, any ideas?

---

### Post by peter07 on 2006-07-08
I've got the same problem. Can someone help us? :confused:

---

### Post by bforbes on 2006-07-08
Try reinstalling or updating your kernel. It's worked for me in the past.

---

