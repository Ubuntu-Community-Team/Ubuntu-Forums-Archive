---
title: "Flac files skipping in Ubuntu 9.04"
date: 2009-04-28
forum: Multimedia Software
---

### Post by walterp98@gmail.com on 2009-04-28
Hi all ... 
 
I just freshly installed XUbuntu 9.04  I'm using the Alsa drivers.  I'm using the Xfce 4.

Overall, the sound is working quite well (Santa Cruz Turtle Beach via CS46xx). Front and rear/sub produce sound with speaker-test.

My problem is that with several music players (rhythmbox, banshee, vlc, movie player, gmplayer, listen), I'm getting 'skipping' on flac files (like a scratched CD).  (Note: I'm NOT using pulseaudio).  

I don't believe the problem is in the flac files because they're fine in audacity and even under winAmp in windoze.

My cpu hovers around 10% when I'm playing music and have firefox, thunar, and xfce-term running with banshee at the same time.
 
I've included my alsa-info.txt

Thanks in advance for your help.  :smile:

Walter

(sorry ... I put the original thread in the wrong forum)

---

### Post by walterp98@gmail.com on 2009-04-30
I installed pulseaudio 1:0.9.14-0ubuntu20 via synaptic and it's running in the background after startup.  I'm still having the same sound issues.  Note that this happens with mp3 files as well, so it's not strictly a flac problem.

I'm trying to get some debugging information about errors that may be happening.  When I run 'vlc *' from one of my music directories, I get the following messages (though they don't appear at the same time as the 'skip')

```
[00000471] alsa audio output error: cannot write: Broken pipe
```

The only pulseaudio information I can find about pulseaudio in /var/log/syslog is

```
Apr 30 09:41:24 wperz-desktop pulseaudio[4338]: pid.c: Daemon already running.
Apr 30 09:41:24 wperz-desktop pulseaudio[4338]: main.c: pa_pid_file_create() failed.

```

What else can I do to try and fix this?

If anyone can provide help on this issue, I'd really appreciate it.

Walter

---

### Post by walterp98@gmail.com on 2009-04-30
I've found the verbose message setting in vlc ...

```
main info: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
alsa debug: recovered from buffer underrun
main debug: audio output is starving (269251), playing silence
alsa error: cannot write: Broken pipe
alsa debug: recovered from buffer underrun
main debug: audio output is starving (41375), playing silence
alsa debug: recovered from buffer underrun
main debug: audio output is starving (265939), playing silence
alsa debug: recovered from buffer underrun
main debug: audio output is starving (266328), playing silence
alsa debug: recovered from buffer underrun
main debug: audio output is starving (266036), playing silence
main debug: audio output is starving (20650), playing silence
alsa debug: recovered from buffer underrun
alsa debug: recovered from buffer underrunalsa debug: recovered from buffer underrun
main debug: audio output is starving (262249), playing silence
main debug: audio output is starving (20954), playing silence
alsa debug: recovered from buffer underrun
alsa error: cannot write: Broken pipe
alsa debug: recovered from buffer underrun
main debug: audio output is starving (41323), playing silence
main debug: audio output is starving (11611), playing silence
main debug: audio output is starving (11612), playing silence

main debug: audio output is starving (262448), playing silence

```That at least seems to be a starting point ...

I'm using an Athlon 2600+ with 512 mb of memory
My alsa-base is 1.0.18.dfsg-1ubuntu8 (listed as latest version in synaptic). 

WP

When I have pulseaudio running, I lose my rear speakers.

---

### Post by maks_zbogar on 2009-08-01
I found almost same problem while playing .wav files. I have new eMachines E525 notebook (2.2GHz Celeron, 2GB Ram, 250GB HDD) and Ubuntu 9.04 fresh installed. I bought this notebook to play wav files on stage, but I found out something is very wrong, because while playing .wav files from Rhythmbox, there are several random skips from time to time. The skips are not only scratched sounds, but exact skips with delays too. I have allready contacted eMachines support in order to find out if this is hardware or software issue, but there was no reply from them.

---

