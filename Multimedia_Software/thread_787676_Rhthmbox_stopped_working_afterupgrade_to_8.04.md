---
title: "Rhthmbox stopped working afterupgrade to 8.04"
date: 2008-05-09
forum: Multimedia Software
---

### Post by jacobj on 2008-05-09
I have a bit of a strange bug, after I upgraded my ubuntu to 8.04 (from 7.10) Rhythmbox stopped to be able to play music. If I press play the song get a play icon in front of it but it don't start to play, the progress bar is static in the beginning of the song.
The sound work in other applications like mplayer and youtube vids etc. So it seem to be just Rythmbox that have the problem. I tried to reinstall the application in packagemanager but the problem persist after application reinstallation.
Anyone have any idea where to start troubleshooting? Can it be some kind of codec problem?

Best Regards
//Jacob

---

### Post by hermes0710 on 2008-05-09
Try starting the application through a terminal and post the output of the terminal when you try to start playback.

---

### Post by jacobj on 2008-05-09
Hello, Thanks for the reply.

This is the outpout I get when I start the app and try to play a song.

[FONT="Courier New"]jacob@mrblack:~$ rhythmbox
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-gzip decoder|decoder-application/x-gzip
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
[/FONT]

---

### Post by hermes0710 on 2008-05-09
As mentioned in the output you are missing plugins. I really don't know what  the exact plugin is but search in synaptic by name using "gstreamer". It seems to be something about gzip though. Try installing related packages... Good luck

---

### Post by jacobj on 2008-05-09
I have reinstalled all gstreamer items I had in package manager, I also installed some additional like gstreamer0.10-fluendo-mp3, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-ugly,  gstreamer0.10-tools, etc.
But still same problem:confused:
It's just regular mp3s. Very strange, can't get it to work :)
It seem to affect all gstreamer apps, like totem player also.
Well, thanks for the help anyway!

---

### Post by hermes0710 on 2008-05-09
> Do you have these installed?

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad


Yeap, you have them... Sorry, i didn't notice

---

### Post by unimatrix on 2008-05-24
Bump

I have the same problem.
Some mp3s will play, others won't (producing the missing x-gzip error).
And it's not just Rhythmbox. Those particular files produce this error in any player.

---

