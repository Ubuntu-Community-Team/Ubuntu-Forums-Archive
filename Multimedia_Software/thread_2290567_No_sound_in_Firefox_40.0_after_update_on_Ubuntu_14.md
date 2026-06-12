---
title: "No sound in Firefox 40.0 after update on Ubuntu 14.04"
date: 2015-08-13
forum: Multimedia Software
---

### Post by samer5 on 2015-08-13
All Firefox based browsers on my system have a problem with video sound. YouTube videos have no sound when played on these browsers.  This is most likely after a recent update to Firefox and perhaps due to it.  I currently have Ubuntu 14.04 and Firefox 40.0.  Could someone help with this?  Thank you.

---

### Post by Yellow Pasque on 2015-08-13
Is it just Youtube? FF 40 now defaults to using HTML5 on Youtube. Maybe you can switch back to using Flash in Youtube's settings and see if it fixes the issue.

EDIT: If you don't have gstreamer1.0-libav package installed, make sure you install it. You can also check [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by slug4 on 2015-08-14
Hi :D
I installed this extension: [https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-player/](https://addons.mozilla.org/en-US/firefox/addon/youtube-flash-player/).  works fine for me...  :)

---

### Post by samer5 on 2015-08-16
I went online and did a search.  I found out it was the sound output that was the problem.  I think the update set the sound to play through Built-in Audio.  if you go to System Settings > Sound > Output then choose your output device such as a headset or Speakers, the sound comes back.  Thanks guys! :D

---

