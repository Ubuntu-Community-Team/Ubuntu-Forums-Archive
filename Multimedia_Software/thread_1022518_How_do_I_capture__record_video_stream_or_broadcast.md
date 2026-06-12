---
title: "How do I capture / record video stream or broadcast?"
date: 2008-12-26
forum: Multimedia Software
---

### Post by sofasurfer on 2008-12-26
I have a Hauppauge 1600 tv tuner card. I never got Myth TV to work. I guess its beyond my expertise for now. I watch tv using Mplayer. So if I want to record tv shows, either from a stream on the internet or from a broadcast, how do I do it?

---

### Post by wolfen69 on 2008-12-26
for a tv show, you could try 
```
cat /dev/video0 > /tmp/name_of_file.mpg
``` of course the recorded program will wind up in your /tmp folder. just do Ctrl-c to stop recording. and you must have mplayer open and on the channel you want ahead of time.

i saw a post one time that told how to schedule recordings, but don't know where it is. if i find it, i'll get in touch.

i'm also assuming that your tv tuner is /dev/video0

---

### Post by sofasurfer on 2008-12-26
I displayed a TV channel on Mplayer and then ran the command that you supplied above. It did indeed record, but the recording is just static. 
In the command "cat /dev/video0 > /tmp/name_of_file.mpg" would "video0" be the problem? What are my other choices?

---

### Post by sofasurfer on 2008-12-27
I found a solution at this site... [http://ubuntuforums.org/archive/index.php/t-369653.html](http://ubuntuforums.org/archive/index.php/t-369653.html).
Its a very good tutorial for using a clunky method to view, record and watch. It also describes how to accomplish the steps with a script.

So I'm off to try out more of the lesson and search for other methods.

---

### Post by Macintosh SE on 2009-01-02
I encountered the same problem about a year ago, and wrote a shell script to schedule recordings.

Have you verified that the card works (for viewing live TV)? If so, I can give you a copy of the shell script that I wrote.

---

