---
title: "Help Cant Play MP3 in totemplayer"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by Maccabee on 2005-11-09
Hi 
      Anyone plz tell me how to play mp3 in ubuntu? in totem or in anyother player

---

### Post by sciurus on 2005-11-09
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse

Hopefully you can play almost anything after that.

---

### Post by Todd_Z on 2005-11-09
[B] sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse
[/B]
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candid


What am I doing wrong?

---

### Post by Todd_Z on 2005-11-09
I figured out what was the problem.  I needed to add all repositories in synaptic.

---

### Post by the_lobotomy_kid on 2005-11-10
[QUOTE=Todd_Z]I figured out what was the problem.  I needed to add all repositories in synaptic.[/QUOTE]

Hi - I'm having trouble with is, trying to get totemplayer to deal with MP3s.  I typed in the solution in the above post and got the same message that you quoted.  Can you explain your solution to me please?  I'm a complete newbie.

Thanks in advance,
Martin.

---

### Post by 23meg on 2005-11-10
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

