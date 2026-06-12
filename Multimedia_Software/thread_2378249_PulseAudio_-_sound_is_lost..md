---
title: "PulseAudio - sound is lost."
date: 2017-11-21
forum: Multimedia Software
---

### Post by smithbox on 2017-11-21
Hi all.
```
uname -a
Linux mike-desktop 4.8.0-59-generic #64-Ubuntu SMP Thu Jun 29 19:38:34 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```
```
dpkg -l | grep alsa
ii  alsa-base                                       1.0.25+dfsg-0ubuntu5                           all          ALSA driver configuration files
ii  alsa-oss                                        1.0.28-1ubuntu1                                amd64        ALSA wrapper for OSS applications
ii  alsa-tools                                      1.1.0-2                                        amd64        Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                  1.1.0-2                                        amd64        GUI based ALSA utilities for specific hardware
ii  alsa-utils                                      1.1.2-1ubuntu1                                 amd64        Utilities for configuring and using ALSA
ii  alsamixergui                                    0.9.0rc2-1-9.2                                 amd64        graphical soundcard mixer for ALSA soundcard driver
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-5                      amd64        ALSA sound mixer for GNOME
ii  gstreamer1.0-alsa:amd64                         1.8.3-1ubuntu1.1                               amd64        GStreamer plugin for ALSA
ii  libalsaplayer0                                  0.99.81-1ubuntu3                               amd64        alsaplayer plugin library
ii  volumeicon-alsa                                 0.4.6-2.2                                      amd64        systray volume icon for alsa
```
```

dpkg -l | grep pulse
ii  gstreamer1.0-pulseaudio:amd64                   1.8.3-1ubuntu1.3                               amd64        GStreamer plugin for PulseAudio
ii  libpulse-mainloop-glib0:amd64                   1:9.0-2ubuntu2.1                               amd64        PulseAudio client libraries (glib support)
ii  libpulse0:amd64                                 1:9.0-2ubuntu2.1                               amd64        PulseAudio client libraries
ii  libpulsedsp:amd64                               1:9.0-2ubuntu2.1                               amd64        PulseAudio OSS pre-load library
ii  pulseaudio                                      1:9.0-2ubuntu2.1                               amd64        PulseAudio sound server
ii  pulseaudio-utils                                1:9.0-2ubuntu2.1                               amd64        Command line tools for the PulseAudio sound server
```

