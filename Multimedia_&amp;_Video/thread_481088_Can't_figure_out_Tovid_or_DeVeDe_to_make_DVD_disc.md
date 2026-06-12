---
title: "Can't figure out Tovid or DeVeDe to make DVD disc"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by toecutter on 2007-06-22
I'm trying to burn an AVI file to a DVD disc so it will play in any DVD player, but when I use Tovid and type in this command as directed:

```
$ dvdauthor -x /tmp/Untitled_disc.xml
```

I get an error saying that the system can't find the '-noask' command - when I *remember* seeing -noask being used in the encoding part of the program.


When I installed and used DeVeDe, the simple interface was great but then I couldn't find the output folder! So I have no idea where the DVD ISO is...

Can anyone help with either of these issues? '-noask' for Tovid or finding the DVD ISO that DeVeDe made...

---

### Post by avik on 2007-06-22
Sorry, I can't help you with either problem, as I don't use those programs.  However, the simplest program I found for making a DVD was DVDStyler.  It's interface is simple and uncluttered, and it supports anything I needed it for.

It's not in the repos but it is at [http://getdeb.net]("http://getdeb.net").

And since you're using amd64, you'll want to look at [this]("http://dvdstyler.sourceforge.net/wiki/FAQMjpegtoolsError?show_comments=1").

---

### Post by toecutter on 2007-06-22
Thanks for that, I'll try it as well :) 

I'll still need to find that DVD ISO, it'll be taking up room on my drive, hehe

---

### Post by toecutter on 2007-06-22
I can't install DVDStyler because it doesn't run on 64-bit systems...

on the other hand, I was able to find the search function (haven't used it up to now! :)) and found the DeVeDe ISO file - worked a treat!

Thanks for the suggestion for DVDStyler though :)

---

### Post by kelvin spratt on 2007-06-22
DE VE DE unless you specify it will be in the home folder under your name, if you are unfortunate and get a sound problem go to their site at the bottom is a patch for mencoder, as it seems to have a bug in feisty, it does do a good job for me all DVD produced play on my home DVD player

---

### Post by avik on 2007-06-22
> **toecutter said:**
> I can't install DVDStyler because it doesn't run on 64-bit systems...

Just use the [64-bit version]("http://www.getdeb.net/app.php?name=DVDStyler") and the fix I linked to above.

It's not that the other programs are bad, it's just I find DVDStyler the simplest.

---

