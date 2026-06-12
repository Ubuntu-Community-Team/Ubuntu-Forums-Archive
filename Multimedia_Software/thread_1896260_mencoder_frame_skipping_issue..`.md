---
title: "mencoder frame skipping issue..`"
date: 2011-12-16
forum: Multimedia Software
---

### Post by Druegan on 2011-12-16
I'm trying to convert a bunch of old kung-fu movies from .rmvb to .avi with mencoder.. and it has worked on a few of them, but in a lot of them, it just skips nearly every single frame.

I really don't know what I'm doing with video encoding.. I've just been trying to kludge together a solution from stuff I've found on various forum sites.. and reading the mencoder docs is about like trying to understand klingon.. I'm just not that video educated.

The command I've been using is ```
mencoder "input.rmvb" -oac mp3lame -lameopts preset=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1200 -ofps 25 -of avi -o "output.avi" 
```

I've read a few bits about how this can be caused by some kind of problem with the stock three-pass encoding, and that it might be solvable by going to a two-pass encoding.. but I have no idea how this can be accomplished.

I've been trying for over 6 months to get these converted, because for some reason every single .rmvb file I have, about halfway though, the video player loses track of where in the file it is at, which screws up subtitles something fierce.   Successful reincodes have worked fine.. and I've tried every player I can find.. all of them exhibit the same behavior.

So I'm trying to convert them to .avi, and now I'm getting this constant stream of "skipped frame" messages... like literally every frame. FFMpeg has shown no love either. I keep getting a bunch of errors..

So could anybody explain to me how the command posted above could be modified to try the two-pass encoding bit that I've heard might solve my problem?

---

