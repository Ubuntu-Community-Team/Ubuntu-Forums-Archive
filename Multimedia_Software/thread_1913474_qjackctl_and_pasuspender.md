---
title: "qjackctl and pasuspender"
date: 2012-01-22
forum: Multimedia Software
---

### Post by Roger E Critchlow Jr on 2012-01-22
The current version of qjackctl (0.3.8-1) on Oneiric 11.10 installs a script in /usr/bin/qjackctl which runs pasuspender before launching /usr/lib/qjackctl/ajackctl.real, which results in pulse audio suspending for the duration of the qjackctl session.

This is the correct thing to do when running jackd1, because jackd1 and pulseaudio don't get along.

But it is incorrect when running jackd2, because jackd2 and pulseaudio negotiate audio sharing over dbus.

I'm running jackd2, so this looks like a bug to me.

Any opinions or fixes?

-- rec --

---

### Post by Roger E Critchlow Jr on 2012-01-29
Bump.

Really would like some advice from someone who knows something about this.

Just now I've encountered another qjackctl queerness.  I tried to start jackd with the netone driver, and qjackctl attempted to set invalid parameters through the dbus interface.  Don't know where qjackctl is getting its parameters from, since the dbus interface will tell you what the valid parameters are, but qjackctl thinks it knows better so it tries to set the number of channels.

This also sounds like a bug to me, does anyone agree or disagree?

-- rec --

---

### Post by ter31 on 2012-05-17
The best option would be to send an email to jack or qjackctl mailing lists as they certainly know something.  As for pasuspender, a big thanks for bringing this up. Running pasuspender breaks suspend-resume, disabling it fixes the issue. Related links: (ubuntuforums.org/showthread.php?p=11944756) ubuntuforums post and ([https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/586209](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/586209)) bug on launchpad.

---

