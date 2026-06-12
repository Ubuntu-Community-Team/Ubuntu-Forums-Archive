---
title: "How do I start pulseaudio with gdm turned off?"
date: 2010-12-03
forum: Multimedia Software
---

### Post by Effcook on 2010-12-03
Hi, I'm having trouble getting pulseaudio to start without gdm/X11.

Briefly, I have a Via C7VCM mini itx system running Ubuntu 9.04
32 bit desktop that I want to run as a timed audio recorder for
a public radio station.  The machine's limited in memory and
can't handle more recent installations of Ubuntu, 9.04's sufficient
for my needs.

I'm porting some old code that worked
under Red Hat 7.3.  I want the ability to run X11, but normally
gdm/X11 will be disabled.  The audio commands I need are aumix,
arecord and sox/play.

When I log in under X11, pulseaudio starts up and everything
works.   I disabled gdm and set PULSEAUDIO_SYSTEM_START=1 in
/etc/default/pulseaudio and rebooted.  play complains about
"cannot open audio device".  I also tried 
DISALLOW_MODULE_LOADING=0 in /etc/default/pulseaudio and also
/usr/bin/pulse-session when logging in, but still no go.

ps ax |grep pulse shows:
 2610 ?        S<sl   0:00 /usr/bin/pulseaudio --system --daemonize --high-priority --log-target=syslog --disallow-module-loading=0
 2996 ?        S<sl   0:00 /usr/bin/pulseaudio --start
 2997 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper

So pulseaudio is running.  Anyone know why this isn't working right?
Also, I would be happy to just run alsa without pulseaudio if that's
easy to do.

---

### Post by Effcook on 2010-12-06
This problem has been solved, I moved my system to Ubuntu 10.10
and reworked my code to use amixer instead of aumix and arecord
instead of ecasound.
Pulseaudio seems to be better behaved in the newer Ubuntu and it
starts up without an X session.

The target machine only had 256MB of RAM and that was insufficient
to install Ubuntu 10.10.  Installation started OK, but became extremely
slow and froze up at different points during different installation
attempts.

I installed 10.10 by moving the target's disk
to a similar machine with 1GB of RAM for the install, then back
to the 256MB machine.  Adding more RAM to the target machine would
probably be a better approach.

GDM and X11 was disabled by changing
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
in /etc/default/grub and running update-grub, this unloaded the
machine enough to run my application without running into swapping
problems.  The machine can still run X11 if needed.

---

