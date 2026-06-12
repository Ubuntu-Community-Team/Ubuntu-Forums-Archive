---
title: "Lose Sound with Flash if Running Media Player"
date: 2009-10-22
forum: Multimedia Software
---

### Post by gary_ragel on 2009-10-22
I've been looking around the forum for a while looking for a solution to this, but haven't had much luck.

From time to time, I won't get any sound with flash videos. This will happen if I'm using Amarok or other media player while doing my daily internet browsing. I'll come across a video I want to watch, so I'll pause/stop the media player and start the flash video. No sound. This doesn't happen every time, but once the issue appears (i.e. don't get any sound in a flash video), I won't get any sound in any further flash videos until I reboot. Any help would be appreciated; it's really annoying having to reboot this often. Thanks.

---

### Post by vinutux on 2009-10-22
Give more info plz............ what version u r using /64 or 32 

r u talking about .flv files form your system or net videos like from youtube.......etc :)

---

### Post by gary_ragel on 2009-10-22
Thanks for the reply. 

Using 9.04 with Firefox 3. I'm getting no sound on Youtube videos, while the media player (normally Amarok 2) is still running. After shutting down Amarok for a while, I'm able to get sound on YT vids again. I have ALSA selected in all my sound preferences under System-->Preferences-->Sound.

---

### Post by vinutux on 2009-10-22
open terminal Applications > Accessories > Terminal ```
sudo apt-get install gnome-volume-control-pulse
```


Log out.... You have a new volume controle now.. delete ol one right click

check this link also helps [http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml]("http://news.softpedia.com/news/How-to-Replace-the-Volume-Control-in-Ubuntu-9-04-with-the-PulseAudio-One-112786.shtml")

---

### Post by gary_ragel on 2009-10-23
Seems to have corrected it; thanks! Individual controls for each app is pretty sweet.

---

### Post by vinutux on 2009-10-23
> **gary_ragel said:**
> Seems to have corrected it; thanks! Individual controls for each app is pretty sweet.

plz...............mark thread SOLVED under thread tools

---

