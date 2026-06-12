---
title: "VLC Mozilla Plugin"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by mertle on 2007-04-03
In the past, I've used VLC's mozilla plugin to listen to Sirius Satellite radio and all has worked well and without having to tweak anything. After doing a fresh install (Kubuntu Edgy), the plugin no longer works. I get no error message, it just..... doesn't stream. I had to install MPlayer and use its plugin to be able to listen, when in the past, MPlayer didn't quite work right for me. What, they switched? *chuckles*

I really like VLC and hate having to install a whole other media player just to use it's mozilla plugin. I just about had every VLC related package installed trying to get it to work, but nada. Perhaps I'm missing a package I didn't realize I installed last time around?

I have installed:

vlc
vlc-nox
mozilla-plugin-vlc
vlc-plugin-alsa (just in case, even though it's a dummy package)

In the past, I believe these were all I needed. Was there an update snuck in the last few days that maybe broke something?

- mertle

---

### Post by Sammi on 2007-04-03
Same prob here. But it's not really a problem at all when Mplayer is doing it's job instead. I just had to uninstall both the vlc and totem mozilla plugins for Mplayer to take control of media playing in firefox.

---

### Post by mertle on 2007-04-03
Well, yeah... the mplayer plugin works just dandy for me as well, but I don't /want/ Mplayer. It seems a waste of HD space to have it installed just for its plugin, and nothing else. Ideally, I'd like VLC to control media play for Firefox. I just don't get it... it worked last week.

- mertle

---

### Post by mertle on 2007-04-07
Yay! Finally solved my problem... I had to use the edgy-backports version of VLC and it's Mozilla plugin to get it all to work. Even though I have that repository enabled, it must be a slightly older version to not have been DLed automatically, but it works- so all is well.

- mertle

---

### Post by kerry_s on 2007-04-07
I use the MediaPlayerConnectivity firefox extension and vlc-> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

I only have vlc installed for all media. :)

---

