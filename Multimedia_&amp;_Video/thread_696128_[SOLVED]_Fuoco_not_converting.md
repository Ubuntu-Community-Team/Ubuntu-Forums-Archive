---
title: "[SOLVED] Fuoco not converting"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2008-02-13
As the title states, I've had the same problem with ConvertIT - I learned that ConvertIT project was dropped and replaced with this -where I have the same problem.

I put a file in, press convert - it flashes the progress screen, says "done" - nothing happened - but it thinks it was successful.  

It's happened on a few files of the same grouping, and worked fine for others.

No info or error log as in Fuoco's eyes it is not an error.

I ran into this problem once before and it was simply b/c it didn't have an extension at the end - but these do, some of them convert fine -  others not - same name format, no spaces, no special chars, etc.

Any advice?

I ran into the same EXACT problem with ConvertIT:
[http://ubuntuforums.org/showthread.php?t=686642](http://ubuntuforums.org/showthread.php?t=686642)

---

### Post by Syndacate on 2008-02-14
*bump, anybody convert video here??

---

### Post by Syndacate on 2008-02-15
*bump

I know I'm not the first guy here...

---

### Post by Syndacate on 2008-02-17
> **Syndacate said:**
> *bump

I know I'm not the first guy here...

I figured it out - don't try to convert files with an ampersand (&) in them, it will confuse the xterm when you go to convert and re-direct it to look for the file under a different filename - rename it or it wont' convert.

---

