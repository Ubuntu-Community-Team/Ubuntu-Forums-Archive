---
title: "problems after recent updates"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by joeashcraft on 2007-08-13
It all started when I restarted my laptop.
It had been up for about 12 days, and I had installed a few updates (I don't think that the updatesare  causing these problems, but that's the only things that's changed recently), one of which required a restart (security, kernel, one of those...), so I restarted. Now I can't use ALSA (changed it in 'gnome-sound-properties'), I have to use OSS (not that it makes a difference to me... if there are differences, please enlighten me). When I play a few tracks in amarok, after the 3rd or 4th track I get an error that says "xine was unable to initialize any audio drivers", then amarok crashes (I can't hear anything using VLC).
Finally, I can't view flash animations/videos/anything thru Firefox, or Galeon. Well, I can see something, but it's not what I'm supposed to see. Attached are a few examples.
As for log files, I'm not sure where to look.


For reference, yes, all of these things were working great until my recent restart.

NEW INFO: I tried to install a different driver for my video card during my 12d uptime, it didn't work, so I reverted to the original (not the ubuntu default). Could x-server have anything to do with audio problems? Or flash problems? I'm pretty sure that I was using the adobe flash software, but now it seems gnash wants to play flash stuff.

Any ideas would be greatly appreciated. If you know where Amarok keeps logs, that'd be helpful, too!

---

### Post by joeashcraft on 2007-08-14
Well, I have done nothing except reboot a few times and now I can watch my precious googlevideos (and youtube, metacafe, and the like). Not sure what the problem was, or why it's fixed now, but it is fixed nontheless. No audio from said videos, tho, and Amarok still crashes after a few songs. I get static when I use ALSA, but I can hear things just fine with OSS (in amarok only).

---

### Post by dannyboy79 on 2007-08-14
have you tried to remove and reinstall alsa? (do a completely remove, which will remove all config files as well) it will tell you that it has to remove gnome-desktop most likely but it's ok as it's only a metapackage. then just reinstall alsa and gnome-desktop if you'd like. maybe even try to reinstall amarok.

---

### Post by joeashcraft on 2007-08-14
completely removed and reinstalled alsa-utils... still no sound. (PS I didn't restart)

oh, and It removed the following, which I reinstalled...
fast-user-switch-applet
gdm
gdm-themes
ubuntu-minimal

---

