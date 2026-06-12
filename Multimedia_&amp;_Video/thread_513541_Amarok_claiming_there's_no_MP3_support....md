---
title: "Amarok claiming there's no MP3 support..."
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by Izobalax on 2007-07-30
...when there blatantly IS!

I have Ubuntu Feisty installed on the system in my sig. I have KDE installed, which I'm currently using. I wish to use AmaroK. Now, ALL my other audio/multimedia apps (mainly GNOME apps, been mostly using Banshee) have been working FINE... MP3 support, codecs, EVERYTHING. 

However, when I ask AmaroK to play an MP3 it brings up a little pop-up box claiming that there's no MP3 support and would I like to install some... when I select OK AmaroK promptly permanently FREEZES. I have to kill it in the System Monitor. 

What am I doing wrong, O' Denizens of Ubuntu?

/izo

---

### Post by hardyn on 2007-07-30
install libxine-extracodecs, through synaptic, or the KDE alternative (name escapes me)

---

### Post by Izobalax on 2007-07-30
> **hardyn said:**
> install libxine-extracodecs, through synaptic, or the KDE alternative (name escapes me)
That worked. You're a star!

/izo

---

### Post by scxtt on 2007-07-30
just in case you're wondering why ... gnome generally uses gstreamer by default, whereas amarok can use both xine and gstreamer (possibly something else too) ... so if gstreamer was playing mp3s, you probably could have gotten amarok playing them too if it was set to use gstreamer ...

---

### Post by Izobalax on 2007-07-31
> **scxtt said:**
> just in case you're wondering why ... gnome generally uses gstreamer by default, whereas amarok can use both xine and gstreamer (possibly something else too) ... so if gstreamer was playing mp3s, you probably could have gotten amarok playing them too if it was set to use gstreamer ...
I see, I see. I'll remember that in future. 

/izo

---

### Post by Gadren on 2007-08-02
Just wanted to pop in and say thanks for the help! ^_^  I was having the same problem.

---

### Post by PetruM on 2007-08-05
Same here. I just made a fresh install of Kubuntu and apparently Amarok couldn't install mp3 support by itself. Thanks again! :)

---

### Post by kansei on 2007-08-05
> **PetruM said:**
> Same here. I just made a fresh install of Kubuntu and apparently Amarok couldn't install mp3 support by itself. Thanks again! :)

Because it's a closed-source, proprietary codec. It should never be installed by default, only if the user desires it.

---

### Post by Burbruee on 2007-08-08
Thanks, I was wondering the same; Why I could play MP3s in XMMS but not in Amarok.

---

### Post by ben55 on 2007-08-08
Just saying thanks . . .i was having the same problem. Its sorted now :D

---

### Post by DarwinsTheory on 2007-08-12
Thanks for the solution, was driving me nuts as well...

Matt

---

### Post by devilishlynice on 2007-08-12
Solved my problem too. =) I've been using ubuntu for a couple monthes now. great decision and I'm starting to figure things out =)

not a true noob anymore- I actually prefer the command line now

---

### Post by Zaff on 2007-11-20
Hey I have the same issue, I'm using Gutsy and it was wonrking perfectly fine until yesterday. I may have had some updates in the mean time. Anyway I tried everything you said and it still tells me that it has no MP3 support. Now I could use RythmBox b ut I really like Amarok and this is really annoying.
I only have one possible engine in the configuration dialog and it'sxine. Is there anyway to change it to gstreamer if that's where the problem comes from ?
Thanks for any help you can give me.

---

### Post by peacepipejv on 2007-11-20
Yay. thanks. Easy enough. Ubuntu is my best friend. Does what I ask and wants nothing in return, cept some attention.

---

### Post by Zaff on 2007-11-20
ok found the answer on this thread : [http://ubuntuforums.org/showthread.php?t=428576&page=3](http://ubuntuforums.org/showthread.php?t=428576&page=3)
Thanks anyway.

---

### Post by peacepipejv on 2007-11-21
Cept now Im having problems with AAC/MP4 support. I followed the AmaroK website threads with no success. Hmm. Either I have to solve this problem or change the files to MP3. I dont want to switch to another app just to play aac.

---

