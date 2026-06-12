---
title: "How to use VLC with gtkPod"
date: 2009-05-05
forum: Multimedia Software
---

### Post by practic on 2009-05-05
I was playing around with gtkpod and vlc, and managed to get them to work relatively well together. Since I couldn't find this info anywhere else, I thought I would post it here.

1. In gtkPod you need to go to the Edit menu, then choose Edit Preferences.

2. Select the Tools tab and in the field that says "The Command for Play Now" put this:

vlc --one-instance %s

This will prevent each new song from spawning another instance of VLC.

3. In the field below that says Command for Enqueue put this:

vlc --one-instance --playlist-enqueue %s

Essentially the same as the first command except that songs are queued into the playlist instead of being played right away.

This seems to work nicely for video and audio. The only drawback is that in the VLC playlist the files show up with their cryptic iPod 4 character names. I don't know if there is any way around that.

---

