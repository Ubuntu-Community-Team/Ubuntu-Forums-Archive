---
title: "Can't get lirc_i2c to register in /dev"
date: 2010-02-03
forum: Multimedia Software
---

### Post by promig3 on 2010-02-03
I just upgraded a working Ubuntu 8.04/MythTV system to 9.10.  Everything went smoothy except I'm having a devil of a time getting my IR Remote to work.  It's funny, I've been running MythTV for at least 6 years now and it always seems like it is the remote that is the biggest hassle.

I've got the Hauppauge 350 card and am using the hauppauge remote.  I'm loading the lirc_dev and lirc_i2c drivers; I've tried both by hand (insmod) and with modprobe.

I see the drivers register with the Kernel, both via a syslog message and an entry in udev.  However I can't find any file in /dev that irrecord or lircd can read.

My first guess is that I'm missing a udev.rule entry for the lirc drivers.  I've tried adding a few with no luck, I think because I don't have the kernel module name right for the match part of the rule.  What I've tried was several things like:
KERNEL=="lirc[0-9]*" NAME=="lirc" 

A couple of other odd things 
- when the lirc_i2c drivers are loaded and I press a key on the remote I do get error messages in the log

- Regardless of the status of the lirc_* drivers, if I use the volume control or the power button on the remote, the GUI turns the volume up/down or goes to sleep.  This sort of makes me think that with 9.10 Ubuntu is grabbing the device or adding drivers I don't know about.

Any suggestions or thoughts would be much appreciated.

---

