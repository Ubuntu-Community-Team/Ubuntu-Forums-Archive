---
title: "No Sound In Feisty"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by mootpoint on 2007-07-03
I'm running (x)ubuntu Feisty on a Dell C600 laptop. As far as I can tell, the drivers and whatnot are all loaded successfully. The mute is turned off, volume is maximum. No noise. :-(



root@lapdog:/# totem

(totem:5093): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (totem:5093): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (totem:5093): WARNING **: Error connecting to DBus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


root@lapdog:/# lsmod | grep snd
snd_maestro3           25220  1 
snd_ac97_codec         94112  1 snd_maestro3
ac97_bus                2432  1 snd_ac97_codec
snd_pcm_oss            43520  0 
snd_pcm                75656  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10248  1 snd_pcm
snd_mixer_oss          16768  1 snd_pcm_oss
snd_seq_dummy           3972  0 
snd_seq_oss            31360  0 
snd_seq_midi            8832  0 
snd_rawmidi            23808  1 snd_seq_midi
snd_seq_midi_event      7424  2 snd_seq_oss,snd_seq_midi
snd_seq                47984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21636  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  12 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7776  1 snd
root@lapdog:/# lspci | grep audio
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

Any suggestions appreciated!

m00tpoint

---

### Post by mootpoint on 2007-07-09
Any ideas out there?

---

### Post by stchman on 2007-07-09
The ESS is not in the HCL.  However somebody got their ESS soundcard working.

[http://ubuntuforums.org/showthread.php?t=284260](http://ubuntuforums.org/showthread.php?t=284260)

I hope this helps.

---

