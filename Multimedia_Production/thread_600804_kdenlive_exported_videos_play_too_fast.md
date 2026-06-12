---
title: "kdenlive exported videos play too fast"
date: 2007-11-02
forum: Multimedia Production
---

### Post by computergee on 2007-11-02
I'm working on a video for a school project, and I've got all the footage shot. I just need to edit it all, for which I'd like to use kdenlive. I've got it how I want it in the preview window, but when I export it, the video plays too fast, maybe 1.5x normal speed. Any tips?

---

### Post by darkadept on 2007-12-17
Same here too.


I'm using gutsy.

---

### Post by philc on 2007-12-17
I don't know the answer, but it might be worth looking at the KDEnlive forum:

[http://www.kdenlive.org/bbforum/](http://www.kdenlive.org/bbforum/)

And logging a bug:

[http://www.kdenlive.org/mantis/view_all_bug_page.php](http://www.kdenlive.org/mantis/view_all_bug_page.php)

---

### Post by ugm6hr on 2007-12-17
> **computergee said:**
> I'm working on a video for a school project, and I've got all the footage shot. I just need to edit it all, for which I'd like to use kdenlive. I've got it how I want it in the preview window, but when I export it, the video plays too fast, maybe 1.5x normal speed. Any tips?

Is this when exported as DVD?  I have just started using kdenlive, and rendered just a "selected" zone to .avi, which runs just great.

You could then use DeVeDe to create the DVD from the .avi if you want to, which works great.

---

### Post by dad311 on 2007-12-18
I had this same issue.  I believe its a Kdenlive issue with NTSC.  You might try exporting to PAL and then convert to NTSC.  Because of this issue,  I switched to Cinelerra.  Cinelerra is a great program, but there is a learning curve.

---

### Post by angrydill on 2008-07-18
> **dad311 said:**
> I had this same issue.  I believe its a Kdenlive issue with NTSC.
I had the same problem as well.  It is indeed related to PAL/NTSC differences.  User "jhardin" on a Gentoo forum suggested a fix that worked for me; which was to set an environment variable:

[FONT="Courier New"]export MLT_NORMALISATION=NTSC[/FONT]

before running kdenlive.  Hope this helps.

-a.d.-

---

