---
title: "OpenShot video editor problem"
date: 2013-09-07
forum: Multimedia Software
---

### Post by Autodave on 2013-09-07
Can add pics and transitions with no problem at all.  However, when I add an audio file, I do not see the pics that are on that track any longer: they do not appear when previewing.  I have tried adding the audio before the pics and after the pics installation, but whatever track I put the audio on, I can no longer see the pics on that track.

I can put music on one track and audio on the other and it works that way, but then I cannot do and effects when going from one pic to the next.

Any ideas?

Running Xubuntu 13.04 64 bit on quad core 3.0 w/8 gig ram.

---

### Post by sudodus on 2013-09-07
I have done that, but probably it was in an earlier version. The audio tracks are 'transparent', they should not change the video at all.

example

```

I==== picture 1 =======I                                  I=== picture 2 ==========I
                  I====== video clip 1 ==========================I
I========== audio =================================================================I
```

If that does not work, there is a bug, or you are doing something wrong. Are you sure the audio track is pure audio, not a track with a black or white screen video?

---

### Post by Pinoy Tux on 2013-09-10
From what you described, I'm guessing you didn't add another track that will hold the audio file.  OpenShot defaults to two tracks when you create a new project.  If you're adding an audio file that overlaps the pictures/transitions/whatever, put it in its own track.

---

### Post by Merrattic on 2013-09-12
Like this:
[IMG]http://tsah.co.uk/tsah/openshot_images_and_audio.png[/IMG]

---

### Post by Pinoy Tux on 2013-09-12
Or this (similar to sudodus'):

[IMG]https://dl.dropboxusercontent.com/u/5521153/screenshots/ubuntu/2013-09-13-audio-on-separate-track.png[/IMG]

---

