---
title: "Pulseaudio issue on 14.04"
date: 2014-10-11
forum: Multimedia Software
---

### Post by PjRhI52Z on 2014-10-11
Recent update to Trusty (14.04).  Using nvidia video card with HDMI -> mutimedia receiver -> flat-screen 1080p TV 
Tried to run Rhythmbox this morning.  Sound not working, pulseaudio not running.

/var/log/syslog shows:
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] authkey.c: Failed to open cookie file '/home/rcs/.config/pulse/cookie': No such file or directory
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] authkey.c: Failed to load authorization key '/home/rcs/.config/pulse/cookie': No such file or directory
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] ltdl-bind-now.c: Failed to open module module-console-kit.so: module-console-kit.so: cannot open shared object file: No such file or directory
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] module.c: Failed to open module "module-console-kit".
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] main.c: Module load failed.
Oct 11 12:42:13 vader pulseaudio[4668]: [pulseaudio] main.c: Failed to initialize daemon.
Oct 11 12:42:13 vader pulseaudio[4665]: [pulseaudio] main.c: Daemon startup failed.

There is no cookie file.  Doing a simple 'touch' doesn't work, of course.
I have backups - but none of them have that file, either.
Tried doing a full delete/purge/reinstall of pulseaudio, then reboot - no joy.  Also tried deleting ~/.pulse - no good.

Alsa is running; my MythTV frontend plays with sound, just fine.

Dr. Google wasn't much help.  

Any ideas?
Thanks!

** Edit: that module really didn't exist.  Commenting it out in /etc/pulse/default.pa allowed it to start. Solved. **

---

