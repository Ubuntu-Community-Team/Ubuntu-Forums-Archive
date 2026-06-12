---
title: "can't see videos online"
date: 2021-08-19
forum: Multimedia Software
---

### Post by santofar on 2021-08-19
I can't play the majority of video clips on ubuntu 21.04. i downloaded software through the command window but i can't get that update installed. i will attach and screen shot. can anyone help me ? I did not open the iso of ubuntu on cd rom, but on a virtual disk. could it be because of that?


Thanks in advance.

---

### Post by Holger_Gehrke on 2021-08-19
You should remove the jonathonf PPA again since it only contains packages for the previous two LTS releases (16.04 and 18.04). This PPA is meant for users of older Ubuntu versions who want the same version of ffmpeg that is available from the standard repositories for users of the newer releases of Ubuntu. After doing that simply install ffmpeg from the standard repositories. Depending on what video player you use you might also want to look at the various packages of gstreamer plugins (gstreamer1.0-plugins-{base,good,bad,ugly}).

Holger

---

### Post by sydneya on 2021-09-23
Check if your adblocker is on. That could also be a problem.

---

### Post by TheFu on 2021-09-23
**VLC** should play any video worth seeing.
If you want a CLI program, **mpv** is quite excellent.
I've never been impressed by gstreamer.

---

### Post by monkeybrain20122 on 2021-09-23
> **sydneya said:**
> Check if your adblocker is on. That could also be a problem.

I always have ad blocker on and have no problem playing any video. Who would go online without an ad blocker?

---

### Post by monkeybrain20122 on 2021-09-23
> **santofar said:**
> I can't play the majority of video clips on ubuntu 21.04. i downloaded software through the command window but i can't get that update installed. i will attach and screen shot. can anyone help me ? I did not open the iso of ubuntu on cd rom, but on a virtual disk. could it be because of that?


Thanks in advance.


Did you install Ubuntu-restricted-extrass? It contains codecs you may need. And as Holger said you should remove the ffmpeg ppa.

---

### Post by monkeybrain20122 on 2021-09-23
> **TheFu said:**
> **VLC** should play any video worth seeing.
If you want a CLI program, **mpv** is quite excellent.
I've never been impressed by gstreamer.

I think OP is talking about video clips online. AFAIK vlc can only stream Youtube and not better than 720p. mpv+youtube-dl can do much better (and there are mpv browser addons) but that doesn't really address OP's problem. If he can't play online videos through his browser without addons or a local video player there is something wrong/missing in his set up.

---

