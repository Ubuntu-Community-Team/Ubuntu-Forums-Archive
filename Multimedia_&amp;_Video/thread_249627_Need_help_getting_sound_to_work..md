---
title: "Need help getting sound to work."
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by bchamberlain on 2006-09-02
I cannot get my sound to work.  My sound works when Ubuntu is starting (when the logon screen appears).  However, when I am in the desktop, nothing works.  I can't even start any applications that deal with sound because they cannot connect to my "sound server".

When I use lspci, I can see my sound card:
Intel Corporation 82801AA AC'97 Audio

However, aplay -l says no sound devices are loaded.  I tried using modprobe and getting the intel drivers (intel8x0 and intel8x0m) but that didn't work either (I typed in sudo modprobe snd-Intel8x0 and I still had no sound).  I am really new to Ubuntu and I am still learning.  I can't start alsamixer or gstreamer to mess with my sound settings so I know that the sound isn't muted or anything.  Please someone help.

---

### Post by ispmarin on 2006-09-02
Sometimes some application that starts together with ubuntu or you start blocks the /dev/dsp, the sink for sound. Try to issue

sudo fuser /dev/dsp

and sees which processes are using the /dev/dsp. Stop/kill there processes and try again. Usually, artsd stops my sound to work...

Hope it helps.

---

