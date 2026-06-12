---
title: "IDJC -- Internet DJ Console"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by pulledteeth on 2007-08-14
Hi, I've been useing IDJC for a couple of days, and I LOVE it. I just have two issues.
 Issue Number one. I have aRts off, it's not running. I have JACK service enabled. I can STILL not use the idjcskype program. It just says the same thing over and over again. ```
ibryan@bryan:~$ idjcskype
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
engine sample rate: 44100
bryan@bryan:~$ ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:558:(snd_pcm_dsnoop_open) unable to open slave

```
That is the output. Some help would be Appreciated. 

The Other problem, is a minor one. When I use the "stop stream" programable application; it just locks up. 

Any help would be greatly appriciated :o thank you in advance.

I also run on ubuntu, under gnome normally. So if you can think of a way to run it under gnome, that would be helpfull too. As of right now though, i am fine with running it under Kubuntu..

---

### Post by deadgobby on 2007-08-14
have you  tried to change jacked from alsa to oss?
Gobby

---

### Post by pulledteeth on 2007-08-14
Nope, doesn't work. Thanks for the advice though :o. 

Any other help?

---

### Post by pulledteeth on 2007-08-14
bump

---

### Post by pulledteeth on 2007-08-14
bump for the win?

---

### Post by pulledteeth on 2007-08-14
bump for the win

---

### Post by deadgobby on 2007-08-15
OK have you installed the program using Ubie or did you install Ubuntu Studio? The reason why I ask this question is this. If you install on just the ubuntu kernel it will not work. You may and I say 
this it may break your system.  Is Ubuntu realtime kernel. The realtime kernel can be buggie and it is up to you.
Gobby

---

### Post by pulledteeth on 2007-08-15
Nah, I figured out what it was. This version of skype is different than that for which idjcskype was used for. So it no longer works. Hopefully it will at a later point though :o

---

### Post by Steveway on 2007-08-15
Yes, I filled a bugreport at Skypes Jira for better Jacksupport.
Everyone should vote for it.
[https://developer.skype.com/jira/browse/SCL-188](https://developer.skype.com/jira/browse/SCL-188)

---

### Post by pulledteeth on 2007-08-15
wait, how did you get it to run while jackserver is on? I just keep getting the same error :o?

---

### Post by Steveway on 2007-08-15
You may need to change the Device in Skypes settings, I have several listed there for my one inbuild soundcard.
Try it out with the different devices and be sure to have an actual release.

---

### Post by puneet on 2007-08-24
Try replacing libesd0 with libesd-alsa0.

----

From ALSA Wiki FAQ

If you get something similar

ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
snd_pcm_open: Device or resource busy (default)

and you believe that you have dmix plugin active (or you have a recent ALSA driver which activates is automatically) then it is possible that some program uses your /dev/dsp exclusively. The ALSA kernel level OSS emulation does not provide mixing in software.

Another reason might be an ALSA program using a hw device directly. One can override the default device to use dmix (which recent ALSA distributions do), but every program can still again override this default setup and use devices exclusively (one prominent example is jackd which does it on purpose). There's many more programs though that do this, due to programming errors and laziness of the authors coupled with moderately bad ALSA documentation).

**For example under Debian/GNU Linux it is possible that you have installed ESD for /dev/dsp instead of ALSA, replace libesd0 with libesd-alsa0.**

---

### Post by StephenF on 2007-08-24
The updated solution to running Skype with IDJC is here:
[www.onlymeok.nildram.co.uk/voip.html](www.onlymeok.nildram.co.uk/voip.html)

Version [0.7.0b]("http://www.onlymeok.nildram.co.uk/download/idjc-0.7.0b.tar.gz") fixes the regression in the playlist controls which was causing the lockup.

---

### Post by sunnshol on 2007-09-29
I have a different problem. Everything seems to work but every time I try to connect to the server, ten seconds or so later it disconnects with the nessage "Automatically disconnected from the server after connection timed out".

I won't post any config stuff right now unless anyone thinks it's relevant. I don't see anything in the Icecast logs. I tried connecting both to an Icecast server on the same machine and one on a Windows machine, same result. It connects - the web interface shows it does - but then loses it every time. Any suggestions?

---

