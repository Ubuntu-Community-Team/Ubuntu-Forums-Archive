---
title: "Real player made Banshee's audio choppy"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by Schalken on 2007-05-13
I downloaded and installed the real player deb as per the wiki and as soon as I ran it the music that was playing in Banshee in the background became incredibly choppy. Real player failed to play the audio of any file so I uninstalled it and restarted and the problem persisted.

How can I fix this?

---

### Post by Schalken on 2007-05-13
It seems Banshee's output is being clipped, i.e, the bass in particular comes out choppy (because it is of higher amplitude than the higer notes). If I turn the volume down the the minimum, and my speakers up, the audio is fine.

It's as if Real Player made the audio system treat the stream coming from Banshee as a lower bit depth than it really is, hence the bass clipping and the workaround of turning the volume down to below the clip point.

Is there a setting for this?

---

### Post by Schalken on 2007-06-29
I am now using KDE and I found out what the problem was. In KMix there is a slider for "PCM" and it is this that RealPlayer (stupidly) changes for its volume slider (instead application-level volume control). When this is set high, it is too much amplification and the audio is clipped giving choppiness. The problem was solved by running KMix and moving the PCM slider down to about halfway.

---

