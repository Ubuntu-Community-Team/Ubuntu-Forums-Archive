---
title: "Pulseaudio missing from libraries."
date: 2017-02-05
forum: Multimedia Software
---

### Post by lammert-nijhof on 2017-02-05
This week I had some problem with audio. Trying to solve it I wanted to re-install pulseaudio. I first used "sudo apt-get remove pulseaudio" and that worked as expected. Afterwards I wanted to install pulseaudio again, so I used: "sudo apt-get install pulseaudio", but got the following very unexpected messages:
 -----------------------------------
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package pulseaudio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source


Package 'pulseaudio' has no installation candidate
----------------------------------
 
The missing package 'pulseaudio' and others depending on it, creates a lot of other problems for me. E.g. I can't install e.g. Kazam, a screen recorder. So somebody knows how to repair pulseaudio?

---

### Post by Perfect Storm on 2017-02-05
Have you changed something in your sourcelist also did you run sudo apt-get update first.

Check if all is set in 'Software & Updates'.

---

### Post by lammert-nijhof on 2017-02-05
Reading your comment I thought" "I'm not that stupid, I wrote OS software since 1969". But since I knew, I deleted some PPAs recently in the "Other Software" tab, I decided to have a look. You were right the main Ubuntu libraries were unchecked. Which proves again "ratio" beats "own believes". I marked them again; reinstalled pulseaudio and a ton of old updates 220 MB in total. I'm sure I did not uncheck that main library. It leaves me with two possibilities, I did it accidentally in the move of the mouse or I have an intruder. I did see in my Conky list of connection some 'ro' web sites, I will check those sites somewhat more often. Some weeks ago I checked my security and found incoming "open", which I changed to "reject" now. Thanks for the help, sometimes you need another with a fresh look.

---

