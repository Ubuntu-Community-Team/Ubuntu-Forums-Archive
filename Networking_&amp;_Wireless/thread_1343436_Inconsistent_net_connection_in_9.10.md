---
title: "Inconsistent net connection in 9.10"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Vektram on 2009-12-01
I've got a Dell Inspiron 1501 laptop with XP & Ubuntu installed. I connect to a wireless network and get my internet connection through that. I have the Broadcom proprietary drivers for my wireless card installed and am able to connect to (and use) my wireless network perfectly.

A couple of days ago, I upgraded from Ubuntu 9.04 to 9.10 and my internet connection started acting strangely. It seems as though I simply cannot connect to particular servers. As an example, if I do a Google search for "ubuntu", I can follow the link to ubuntu.com and navigate around that site but following the link to ubuntuforums.org does, well, nothing - I stay on the Google search result page.

I'm not sure if the sites this problem is affecting change, although I initially couldn't access google.com and now am able to. When upgrading, there are certain repositories I cannot connect to either - when the upgrade manager tries to connect to these repositories my network activity goes down to 0 bytes/second for a long time until (presumably) the upgrade manager stops trying and goes on to the next one.

This problem is not isolated to one or two sites - the majority of sites that I try to reach give me the same problem. Note, as well, that I can navigate around on one site (i.e. ubuntu.com) while simultaneously being unable to connect to another (ubuntuforums.org).

As I said, I didn't get any issues with my wireless or internet connection when using 9.04, and I'm not having any issues with my XP installation, so I figure the problem is something to do with 9.10.

Any advice?

I apologise if this is in the wrong section, though Networking & Wireless looked to be the most relevant. I also apologise if this problem's been resolved already, I looked around for a solution but didn't really know what I was looking for.

I am, of course, happy to provide any info that I've left out of this post - I didn't know what would be required.

---

### Post by Vektram on 2009-12-06
No replies? Not looking for a fix necessarily, just some advice on whether this is a bug, whether it's my fault, whatever.

Cheers.

---

### Post by coffeeaddict22 on 2009-12-06
Hi,
Sounds like a network problem. There's a nice article [here in Linux journal]("http://www.linuxjournal.com/content/troubleshooting-network-problems")  from 9 months ago that will give you some ideas to start with.  Post back if you need more help.

---

### Post by Vektram on 2009-12-06
Thanks for the reply.

I did some troubleshooting according to the instructions in that article.
 - I was able to ping my default gateway successfully (avg. time of 3.19ms).
 - I was able to access google.com and ubuntu.com in my browser perfectly, and was (obviously) able to ping them as well.
 - Attempting to come to ubuntuforums.org gave me the original issue again (after I tested google.com and ubuntu.com).
 - Pinging ubuntuforums.org gave me:
```
vektram@laptop:~$ ping ubuntuforums.org
connect: invalid argument
```
Around half a minute later, though, I was able to access ubuntuforums.org in the browser, and pinging it (using the exact same command) worked.

From this, I deduce that I have a "bona fide networking problem, which needs to be reported." Not really sure what to do from here, though...

---

### Post by coffeeaddict22 on 2009-12-06
what's the output of ```
sudo iwlist scan
``` if there's other networks sitting on the same frequency, that'd explain things nicely.

---

