---
title: "Sound not working in Breezy"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by balster neb on 2006-01-04
Hi, I have not been able to get any sound working in Breezy after installing it for the first time 2 days ago. Sound worked fine under Hoary and works fine with Windows XP.

My sound card is a Creative Sound Blaster/Ensoniq AudioPCI. From what I can tell, it is being detected properly. The card appears correctly in the Sound Preferences list and in the Volume Control program as Ensoniq AudioPCI (same as in Hoary).

I have also used alsamixer to ensure that all the channels are set to high and none are muted.

None of the apps give any errors when I play sounds, including Totem, Xine, XMMS and beep media player. Totem actually shows accurate looking visualisations, but no actual sound comes out of my speakers.

I have looked around on these forums a bit and tried some of the instructions, including the ones in [thread=44753]this thread[/thread], but it didn't help at all. :( 

As far as I can tell my sound module is snd_ens1371. Anyone else having similar problems?

---

### Post by balster neb on 2006-01-05
I tried a few more things but it hasn't helped. I am still not getting any sound. Here's the output of running [COLOR="DarkRed"]lsmod | grep snd[/COLOR]:

```

snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

```

I also happened to noticed that there's no PCM track present when I use alsamixer or the Volume Control app.

---

### Post by stratotak on 2006-01-05
have you tried to adjust sound with  gnome-aslamixer...maybe the pcm volume is all the way down

---

### Post by balster neb on 2006-01-05
Hi,
I just tried gnome-aslamixer but it doesn't help either -- there is no PCM slider at all. :( 

The only playback channels available in the Volume Control app, alsamixer and gnome-alsamixer are: Master Mono, Bass, Treble, Center, LFE, and PC Speaker.

---

### Post by stratotak on 2006-01-05
tried running  alsaconf from console..???maybe that will work out the kinks..

---

### Post by balster neb on 2006-01-05
I do not seem to have alsaconf installed, and can't find any alsaconf package in the Ubuntu repositories. I googled around a bit too, but couldn't find anything concrete.

Any idea where I can find it?

---

### Post by vrode on 2006-01-05
hi,

goto gnome-aslamixer->volume control->edit->preference->select 'front'.

this should fix it. atleast it did in my case.


good luck!

regards,
/virendra

---

### Post by mpvano on 2006-01-05
I've occasionally had the same sort of problem with various 1370/1371 and SB PCI cards. They seem to be misconfigured once in a while at the first startup after a version upgrade or new install. Perhaps some load time probing of subtle model variations is failing.

I don't know what's going on, and once the problem goes away (often after a few boot cycles), it seems to disappear for good.

When it happens, there always seem to be some controls missing from the mixers - even the alsamixer! Usually the missing control is the problem - once it shows up it can be set properly and everythings fine. Sometimes it's playback that fails, other times it's recording.

By the way, I'm having the same problem on Gentoo. It seems to have something to do with changes made in updates between recent alsa versions.

I'm guessing that wherever the alsa configuration is stored at shutdown is not compatible with later revisions due to fixes and renaming of some mixer element. 
I have fixed the problem twice now (once on Gentoo, and once on Breezy) by installing the oss mixer program called "aumix" and screwing around with the settings in aumix a few times and then rebooting. This is not a reliable way to fix it, however.

Once it goes away, everything's fine until some (but not all) later update to the alsa drivers....

I have no idea what's causing the problem at this point or how to fix it, but I thought I'd point out that you're not alone...

Mario

---

### Post by pakux on 2006-01-09
hi, in my case my gateway laptop didn't want to play sound even do everything seemed to be ok (soundcard recognized, alsa apparently working well, etc); after looking around and following every kind of suggestion in the forums for a couple of weeks some time ago i've almost resigned to have a mute friend. However, yesterday evening i've found this thread: 

[http://www.ubuntuforums.org/showthread.php?t=114032]("http://www.ubuntuforums.org/showthread.php?t=114032")

the matter was that #$%$ external amp setting: setting it to mute with ctrl-M (yeah mute, ironic eh?) sound works.

hope it helps.

---

### Post by axm on 2007-09-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137734](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/137734) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				`Since feisty, the automatic sound (driver/device?) recognition does not work anymore. Turned System->Prefs->Audio devices to ES1371 DAC1, did not bother to look further once I found one that worked.

Since I file a possible relation (or better: working proof) to Bug #137734: 

2.6.20-16-386

`modprobe snd_ens1371` returns nothing / no errors in /var/log/messages

---

