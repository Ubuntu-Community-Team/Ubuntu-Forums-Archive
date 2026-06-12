---
title: "Vlc wont play dvd"
date: 2017-12-14
forum: Multimedia Software
---

### Post by chancuu on 2017-12-14
so i've read like every forum on this and i can not get it to work. i've installed all the libdvd stuff i need, the libdvd-pkg and also ubuntu restricted extras. i've done everything i can think of. i have 16.04, it's a fresh install. about a month ago, it worked just fine. didnt try to watch anythign for a while, and now it wont work. i'm pretty good with linux, but not good enough to figure all this out, so if someone could please help me figure this out. my laptop reads my dvd, but vlc just wont play it. so any help would be great.

---

### Post by shantiq on 2017-12-15
if you have indeed installed  ```
sudo apt-get install libdvd-pkg
```    i do not know but ...

[ here at n°3 it says]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Decryption errors If you've installed libdvdcss2 as described above, it should Just Work. However, I had to ```
chmod 660 /dev/sr0; chgrp cdrom /dev/sr0
``` (replace with the path to your dvd drive) in order to get videos to play.    ....maybe try that




I know you have checked forums   maybe go through all of these too ...   see it any of these swing it


&#9679; and I must ask this because it has happened to me often with VLC it automutes :]  on start   ....
&#9679;[ and also]("https://help.ubuntu.com/stable/ubuntu-help/video-dvd.html")
&#9679; and a few more tricks [URL="https://askubuntu.com/questions/505684/vlc-wont-play-dvd-movies"]here  


[/URL]Please say if any of these work

---

### Post by chancuu on 2017-12-15
Thanks for the reply. I'm not sure what i did. I did the same thing i tried like 100 times, but for some reason it worked today. My dvds play just fine now. Thanks for the help, I read your links and did what it said, was the same I did before like i said but maybe there was one difference that i didn't notice. This time i'm not gonna go crazy and try to upgrade to a non LTS haha. All my stuff works how i want it and how it should, so i'm gonna be patient and wait for LTS release so i don't have to do a fresh install again and go through this again.

---

### Post by shantiq on 2017-12-16
yea chancuu   that is my experience too. First 2 or 3 years I would update to all the latest ;   nowadays I stay in the safety of the LTS since it it nice when things just work :]   
Also the "I did this 25 times and the 26th it worked and I did not change anything"  will always amaze me as it happens time and time again .   Do we change anything without knowing? Is there a ghost in the machine?    I do not know but it is one of the wondrous and mildly scary things which happen in this supposedly totally logical realm ...
Anyway good it works VLC still a great video player although these days I personally only use one >> [*MPV*]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")   as so stable and plays *everything* and use VLC [as a radio]("https://ubuntuforums.org/showthread.php?t=1774325") :]

---

