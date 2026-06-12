---
title: "Sound problem on my Acer 3624 laptop"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by ajack on 2006-06-21
Hi all,

I have a problem with sound on my laptop.  I have an Acer 3624 and Dapper detected my soundcard as an Intel ICH-6/Realtek ALC655 sound card.

I can get sound from some applications, system sounds, etc.  However, for most games, I either get no sound or the menu sounds work but during gameplay it doesn't.  The symptom is usually the graphics hang (ie. stop moving) and the last sound in the sound buffer plays back repeatedly.  

The only option I have then is to hit CTRL-ALT-F1, log in and do a "ps aux" followed by the "kill" command to terminate the application.  When I started playing with Dapper in April, the sound was working correctly but about two weeks into final release, this problem crops up.

Is there somebody I can talk to about this problem?  I had opened a bug report at launchpad and have read the forums and all suggestions seem not to work for me.  ](*,) 

All I am looking for is for somebody in charge of the ALSA code for Ubuntu to acknowledge this problem and let me know that they are looking into it.  I can wait if I know the problem is being looked into.  :confused: 

Can anybody please help me... :(

---

### Post by ajack on 2006-06-27
Guess I am the only one with this problem... :confused:

---

### Post by LordRaiden on 2006-06-29
What games are you playing? since you have ICH6 you will probably need the hda-intel driver. do **lsmod | grep snd** in a shell and please paste the output here.

---

### Post by ajack on 2007-05-08
> **LordRaiden said:**
> What games are you playing? since you have ICH6 you will probably need the hda-intel driver. do **lsmod | grep snd** in a shell and please paste the output here.

Upgraded to 7.04, now my games have no sound at all.  I play all idsoftware games... anyway, I did the lsmod command on my 7.04:

snd_intel8x0           34204  2
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0
snd_mixer_oss          17408  3 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_$
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawm$
snd                    54020  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mi$
soundcore               8672  3 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm

---

