---
title: "Can video from web page be made to open in a movie player"
date: 2009-03-03
forum: Multimedia Software
---

### Post by sofasurfer on 2009-03-03
Sine there is no system wide audio equalizer on my system, can I cause videos from a web page to open in MPlayer, for instance, since it does have an equalizer?

---

### Post by rjmoerland on 2009-03-03
This worked for me (if you're using firefox as browser): [https://addons.mozilla.org/nl/firefox/addon/446](https://addons.mozilla.org/nl/firefox/addon/446)

---

### Post by sofasurfer on 2009-03-03
Thanks. This is what I need. However, at the moment it won't work. When it searches for list of players it freezes.

---

### Post by sofasurfer on 2009-03-03
I can't tell if the search for movie players actually completes or if the window just freezes. But the wizard can not be used because of this freeze. When I go to extensions>preferences and choose application, is it meaning to go to /usr/bin?

---

### Post by xtremethegreat1 on 2009-03-03
Can't say about other streaming sites, but if you're using Youtube (because I've tested it there), just go to the /tmp directory. This is where all streaming flash videos are stored. Find out the filename starting with Flash, and try playing it with vlc. If it is the same, you can simply copy it to your desktop. But do make sure that the video had finished streaming.

The original post is available [here]("http://thehcl.blogspot.com/2009/03/download-youtube-videos-in-linux.html"). It contains further information about how to do it.:)

---

### Post by sofasurfer on 2009-03-03
Thank you all.
I will tinker some more after work.
I am able to watch anything I find so far. I can get youtube on mplayer. I want to get streaming tv shows on mplayer (because of the audio equalizer)but currently they only open in a firefox page. Needly to say there is no audio equalizer available in Firefox.

---

### Post by rjmoerland on 2009-03-04
> **sofasurfer said:**
> I can't tell if the search for movie players actually completes or if the window just freezes. But the wizard can not be used because of this freeze. When I go to extensions>preferences and choose application, is it meaning to go to /usr/bin?

Well, I use VLC for all streams, so I let all file types point to /usr/bin/vlc. Does that help you?

---

