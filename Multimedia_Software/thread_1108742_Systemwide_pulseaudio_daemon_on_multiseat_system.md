---
title: "Systemwide pulseaudio daemon on multiseat system"
date: 2009-03-28
forum: Multimedia Software
---

### Post by guus123 on 2009-03-28
Hi everybody.

We (my wife and I) have a multiseat system and therefore chose to use a single pulseaudio daemon instead of one per logged in user. We are sitting next to each other, between the surround speakers and there's no point in having separate sound.

Starting the sound deamon at system startup is no problem. What I'm missing though is a good way to NOT start a separate pulseaudio during login. 

The first one of us that uses sound will grab the device so the other two daemons (systemwide and other user) are cut off. What I want is to avoid starting the user daemons and have the configuration point to the "Default" default server (Pulseaudio applet).

I'm quite sure I'm missing something obvious so I hope somebody can point it out to me.


TIA, Guus

---

### Post by barshociaj on 2009-04-30
I only need these to get what you are asking for:

/etc/pulse/daemon.conf:

daemonize = yes
system-instance = yes


/etc/default/pulseaudio:

PULSEAUDIO_SYSTEM_START=1

---

### Post by Despot on 2009-08-03
This probably won't affect the majority of users, but I found that to make this change, you must ensure that the users that need access to the sound system must be part of the "pulse" and "pulse-access" groups. Membership in these groups does not appear to be necessary when PulseAudio is run in per-user mode.

---

### Post by skliarie on 2009-08-05
Instead of creating ad-hoc solution for the audio on multiseat systems, the solution should be flexible enough so it can serve thin X-servers with audio cards as well.

X11 Audio [[X11 Audio Extension]("http://www.chaoticmind.net/~hcb/murx/xaudio/") appears to be fitting for a general solution for audio on multiseat systems.

---

### Post by skliarie on 2009-08-05
Hmm, looks like the X11 Audio is not welcome in ubuntu:
[http://brainstorm.ubuntu.com/idea/14814/](http://brainstorm.ubuntu.com/idea/14814/)

So, what solution does pulseaudio provides us?

---

### Post by jd' on 2010-05-25
I've set up something rather neat on several jaunty boxes :
[http://disjunkt.com/jd/2010/en/multiseat-linux/multiseat-linux-system-wide-pulseaudio-for-routing-sounds-109/](http://disjunkt.com/jd/2010/en/multiseat-linux/multiseat-linux-system-wide-pulseaudio-for-routing-sounds-109/)
one of them even routes the sound on different channels according to the seat used ...
no more fight for the sound !

---

