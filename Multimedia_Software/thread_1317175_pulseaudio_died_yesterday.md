---
title: "pulseaudio died yesterday"
date: 2009-11-06
forum: Multimedia Software
---

### Post by deankovell on 2009-11-06
Karmic. NVidia (realtek) alc1200.
Audacious just stopped playing in the middle of a song. I restarted the program and it wouldn't play anything. it would just show 00:00 on the display. I switched the output of audacious to alsa and it worked again.  since then I've rebooted a couple times. I have no volume control in the tray, and sound preferences won't open up. 


```
pulseaudio -D
E: main.c: Daemon startup failed.
pulseaudio -k
E: main.c: Failed to kill daemon: No such process
```Things I had done prior to this happening:
I edited /etc/modprobe.d/alsa-base.conf  to deal with the crackle/pop whenever I did anything with the computer.
-changed the last line to this.
 ```
options snd-hda-intel power_save=0 power_save_controller=N
```I also had changed the pulse output to stereo instead of 5.1 because it helped with this annoying tinny whine that was coming out through the speakers when music was playing.

What do I need to do to figure out what's going on here. I've been searching through the forums and haven't really found anything simmular to this. I'm also reluctant to go around making more changes without a little guidance. I don't want to mess things up worse, and make it impossible to figure out what the problem really is. I also don't want to uninstall, and reinstall, because I'll probably end up causing the problem again.

---

### Post by pcvii on 2009-11-19
i was updating to the new version of pulseaudio and now i'm having the same problem. it worked the first timie i booted with it now it doesn't. i even tried reinstalling the old version. but it didn't work. the new version stayed in place of the old one.

pulseaudio --version
pulseaudio 0.9.20
~$ pulseaudio -D
E: main.c: Daemon startup failed.
~$ pulseaudio -k
E: main.c: Failed to kill daemon: No such process

---

### Post by pcvii on 2009-11-19
Nov 19 00:25:17 robert-desktop pulseaudio[3274]: socket-server.c: bind(): Address already in use
Nov 19 00:25:17 robert-desktop pulseaudio[3274]: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
Nov 19 00:25:17 robert-desktop pulseaudio[3274]: main.c: Module load failed.
Nov 19 00:25:17 robert-desktop pulseaudio[3274]: main.c: Failed to initialize daemon.
Nov 19 00:25:17 robert-desktop pulseaudio[3272]: main.c: Daemon startup failed.

---

### Post by pcvii on 2009-11-19
my problem was after installing pulseaudio from source i had both .19 and .20 installed and they were conflicting.

I managed to uninstall pulseaudio* with apt-get and the .20 one was still there and everything was working.

i thought doing ./configure make and make install would just replace the old one. i guess it didn't. weird

---

