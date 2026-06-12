---
title: "Mplayer gives &quot;no matching vobsub language found&quot; since upgrade to 9.10"
date: 2010-05-31
forum: Multimedia Software
---

### Post by m0116815 on 2010-05-31
So, weird thing happens since I upgraded to 9.10. I have no idea what causes it nor can I find a fix. Could be an Mplayer thing, but the symptoms are odd.

I frequently play music or video on shuffle. The typical command is: mplayer * -shuffle
Since the dist-upgrade, this gives:

Playing foo.avi.
VobSub: mpeg_run error
No matching VOBSUB language found!
Seek failed

... for every file except the first in the list, so only when it moves to the second file. If I hit enter (for moving to the next file on the list) before the first is finished, everything proceeds normally. If I let it go to the second file on its own, the above message shows for each remaining file and Mplayer quits.

Now the weird part (that I'm hoping is diagnostic): after this has happened, my command line interface doesn't seem to know in which directory it is. The command prompt shows the expected (unchanged) directory and typing 'pwd' gives the same, but tab autocompletion seems to think it's one dir up the tree, and sometimes suggests completions that don't seem to exist anywhere (eg. when I type mpla[tab] it suggests mpla/, which doesn't exist). Typing 'cd .' fixes that weird behavior.

This isn't a huge problem, but an annoyance. I've reinstalled mplayer to no avail. I am clueless here.

---

### Post by m0116815 on 2010-06-01
It is perhaps worth adding that I have root access to this machine, but physical access is harder. I'm not sure if that makes a difference if I'll be reinstalling bash.

---

### Post by m0116815 on 2010-06-02
Actually, the weird issue seems to have nothing to do with the -shuffle, or with the multiple files. If I just play a file in mplayer, bash gets confused after it's done.

---

### Post by m0116815 on 2010-06-06
Anyone? This is actually getting irritating. Somehow mplayer finishing certain files messes something up. All help appreciated.

---

