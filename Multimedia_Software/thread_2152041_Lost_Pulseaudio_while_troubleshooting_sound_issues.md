---
title: "Lost Pulseaudio while troubleshooting sound issues in spotify"
date: 2013-06-06
forum: Multimedia Software
---

### Post by marinecomm on 2013-06-06
I was troubleshooting my sound issues with spotify when all of a sudden the pulseaudio button disappeared. When I go to Applications Menu -> Multimedia -> Pulseaudio Volume Control I get the following error message:

Fatal Error: Unable to connect to Pulseaudio: OK

I have verified that pulseaudio is installed but is not running. How do I get pulseaudio up and running again?

---

### Post by ajgreeny on 2013-06-06
From alt+F2 run command **start-pulseaudio-x11** to start pulse again, and check in your **Settings-manager -> Session and Startup** that you have that included.

---

### Post by marinecomm on 2013-06-06
Checked **Settings-manager -> Session and Startup** and Pulseaudio is included

When I issued the command **start-pulseaudio-x11** I got the following error message:

Connection failure: Connection refused
pa_context_connect() failed: Connection refused

---

### Post by Yellow Pasque on 2013-06-06
So you've tried logging out and back in (or rebooting) after running that command I gave you in the other thread?

> I was troubleshooting my sound issues with spotify 
Please elaborate. What exactly did you do?

Please get alsa info to make sure everything's working at the driver level: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Verbose pulseaudio log may be helpful too: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by marinecomm on 2013-06-06
Rebooted and still the same. Have tried installing and reinstalling Pulseaudio to no effect. Here is the results of the alsa log.

[http://www.alsa-project.org/db/?f=a2da5d45f1bf4e054bc7bd766bf72cedaab4fa64]("http://www.alsa-project.org/db/?f=a2da5d45f1bf4e054bc7bd766bf72cedaab4fa64")

I currently unistalled Pulseaudio and am attempting to use ALSA but I'm still not getting any sound except with the headphones.

---

### Post by Yellow Pasque on 2013-06-06
You still haven't told us what you did that caused the sound loss in the first place. It's difficult to help someone undo domething if they haven't told you what they've done.

---

### Post by marinecomm on 2013-06-07
I understand but that's part of the problem. I was making so many changes at one time I don't know what I did that triggered it. Is there any way I can uninstall/reinstall both of them and start over without doing a fresh install of Xubuntu? Both os them meaning Pulseaudio and ALSA.

---

### Post by ajgreeny on 2013-06-07
Perhaps remove (or rename) the hidden **~/.pulse** folder in your home; it may be as simple as some configuration change you've made that needs removing.

---

### Post by marinecomm on 2013-06-07
Update: I have sound now even in Spotify. Now my only issue is that whenever I restart the computer the sound volume starts out really low and I have to open the Pulseaudio Volume Control to turn it up.

---

