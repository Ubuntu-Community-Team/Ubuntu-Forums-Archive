---
title: "[SOLVED] Mplayer video ripple"
date: 2008-06-24
forum: Multimedia Software
---

### Post by keiichidono on 2008-06-24
When i try to play any of my anime files with Mplayer (or any video player in Linux) i get these little "ripples" in my video. It can be described as "It looks like the horizontal scan lines you see when a video recording is made of a real TV playing something." or "When i say ripple i mean like when the tv is having trouble receiving the feed and you get "ripples" on your tv briefly.". I was thinking that updating to the latest SVN version may fix this problem but i don't know how to install the latest SVN version at all. Please and thank you for any help on this matter.

---

### Post by Pjotr123 on 2008-06-24
Try disabling the visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

### Post by keiichidono on 2008-06-24
Thanks, i'll give it a shot (although i love my visual effects).

---

### Post by keiichidono on 2008-06-24
It fixed it, but can you explain to me why having Compiz enabled messed it up? Is there any way to have Compiz running and still keep videos from stuttering?

---

### Post by markbuntu on 2008-06-24
The problem is that compiz uses indirect rendering, ie rendering of the desktop through the cpu instead of directly by the graphics card and video playback is slowed way down by that so it tears and skips frames, etc.

The people who write the drivers for these cards are aware of this problem and a working on a solution. It is probably months away.

---

### Post by keiichidono on 2008-06-24
Thank science, i hope it gets released for 8.10, that would be amazing.

---

