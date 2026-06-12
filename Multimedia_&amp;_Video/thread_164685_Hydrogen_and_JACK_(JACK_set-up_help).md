---
title: "Hydrogen and JACK (JACK set-up help)"
date: 2006-04-23
forum: Multimedia &amp; Video
---

### Post by .t. on 2006-04-23
I have installed a few apps, as directed on the Breezy Studuo Preparation page (hydrogen jackd jackeq jack-rack jamin qjackctl qsynth seq24 vkeybd ams amsynth) - although I'm using Dapper - but cannot get JACK setup right. When I set Hydrogen to use JACK, I get two errors:
1: Error starting driver
2: Jack driver: cannot connect output port.

However, I get these same errors with every driver setting.

I would also like to know how to get amaroK to play through JACK. 

Thanks much, .t.

---

### Post by bwanab on 2006-04-25
[QUOTE=.t.]I have installed a few apps, as directed on the Breezy Studuo Preparation page (hydrogen jackd jackeq jack-rack jamin qjackctl qsynth seq24 vkeybd ams amsynth) - although I'm using Dapper - but cannot get JACK setup right. When I set Hydrogen to use JACK, I get two errors:
1: Error starting driver
2: Jack driver: cannot connect output port.

However, I get these same errors with every driver setting.

I would also like to know how to get amaroK to play through JACK. 

Thanks much, .t.[/QUOTE]

Sorry for asking such a dumb question, but from your description I can't tell - are you launching jack before you run hydrogen? One of the programs that you installed is qjackctl. Launch that and it should start jackd. Then you should be able to launch hydrogen. If you are launching it, post the output from qjackctl's messages and we can try to see what might be the problem.

---

### Post by .t. on 2006-04-26
Yeah, I set up JACK in qjackctl and start with OSS - not I cannot get it to start with ALSA. I'm often getting these ALSA errors:

```

ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.ctl.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv 
returned error: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or 
directory
ALSA lib control.c:817:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such 
file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such 
file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card 
'Audigy2'
ALSA lib conf.c:3493:(_snd_config_evaluate) function 
snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat 
returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM default
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, 
please install this library to use jack
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.ctl.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv 
returned error: No such file or directory
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such file or 
directory
ALSA lib control.c:817:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such 
file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,0
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 
'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer 
returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such 
file or directory
ALSA lib pcm.c:2099:(snd_pcm_open_noupdate) Unknown PCM hw:0,0

```

---

### Post by .t. on 2006-04-26
Yeah, I fixed all the ALSA problems by adding the missing definitions to my ~/.asoundrc[.asoundconf]. It all works now; woot!

---

### Post by dolson on 2006-04-27
That's weird. I had to delete that file on my system for JACK to work correctly (using Dapper, this is).

---

