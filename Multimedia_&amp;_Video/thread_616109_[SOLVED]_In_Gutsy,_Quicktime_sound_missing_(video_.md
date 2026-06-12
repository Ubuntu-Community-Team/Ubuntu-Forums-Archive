---
title: "[SOLVED] In Gutsy, Quicktime sound missing (video is fine, other audio is fine)"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by phyzome on 2007-11-17
I upgraded to Gutsy a week or so ago, and I've just now noticed that Quicktime (.mov) files will play video but not audio.

[LIST]
[*] VLC would play
[*] MPlayer would play
[*] Totem would crash
[*] Xine would crash
[/LIST]

(**Edit:** Okay, while I was writing this post, I fixed the problem, but I'll leave this up for others to see.)

So, I remembered that the upgrade from Feisty Fawn to Gutsy Gibbon had killed a bunch of packages, and I realized that it had probably removed non-free/restricted codecs.  I installed **ubuntu-restricted**, and VLC works now. (Haven't tested others.)

---

