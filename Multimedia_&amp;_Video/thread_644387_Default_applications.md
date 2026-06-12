---
title: "Default applications?"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by Ertai87 on 2007-12-18
OK, so I installed Gutsy on my computer, but I'm a bit of a noob.  Right now my default program for video is Totem, but I want to use VLC.  How do I switch?  I tried doing System -> Preferences -> Preferred Applications, but that didn't go over well.  How do I do it?  Thanks.

---

### Post by jjalocha on 2007-12-18
One of the first things I usually do on a fresh Ubuntu installation is to install VLC and remove the default media players. ;)

You can use Synaptic for that.

Or you can right click your media files on your file-browser, choose "open with other application" and select VLC, making sure you have the "use as default" checked. (At least that's how it works with Thunar under Xubuntu.)

---

### Post by Ertai87 on 2007-12-18
I tried that but for some reason after Totem is uninstalled it still tries to run it.  I'm also trying to change the default player for DVDs and other autoplay media.

---

### Post by jjalocha on 2007-12-19
Have you tried the second method I described? It's quite annoying, but it works for me. You just have to change the default application once for each file/MIME type.

---

### Post by Ertai87 on 2007-12-19
That worked for video files (although the setting was under "properties", not "open with"...I was a bit confused last night cause I looked under "open with"), but it still doesn't work with autoplaying DVD movies.  I can go into VLC and say "play DVD", but I'd prefer if it was more convenient than that.  Any ideas?

---

### Post by jjalocha on 2007-12-19
Quick google for 'ubuntu autoplay cd OR dvd':

[http://ithacafreesoftware.org/forum/viewtopic.php?t=210](http://ithacafreesoftware.org/forum/viewtopic.php?t=210)
[http://ubuntuforums.org/showpost.php?p=3955819&postcount=3](http://ubuntuforums.org/showpost.php?p=3955819&postcount=3)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/818322.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/818322.html)

Hope this helps!

---

### Post by archivator on 2007-12-19
You need to go to Removable Drives and Media Preferences -> Multimedia and change the command to be executed. That being said, you will need to look up the correct parameters to pass to VLC.

---

### Post by Ertai87 on 2007-12-19
Awesome.  That last link had exactly what I was looking for.  Thanks!

---

### Post by kryth on 2008-01-02
OR you can right click ---->properties---->open with---->then choose default player.

---

