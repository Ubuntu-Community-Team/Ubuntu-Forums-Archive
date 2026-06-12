---
title: "Error installing Timidity"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Blastomorpha on 2008-04-28
I can't install Timidity on my fresh upgraded Hardy (neither in Gutsy),
I get these errors (I'm italian):
```
Configuro freepats (20060219-1) ...
Configuro timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
   ...fail!
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: errore processando timidity (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
Installazione di un pacchetto fallita. Tentativo di ripristino:
Configuro timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
   ...fail!
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: errore processando timidity (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
```

My sound card is a Creative Extigy (via USB) and it can play sounds, mp3 and so on...
Any ideas? :confused:

---

### Post by Blastomorpha on 2008-04-29
After reading [this similar topic]("http://ubuntuforums.org/showthread.php?t=704722&highlight=timidity"), I tried to install timidity from terminal (using sudo instead of the root account, like the linked thread) and it worked!
Actually timidity worked even if I got errors using Synaptic...
So problem seems to be solved.

---

