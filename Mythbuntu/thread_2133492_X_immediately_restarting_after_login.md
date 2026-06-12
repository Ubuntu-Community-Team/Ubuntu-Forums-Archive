---
title: "X immediately restarting after login"
date: 2013-04-08
forum: Mythbuntu
---

### Post by brg7 on 2013-04-08
I'm having a very frustrating time trying to troubleshoot this, but when my combined front/backend machine boots, it won't autologin (or rather, it tries, but... well you'll see).  The first thing I see is the login prompt.  When I try to log in, X immediately begins a restart sequence.  I think this is why it looks like autologin is failing; it succeeds, but since X immediately restarts, it doesn't try again. As soon as the login succeeds, I see [...] evdev: Power Button: Close [...], in Xorg.0.log, followed by X restarting.  I've looked in every log I can find that was touched on the same day as my issues, and the only thing I've been able to find is that the lightdm log shows that the mythbuntu session script starts to run, then shows that the process ID assigned to the script thread returned a value of 1, then the restart begins.  I've looked in all the var/log/mythtv/* logs ( as well as kern.log, syslog, dmesg, etc. for any sign of what might have caused it, but can't see what's going on.  I'm pretty sure something is segfaulting, but I've no idea what.  I've tried rolling back to an earlier kernel version (I just did an apt-get upgrade), and rolling back some recent hardware changes, but that doesn't help.  Anyone have any ideas how to make progress on troubleshooting?

---

### Post by tgalati4 on 2013-04-08
What type of graphics card?  It's possible that your graphics card is failing when switching graphics mode.  Hardware failures are not captured well in linux.  It expects perfect hardware.  So strange behavior like this looks like a software issue, but could be a hardware issue.  The fact that you can't find anything in the log files points to a hardware issue.  Try another graphics card or switch to smaller resolution to see if it boots correctly.

---

### Post by brg7 on 2013-04-08
Funny you should ask - I swapped out a 9500 GT for a GT610 right before this happened, but I suspected that the graphics card could be a problem, so I swapped it back, and still got the same results.  One question though - I think the NVidia driver was updated as part of the dist upgrade.  How do I roll back to a previous version to see if that might be the issue?  EDIT: never mind - found how to do a package downgrade. I'll try that and see if it works.

---

### Post by brg7 on 2013-04-09
OK, more detail from the lightdm log, with the section I think is most interesting in bold.  Any way to know whether this is a significant symptom, or just something else?  From the lack of a client connection in the mythbackend log, it looks like the mythfrontend never starts:> [+1.25s] DEBUG: Autologin using session mythbuntu
[+1.26s] DEBUG: Dropping privileges to uid 1000
[+1.26s] DEBUG: Restoring privileges
[+1.27s] DEBUG: Dropping privileges to uid 1000
[+1.27s] DEBUG: Writing /home/xxxxxxxx/.dmrc
[+1.31s] DEBUG: Restoring privileges
[+1.37s] DEBUG: Starting session mythbuntu as user xxxxxxxx
[B][+1.37s] DEBUG: Session 1659 running command /usr/sbin/lightdm-session /usr/share/mythbuntu/session.sh
[+1.42s] DEBUG: New display ready, switching to it
[+1.42s] DEBUG: Activating VT 7
[+1.42s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+1.42s] DEBUG: Session 1659 exited with return value 1[/B]
[+1.42s] DEBUG: User session quit
[+1.42s] DEBUG: Stopping display
[+1.42s] DEBUG: Sending signal 15 to process 1502
[+1.71s] DEBUG: Process 1502 exited with return value 0
[+1.71s] DEBUG: X server stopped
[+1.71s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+1.71s] DEBUG: Releasing VT 7
[+1.71s] DEBUG: Display server stopped
[+1.71s] DEBUG: Display stopped
[+1.71s] DEBUG: Active display stopped, switching to greeter
[+1.71s] DEBUG: Switching to greeter
[+1.71s] DEBUG: Starting new display for greeter
[+1.71s] DEBUG: Starting local X display
[+1.71s] DEBUG: Using VT 7
[+1.71s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+1.71s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+1.71s] DEBUG: Launching X Server
[+1.71s] DEBUG: Launching process 1770: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+1.71s] DEBUG: Waiting for ready signal from X server :0
[+2.32s] DEBUG: Got signal 10 from process 1770
[+2.32s] DEBUG: Got signal from X server :0
[+2.32s] DEBUG: Connecting to XServer :0
[+2.32s] DEBUG: Starting greeter
[+2.32s] DEBUG: Started session 1789 with service 'lightdm', username 'lightdm'
[+2.34s] DEBUG: Session 1789 authentication complete with return value 0: Success
[+2.34s] DEBUG: Greeter authorized
[+2.34s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+2.34s] DEBUG: Session 1789 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
[+2.48s] DEBUG: Greeter connected version=1.2.3
[+2.48s] DEBUG: Greeter connected, display is ready
[+2.48s] DEBUG: New display ready, switching to it
[+2.48s] DEBUG: Activating VT 7
[+2.48s] DEBUG: Stopping greeter display being switched from
[+3.16s] DEBUG: Greeter start authentication for xxxxxxxx


---