```
systemctl status pulseaudio.service
&#9679; pulseaudio.service - PulseAudio system server
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)

Nov 21 14:48:16 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:16 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:19 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:19 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 16:27:13 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 16:27:13 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
lines 1-14/14 (END)...skipping...
&#9679; pulseaudio.service - PulseAudio system server
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)

Nov 21 14:48:16 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:16 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:19 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:19 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
Nov 21 16:27:13 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service
Nov 21 16:27:13 mike-desktop systemd[1]: pulseaudio.service: Service lacks both 
~
~
~
~
~
~
~
~
~
~
lines 1-14/14 (END)...skipping...
&#9679; pulseaudio.service - PulseAudio system server
   Loaded: error (Reason: Invalid argument)
   Active: inactive (dead)

Nov 21 14:48:16 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service:7] Executable path is not absolute, ignoring: pulseaudio --daemonize=no --system --realtime --log-target=journal
Nov 21 14:48:16 mike-desktop systemd[1]: pulseaudio.service: Service lacks both ExecStart= and ExecStop= setting. Refusing.
Nov 21 14:48:19 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service:7] Executable path is not absolute, ignoring: pulseaudio --daemonize=no --system --realtime --log-target=journal
Nov 21 14:48:19 mike-desktop systemd[1]: pulseaudio.service: Service lacks both ExecStart= and ExecStop= setting. Refusing.
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service:7] Executable path is not absolute, ignoring: pulseaudio --daemonize=no --system --realtime --log-target=journal
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both ExecStart= and ExecStop= setting. Refusing.
Nov 21 14:48:38 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service:7] Executable path is not absolute, ignoring: pulseaudio --daemonize=no --system --realtime --log-target=journal
Nov 21 14:48:38 mike-desktop systemd[1]: pulseaudio.service: Service lacks both ExecStart= and ExecStop= setting. Refusing.
Nov 21 16:27:13 mike-desktop systemd[1]: [/etc/systemd/system/pulseaudio.service:7] Executable path is not absolute, ignoring: pulseaudio --daemonize=no --system --realtime --log-target=journal
Nov 21 16:27:13 mike-desktop systemd[1]: pulseaudio.service: Service lacks both ExecStart= and ExecStop= setting. Refusing.
```
When I print PulseAudi icon, response is [https://imgur.com/a/a9FWj](https://imgur.com/a/a9FWj)
Whats wrong with my PulseAudio?

Regards.

---

### Post by Yellow Pasque on 2017-11-21
Since you hace pulseaudio 9.x, you're running Ubuntu 16.10, correct? (Before anyone else tells you it's EOL/unsupported/insecure, I'll do it.)

Can you copy/paste the /etc/systemd/system/pulseaudio.service file?

---

### Post by smithbox on 2017-11-22
```
[Unit]
Description=PulseAudio system server

[Service]
Type=notify
ExecStart=pulseaudio --daemonize=no --system --realtime --log-target=journal

[Install]
WantedBy=multi-user.target


```

IYO - if PA is unsecure, what to use instead ?

---

### Post by slickymaster on 2017-11-22
*Thread moved to **Multimedia Software**.*

---

### Post by Yellow Pasque on 2017-11-22
Based on the error message, I would try changing:
```
ExecStart=pulseaudio --daemonize=no --system --realtime --log-target=journal
```
to:
```
ExecStart=/usr/bin/pulseaudio --daemonize=no --system --realtime --log-target=journal
```

But I question where you got the file and whether you understand what you're doing by running pulseaudio in system wide mode instead of as a per user daemon.

From the manual:
```
--system[=BOOL]
              Run as system-wide instance instead  of  per-user.  Please  note
              that  this  disables  certain  features  of  PulseAudio  and  is
              generally not recommended unless the system knows no local users
              (e.g.   is   a   thin   client).   This  feature  needs  special
              configuration and a dedicated UNIX user set  up.  It  is  highly
              recommended  to combine this with --disallow-module-loading (see
              below).
```

> **smithbox said:**
> IYO - if PA is unsecure, what to use instead ?
I didn't say PA was insecure. I said your entire distro version (Ubuntu version 16.10) is EOL and no longer receives updates, making it theoretically insecure.
[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by smithbox on 2017-11-22
I have done change, without any positive results, run pulseaudio as a per user daemon.
Think, ALSA reinstall is the only option.

Update ALSA driver solved my problem. [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html)
Regards.
Mark.

[CENTER][COLOR=#FFFFFF][FONT=Lucida Sans]**Update ALSA driver for Ubuntu for Intel HDA**[/FONT]
[FONT=Arial][/FONT][/COLOR][/CENTER]
 [COLOR=#FFFFFF][FONT=Arial] [/FONT][/COLOR]
[CENTER][COLOR=#FFFFFF][FONT=Lucida Sans]**Update ALSA driver for Ubuntu for Intel HDA**[/FONT]
[FONT=Arial][/FONT][/COLOR][/CENTER]
 [COLOR=#FFFFFF][FONT=Arial] [/FONT][/COLOR][CENTER][COLOR=#FFFFFF][FONT=Lucida Sans]**Update ALSA driver for Ubuntu for Intel HDA**[/FONT]
[FONT=Arial][/FONT][/COLOR][/CENTER]
 [COLOR=#FFFFFF][FONT=Arial] [/FONT][/COLOR]
[CENTER][COLOR=#FFFFFF][FONT=Lucida Sans]**Update ALSA driver for Ubuntu for Intel HDA**[/FONT]
[FONT=Arial][/FONT][/COLOR][/CENTER]
 [COLOR=#FFFFFF][FONT=Arial] [/FONT][/COLOR]

---

