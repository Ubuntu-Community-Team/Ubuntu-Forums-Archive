---
title: "trouble playing some videos"
date: 2008-04-28
forum: Multimedia Software
---

### Post by geovino on 2008-04-28
Since installing Hardy, I've noticed that many of the ads and videos in firefox are in gray until you click on them. for instance the Hulu site can't play the videos. Also I can't use the Election Dashboard in Yahoo
[http://news.yahoo.com/election/2008/dashboard;_ylt=AlQVeo8rbaQJxlWZlLdfLbxLzZB4](http://news.yahoo.com/election/2008/dashboard;_ylt=AlQVeo8rbaQJxlWZlLdfLbxLzZB4)

 what plugin is needed to correct this problem?

---

### Post by Bablefish on 2008-04-28
Just checked it it's Flash; Have you the lastest version installed? I had the same problem.

---

### Post by geovino on 2008-04-28
> **Bablefish said:**
> Just checked it it's Flash; Have you the lastest version installed? I had the same problem.

I have flash... where do I get the latest version? 

... i found it:

run this command:
sudo apt-get purge flashplugin-nonfree gnash gnash-common swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

it's from this page:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=install+latest+flash](http://ubuntuforums.org/showthread.php?t=766683&highlight=install+latest+flash)

It all works now :)
[Solved]

---

