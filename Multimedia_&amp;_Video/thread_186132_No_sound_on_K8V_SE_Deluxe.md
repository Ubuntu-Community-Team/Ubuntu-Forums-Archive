---
title: "No sound on K8V SE Deluxe"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by JGKC9AYC on 2006-06-01
Just did a SUDO Apt-Get Dist-Upgrade & got a "No volume control GStreamer plugins and/or devices found."

Here's some things I typed in the terminal & the messages:

jerry@ubuntu:~$ cat /proc/asound/cards
--- no soundcards ---
jerry@ubuntu:~$ sudo gedit /etc/modprobe.d/alsa-base
Password:
- using device default
- using device default
ALSA lib confmisc.c:672: (snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072: (snd_func_refer) error evaluating name
ALSA lib conf.c:3493: (_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962: (snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102: (snd_pcm_open_noupdate) Unknown PCM default

(*Edited to put a space between the colon & the left parenthesis to keep from displaying a frowny face)

I had no problems with sound w/Breezy, btw.
Will this be an easy fix or should I delete the partitions & do a fresh install?

Can anyone help?
Thanks in advance!

---

### Post by screamz on 2006-06-01
I have the same situation

here is some debug information

[http://pastebin.com/752228](http://pastebin.com/752228)

Can anyone get me on track to solve this problem please

thank you

---

### Post by JGKC9AYC on 2006-06-01
Do you have the same motherboard or just the same error message?
Did you do an upgrade or a fresh install?
I'm wondering if that might've had something to do with it.

---

### Post by screamz on 2006-06-01
update from breezy -> dapper


guess it 's something with the nforce soundcard
asus a8n5x mobo

---

### Post by barney_1 on 2006-06-02
Not much help but I've got the K8V SE Deluxe and my sound works fine after the upgrade.

Good luck.

---

### Post by screamz on 2006-06-07
ok, got mine working by installing the latest kernel

actually the latest kernel was installed but due to a self inflicted issue in grub's menu.lst the latest kernel was'nt booted.

I m using standard 2.6.15-23 image now and everything runs supahsmooth

---

