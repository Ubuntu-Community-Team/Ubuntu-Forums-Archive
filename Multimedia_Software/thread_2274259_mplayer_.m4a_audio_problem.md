---
title: "mplayer .m4a audio problem"
date: 2015-04-19
forum: Multimedia Software
---

### Post by bill-lancaster on 2015-04-19
Hello,
I'm running mplayer from the command line.  An audio file of type .m4a seems to automatically invoke a sort of mplayer gui.
Is there a way of avoiding this?

---

### Post by speartip on 2015-04-19
Same thing happens here.
when running "mplayer -ao pulse nameoffile.m4a"
I can't help with your issue, other than to suggest that it must be something embedded in the file.

---

### Post by bill-lancaster on 2015-04-19
Thanks, my only thought is that .m4a typically is for video (?).  So I wonder if there's a command to supress the attempt to show the video.

---

### Post by bill-lancaster on 2015-04-19
Found it!
"-novideo" stops the gui thing from showing.
But now I have further problems with audio only .m4a which I'll start in a new topic.

---

