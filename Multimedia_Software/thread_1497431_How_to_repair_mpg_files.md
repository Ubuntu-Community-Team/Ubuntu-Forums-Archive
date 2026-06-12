---
title: "How to repair mpg files?"
date: 2010-05-30
forum: Multimedia Software
---

### Post by csmith6594 on 2010-05-30
I have a few files that are mpg format, but do not play.  What happens is the video will stop for a given period of time, and then start up again, but later in the video.  I tried DivFix++, but this only fixes AVI files.  I also tried using VLC to see if it would start up the auto fix box, and repair it, but that does not do anything as well.  I have looked for solutions on the Internet, but there is no help out there as well.  So I am at a dead end.  If I can get some help on it I would be thankful.:guitar:

---

### Post by xc3RnbFO8P on 2010-05-30
Did you try to play it from Terminal:
> totem

---

### Post by csmith6594 on 2010-05-30
Yup.  still the same problem.  If there is no fix to this, then I may have to get another laptop (which I planned to do anyway), and see if I can find some program in Windows to fix it because right now I am out of ideas.  I would re-download the files, but they are BIG.  Unless I become a linux genius during the summer and write a program for things like this.  Ugh.  The stress.

---

### Post by csmith6594 on 2010-05-30
Yup.  still the same problem.  If there is no fix to this, then I may  have to get another laptop (which I planned to do anyway), and see if I  can find some program in Windows to fix it because right now I am out of  ideas.  I would re-download the files, but they are BIG.  Unless I  become a linux genius during the summer and write a program for things  like this.  Ugh.  The stress.

---

### Post by csmith6594 on 2010-05-30
Sorry for the double post.

---

### Post by xc3RnbFO8P on 2010-05-30
> What happens is the video will stop for a given period of time, and then start up again
Were there any error message in Terminal?

---

### Post by LuridCinema on 2010-05-30
Might work.....

```
ffmpeg -i INPUT.mpg -sameq OUTPUT.mpg
```

---

### Post by csmith6594 on 2010-05-31
There were no error messages in the terminal.  I will surrender in saying that I am just going to find something in Windows to handle the problem.  Windows is like smoking, you truly never quit.

---

### Post by no2498 on 2010-05-31
windows does not like mpeg files lol

[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)

that can make them avi/mov files

hope this helps

---

### Post by TBerk on 2010-05-31
I have been have similar troubles (although my current solution in training involves .AVI files...).

 I have found running the files through something like AVIDEMUX (and saving as a new file name) has corrected the problems.

As I mentioned, it is a solution but still in development, so I'm not yet ready to proclaim "WIN!" but so far, so good.

As with any conversion or other process there is a some concern with loosing data (lossless vs lossy, etc). What I've seen doesn't reduce the file size by any appreciable amount.


berk

---

### Post by csmith6594 on 2010-05-31
I appreciate the replies.  I will think of something.  It is not super important that I take care of these files.  As if it isn't noticeable, I am so new to using linux that I spent a few hundred dollars on various books to understand this thing.  Compile this, command line that.  sigh

---

