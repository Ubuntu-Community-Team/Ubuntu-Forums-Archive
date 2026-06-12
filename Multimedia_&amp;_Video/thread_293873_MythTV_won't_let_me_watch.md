---
title: "MythTV won't let me watch?"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by carlos1 on 2006-11-05
I managed to install MythTV (I think) on my Edgy install, running KDE and Beryl.

I had various problems, mainly with MySQL database, but I got through all those with the help of various threads on the forums (thanks for those who posted as I didn't need to post again, just read what was there).

Anyhow, when I went to scan for channels, it imported 80 channels, which I believe is the correct amount, but they were only number, no names.
However, I took it from this that my TV Tuner card was working.

When I go into the main menu for MythTV, and hit "watch live TV" I get a black screen for about 30 seconds, then it goes back to the main menu.

I cannot find anyone else having this problem, and can't find anything in the HOWTOs about it.

Can anyone advise what might be wrong? Thanks.

---

### Post by John.Michael.Kane on 2006-11-05
Heres a guide that may offer some answers.
[https://help.ubuntu.com/community/MythTV#head-e8488a1209f25fb40b2acd56716145fac6a8383a](https://help.ubuntu.com/community/MythTV#head-e8488a1209f25fb40b2acd56716145fac6a8383a)

---

### Post by carlos1 on 2006-11-05
Thanks, I did try that HOWTO, which is how I got part of it installed already.

But I can't find anything in there, or in any of the linked HOWTOs, about the problem I am having. Does anyone know?

---

### Post by winter_rob on 2006-11-06
I got the same problem. I tracked it down to ivtv not loading properly.

Did you try tvtime? Or any of the other tv programs. And did THEY give you a picture?

I got tvtime etc working, but they only gave a bad (B&W) picture with no sound. The bttv module was loaded, but didn't work propperly. I haven't solved it yet

My problem is posted here:
[http://ubuntuforums.org/showpost.php?p=1716788&postcount=1](http://ubuntuforums.org/showpost.php?p=1716788&postcount=1)

Rob

---

### Post by superm1 on 2006-11-07
Did you associate the channels with an input from zap2it/xmltv?  If the channels don't have guide data associated, you won't be able to tune them in myth.

---

