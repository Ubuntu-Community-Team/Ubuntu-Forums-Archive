---
title: "Can't Start JACK"
date: 2012-11-17
forum: Multimedia Software
---

### Post by doppel.ganger on 2012-11-17
Hello,
My desktop's old speaker just died, so I got the idea of using my laptop's speaker temporarily using JACK and QJackCtl. I opened it and went to connections to attempt to route my computer's audio from the mic input to the laptop speakers. However, no connections showed up. I haven't used Jack in a while, so I assumed I had to start JACK first. When I tried that, I got 2 error dialogs saying the JACK server failed to start. Here are the logs:
```
07:58:31.612 Patchbay deactivated.
07:58:31.660 Statistics reset.
07:58:31.774 ALSA connection change.
07:58:31.904 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
07:58:31.931 ALSA connection graph change.
07:58:43.813 D-BUS: JACK server could not be started. Sorry
Sat Nov 17 07:58:43 2012: Starting jack server...
Sat Nov 17 07:58:43 2012: JACK server starting in realtime mode with priority 10
Sat Nov 17 07:58:43 2012: [1m[31mERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[0m
Sat Nov 17 07:58:43 2012: control device hw:0
Sat Nov 17 07:58:43 2012: control device hw:0
Sat Nov 17 07:58:43 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Method "RequestRelease" with signature "i" on interface "org.freedesktop.ReserveDevice1" doesn't exist
[0m
Sat Nov 17 07:58:43 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired...[0m
Sat Nov 17 07:58:43 2012: [1m[31mERROR: Cannot initialize driver[0m
Sat Nov 17 07:58:43 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
Sat Nov 17 07:58:43 2012: [1m[31mERROR: Failed to open server[0m
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl.real:3418): Gtk-WARNING **: Theme directory status/16 of theme NITRUX-Clear-All has no size field
Sat Nov 17 07:58:45 2012: Saving settings to "/home/thomas/.config/jack/conf.xml" ...
07:58:53.316 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```
Does anyone know how I might get this working? Any help would be greatly appreciated!

Thanks,
Thomas

---

### Post by Kevin McCready on 2012-11-17
I'm still a newbie, but would purging and reinstalling help?
sudo apt-get purge jack
sudo apt-get update
sudo apt-get install jack

---

### Post by doppel.ganger on 2012-11-17
Nope, didn't help :(

---

### Post by doppel.ganger on 2012-11-20
*bump*

---

### Post by sandyd on 2012-11-20
Moved to multimedia and video

---

### Post by doppel.ganger on 2012-11-21
I think it might have something to do with the 5th line in the log, but i'm not totally sure.

---

