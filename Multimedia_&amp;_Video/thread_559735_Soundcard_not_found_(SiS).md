---
title: "Soundcard not found (SiS?)"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by ender42 on 2007-09-25
So Ubuntu has never found my soundcard.

Looking thru some webpages, these commands were to help diagnose stuff:

[i]user@machine: ~$ cat /proc/asound/cards
--- no soundcards ---

user@machine:~$ aplay -vv /usr/share/firefox/res/samples/test.wav
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:544: audio open error: No such device


user@machine: ~$ lsmod | grep snd
snd_pcm_oss            47652  0
snd_pcm                84872  1 snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
snd_mixer_oss          16768  1 snd_pcm_oss
snd                    50276  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  1 snd

user@machine: ~$ aplay --list-devices
aplay: device_list:221: no soundcards found...

user@machine: ~$ lspci -v
[snip out things other than sound stuff]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems: Unknown device 1b13
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=128]
        Capabilities: <available only to root>

user@machine: ~$ tail -2 /proc/asound/oss/sndstat

Mixers: NOT ENABLED IN CONFIG

user@machine: ~$ amixer
amixer: Mixer attach default error: No such device

user@machine: ~$ cat /etc/asound.conf ~/.asoundrc*
cat: /etc/asound.conf: No such file or directory
cat: /home/user/Home/.asoundrc*: No such file or directory[/i]


So, it looks like I've got an SiS soundcard, there's serveral different drivers associated with that company, but I don't know how to tell which one to use.  Should I just add them all, or try them in series?

Or, should I be doing something else?

---

### Post by reckless2k2 on 2007-09-25
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)


i used this doc then added each until i got the right one. hope this helps.

---

### Post by ender42 on 2008-01-20
I'm going to assume you mean that you added one, tried it (rebooting perhaps?), then removed it, then tried the next one.

---

