---
title: "MuSE crashing on dapper"
date: 2006-05-24
forum: Multimedia &amp; Video
---

### Post by stbub on 2006-05-24
Anyone has MuSE working on dapper?

It crashes at my end.

---

### Post by dolson on 2006-05-24
Well, I don't run MuSE, but you might want to open a bug in Launchpad/Malone. But with less than a week away from Dapper's release, I doubt we'll see it fixed in time.

---

### Post by ReddoC on 2006-06-04
The only way i can start it is :

# sudo jackd -d alsa
# sudo muse 


i can't run it as my user here is the error message:


No superuser privileges, using system timer fallback
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
NO Config File </home/vb/.MusE> found
Trying RTC timer...
fatal error: open /dev/rtc failed: Périphérique ou ressource occupé
Trying ALSA timer...
got timer = 12
QObject::connect: No such signal PartCanvas::horizontalScroll(int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
Arranger::configChanged - no bitmap!
open projectfile: Aucun fichier ou répertoire de ce type
starting with default template
  name2route: <alsa_pcm:playback_1> not found
  name2route: <alsa_pcm:playback_2> not found
Arranger::configChanged - no bitmap!
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 1000)
  freq stays at 1000 Hz
Erreur de segmentation

---

### Post by bruder_s on 2006-06-05
I just got 'segmentation fault' error. Now using version 0.8.1 and it works (but got problems with QJackCtl)...

---

### Post by floogy on 2006-08-19
Where can I find the new version in ubuntu? 
Is there no switch in the MuSe configuration to increase the frequence?
Or is there a way to fix this by ulimit, or adding (dev/rtc to the audio group, or whatever?

[https://launchpad.net/distros/ubuntu/+source/muse/+bug/41780](https://launchpad.net/distros/ubuntu/+source/muse/+bug/41780)

Edit:
Hmmm.. rtc is already in audio: ```
$ ls -l /dev/rtc
crw-rw---- 1 root audio 10, 135 Aug 19 18:16 /dev/rtc
```
```
$ muse
No superuser privileges, using system timer fallback
Trying RTC timer...
RtcTimer::setTimerFreq(): cannot set tick on /dev/rtc: Permission denied
  precise timer not available

```
```
AlsaTimer::setTimerTicks(): requested freq 1024 Hz too high for timer (max is 1000)
  freq stays at 1000 Hz
Segmentation fault
```

$ groups
[...] audio [...] ???? it's read-/writable by members of group audio, isn't it??

Edit:

sudo dpkg-reconfigure muse:
```
 &#9474; For good timing, MusE needs to set the real time clock (/dev/rtc) to a    &#9474;
 &#9474; higher clock rate, and raise its scheduling priority. Usually, only the   &#9474;
 &#9474; root user is allowed to do this. MusE can be installed "suid-root", so    &#9474;
 &#9474; that it always runs with superuser capabilities. In such a setup,         &#9474;
 &#9474; ordinary users can tweak the clock rate as well. However, this is a bad   &#9474;
 &#9474; idea in general because large applications like MusE most definitely      &#9474;
 &#9474; contain security holes that a local user might exploit to gain access to  &#9474;
 &#9474; the root account.                                                         &#9474;
 &#9474;                                                                           &#9474;
 &#9474; If you intend to use MusE for timing-sensitive recordings, make sure you  &#9474;
 &#9474; setup a computer with only a few trusted local users, preferably no       &#9474;
 &#9474; network connection, and give an affirmative answer to this question.      &#9474;
 &#9474; Deny if unsure.  
```

If this is such a security risk, did you guys disabled your internet connection?

Is there a backport of the edgy version for dapper?

Edit:

The setuid workaround doesn't work if qtjackctl is running by a member of the audio group:
qjackctl:
> 19:29:23.566 Audio active patchbay scan...
19:29:55.610 Audio connection change.
cannot connect ports owned by inactive clients; "MusE-1" is not active
cannot connect ports owned by inactive clients; "MusE-1" is not active
19:29:55.767 Audio active patchbay scan...

muse:
```
got timer = 14
QObject::connect: No such signal PartCanvas::horizontalScroll(int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
Arranger::configChanged - no bitmap!
starting with default template
Arranger::configChanged - no bitmap!
JACK ERROR: jack_client_create_thread: error 11 creating realtime thread: Resource temporarily unavailable
JACK: cannot activate client
*** glibc detected *** WatchDog: fatal error, realtime task timeout
   (3074,0-3) - stopping all services
watchdog exit
```
muse hangs... have to kil it with killall muse.

This is on dapper amd64.

---

### Post by zettberlin on 2006-08-19
Well, i muse 8.1 it running just fine on my dapper, but alas!! i forgot how I actually made it :-|
it is for sure something with the timer, i have manipulated one of the files to build muse with a default-timing, that is OK with dapper (yet might not be OK at all for those, who need exact timing...)

Anyway, you might want to try one of my working projectfiles:

[http://www.gnupc.de/~zettberlin/law/muse-working/muse-0.8.1](http://www.gnupc.de/~zettberlin/law/muse-working/muse-0.8.1)

good luck!
Z

---

