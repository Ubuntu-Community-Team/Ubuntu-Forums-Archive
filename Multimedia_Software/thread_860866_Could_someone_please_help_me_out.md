---
title: "Could someone please help me out?"
date: 2008-07-16
forum: Multimedia Software
---

### Post by liekWTFmang on 2008-07-16
I'm having some issues with my speaker. No sound comes out when i just normally turn it on. Could someone please help me out?

---

### Post by coolaj86 on 2008-07-16
I had that problem myself. I was suffering more from lazy-man syndrome though. I went 3 months without sound and one day when cleaning I finally got behind my computer to find out that the plug had come loose.

If that isn't your problem too then we'll need some more info to help you. Did sound work on the liveCD? Did sound ever work for you? Does whatever you're trying to play actually play?

---

### Post by liekWTFmang on 2008-07-16
Well actually, I just switched to Ubuntu quite a while ago from Windows. So I'd just turn on the speakers like I did with Windows, but sound doesn't come out from the speakers. Would you have any idea what could be the problem?

---

### Post by vandorjw on 2008-07-16
In the top right corner of the screen there is a volume control thing, the thing that looks like a speaker. I hope your volume is just turned down, but it might say, "No Device".

There was one time when my sound didn't work, back when I used Ubuntu 7.10.
Then all I had to do was put this 
>  sudo apt-get install linux-backports-modules-generic
into the terminal. (Restart Needed After install is complete)

Applications -->Accesories --> Terminal

but before you do that, type >  alsamixer in the terminal.

Use the arrow keys to turn everything up, and test if sounds works then.
(press "esc" to exit alsamixer when you're done)

Cheers - CC7

---

### Post by liekWTFmang on 2008-07-16
Well I tried using alsamixer before, but nothing worked then, so I'll try out the first thing then :P Thanks for the help.

---

### Post by liekWTFmang on 2008-07-16
> sudo apt-get install linux-backports-modules-generic

Hm. That didn't work for me :/

---

