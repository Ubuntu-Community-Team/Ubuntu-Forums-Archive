---
title: "Another MPD question"
date: 2009-09-22
forum: Multimedia Software
---

### Post by pseudohybrid on 2009-09-22
So I installed MPD by:

```
sudo apt-get install mpd mpc gmpc
```I went to configure it:

```
sudo dpkg-reconfigure mpd
```And I get this error

```

 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             No "audio_output" defined in config file
Attempt to detect audio output device
Attempting to detect a alsa audio device
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 18590] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
Successfully detected a alsa audio device



```Any suggestions?

---

### Post by pseudohybrid on 2009-09-22
Ok so I messed with the mpd.conf file and now I get this error

```
 sudo dpkg-reconfigure mpd
 * Starting Music Player Daemon mpd                                             problem opening log file "/var/log/mpd/mpd.log" (config line 11) for writing
Aborted
                                                                         [fail]
invoke-rc.d: initscript mpd, action "start" failed.

```

---

