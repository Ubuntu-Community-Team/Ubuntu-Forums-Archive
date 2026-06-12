---
title: "No sound from Ubuntu 10.04"
date: 2010-05-07
forum: Multimedia Software
---

### Post by joec2000 on 2010-05-07
Hi Everyone,

I did a search to see if this has been asked before and not much came up. My situation is a bit peculiar as well.

Here's my hardware setup:
(1) Desktop computer Intel DP35DP motherboard
(1) Server computer also with an Intel DP35DP motherboard (also doubles as an HTPC)

Both machines were recently upgraded to Ubuntu 10.04 Desktop.

The sound works perfectly on my desktop computer, but doesn't on the server. I tried launching the gnome-volume-control app and it just comes up saying "Waiting for sound system to respond..." and sits there indefinitely. Here's an example of what happens in mplayer when I try to play an MP3:

root@fileserver:/data/music# mplayer John\ Mellencamp\ -\ Check\ It\ Out.mp3 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing John Mellencamp - Check It Out.mp3.
Audio only file format detected.
Clip info:
 Title: Check It Out
 Artist: John Mellencamp
 Album: Words & Music: John Mellencamp
 Year: 2004
 Comment:                             
 Track: 7
 Genre: Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.3 (01.2) of 261.0 (04:21.0)  1.1% 


The part that perplexes me is that both computers have identical hardware (from a sound perspective), same BIOS and the same OS yet sound works on one machine and not the other.

In an effort to try to figure out what's going on, I set the log-level to 4 for pulseaudio and didn't really see a "smoking gun" in there. I can post the pulseaudio log (or something else) if that would be helpful.

Can someone give me some ideas on how I can debug this?

Thanks!

- Joe

---

### Post by Arturpc on 2010-05-11
Hi joec2000,

I'm with the same problem. I see in /var/log/user.log:

May 11 23:05:46 Speaker pulseaudio[1513]: ratelimit.c: 10 events suppressed

Will be a bug in ratelimit.c?

I resolved by remarking the lines in /etc/pulse/default.pa

### Automatically load driver modules for Bluetooth hardware
#.ifexists module-bluetooth-discover.so
#load-module module-bluetooth-discover
#.endif

I restarted the pulseaudio and it's running now!


Thanks,

Artur

---

### Post by wiggins32 on 2010-05-13
To fix this problem you need to remove the bluetooth modules of alsa drivers

sudo apt-get purge bluez-alsa

bye

---

