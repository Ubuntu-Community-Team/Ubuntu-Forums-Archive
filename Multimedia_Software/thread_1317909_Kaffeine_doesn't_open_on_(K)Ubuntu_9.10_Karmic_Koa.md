---
title: "Kaffeine doesn't open on (K)Ubuntu 9.10 Karmic Koala"
date: 2009-11-07
forum: Multimedia Software
---

### Post by kuric on 2009-11-07
Hello, I don't know why, but the last version of Kaffeine available from Ubuntu repositories (1.0-pre2 released) stopped working here, that happened in 2 computers at the same time. Maybe a conflict or something with another application, I don't know...

It doesn't even open! No main window, no output, no errors on the terminal, nothing. It just hangs on startup and the CPU usage goes to 100% in a few seconds.

But here's how I've solved it temporarily. I've uninstalled the current version and went to this website: 

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

And then searched for a previous version of Kaffeine... 0.8.7-1 did the job! 

Anyone else had the same issue? If so, how did you solve it? What's going on?

---

### Post by sider on 2010-02-01
Hello,

I had the same problem. The solution for me was to delete kaffeine (aptitude purge kaffeine) and to delete the directory ~/.kde/share/apps/kaffeine and the file ~/.kde/share/config/kaffeinerc

After the reinstall of kaffeine, all was OK.
Hope it will help you

---

