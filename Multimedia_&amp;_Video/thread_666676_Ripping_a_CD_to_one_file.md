---
title: "Ripping a CD to one file?"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by tim1976 on 2008-01-13
Some on my CD's have overlapping tracks and rather than rip each track I'd prefer to rip the whole CD in one go.

I know of a few apps on Windows that will do this but so far I've found nothing on Ubuntu.

Anyone have any ideas?

---

### Post by logos34 on 2008-01-13
You can rip a whole cd to single flac file with ABCDE, but it's command line and you need to configure it.

What about running EAC with Wine?  Yiou can do everything with EAC.

---

### Post by tim1976 on 2008-01-13
Thanks for pointing me in the right direction!

Manged to do the job with ABCDE, didn't seem to need any configuration which was a bonus.

:):):):)

---

### Post by logos34 on 2008-01-13
great.  I thought you had to add 'flac' to OUTPUTTYPE line (and a few other things), but I guess not.

What's nice about the 'abcde -1 -M -o flac' is you can then archive it and encode it to any lossy format abcde handles--mp3,ogg,aac,mpc etc.

i.e.

abcde -d file.flac -o ogg (but that will rip it to separate tracks)

Or did you just use the '-1' option?

abcde will also rip to lame/mp3 with 'nogap' option

---

### Post by andrew.46 on 2008-02-04
Hi,

 I can see that your question has mostly been answered:

> **tim1976 said:**
> Some on my CD's have overlapping tracks and rather than rip each track I'd prefer to rip the whole CD in one go.

I know of a few apps on Windows that will do this but so far I've found nothing on Ubuntu.
Anyone have any ideas?

But I can make 2 extra suggestions:

1. If you simply wish to rip the whole cd as a wav file to edit after you can always use cdparanoia from the command line. To rip  a 10 track cd to a single wave file:

```
$ cdparanoia 1-10
```

2. Have you tried to setup an ~/.abcde.conf file? Have a look at: [URL="http://www.andrews-corner.org/abcde.html"]abcde: Command Line Music CD Ripping for Linux
[/URL] which has a few 'recipes' to get you started.

 Regards,

  Andrew

---

