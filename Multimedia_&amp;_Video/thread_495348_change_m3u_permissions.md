---
title: "change m3u permissions"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by seraph47 on 2007-07-07
I am using XMMS as my media player, and would like to 2x click on m3u files to get them to load in XMMS. The problem is that I am getting a pop-up window asking if i want to run the file. I figured that I need to change the permissions of m3u files so that they are NOT executable, but I need to be logged in as root. How would I be able to do this from the command line?

When I was on irc chat, someone mentioned using the command " find ./ -type f -iname *.m3u -exec chmod -644 '{}' \; " but it wasnt working for me. Any ideas? Thanks

---

### Post by iAlta on 2007-07-15
you just need to change the default program to open the m3u with... I think.

---

