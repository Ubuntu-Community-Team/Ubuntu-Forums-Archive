---
title: "I can get JACK to work.  Help, please!"
date: 2011-02-06
forum: Multimedia Software
---

### Post by Solomon Douglas on 2011-02-06
I'm using Ubuntu 10.10 on a Dell Inspiron 6400 (or Inspiron e1505).  I'm having an impossible time getting JACK to work.  In my attempt to follow the instructions given by the user cb951303 in [http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730), Here's what I've tried so far:

I've installed packages jackd and qjackctl.  I've added my user to the "audio" group.  I've added the following three lines to /etc/security/limits.conf:
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -19
```

I've logged out and in, and restarted the system, countless times.

I've configured the JACK settings as per [http://ubuntuforums.org/attachment.php?attachmentid=71520&d=1211718505](http://ubuntuforums.org/attachment.php?attachmentid=71520&d=1211718505) and [http://ubuntuforums.org/attachment.php?attachmentid=71521&d=1211718505](http://ubuntuforums.org/attachment.php?attachmentid=71521&d=1211718505) (as recommended in [http://ubuntuforums.org/showthread.php?t=806730](http://ubuntuforums.org/showthread.php?t=806730)).

I click on "Start", and I get the following error message:
```
Could not connect to JACK server as client.
- Overall operation failed.
- Server communication error.
Please check the messages window for more info."
```

The messages window is full of this:
```
JackAudioDriver::ProcessAsync: read error, skip cycle
alsa_driver_xrun_recovery
```

I've tried changing "Frames/Period" to every value in the drop-down list.

What should I try next?

---

### Post by cchhrriiss121212 on 2011-02-07
Xruns mean jack can start but your settings are not optimal. I used to have an Inspiron 6400 and I remember the onboard card did not work well with jack, but I never did find out why.
Could you post the complete message window output?
And also this from a terminal:
aplay -l

---

### Post by waperboy on 2011-02-07
"Could not connect to JACK server as client" indicates that jackd failed to start, the cause of which should also be in the log output, somewhere above that message.

---

