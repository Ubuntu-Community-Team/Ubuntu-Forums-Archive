---
title: "Amazonmp3 download tool and ubuntu 10.4 64 bit"
date: 2010-05-01
forum: Multimedia Software
---

### Post by bigpook on 2010-05-01
Using 64 bit 10.4 and have 2 problems.

The first was I couldn't get the amazonmp3 download tool to work.
It complained about missing/wrong libboost* libraries.

There may be a better way of fixing this, I have no idea, but what worked for me was this:

I had spare machine running 9.10 so I installed the amazonmp3 loader on it and did the getlibs to make it work.

Once done, I copied the /usr/lib32/libboost* files over to my 10.4 machine, ran getlibs /usr/bin/amazonmp3 and it went in clean.
It now works : )


My second problem that I am working is that gdesklets does not start. Still looking at that. If someone has a solution please post.

---

### Post by jbellessa87 on 2010-06-24
Good post.  I didn't have access to an older version but I stumbled across this page and thought it might be a good idea to post in case anyone else was in the same boat:
 [http://threebrothers.org/brendan/blog/amazon-mp3-downloader-on-64-bit-ubuntu-lucid-lynx/](http://threebrothers.org/brendan/blog/amazon-mp3-downloader-on-64-bit-ubuntu-lucid-lynx/).


As for the gdesklets, I'm not sure. Sorry. :-?

---

### Post by mdbarton on 2010-10-16
> **jbellessa87 said:**
> Good post.  I didn't have access to an older version but I stumbled across this page and thought it might be a good idea to post in case anyone else was in the same boat:
 [http://threebrothers.org/brendan/blog/amazon-mp3-downloader-on-64-bit-ubuntu-lucid-lynx/](http://threebrothers.org/brendan/blog/amazon-mp3-downloader-on-64-bit-ubuntu-lucid-lynx/).


Perfect - thank you.  I was going to use the Ubuntu One music store but Amazon are cheaper.

---

