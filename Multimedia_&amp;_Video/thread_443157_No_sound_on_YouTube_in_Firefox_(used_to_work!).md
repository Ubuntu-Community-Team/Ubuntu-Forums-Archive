---
title: "No sound on YouTube in Firefox (used to work!)"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by clconway on 2007-05-14
YouTube sound in Firefox disappeared a few days ago. I've got all the necessary components installed. Everything worked perfectly before and sound still works for MP3s and AVIs (including, e.g., the MPlayer plugin to firefox). This roughly correlates with the hal 0.5.9-1ubuntu2~feisty1 update I installed on 5/11.

The sound in YouTube does work if I do "sudo -H firefox". But, unlike [the user in this thread]("http://ubuntuforums.org/showthread.php?t=247709"), I own ~/.macromedia/Flash_Player (and everything underneath ~/.macromedia).

---

### Post by jjbean on 2007-05-14
I have the same problem. It just stopped working. I have searched the forums and tried most of the how to threads. Uninstalled and reinstalled flash several different ways. Nothing has worked. Atleast I still have a Windows pc our IE6 in wine, neither of those have any problems and work fine. (kinda ironic)

---

### Post by jjbean on 2007-05-15
I do not know if you have fixed your problem yet. If you have not check this link out. It got mine working, but the sound lags. I am going to try to figure that out next.

[COLOR="Red"][http://pulseaudio.revolutionlinux.com/PulseAudio]("http://pulseaudio.revolutionlinux.com/PulseAudio")[/COLOR]


**Fixed the sound lag. I actually read the page again, closer this time(gasp). I used Synaptic to install pulseaudio and pulseaudio-esound-compat to fully replace ESD sound. That cleared everything up. Hope this helps.**

---

