---
title: "Sound DG45ID HDMI Jaunty 9.04"
date: 2009-06-04
forum: Multimedia Software
---

### Post by kgatan on 2009-06-04
Hi Guys,

I have some problem with the sound on HDMI channel on my DG45ID board.

I have set all outputs in settings/sound to the HDMI output and when i press "Test" i get a signal on my TV but when i play a media file i still get only sound in head phones.

Have i missed some setting or is this same problem everyone else seems to have with HDMI sound?


Im running Ubuntu Jaunty 9.04 with alsa 1.0.20 drivers.

---

### Post by soniqfreq on 2009-08-05
Sound through HDMI definitely works on a DG45ID after a fresh install of Mythbuntu 9.04 and upgrading ALSA to v 1.0.20. (FINALLY!!)

This is how I did it:

1) Install of mythbuntu 9.04
2) Upgrade ALSA to 1.0.20 using Soundcheck's excellent upgrade script
     [http://ubuntuforums.org/showthread.php?p=6589810]("http://ubuntuforums.org/showthread.php?p=6589810")
3) Verify and test device with the command aplay -l
[INDENT]The HDMI device should be hw:0,3[/INDENT]
4) Configure mythtv settings for audio playback: Utilities/Setup>Setup>General>Audio [/INDENT]
[LIST][*]Audio output device>ALSA:plughw:0,3
[*]Configure passthrough settings as needed
[*] IMPORTANT: turn off (uncheck) Aggressive Sound card Buffering
[*] Mixer>ALSA:default
[*]Mixer controls>PCM
[/LIST]
5) configure additional media player commands if other media players are used within mythTV to playback audio or video {e.g. xine, mplayer, etc.}  
[LIST]
[*]For Xine, you need to add the output device [plughw:0,3] directly in the player preferences/settings.
[*]If you use mplayer, then the playback command in needs an option added (can't recall now since I use xine for most playback, a search will yield the correct option...maybe -ao plughw:0.3) 
[/LIST]

6) the last step is to TURN AUTOUPDATE OFF!!!!  Basically one update and it borked my sound back to the stone age.

I hope this give some hope to DG45ID owners out there.  I know I have been waiting for audio to work for quite sometime and basically wrote this board off a while ago.

---

