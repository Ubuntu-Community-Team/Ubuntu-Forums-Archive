---
title: "Enna Media Center~ ... is Fantastic! :D"
date: 2010-05-20
forum: Multimedia Software
---

### Post by Rasa1111 on 2010-05-20
Hey all, 

I recently stumbled on "Enna Media Center" in Ubuntu software center, 
and it is great! 

 I was using Moovida before that, mostly just for movies/videos...
and I really liked Moovida~  but after finding and using Enna....
I am just amazed at this lil piece of software!  lol

 Ive attached a few screenshots of it if anyone finds it of interest..

Moovida worked well, but it's 'response time' was rather "slow" compared to this. 
This is very quick with nice fluid motion, very nice on the eyes, and works great!!
 I am impressed! 

 Deep bows to the creators!  :KS  +11
<3<3<3

 Rasa

---

### Post by xavier_ex on 2010-05-21
looks really cool, but it can only browse your home folder, and what if my videos are not placed in my home folder?
and also there's nothing in configuration yet, like I can't change the temperature unit used in weather reporting...
but anyway, this is a nice looking app after all!! hope it becomes better~!

---

### Post by Rasa1111 on 2010-05-21
> **xavier_ex said:**
> looks really cool, but it can only browse your home folder, and what if my videos are not placed in my home folder?
and also there's nothing in configuration yet, like I can't change the temperature unit used in weather reporting...
but anyway, this is a nice looking app after all!! hope it becomes better~!


 hi xavier, 

 I can browse anywhere to find any media with it...
Im not quite sure what you mean?

 I just attached my external drive.. [Seagate]
and it now shows in the menu. 

 I can go to any folder~ home, videos, external device, etc.

Im not sure on you weather Q. yet though..

---

### Post by Rasa1111 on 2010-05-21
Quick note:

The only thing I can find that I "dont like" is no independent volume control. 
But I like it [Enna] soo much Ill just deal without it.
there are other places to control volume.  lol :)

---

### Post by JedMeister on 2010-08-12
> **xavier_ex said:**
> looks really cool, but it can only browse your home folder, and what if my videos are not placed in my home folder?
and also there's nothing in configuration yet, like I can't change the temperature unit used in weather reporting...
but anyway, this is a nice looking app after all!! hope it becomes better~!
I'm with xavier_ex, at least in part. I can browse places other than home fine. From what I can gather you can change default paths too (in the config file: ~/.enna/enna.cfg)

What has me stumped is changing temp to Celsius. It supposedly detects it automatically, but it came with location set to New York and in degrees F. I have changed it to my city in Australia which seems to be working fine but still displays in F - not C! I did lots of searching and came across an Enna bug report about it [here]("http://enna.geexbox.org/trac/ticket/28") (on the Geexbox bug tracker) but it was supposedly fixed 7 mths ago. It states there that you have to add unit=C (or F depending on what you want) to the enna.conf but that has made no difference. Anyone got any ideas?

---

### Post by mxb on 2010-09-16
I've just stumbled across enna as well.  I was unable to browse anywhere other than the home directory by default. I added a symlink to my media drive and was able to browse & play that way.  So far I haven't been able to figure out how to add to the media library, or the correct syntax for the directory locations in enna.cfg  Either I haven't deciphered this correctly, or enna just ignores changes. eg  ```
path_video=file:///path/to/Videos,Videos,icon/favorite
```  I tried:  ```
path_video=file:///media/video
```  and  ```
path_video=file:/media/video
```    No joy.    Also, X locks up after the screensaver kicks in with enna running. :D  Any hints or tips on configuring enna will be appreciated!

---

### Post by AAM on 2010-11-20
Instead of:

[INDENT]path_video=file:/media/video[/INDENT]

perhaps you should try:

[INDENT]path_video=file://media/video[/INDENT]

also

I can't install from Software Centre or Synaptic on Meerkat, lots of unresolved dependencies.[/FONT]

---

### Post by Rasa1111 on 2010-11-21
> also

I can't install from Software Centre or Synaptic on Meerkat, lots of unresolved dependencies.

 Same here~
Ive yet to be able to install enna in ubuntu 10.10
Ive tried like 3 different times now,
all failures. lol  :/

---

### Post by abumaia on 2010-12-22
I think you need to add geexbox's repository to your sources to get these dependencies, however they come with a warning of being unauthenticated.  I'm still looking to figure out how to authenticate them before I proceed with installation.

---

### Post by seragx99 on 2012-06-26
I'm currently installing it from Synaptic on Precise Pangolin, even though on enna's home page it says  you have to manually add the repository. I found it on Synaptic with no problem. Let's see how it turns :popcorn:

---

### Post by rubylaser on 2012-06-26
This is a very old thread. Enna hasn't been updated since November of 2010.  Personally, I use [XBMC]("http://xbmc.org/download/") at home on my Linux boxes, and it works fantastically.

---

