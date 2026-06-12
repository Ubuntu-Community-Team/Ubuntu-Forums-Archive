---
title: "am i the only one who can't get the vanilla kernel to work?"
date: 2006-04-11
forum: Multimedia &amp; Video
---

### Post by jmxhgyZN8wK7 on 2006-04-11
and i mean with a regular 32-bit computer and kernel.

[http://www.ubuntuforums.org/showthread.php?t=158275]("http://www.ubuntuforums.org/showthread.php?t=158275")

(sorry - i posted it under "ubuntu 5.10 support" before i found out that there was a forum dedicated entirely to ubuntustudio.org)

---

### Post by dolson on 2006-04-12
(Same reply posted in that thread.)

jmxhgyZN8wK7, don't listen to what they say.. The first reply is telling you how to install the kernel you already have, and they clearly didn't even read your post to understand what you are doing. Also, they don't appear to know what kernel-package is. Either that, or they prefer to not have their kernels packaged nicely into .deb packages... Either way, forget that response.

The second response does not tell you how to get a realtime-capable kernel installed, so ignore that as well.

The issue you are having is definitely with the patch you are trying to apply.

In your error message, you see two files drivers/net/skge.c and drivers/net/skge.h. One of these either got failed hunks while patching, or the patch added something unnecessary. This doesn't make sense to me, because if you followed the tutorial to the letter, then you should have the same kernel that I am running right now.

You can search for patch rejects with **find . -name "*.rej"** and it should show you a file or two. These contain parts of the patch that did not apply successfully. You'll have to fix them by hand, or, as I recommend, delete it all and try it over from scratch.

Someone in IRC once had a similar issue, and for some reason, the second time they tried, it worked. I don't know why.

---

### Post by jmxhgyZN8wK7 on 2006-04-13
hey, thanks!  THAT was the kind of answer i was looking for.

i've tried this several times (on completely fresh installations of ubuntu), though; the same thing has always happened.

i'm guessing it has something to do with apt-get dist-upgrade.  maybe when they wrote the tutorial, the things that you would get by doing dist-upgrade were slightly different from the things that you would get by doing it today...

---

### Post by zorlab on 2006-04-18
**jmxhgyZN8wK7**

Same exact error message here.....   did you do it over as sugested and have good results?   ~~>If so  what was meant by **dolson:** "delete it all,"  all what the load modules that took over an hour???
:-?

---

### Post by dolson on 2006-04-18
"delete it all" means to delete the source tree and try it fresh again. This has solved it for several people. I don't know what the reason is that Ingo's patch does not apply cleanly for some people.

---

### Post by daveZ on 2006-04-22
jmxhgyZN8wK7, I had the exact same problem you are having and I fixed it by following dolson's advice in this post:

[http://ubuntuforums.org/showthread.php?t=161915](http://ubuntuforums.org/showthread.php?t=161915)

Follow what I did there, recompile and hopefully you'll get through errorless.

~daveZ

---

