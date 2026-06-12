---
title: "Sound problems..."
date: 2008-11-10
forum: Multimedia Software
---

### Post by redioactif on 2008-11-10
OK...
So I have the sound when I start my computer and when I play music...But after I go on Youtube or some site containing music, then all the other sounds won't work fron the moment on until I restart my system...And vice-versa: when I play a movie on VLC and then decide to go watch a video on Youtube, the sound won't work...
If anyone could help me it would be great...
I have UBUNTU 8.04

---

### Post by redioactif on 2008-11-11
bump

---

### Post by shimi on 2008-11-12
Look at this Blog post, it describes the same [sound problem with Ubuntu 8.04]("http://mylinuxnotebook.blogspot.com/2008/07/ubuntu-sound-flash-problem.html")

---

### Post by psyke83 on 2008-11-12
Here's your warning: don't install the libflashsupport library. It will enable PulseAudio output in Flash, but it will also make Firefox extremely unstable. This is bug [192888]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888").

This bug is fixed officially in Intrepid, but it is not fixed in Hardy due to the complexity of the fix.

Here is the unofficial fix to get PulseAudio working properly (and will also upgrade Flash to the latest release): [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

