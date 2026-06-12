---
title: "Something wrong with my ID tags"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by MarkCarras on 2008-01-06
Ok, so I am starting to do more stuff in Ubuntu then anything now.  When I rip cd's, the ID tags are messed up.  It shows that it has the album title, artist name, and everything when I right click on the properties of an MP3 file.  When I go to play that music on my smartphone though, it doesn't read them at all.

So I did some research and a program called EasyTag looks like it might be the solution, but the download section left me really confused about which version would work best in Ubuntu.

Anyone know which version of EasyTag works best with the latest version of Ubunu?  Or maybe a better solution?

---

### Post by nick_h on 2008-01-07
Just install it from the repositories:
```
sudo apt-get update
sudo apt-get install easytag
```

---

### Post by ron999 on 2008-01-07
Hi
Go with EasyTag.

There are two types of ID3 tag, two versions. One puts the tag on the back end of the file and the other puts it on the front end.
Some players only read ID3v1 and some only read ID3v2.

EasyTag allows you to apply both types to the files. (Look in Preferences...> ID3 Tag Setting - make sure that the boxes are ticked). So your smartphone and everything else should be happy.

The latest version of EasyTag that's in the repos (2.1) won't read MP4/AAC tags. That's why some people install the earlier version (1.99).


Read all about those tags if you like at Wikipedia here:-[http://en.wikipedia.org/wiki/ID3]("http://en.wikipedia.org/wiki/ID3")
:guitar:

---

### Post by MarkCarras on 2008-01-08
Thanks for trying to help guys.  I still can't get these things to read.  

The program was easy to install.  Made sure both boxes were checked in the preferences.  Still doesn't read them when I transfer them to my pocket pc. This phone has never given me this problem before, so I'm not sure what is causing this.  

Thanks for trying though. I do appreciate it.

---

