---
title: "How do you import tv shows into mythtv?"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by dfreer on 2007-08-01
Hi,

I have a bunch of movies, and tv shows on my computer (not recorded with mythtv). Videos work great in MythVideo, I can search IMDB for the metadata and everything works great. The problem I'm having is with the TV shows. If I lump them in with MythVideo, it makes navigating the video manager horrible, and I can't add metadata for the shows (IMDB search doesn't work, and the metadata isn't designed to handle individual tv episodes anyways).
So I googled, and it appears the preferred method is to put TV shows in the "Previously Recorded" section and not mythtv. Here's an how-to:
[http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php](http://www.myhdbox.com/mythtips/2006/05/tip-3-importing-downloaded-tv-shows.php)
However, I can't find the file myth.rebuilddatabase.pl *anywhere* on my system. I assume this comes from using debian packages (from ubuntu's official repository) to install instead of compiling mythtv myself. Can anyone please help me, this is really frustrating me!

---

### Post by Scorpuk on 2007-08-02
I installed my MythTV from the repositories and just checked to see if the script exists and it does:


```

updatedb
locate myth.rebuilddatabase.pl
```


may need sudo for above, not sure as accessing my linux computer with webmin as root. :)

result:

> /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.plz.gz


Maybe a compressed file and maybe in the docs folder, but just checked with gzip and the contents is the .pl file :D

to view contents

```
gzip -l myth.rebuilddatabase.pl.gz
```

to extract I think its

```
gzip -d myth.rebuilddatabase.pl.gz
```


Hope this helps. I for one will be trying this out at some point as I will need to import all existing recordings into a fresh install when i build my new backend :D

---

### Post by CoNMaN on 2008-06-01
thanks for the help on locating the .pl it worked for me, but now I cannot run it.  I get this error

./myth.rebuilddatabase.pl --ext avi
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at ./myth.rebuilddatabase.pl line 55.


mythbuntu 8.04

---

### Post by Joeb454 on 2008-06-01
I'm guessing there's a pretty big difference between mythbuntu (and mythtv) since August last year ;) I'd suggest creating a new thread in the current forums (not continuing the Archived posts) and going from there :)

---

### Post by dfreer on 2008-06-03
> **CoNMaN said:**
> thanks for the help on locating the .pl it worked for me, but now I cannot run it.  I get this error

./myth.rebuilddatabase.pl --ext avi
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at ./myth.rebuilddatabase.pl line 55.


mythbuntu 8.04

Barring a change in mythtv since this post was created, I was able to use the script above by installing a couple packages. To be able to figure out what packages you need, look at the very first error:
```
Can't locate Time/Format.pm
```

Check out [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and see which package this file belongs to:
[http://packages.ubuntu.com/search?searchon=contents&keywords=Time%2FFormat.pm&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=Time%2FFormat.pm&mode=exactfilename&suite=hardy&arch=any)

So, all you need to do is install this libtime-format-perl package, run the script again, see if it complains about any other files.

BTW, this whole import TV shows thing will only bring you tears. Mythtv really screwed things up here. My advice? either just leave your TV shows in the "Videos/Movies" section, or try a better media center solution.

---

### Post by CoNMaN on 2008-06-03
Joeb454 - Thanks, I saw the dates on it after I posted.  This was the number one hit on google for "import myth tv shows"

dfreer - Thanks for explaining to me how to read that error.  I will try that when I get home today.

---

