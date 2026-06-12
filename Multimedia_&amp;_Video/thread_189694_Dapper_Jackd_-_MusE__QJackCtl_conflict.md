---
title: "Dapper Jackd - MusE / QJackCtl conflict"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by bruder_s on 2006-06-05
Hi everyone,

yesterday, I managed to get some things running (rosegarden, qjackctl, qsynth), so I guess my system is configured somewhat ok.

(jackd is started by rosegarden)

Today I wanted to have a look at MusE. The installation via Synaptic (0.70...) gave just a segmentation fault so I installed 0.80.1 myself.

I haven't managed to get QJackCtl start Jack for me (see Edit), so I start it manually via command line and there's the problem:
If I start Jack with 'jackd -d alsa', MusE works fine (outputs a wave-track) but QJackCtl doesn't detect Jack.
When I start Jack with '/usr/bin/jackd -d alsa', QJackCtl detects Jack (active) but MusE gives me an error ('MusE failed to find a Jack audio server').

So it seems that at the moment I can run either QJackCtl or MusE, which is not what I want...
I'm relatively new to linux and confused - does someone know what to do now?

Edit:

I got QJackCtl to start jackd by changing the Server Path from 'jackd' to '/usr/bin/jackd' in the Setup, but still MusE only gets me the error above...

---

### Post by srv104 on 2006-07-07
Have you tried:
~$ sudo qjackctl
~$ sudo muse     

I compiled muse from source and it seems to be working fine. Initially it wasn't able see that the alsa midi sequencer was started, which it wasn't. So I ran:
~$ sudo modprobe snd-seq-oss
and then started qjackctl and muse.

---

### Post by kellogs on 2006-07-13
It seems that muse has got a bug and it cannot start if you dont use Root user. the only way by now is to start jack and muse as root, havent checked last muse version so I could be wrong.

Other programs (rosegarden, seq24) do not have this problem.

---

### Post by zettberlin on 2006-07-14
> **kellogs said:**
> It seems that muse has got a bug and it cannot start if you dont use Root user.

I doubt, this is a bug - there is a configure-option for muse, that builds/installs it setuid root - this option should not be used when building for dapper.

I have 0.8.1 build and working very good with the rest of dapper from the standardrepositories.

---

### Post by norv on 2006-07-20
I have problems running Muse and Rosegarden with Ubuntu Dapper.

My limited reading suggests that Muse need to be run suid root:
See Muse installation page - [http://www.muse-sequencer.org/wiki/index.php/Installation#Setuid-root]("http://www.muse-sequencer.org/wiki/index.php/Installation#Setuid-root")
Also Muse Security page -
[http://www.muse-sequencer.org/wiki/index.php/MusE_securty]("http://www.muse-sequencer.org/wiki/index.php/MusE_securty")

And there are ongoing problems with Rosegarden as in this page -
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34831]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34831")

I have got seq24 running very well with jack, Hydrogen, Ardour etc... but would be nice to get a Muse/Rosegarden DAW style sequencer app working too.

---

### Post by dolson on 2006-07-20
Just my personal opinion, and that is that if an app *requires* to be run as root, and it's something as simple as an audio app like all the others, then it should be avoided until this is changed. It really is not a good option. I am assuming that it was done for realtime privileges, which hasn't been required for quite some time, given that most distros and music users have the realtime-lsm module, or more modern distros have a PAM that supports it automatically.

---

