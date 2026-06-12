---
title: "So I ruined my sound with alsa-utils."
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by SoulinEther on 2007-01-12
So.... as the title goes, while I was trying to tinker with getting my default sound card to be the second one seen in my PC (this would be my onboard sound card, a via82xx), I decided I'd do something that seemed somewhat logical at the time. Taking a trip down memory lane, I scrolled up through my bash stuff and found this nice little line:

etcetcetc$ sudo /etc/init.d/alsa-utils stop 0

And since then, it's been a quiet world here in Linux.

I've gone through the comprehensive... sound... deal. Twice. And i've tried to compile drivers from source from their website. That really... really didn't work for me at all lol.

So.. any suggestions?

(and while I'm on the matter of problems... why does my apt feel so inclined to want to remove all my gnome stuff? then again, I just reinstalled the GDM and stuff after a little bit of turmoil.

I suppose you can tell i've had a bit *too much* fun with Ubuntu ;P)

Thanks in advance... heh.

---

### Post by Hub-1 on 2007-01-12
Try:
```
sudo /etc/init.d/alsa-utils start
```

---

### Post by SoulinEther on 2007-01-12
I have tried that, no visible result. I'll try it again:

```
 * Setting up ALSA...                                                    [ ok ]
```

And... somewhat later...

```
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'V8237'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

```

---

### Post by sgx on 2007-01-13
Do you have    /home   on it's own partition?
If not, now is the perfect time  to reinstall, and
make that extra partition, so future reinstalls
will keep your desktop and settings intact, when you tell the installer
not to reformat   /home. 

If you do have a separate    /home   partition, it is also
the perfect time to reinstall...let the kernel fix your sound,
as few experts can go beyond the obvious things...get all
the latest goodies -and- working sound today...run. don't walk,
have some coffee or tea, your happiness is at stake!

---

