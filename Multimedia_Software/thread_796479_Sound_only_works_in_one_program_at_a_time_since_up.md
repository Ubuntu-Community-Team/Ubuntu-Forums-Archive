---
title: "Sound only works in one program at a time since upgrade to 8.04"
date: 2008-05-16
forum: Multimedia Software
---

### Post by sicone on 2008-05-16
As the title says, since I upgraded to 8.04 last night, sound only works in the first program I open.

For example, if I open Kaffeine, I will not have any sound in Wine until I close Kaffeine.

If it's of any use Wincfg gives (whilst Kaffeine is running): 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib confmisc.c:768:(parse_card) cannot find card 'CMI8738MC6'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib confmisc.c:768:(parse_card) cannot find card 'CMI8738MC6'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```

---

### Post by Gunman1982 on 2008-05-16
check if the files .asoundrc and .asoundrc.asoundconf exist in your home directory
(open a console and type 'ls -a | grep asound') if yes try to rename them ('mv .asoundrc asoundrc_backup; mv .asoundrc.asoundconf asoundrc.asoundconf_backup') and try again

---

### Post by samathyr on 2008-05-17
I have the same problem...
This is a problem since you cannot listen to te aMSN alerts while listening music / surfing youtube  or doing something else...

and I don't have that file at home 

pd: I subscribed here :D :popcorn:

---

### Post by sicone on 2008-05-17
> **Gunman1982 said:**
> check if the files .asoundrc and .asoundrc.asoundconf exist in your home directory
(open a console and type 'ls -a | grep asound') if yes try to rename them ('mv .asoundrc asoundrc_backup; mv .asoundrc.asoundconf asoundrc.asoundconf_backup') and try again

Tried this and it tidied up the errors given by winecfg, but hasn't worked. Winecfg now only gives: ```
fixme:spoolsv:serv_main (0 (nil))
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave

```.

I did manage to find a suggestion to type 'killall pulseaudio' into the terminal which works until the next reboot. Is there any where I can write this command so it automatically does it when Hardy loads?

---

### Post by samathyr on 2008-05-17
Yes! That worked perfectly

What I did to keep it for following reboots is  System/Preferences/Sessions

And in Startup Programs add that "killall pulseaudio" command :D

Thanks!

---

### Post by crusti on 2008-10-03
Thank you for this fix! :o)

---

### Post by Yellow Pasque on 2008-10-04
Instead of killing PulseAudio every time your computer starts, uninstall pulseaudio through Synaptic.

---

