---
title: "Muthtv hangs on exit (futex_wait_queue_me)"
date: 2010-12-18
forum: Multimedia Software
---

### Post by avoa on 2010-12-18
Hi, 
I have used Ubuntu Lucid with Mythtv from Avenard repository. Everything works except Mythtv doesn't recognize lirc commands, however command **ircat mythtv ** shows correct commands. Then I upgraded Ubuntu to Maverick, and then Mythtv hangs on exit (system monitor shows status futex_wait_queue_me). Hangig happens, when exiting TV, video, recording and music. From menu Mythtv exits normally. 
I noticed, that Avenard repository doesn't support Maverick. Then I changed Mythtv repository to Mythtv 0.24 from [www.ubuntuupdates.org/ppa/mythtv_0.24](www.ubuntuupdates.org/ppa/mythtv_0.24), which supports Maverick. Result is the same, exiting Mythtv hangs with status futex_wait_queue_me. Can somebody help to fix this problem?

PS. I also tried to downgrade Mythtv to version 0.23, but as Mythtv database chema is changed, then Myhtv cannot start (error: mythtv database has newer TV schema). I couldn't find way to fix database schema.

Can somebody give any idea, where the problem can be? What kind of additional information is needed for problem solving?

Avo Aasma

---

### Post by avoa on 2010-12-18
Additional information to previous message.
I noticed, that Mythtv cannot play audio. Starting mythfrontend from terminal, I can see the following:

> 2010-12-18 10:55:03.481 Pulse: PulseAudio suspend OK
2010-12-18 10:55:03.519 AO: Opening audio device 'default' ch 2(2) sr 44100 sf signed 16 bit reenc 0
2010-12-18 10:55:03.523 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2010-12-18 10:55:03.562 ALSA, Error: no playback control PCM found on mixer device default
2010-12-18 10:55:03.562 ALSA, Error: Unable to open audio mixer. Volume control disabled
2010-12-18 10:55:03.692 ScreenSaverX11Private: DPMS Deactivated 1
[mp3 @ 0x61346a0] max_analyze_duration reached
[mp3 @ 0x61346a0] Estimating duration from bitrate, this may be inaccurate

May-be this is the reason for hang? How to fix this problem?

Avo Aasma

---

### Post by avoa on 2010-12-18
Solved.
From mythfrontend setup (General) in Audio system I selected Audio output device ALSA: pulse.
After that Mythtv starts to play audio and music. Now Mythtv can exit normally and everything works fine.

Previous value for Audio output was ALSA:default. I guess, it was set from previous version of Mythtv, where it works. With upgrade to Maverick Audio output device was changed. 

Avo Aasma

---

### Post by SniperKIng on 2010-12-20
Thanks alot. That fixed my problem, too.

---

### Post by thearchermdd on 2011-01-09
A note on downgrading: if you backup your database before you update, you can restore it if you need to downgrade. I recently updated to 0.24. When I restarted the backend, it updated the DB schema. I went through the backend log, I saw that it did a DB backup before upgrading the schema. So, you may have a backup laying around somewhere. I have no idea where it would be on your system, but my backups are in my video directory.

---

### Post by riptool on 2011-12-10
WOW, a month stressing over this same problem. Reinstalling, trying older versions, trying mythbuntu vs mythtv version....  Changing video drivers, back dating video drivers... blah blah blah.  

Changes to pulse sound and now openGL works flawlessly. 

ATI 4350HD, lastest drivers as of 12/10/11  version 11-11

---

