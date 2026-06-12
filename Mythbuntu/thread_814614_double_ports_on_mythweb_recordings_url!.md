---
title: "double ports on mythweb recordings url!"
date: 2008-05-31
forum: Mythbuntu
---

### Post by OldGaf on 2008-05-31
Hi,

Another mythweb question. :confused:

When I look at the recorded page, I see some thumb nails and some are not found. THe recordings with no thumb nails have a "B" for a file size. Also, on all recordings, if I hover the mouse over the download link, I see there are two ports listed......  [http://xx.xx.xx.xx:81:80/mythweb/pl/stream/1014/1212278400](http://xx.xx.xx.xx:81:80/mythweb/pl/stream/1014/1212278400)

I have apache2 setup on port 81. If I copy and paste the above url and remove the :80, the file is accessable. 

I have no problem streaming my music from the same box......

1) Is there another port setting I need to change?
2) What is up  with the missing Thumbs and the "B" file size?

BTW - I am using recording groups on two hard drives..... I have another thread on that.

---

### Post by OldGaf on 2008-07-03
No one?

---

### Post by jzrlost on 2008-10-31
did you ever get this fixed...I am having the same issue with a new server installed last week.

---

### Post by ian dobson on 2008-11-02
Hi,

Sounds like an apache configuration problem. Are you using virtual hosts in apache and are they configured correctly?

I'll try this myself maybe today when I get the time.

Regards
Ian Dobson

---

### Post by ian dobson on 2008-11-02
Hi,

Just tried it myself (with port 8000) on my working system and I'm able to repeat the problem.

I'll have a quick look in the code to see if I see whats wrong.

EDIT: Maybe you'll find something usefull here:- [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=730054](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=730054)
Regards
Ian Dobson

---

### Post by jzrlost on 2008-11-03
Good to see you can recreate the issue.  My install is stock Mythbuntu which yes does setup Virtual hosts, but the config looks pretty standard for Apache2.


If I run the Mythweb on standard port 80 everything works fine.  My guess is the Mythweb page code is automatically inputing :80 for some reason.  Just my guess.

---

### Post by jzrlost on 2009-01-29
ian,
   Any luck on this issue?

thx josh

---

### Post by ian dobson on 2009-01-29
Hi,

No, I had a quick look in the code and didn't find what could be causing it.

Maybe it would be possible to use mod_rewrite to rewrite the urls outputted by mythweb.

I've just tested mythweb again with port 8000 and it seems to work for me, I don't think I've changed anything (apart from upgrading to 0.21).
 
Regards
Ian Dobson

---

