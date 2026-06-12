---
title: "pulseaudio causes mozilla, thunderbird to freeze."
date: 2009-11-05
forum: Multimedia Software
---

### Post by TrevorBradley on 2009-11-05
I've upgraded from Jaunty to Karmic earlier this week, and having a nasty time with it.

Pulseaudio seems to be a big source of my problems.  I've noticed that when Thunderbird attempts to play a new mail sound at the same time mozilla is playing a flash video, one or the other or both will hang.  If I run "pkill pulse", all is well again.

I *think* the error I'm getting in user.log is:

Nov  5 08:58:28 pergamon pulseaudio[2569]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy

.. but I haven't explicitly checked it yet.

I've also had mythbuntu issues directly related to pulseaudio that were solved by uninstalling pulseaudio.  However I'm worried about removing the ubuntu-desktop package and what that might do to my backend Karmic ubuntu server.

Pulseaudio has been the source of about 50% of my headaches for the household karmic upgrade.

Are there any hints for diagnosing a pulseaudio freeze?  I'd rather try to solve this than simply delete pulseaudio and have a slightly broken system.

---

### Post by iamnotthemessiah on 2009-11-05
ditto
cant help unforunately :(

edit: mine was a clean install with clean firefox profile and the 64bit alpha flash

---

### Post by TrevorBradley on 2009-11-07
Well, I'm giving up... removing pulseaudio on my server.  It may screw up future updates but not having to open up a terminal and type "pkill pulse" twice a day will give me a bit of peace.

EDIT: Well, if I attempt to play two audio sources at once, one is muted.  Better than having one or both applications hang.

---

### Post by stoepvats on 2009-11-07
I also had quite a lot of trouble using pulseaudio, especially when I was recording sound. I also had stuttering playback of sound, which I fixed by just removing pulseaudio and instelling esound, and rebooting:
```
sudo apt-get purge pulseaudio
sudo apt-get install esound

```However, this seemed to kill all my recording capabilities, but playback sounded quite ok. Now I just use an usb sound system I had laying around and that seems to work fine in pulseaudio.

BTW: removing pulseaudio didn't remove ubuntu-desktop for me, so it could easily turn it around when it didn't work

---

