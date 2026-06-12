---
title: "[SOLVED] How to use mplayer wmv codecs in Totem??"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by MadKAT on 2008-01-17
Hello

I got an ubuntu gutsy (upgraded) and have both totem and mplayer installed. Had them since Fiesty and even before that I think.

Anyway both play mp4 and avi files quite well, but my problem is with wmv files. mplayer plays them just fine but when played in totem, i get pixelization on transitions, making the video unwatchable. So how do I get totem to play wmv's just like mplayer?

Any ideas?

Thanks!

---

### Post by eye208 on 2008-01-17
Totem can use two different back ends for video playback: GStreamer and Xine. The plugin-based GStreamer is default, but Xine (which actually shares some code with MPlayer) may give you better results. Just install the "totem-xine" package. You can always switch back to "totem-gstreamer" later.

---

### Post by MadKAT on 2008-01-17
Thanks for the reply! :)

But it seems I already have totem-xine installed. apt-get said "totem-xine is already the newest version".  Now how do I find out if this is what totem is using? I can't find it anywhere in totem's preferences or plugins dialogs.

---

### Post by eye208 on 2008-01-17
Well, maybe Xine was causing the WMV problems in the first place. In this case I would suggest switching back to GStreamer.

totem-xine and totem-gstreamer are conflicting packages, i.e. you can't install them side by side.

---

### Post by namnam on 2008-01-17
If what eye208 said doesn't work for you, you can try manually removing totem-gstreamer by running "sudo aptitude remove totem-gstreamer".

---

### Post by MadKAT on 2008-01-17
That did it!

I installed totem-gstreamer using "sudo aptitude install totem-gstreamer" and it automatically removed totem-xine, too. And that did the trick totem is now playing wmv files cleanly.

Thank you very much, both of you! :)

---

### Post by cor2y on 2008-01-17
Add a [solved] to your post title, so others now the problem is gone.

---

