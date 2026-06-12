---
title: "Ubuntu 10.4 won't reconise some mp3s"
date: 2011-05-30
forum: Multimedia Software
---

### Post by 2steps on 2011-05-30
[SIZE=2]I have an external hard drive with most of my music on either mp3s or ripped from cds. I have imported the folders into gmusicbrowser but it doesn't show up some of the files. I have also tried rhythmbox and banshee media player but they all have the same problem. The files play fine on my other pc runnin xp pro so they are fine. Also some folders have nothing in under ubuntu but have mp3 files in (as they should) under xp. Can anyone help? [/SIZE]

---

### Post by 3xp10r3r|X13 on 2011-05-30
hello there,
your files are fine, you're right, but banshee etc. is missing a certain mp3 plugin. So I'll just assume that you are able to play wav files but not mp3s. If you try to play an mp3 file with banshee or amarok, it should offer you to install the missing plugin.

however, if it doesn't, this might be helpful or rather should be helpful:
[http://packages.ubuntu.com/dapper/vdr-plugin-mp3](http://packages.ubuntu.com/dapper/vdr-plugin-mp3)

edit: in the top right corner, you are able to select the needed ubuntu version - sry for dapper :D

hope this helped

---

### Post by 2steps on 2011-05-30
[SIZE=2]Thank you. The rest of my mp3s are working fine, it's justs ome having the problem. Will give that a go[/SIZE]

---

### Post by Chronon on 2011-05-30
That link will take you to a package for Dapper Drake.  Since you're running Lucid you probably don't want this version.  Search for this plugin in your package manager instead.  Also, after reading the description it seems to just be a plugin for a Video Disk Recorder application, so probably not what you want.

I usually just install ubuntu-restricted-extras, which should install codecs for mp3 and a few others.

---

### Post by 3xp10r3r|X13 on 2011-05-30
sry, you're rigth --> mixed up the versions:

[http://packages.ubuntu.com/natty/vdr-plugin-mp3](http://packages.ubuntu.com/natty/vdr-plugin-mp3)

However, in the top right corner, you are able to select the wanted ubuntu version.

--> but chronon is right, installing the restricted extras is probably the easiest way to go

---

### Post by 2steps on 2011-05-31
[SIZE=2]Still not working :( Some of what are missing where ripped from cds, could that be a problem?[/SIZE]

---

### Post by 3xp10r3r|X13 on 2011-06-01
it shouldn't really be a problem...but we are talking about wav files aren't we, not about mp3s?

---

### Post by Chronon on 2011-06-01
Did you install ubuntu-restricted-extras?

Do any mp3s play properly?  Is there any common feature to the files that aren't working?

---

### Post by ufugu on 2011-06-01
I have the same issue.  95% of my mp3 files play fine, no problem, but some files just don't play at all.

They won't play on my Android device either.  They play fine in iTunes on Windows 7 at work (blech).

I have re-encoded them to ogg as a workaround, but I'm still curious as to what happened.

---

### Post by Chronon on 2011-06-01
Maybe something about the metadata is causing problems?  Will the tracks play if you strip all metadata from them?

---

