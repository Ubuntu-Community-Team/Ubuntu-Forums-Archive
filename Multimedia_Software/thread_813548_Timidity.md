---
title: "Timidity"
date: 2008-05-30
forum: Multimedia Software
---

### Post by kd5ob on 2008-05-30
root@roam:~# apt-get install timidity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  pmidi
The following NEW packages will be installed:
  timidity
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/545kB of archives.
After this operation, 1729kB of additional disk space will be used.
Selecting previously deselected package timidity.
(Reading database ... 208964 files and directories currently installed.)
Unpacking timidity (from .../timidity_2.13.2-19ubuntu1_i386.deb) ...
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                                   ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
                                                                         [fail]
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@roam:~# 


Enough said,

Charlie

---

### Post by spud.dups on 2008-07-25
Try this.

sudo gedit /etc/default/timidity

Line ten should say:

TIM_ALSASEQ=true

Comment this out with # and save the file.  The open another terminal window and do:

sudo apt-get update
sudo apt-get upgrade

If it works then there will be no error messages.  After that go back and uncomment TIM_ALSASEQ=true.  Do the update and upgrade again and you shouldn't get any error messages.  Let me know if this works for you.

---

### Post by ralphm on 2008-08-16
worked for me, at least... thanks!

---

