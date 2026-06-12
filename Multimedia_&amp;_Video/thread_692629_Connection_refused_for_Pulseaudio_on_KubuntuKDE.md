---
title: "Connection refused for Pulseaudio on Kubuntu/KDE"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by jdogzilla on 2008-02-09
Hello, I am running Kubuntu Gutsy 7.10.  I just installed PulseAudio 0.9.6, and am not getting any sound.  Seems like the server is refusing connection.  Any help/advice in getting this to work will be appreciated. 

Some of my outputs are as follows:

% aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


% pulseaudio
E: authkey.c: failed to open cookie file '/home/XXX/.pulse-cookie': Permission denied
E: authkey.c: Failed to load authorization key '/home/XXX/.pulse-cookie': Permission denied
E: module.c: Failed to load  module "module-native-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: failed to initialize daemon.

% alsamixer
E: authkey.c: failed to open cookie file '/home/XXX/.pulse-cookie': Permission denied
E: authkey.c: Failed to load authorization key '/home/XXX/.pulse-cookie': Permission denied
*** PULSEAUDIO: Unable to connect: Connection refused

:confused:

---

### Post by jdogzilla on 2008-02-11
Any takers?  Any suggestions?

I did what I needed to do to get sound back - removed pulseaudio and reinstalled esound.  I'm all good for now, but still looking for a way to get pulseaudio to work with KDE 3.x

---

### Post by Giannis68 on 2008-02-11
Hi,
check the owner and group in folder /home/XXX/ 
and change permission for  .pulse-cookie
sudo chmod ...

---

### Post by jdogzilla on 2008-02-13
Tried that ... now I get the following errors

% pulseaudio
E: module-zeroconf-publish.c: avahi_entry_group_add_service_strlst(): Invalid service name

% alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused

alsamixer: function snd_ctl_open failed for default: Connection refused

Any further suggestions?

Thank you for your response though.  At least I moved one step ahead.

---

### Post by Giannis68 on 2008-02-14
your system have the latest updates???
these errors looks like bugs from older pulseaudio version..
[http://www.pulseaudio.org/ticket/39](http://www.pulseaudio.org/ticket/39)
[http://www.pulseaudio.org/ticket/133](http://www.pulseaudio.org/ticket/133)

---

### Post by prototype_angel on 2008-02-14
I'm currently trying to fix pulseaudio myself, but here's what I figured:

go to applications>sound and video>pulseaudio manager and click the "connect" button. For me the connection is being refused.

---

### Post by jdogzilla on 2008-02-14
OK ... I have it working now.  I went in and added some random avahi packages, just to make sure I wasn't missing anything.  I added gnome-audio, since that has a file that pulseaudio was looking for.  But I think what did the trick was to set the server from default to "localhost:4713".  All of a sudden, I had sound and it even works now after rebooting.  :guitar:

Thanks for your help in getting past each little hurdle.

---

