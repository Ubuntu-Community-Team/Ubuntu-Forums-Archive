---
title: "[SOLVED] playing sound freezes applications (vlc, totem, whatever)"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by mopi on 2007-08-05
Hi all.

My sound has stopped working suddenly. It worked the other day. It doesn't seem to be related to a muted setting somewhere because when I try to play an mp3 or ogg/vorbis in vlc the application actually freezes and stop responding. If I play an .avi file I get video but no sound and the GUI goes non-responsive. I.e. I can't stop the video, open another video etc. I need to kill the application to stop it. 

Wasn't there some alsa related updates the other day? Anyway, do anyone have some hints on how to diagnose this?

I'm using a nforce2 card on Feisty.

---

### Post by mopi on 2007-08-05
Solved it.

It was a simple matter of 
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

```
+ reboot

Why my sound disappeared in the first place is still a mystery though.

---

### Post by Gremlinzzz on 2007-08-05
You should mark this solved so others will see it and fix there same problem. just look at top of post you will see thread tools solved is on the list.:guitar:

---

### Post by wolfsandwich on 2007-08-11
i had the same problem and your solution worked for me, too.  thanks a lot.

i think the problem started when i was trying to customize my log in page by adding clever wav files (i tried that again and broke it again, thankfully the fix worked again).



thanks for posting that, i thought i was going to die without my media players.

---

