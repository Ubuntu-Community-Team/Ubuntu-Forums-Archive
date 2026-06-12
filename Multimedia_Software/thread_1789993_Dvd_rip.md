---
title: "Dvd rip"
date: 2011-06-24
forum: Multimedia Software
---

### Post by linux_trojan on 2011-06-24
When I was using 10.04 I had no problems viewing and ripping DVDs.  Now that I am using 11.04, I cant view nor rip anything.  Would appreciate any suggestions

---

### Post by nomko on 2011-06-24
Tell us first what programs you're using. And how did you installed 11.04?

---

### Post by linux_trojan on 2011-06-24
I tried to do an internet upgrade but it muffed up, so I finally had to do a clean install but only on the / partition.  I had homes, and other stuff on different partitions.  So only / was reformated

I am using acidrip, dvdrip, xine, k9copy, open movie player, nothing works

---

### Post by nomko on 2011-06-24
When you have your /home on a different partition, make sure you also remove the hidden files => Nautilus > Ctrl=H > remove all files and folders which starts with a . (dot) like .mozilla or .xine. Those folders may contain configuration files which can be out of dated for your new 11.04 installation.


For movieplayer you can use Vlc. This program doesn't need any extra plugins and plays almost everything.

---

### Post by linux_trojan on 2011-06-24
Still not working, please help

---

### Post by linux_trojan on 2011-06-24
The only DOT file I deleted was Xine.  Coming to think of it, if I deleted all the DOT files then the point of having /homes on a different partition really doesnt make sense.

In anycase, I discovered my own solution.  I forgot about Medibuntu. 

For anyone thats interested, check this out.

[http://www.youtube.com/watch?v=hOD4qcWZ9Hc](http://www.youtube.com/watch?v=hOD4qcWZ9Hc)

---

### Post by nomko on 2011-06-24
> **linux_trojan said:**
>   Coming to think of it, if I deleted all the DOT files then the point of having /homes on a different partition really doesnt make sense.

Exactly!

Nice to see you found a solution on your own!

---

### Post by handy on 2011-06-24
> **nomko said:**
> Exactly!

Nice to see you found a solution on your own!

There are some very valid reasons for having a separate /home partition, that have nothing to do with upgrading or changing distros.

/home gives you more data security re. & the ability to backup that partition using Clonezilla (for example) without having to backup your / partition. There are other good reasons to keep a separate /home partition as well.

---

### Post by Duncan Williams on 2011-06-25
It took me awhile to work out how to watch a dvd until I found this link:
To setup dvd playing:
[http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/](http://www.dreamingisdigital.com/2011/05/13/how-to-play-dvds-in-ubuntu-11-04/)

---

