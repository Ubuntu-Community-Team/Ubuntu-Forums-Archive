---
title: "remove alsa-driver install"
date: 2010-05-03
forum: Multimedia Software
---

### Post by Bacaryu on 2010-05-03
I don't know if I'm the right section of the forum, but since it all started with the microphone I post it here.

I did something stupid, In skype my microphone didn't work and it also didn't work with the recorder.

So what I did was searched a solution on google and i read something about install alsa-driver. So I downloaded it and tried to install it (took a very long time) and didn't installed (errormsg). When I looked a little further i saw my microphone was muted in the audio settings (DOH !)

but now everytime i do an apt-get i get this errormessage from alsa-driver that want to setup

> 
sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up alsa-driver-linuxant (1.0.20.3) ...
Building modules for the 2.6.32-21-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.24343.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)How can I remove this ?

---

### Post by rabideau on 2011-01-10
What I discovered is that if you use Synaptic to remove alsa-linuxant completely and then reinstall all your linux kernel modules, things go back to the before alsa-linuxant state.  That doesn't help your device, in my case speakers, but at least the errors go away.  Maybe a future kernel will fix things.

---

