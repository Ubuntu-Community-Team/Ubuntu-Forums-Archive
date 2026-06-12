---
title: "Cinelerra: How do I &quot;lock a track&quot; to keep it from being edited?"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Arwen17evenstar on 2009-12-18
I'm used to adobe premiere pro on windows and I've decided to try out cinelerra on linux for the first time. I'm slowly find my way around the interface. 

But I can't figure out how to "lock" the audio track so even if I accidentally click on it or am doing something with the video track the audio track shouldn't move around or anything else. I want the audio to remain where it is, exactly as it is. Premiere pro had this feature, but I can't figure out whether cinelerra does or not.

Also, currently I have the audio that is attached to the video on a track that is muted because I don't see any way to just insert the video part of the video without its audio. Is that the best way to go about it?

---

### Post by wildhostile on 2009-12-18
> **Arwen17evenstar said:**
> .

You can "arm" or "unarm" the tracks you want to modify or not. (it's the red button in the "patchbay").
There ar two ways to load videos without sound:
- you can load the video with his associated sound tracks and delete these one afterward.
- you can add just a video track (add track -> Video) and drag and drop the video from the ressources window (Media or Clips) or from the Viewer.

The arm/unarm feature is both a great feature and a pain when you have multiple tracks to manage. When you want to insert a new track above or through your existing one you have to make sure that all the others tracks (video and audio) are nor armed.

---

