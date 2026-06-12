---
title: "Headless X Server"
date: 2012-04-11
forum: Multimedia Software
---

### Post by Cadmus on 2012-04-11
Hello everybody

I have a small headless Ubuntu Server I'd like to use for making some videos from MAME. Now I've got Xvfb working properly giving me a virtual X screen, now I want sound too.

As I understand it you can get pulseaudio to provide sound with such a set up, but when I try to start pulseaudio I get this:

```
cadmus@server:~$ export DISPLAY=:1
cadmus@server:~$ Xvfb -screen 0 1027x768x16 &
[1] 6215
cadmus@server:~$ [dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
[dix] Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

cadmus@server:~$pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
cadmus@server:~$ pulseaudio -nC
E: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.Spawn.ExecFailed: //bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
cadmus@server:~$ 
```

Can anyone help me get this to go? I've dome some googling but it seems not many people want to run a full X server on a headless box, and yes I realise how silly that sounds.

---

### Post by Cadmus on 2012-04-19
If it's any help this is on 11.10.

---

### Post by Cadmus on 2012-05-10
A-ha, you can create a dummy soundcard by doing a modprobe snd-dummy. Now to see how this affects the output video.

---

