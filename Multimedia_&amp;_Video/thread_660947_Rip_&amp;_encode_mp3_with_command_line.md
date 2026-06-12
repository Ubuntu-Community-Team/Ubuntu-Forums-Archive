---
title: "Rip &amp; encode mp3 with command line"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by PaulVDV on 2008-01-07
Hi,

I would like to automate ripping CD's and encoding them to MP3 (with lame).
I'm on Ubuntu 7.10 with lame and gstreamer installed.

What command line (or script) can I use ?

Thanks in advance,
-Paul

---

### Post by nick_h on 2008-01-07
Have a look at abcde.  It is in the repositories:
```
sudo apt-get install abcde
```

---

### Post by mdebusk on 2008-01-07
> **nick_h said:**
> Have a look at abcde.  It is in the repositories

Here's [a nice abcde setup script]("http://www.andrews-corner.org/abcde.html") from Andrew Strong.

---

### Post by PaulVDV on 2008-01-08
This looks indeed very promising; Will give it a try.

Any idea where I can find more info on mp3 tagging ? Looks to be so many versions that all not mp3 players understand. It's very confusing.

Thanks,
-Paul

---

### Post by nick_h on 2008-01-08
For tagging, have a look at easytag.  It is also in the repositories:
```
sudo apt-get install easytag
```

---

### Post by andrew.46 on 2008-01-19
Hi,

> **mdebusk said:**
> Here's [a nice abcde setup script]("http://www.andrews-corner.org/abcde.html") from Andrew Strong.

It warms my heart a little to see my pages being mentioned :-)

       Andrew

---

### Post by PaulVDV on 2008-01-20
Hi,

I finally found some time to work with the "abcde" tool and it is just ... wonderful.

One last question do, is it possible to retrieve automatically from the cddb the album art cover ?

Thanks.

---

### Post by thecrwth on 2008-01-21
I vote abcde as well.  Even some basic coding knowledge I was able to get it to do roughly what I want.  I just need to brush up a bit on my coding.  Andrew's script gives a nice explanation of the options and the actual function of his script.  Yay Andrew.

---

### Post by mdebusk on 2008-01-21
> **andrew.46 said:**
> It warms my heart a little to see my pages being mentioned :-)

If you do good work, people talk about you. :)

---

