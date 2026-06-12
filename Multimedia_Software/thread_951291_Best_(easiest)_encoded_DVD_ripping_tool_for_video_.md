---
title: "Best (easiest) encoded DVD ripping tool for video noob??"
date: 2008-10-18
forum: Multimedia Software
---

### Post by swoody on 2008-10-18
I'm wanting to rip my encoded DVDs to my computer, but I don't like having a billion settings to worry about getting right. I've tried dvdrip, but that just has way too many settings on it, and is not that simplistic to a multimedia noob. 

I just want to be able to pop in a DVD, open a program, click on Rip, and have a copy of the entire disc made into a single file I can then play on my computer or burn to a blank disc. I'd like something where the movie and sound quality will be as good as they were on the original disc, and I don't mind it taking longer to do so. Hopefully this isn't asking a lot, but I know you guys can help me out! :D Any and all advice is greatly appreciated. Thanks in advance!

Woody

---

### Post by theirishfozz on 2008-10-18
I would suggest installing dvd decrypter and dvd shrink on wine. You can use dvd decrypter to rip to iso, and then dvd shrink to convert the iso (reduce sizes etc) before reburning with dvd decrypter.

---

### Post by swoody on 2008-10-18
I heard that the rippers/burners running on Wine are a lot slower than linux ones; have you noticed that at all? Also, is this just to burn to other discs? Or can you have the output of dvd shrink be a file that you can play on your computer?

---

### Post by fenian on 2008-10-18
k9copy you can install it from the terminal with...

> sudo apt-get install k9copy

A guide on how to use it is [here]("http://www.dvd-guides.com/content/view/213/59/")

---

### Post by swoody on 2008-10-18
Thanks :) K9 seems pretty simple. I'm trying it out right now, and we'll see how my first try turns out :D

---

### Post by swoody on 2008-10-18
Well, now I'm not getting such good results. VLC, k9copy, and dvdrip are all freezing up or just not doing anything :(

---

### Post by Zack McCool on 2008-10-18
k9copy and dvd::rip are the 2 best, IMO.

```

sudo apt-get install k9copy dvdrip subtitleripper rar mjpegtools xvid4conf

```

Try them both.  dvd::rip also needs helper apps for certain things, which is why all those others are listed at the end...

---

### Post by theirishfozz on 2008-10-19
Oh dear.

Well I've been using dvd decrypter and dvd shrink. Haven't had any problems, doesnt seem slow at all, perfect results. I'm also using qdvdauthor and ffmpeg to convert from pal to ntsc which can do the same thing as the first two apps but is a lot more complicated to install and configure. I'll certainly look into k9copy and dvd rip. Can that combo break encryption and reduce image size? What about pal->ntsc?

---

