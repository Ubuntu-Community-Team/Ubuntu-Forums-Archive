---
title: "Log messages concerning audio"
date: 2019-05-26
forum: Multimedia Software
---

### Post by hans.ankarlid on 2019-05-26
Hi

I'm using Ubuntu 18.04 64bit on a Asrock G31M-VS2 Motherboard and a Intel Core 2 Quad CPU (Q6600). I'm using the rig as an audio playstation. I have a Soundblaster Audigy soundcard wich outputs the music to my home-stereo + subwofer and backspeakers. I have no issues with this, except i always get a message after boot or sometimes after a while, I include it below, it's not a big thing but it's annoying:

12:12:44 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
12:12:21 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
12:12:19 pulseaudio: [alsa-sink-emu10k1] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
12:11:36 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
12:11:36 colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1

Thanks in advance from the kingdom of Sweden!

---

### Post by TheFu on 2019-05-26
If it is working, then I wouldn't worry.
When posting logs, please use "code tags" so it is readable

bluez is a bluetooth thing. Best to remove bluetooth stuff if you don't use it. It is a security liability. I've been hacked over bluetooth on Ubuntu.

spice is a display protocol for virtual machines.  If you didn't go way, way, out of your normal effort to setup audio to work inside a virtual machine, I wouldn't expect it would work.  Probably best to remove any audio virtual hardware from being presented to the VM at all.

---

### Post by hans.ankarlid on 2019-05-26
OK, thanks for the fast reply... ;)

---

### Post by hans.ankarlid on 2019-05-26
Found a tip to get rid of these messages:
[https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)

---

