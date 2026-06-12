---
title: "Internet connection cuts out for browsers if downloading files..."
date: 2012-07-23
forum: Multimedia Software
---

### Post by shantiq on 2012-07-23
I have found in the last few weeks that if i am downloading using say  Vuze and it goes over a certain speed my internet connection on browsers stop to work


this has never happened before



Also getting same when using get-iplayer and other downloaders


Anyone understands why this could be and how to remedy it


shan

---

### Post by sanderj on 2012-07-23
In Vuze, have you limited your **UPstream**? You should. To be safe, set your Vuze upstream limit to 10 kBps and test again.

HTH

---

### Post by shantiq on 2012-07-23
hi sanderj thanx for reply    do you mean this here?

[ATTACH]221678[/ATTACH]

---

### Post by sanderj on 2012-07-23
> **shantiq said:**
> hi sanderj thanx for reply    do you mean this here?

[ATTACH]221678[/ATTACH]

No, I mean the number at the top of that page, which is now 312 KB/s ... that's very much: 3.1 Mbps UPstream. 

Lower that number to 10 KB/S

---

### Post by jonnyboysmithy on 2012-07-23
10kB/sec? 
It doesn't have to be *that* slow. 

If you want torrenting to work (by giving back as much as you are using) 
YOU also have to upload to others. 
Uploading at 10kB/sec its going to take looong time for you to upload as much as you download.

If you limit the upload speed to 80% of your maximum it should be just fine.

---

### Post by shantiq on 2012-07-23
thanx for input guys

may i suggest we are barking up the wrong tree here

312kb/s   is a fine speed for upload on my system


ANYWAY this happens when i download and it shoots up to say 1MB/s  but the thing is
it never used to care even 2MB/s would not stop the Browsers from working


so the "fault" must be elsewhere

also happens with get-iplayer and youtube-dl  and it never ever did that say a month ago  [up to 2.8MB/s] 


so  something has changed and i do not see what it is



any other thoughts?

---

### Post by Grenage on 2012-07-23
If this is torrents, then what you are describing is classic router overload.  Most residential routers are rather lightweight, so many connections will cause them to bottom out and reject new connections (such web browsing sessions).

Drop your maximum connection count (globally, or per-torrent if you only allow 1-2 active in a queue), and find what your router can handle.  Multiple machines with NAT, plus hundreds of torrent threads = far too much for most home routers.

---

### Post by shantiq on 2012-07-23
again thanx for input    that feels like it might be to do with that


i have 48 in my upload half of vuze   but no more than say 10 will be going

and i have a maximum upload rate of 312kb/s


never more than say 2 or 3 downloads at any given time


but yes overall volume on the router probably where the kink is


hmmmmm     will have to think here

---

### Post by sanderj on 2012-07-23
> **shantiq said:**
> 

312kb/s   is a fine speed for upload on my system



How do you know? On what kind of connection are you? If you don't know, go to [http://speedtest.net/](http://speedtest.net/) and post back the results.

Oh: And you do know the difference between 312kb/s and 312 KB/s, don't you?

---

### Post by shantiq on 2012-07-23
took it as read they meant kb

> 312kb/s and 312 KB/s   so KB here is 3.12 MB/s ?


testing it if i put it on 20  it takes all my uploads to ridiculous low level

like 1kb per file    useless to the guys at the other end


are you sure KB  is not the same is kb here ?   just asking


PS my connection is 50MB Virgin

---

### Post by jonnyboysmithy on 2012-07-23
> **shantiq said:**
> took it as read they meant kb

   so KB here is 3.12 MB/s ?

are you sure KB  is not the same is kb here ?   just asking
8bits (small b) = 1Byte (capital B)

8kb/sec =1KB/sec
8Mb/sec = 1MB/sec

Also watch out for this one:
To quote wikipedia:
> A **megabit per second** (**Mbit/s**, **Mb/s**, or **Mbps**; not to be confused with **mbit/s** which means, ***milli*bit per second**)

Generally I just grab the calculator and either multiply or divide by eight. :)

---

### Post by shantiq on 2012-07-23
so 40 in that box becomes 320 kb/s  ?    :KS  which is about what i want

i shall try that see what it does



thanx guys:KS

---

### Post by jonnyboysmithy on 2012-07-23
Yes 40kB/sec should be 320kb/sec.

---

### Post by shantiq on 2012-07-24
ok have changed to 40KB/s   [and thank you for explanations on that]

and to test started up a get-iplayer download  and browsers stop to work


[ATTACH]221705[/ATTACH]


so as i suspected the reason for this is elsewhere

any more thoughts as to possible cause?

---

### Post by Grenage on 2012-07-24
> **shantiq said:**
> any more thoughts as to possible cause?

Have you tried reducing maximum global connections to 50?  Start low, and work upwards until you encounter problems.  Back in the day it was handy to have 500 connections, when the average speed was a 56k modem; these days, you rarely need many concurrent connections - you could get maxed out with just one.

---

### Post by shantiq on 2012-07-24
ok set to 50

---

