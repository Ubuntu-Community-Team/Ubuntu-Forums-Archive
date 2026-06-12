---
title: "can not play anything from firefox"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by broekskw on 2008-01-19
every time i try to play a video from a web site it will not play, using firefox in ubuntu,  did a search and did follow some other post with no luck

any suggestions ??

thanks

---

### Post by RomeReactor on 2008-01-19
Hi. What videos are you trying to play--Flash, avi, etc?

---

### Post by broekskw on 2008-01-19
when i go to youtube and try to watch a video, on the home page you see all the videos that people are watching right now all is see in each video is a blue screen??

must have to install something to make it work but not sure what??
:confused:

---

### Post by broekskw on 2008-01-19
how do i find what format it is, trying to watch the bucket list trailer 

take a look at my screen shot, just keep trying to load forever

---

### Post by RomeReactor on 2008-01-19
The **flashplugin-nonfree** is currently broken; you need to download [this fixed package]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"), close Firefox, and double click on the downloaded package to install; then open Firefox again and see if you can play the videos now. More information on the [bug here]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by broekskw on 2008-01-19
RomeReactor thanks will give it a try:popcorn:

will keep you updated

---

### Post by broekskw on 2008-01-19
ok downloaded file and restarted firefox but get the same thing, here is a screen show of youtube showing the blue movie screens:confused:

---

### Post by RomeReactor on 2008-01-20
Make sure you don't have Gnash installed, as it will conflict with Flash; close Firefox, then:
```
sudo aptitude remove --purge gnash gnash-common gnash-tools mozilla-plugin-gnash
```
Then open Firefox again and check if the videos play now.

---

### Post by broekskw on 2008-01-20
RomeReactor that command did it for me :popcorn: great and thanks for the help

this site rocks big time, :lolflag:

---

### Post by birofunk on 2008-01-20
hi im having a similar problem, i downloaded your flashplugin nonfree 

and got an error when i tried to install it:

Error: Wrong architecture 'i386'

---

### Post by RomeReactor on 2008-01-20
Hi. birofunk, for the 64-bit architecture download [this package]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466").

---

