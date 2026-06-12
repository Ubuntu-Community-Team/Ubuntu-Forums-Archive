---
title: "Jack beat"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by walsh416 on 2008-03-10
I dowloaded jack beat recently but everytime I try to open it up, I get the same pop-up error message:

Unable to get on air. Is the JACK server up ?

I was wondering if anyone could help me with this problem of mine.:confused:

---

### Post by kapello on 2008-03-11
You need the program qjackctl (aka 'the jack server' ) installed and running, in order to run jackbeat, and also many other 'jack' audio programs.

The jack server kinda co-ordinates the sound connections for all these other programs that rely on it. 

so do 

sudo-apt get install qjackctl

and once it's installed run it - either find under programs menu or type in terminal

qjackctl &

It must be running *before* you start Jack Beat. You may well need to adjust the settings in qjackctl also - here's a screenshot from another user on these forums of some typical settings, though you may need to adjust them for your machine: [http://ubuntuforums.org/attachment.php?attachmentid=61637&d=1204700049](http://ubuntuforums.org/attachment.php?attachmentid=61637&d=1204700049)

---

