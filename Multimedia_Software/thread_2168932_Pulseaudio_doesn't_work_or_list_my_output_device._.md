---
title: "Pulseaudio doesn't work or list my output device. Ubuntu 12.04 LTS"
date: 2013-08-20
forum: Multimedia Software
---

### Post by mikesentenial on 2013-08-20
I am running Ubuntu 12.04 LTS. I recently tried replacing pulseaudio with alsa due to the issues being cause by PA during video playback. I used this guide: [http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/](http://linuxg.net/how-to-properly-replace-pulseaudio-with-alsa-on-crunchbag-linux-and-debian-squeeze/). That didn't work right, so I used this guide: [http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/](http://www.hecticgeek.com/2012/01/how-to-remove-pulseaudio-use-alsa-ubuntu-linux/).
Neither worked correctly, so I've re-installed PA along with pavucontrol, and I also re-installed alsa-base. I'm not getting any output at all. The test sound returns no results, and my output device isn't listed, although the control panels for sound settings are all there and seem to function. 
I think I may have either uninstalled PA incorrectly the first time around, or re-installed it incorrectly.
If someone could help me fix this issue, I would be very grateful. If I need to uninstall/re-install, telling me how to do so CORRECTLY would be great.


Thanks.

-Mike

---

### Post by Yellow Pasque on 2013-08-20
Let's start with: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mikesentenial on 2013-08-20
I uploaded the information. 
[http://www.alsa-project.org/db/?f=5f56e56998c13adebba7f108cb66ae5a084f2f4b](http://www.alsa-project.org/db/?f=5f56e56998c13adebba7f108cb66ae5a084f2f4b)

---

### Post by Yellow Pasque on 2013-08-20
ALSA info looks okay. Try resetting your user's pulse configuration:
```
rm -r ~/.pulse*; pulseaudio -k
```
Sound?

---

### Post by mikesentenial on 2013-08-20
```
michael@ubuntu:~$ rm -r ~/.pulse*; pulseaudio -k
E: [pulseaudio] main.c: Failed to kill daemon: No such process

```

---

### Post by Yellow Pasque on 2013-08-21
So pulseaudio didn't start. Hmm. Try getting a log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by mikesentenial on 2013-08-21
[COLOR=#333333][FONT=Ubuntu Beta]" ~/.pulse/client.conf " doesn't seem to exist, and what does it mean by "open your Launchpad bug"?[/FONT][/COLOR]

---

