---
title: "Sound AND video issues with Skype in Ubuntu 13.10"
date: 2013-11-10
forum: Multimedia Software
---

### Post by tattvamasi83 on 2013-11-10
I had some issues with sound in Skype running on Ubuntu 13.10, but the PULSE workaround fixed it (changing the run-command to **[FONT=Arial]env PULSE_LATENCY_MSEC=30 skype[/FONT]**). However, I used to run another script bacause my video (only in skype) was upside down (**bash -c'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'**). After installing Ubuntu 13.10 however, the latter solution seems not to work, and is it possible to run TWO such pathces at the same time? I don't want to choose between sound OR video.

Q: How can I let the PULSE_LATENCY run, and ALSO flip my video back from being upside down? My experience with Linux is limited, so be kind to explain ALL steps, should you have a solution. Thanks :p

---

### Post by anounax on 2013-11-11
[SIZE=2]I believe you can just put those options together like this
```
[FONT=arial][SIZE=2]**PULSE_LATENCY_MSEC=30 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype**[/SIZE][/FONT]
```

[FONT=arial]**env** in your first solution was a command 'skype' running with environment variable **PULSE_LATENCY_MSEC **set to 30, and your second command was bash (shell interpreter) executing 'skype' with variable** LD_PRELOAD** set to **/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so**[/FONT], so you can probably just mash them together and it should work.[/SIZE]

---

### Post by anounax on 2013-11-11
Also, I found another solution for a crappy sound, that fixes not only skype, but some other programs like audacity, too. Here [http://askubuntu.com/questions/307951/how-do-i-fix-the-weired-skype-noises](http://askubuntu.com/questions/307951/how-do-i-fix-the-weired-skype-noises) (here it is explaned for another distro, but with a reason why this works [https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling) )

---

### Post by tattvamasi83 on 2013-11-11
Thanks a lot. It works great from the terminal, but the Skype icon has disappeared from the dash search. The icon is still in /usr/share/applications/ but I cannot run it from there for some reason, or copy the icon to the launcher on the side (or anywhere else). What could have happened? I'd prefer to have an Icon, and not have to run it from the terminal... I tried making a launcher with the command: ```
PULSE_LATENCY_MSEC=30 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```
It didn't work either. What can I do?

---

### Post by tattvamasi83 on 2013-11-11
Btw; I open nautilus through the terminal with sudo nautilus, and navigate to /usr/share/applications/ where I right click the Skype icon, and that's how I enter the code you suggested. When I do that, Skype disappears from the dash, and won't open when I press the icon in the launcher. It runs from the terminal however. After reinstalling skype, the icon is back, but runs only the PULSE command. When I add the PRELOAD command (through right clicking the Skype icon in usr/share/applications/ the icon disappears again. I am confused :D

---

