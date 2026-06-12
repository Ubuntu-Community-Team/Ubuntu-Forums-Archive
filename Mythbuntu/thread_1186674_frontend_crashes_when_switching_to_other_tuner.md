---
title: "frontend crashes when switching to other tuner"
date: 2009-06-13
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-06-13
i have a main be/fe running mythbuntu hardy heron with mythtv: 0.21.0+fixes19961-0ubuntu8 with a PVR-350. I have a slave be/fe running mythbuntu hardy heron with mythtv: 0.21.0+fixes19961-0ubuntu8 with a PVR-500. WHen trying to switch between tuners in mythfrontend.real with the "y" button the frontend crashes each time. Doesn't matter if I am on the slave or the main frontends. Here are some log files for someone who can help me please.

---

### Post by nofear07 on 2009-06-13
I just ran into this issue myself.  What I think is causing it, is Gnome desktop.  If I install it, log out and log into gnome, and fire up the FE, then when I hit Y to change the tuner card it crashes.  If I do the same under Mythbuntu session it doesn't crash.

I'm not sure what exactly would be causing it yet, but that's my thoughts.

FYI I have a BE/FE and 2 other FE's and they all experience this.

Update, so after rebooting now mythbuntu session on the FE won't allow me to change tuners.

---

### Post by nofear07 on 2009-06-13
Last line in my frontendlog is
```
attempting to change from watchinglivetv to none
```

---

### Post by dannyboy79 on 2009-06-14
> **nofear07 said:**
> Last line in my frontendlog is
```
attempting to change from watchinglivetv to none
```

yeap, that's always my last line as well.

---

### Post by nofear07 on 2009-06-14
This is rather frustrating though.  I cant figure out for the life of me why it keeps crashing the FE now?  I had it a couple of times last night, and all that I changed was my default "UI" session from xfce to gnome, back to xfce.

---

### Post by nofear07 on 2009-06-14
here are the logs from the backend:
> 2009-06-14 11:18:23.519 TVRec(14): Changing from WatchingLiveTV to None
2009-06-14 11:18:24.593 Finished recording Unknown: channel 2404
2009-06-14 11:18:24.610 MythSocket(924b988:-1): writeStringList: Error, socket went unconnected.
2009-06-14 11:18:33.195 Expiring 3 MBytes for 2404 @ Sat Jun 13 19:06:48 2009 => Unknown
2009-06-14 11:18:33.199 Expiring 2 MBytes for 2404 @ Sun Jun 14 11:14:55 2009 => Unknown
2009-06-14 11:18:33.210 ProgramInfo, Error: GetPlaybackURL: '2404_20090613190648.mpg' should be local, but it can not be found.
2009-06-14 11:18:33.239 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend-1/2404_20090613190648.mpg. File doesn't exist.  Database metadata will not be removed.
2009-06-14 11:20:03.848 MainServer::HandleAnnounce Monitor
2009-06-14 11:20:03.855 adding: backend-1 as a client (events: 0)
2009-06-14 11:20:33.249 Expiring 3 MBytes for 2404 @ Sat Jun 13 19:06:48 2009 => Unknown
2009-06-14 11:20:33.251 Expiring 0 MBytes for 2404 @ Sun Jun 14 11:18:08 2009 => Unknown
2009-06-14 11:20:33.263 ProgramInfo, Error: GetPlaybackURL: '2404_20090613190648.mpg' should be local, but it can not be found.
2009-06-14 11:20:33.267 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/backend-1/2404_20090613190648.mpg. File doesn't exist.  Database metadata will not be removed.

and here are the logs from the frontend:
> 2009-06-14 11:18:13.991 Opening ALSA audio device 'spdif'.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
2009-06-14 11:18:14.245 NVP: Enabling Audio
2009-06-14 11:18:14.396 AO: dropping back audio_buffer_unused

---

### Post by dannyboy79 on 2009-06-15
can someone lease help me with this? I can't figure it out. I have now spent over 48 hours trying to figure this out! i had a nice stable mythtv running on feisty (main be/fe) and a slave running on gutsy using mythtv .20-2-fixes (or whatever it was before .21 came out) and now it's not working. I have attached my liked mythbuntu log file which got pasted to pastebin. thank you sooo much if you can walkme through what is wrong.

[http://mythbuntu.pastebin.com/f1b7a0241](http://mythbuntu.pastebin.com/f1b7a0241)

---

### Post by dannyboy79 on 2009-06-15
ok. i can be sitting at my master be/fe watching live tv. the tuner it's using is the second tuner on the PVR-500 from the slave be/fe. When I click on either "Y" or hit "M" and then chose the PVR-350 tuner, the frontend crashes? I have pasted a VERBOSE mythfrontend.real log below.
pleeeeeeeeeease help me......

[http://pastebin.com/meb6d0b8](http://pastebin.com/meb6d0b8)

---

### Post by ian dobson on 2009-06-15
Hi,

Maybe try increasing the size of your ringbuffer (Frontend setup I think) or enabling/disabling aggressive buffering.

It looks as if the frontend is timing out waiting for data from the new tuner (You log file has messages about bad frames).

I think here's an option in myth backend setup to configure the tuning delay under tuner configuration, maybe try increasing this abit to give the tuner abit more time to latch onto the frequency and produce a good data stream.

Also maybe try increasing the mpg buffers used by ivtv. Configuration in /etc/modprobe.d. Create a file called ivtv.conf in that directory and add the following:-

options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2

Hope this helps abit. Debugging problems like this is a real pain.

Regards
Ian Dobson

---

### Post by dannyboy79 on 2009-06-15
BUMP. please please someone try to help me with this. I have emailed the mythtv mailing list but I am trying to get help from all angles. It's so frustrating because I had a perfectly working setup before I tried to go to the latest Ubuntu and mythtv .21. I knew it was going to be difficult but I would have never thought it would work at all!

---

### Post by dannyboy79 on 2009-06-16
BUMP. all my info is here: [http://pastebin.com/m466d722e](http://pastebin.com/m466d722e)

---

### Post by ian dobson on 2009-06-17
Hi,

Have you read my post? Have you tried any of the things I've written?

Regards
Ian Dobson

---

### Post by dannyboy79 on 2009-06-19
> **ian dobson said:**
> Hi,

Maybe try increasing the size of your ringbuffer (Frontend setup I think) or enabling/disabling aggressive buffering.

It looks as if the frontend is timing out waiting for data from the new tuner (You log file has messages about bad frames).

I think here's an option in myth backend setup to configure the tuning delay under tuner configuration, maybe try increasing this abit to give the tuner abit more time to latch onto the frequency and produce a good data stream.

Also maybe try increasing the mpg buffers used by ivtv. Configuration in /etc/modprobe.d. Create a file called ivtv.conf in that directory and add the following:-

options ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2

Hope this helps abit. Debugging problems like this is a real pain.

Regards
Ian Dobson
yes. i tried it all. i basically gave up after spending 20 hours on the computer goggling and trying various things. I just did a fresh install and now all is well! I am using Hardy Heron now and I installed Mythtv seperately without using mythbuntu.

---

