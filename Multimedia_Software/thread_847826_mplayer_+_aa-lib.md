---
title: "mplayer + aa-lib"
date: 2008-07-02
forum: Multimedia Software
---

### Post by bodaciousllama on 2008-07-02
I'm having a problem with playing movies using mplayer redirected through aa-lib (if you don't know, this makes the movie look like ASCII art).

The problem is that when I simply invoke the combination with 
```
mplayer -vo aa escape.avi
```
the movie is not in the right aspect ratio, it seems to cut off the right 1/4 of the frame. Looking around on the internet, I found this command 
```
xterm -fn 5x7 -geometry 720x320 -e "mplayer -vo aa:driver=curses escape.avi"
```
which *seems* to have put the image in the correct aspect ratio. I say *seems* because now I can't watch the movie - the image flickers in on occasion, but for the most part the window stays black.

Can anyone help me?

Thanks

---

### Post by bodaciousllama on 2008-07-03
*le* bump

---

### Post by Altay_H on 2009-01-13
I'm having the exact same on both of my Ubuntu computers. Both are running Intrepid, and I can only see the left half of the video using aalib. When I don't specify a -vo, it plays correctly. Also, if I mess with any other settings or try to run it in a tty, I end up with just flickers of text and nothing I can make out.

---

### Post by itang sanjana on 2009-02-12
use suboptions *-monitorpixelaspect x.x* e.g.,
```
mplayer -vo aa -monitorpixelaspect 0.5 foo.ogv
```
HTH

---

### Post by Altay_H on 2009-02-18
> **itang sanjana said:**
> use suboptions *-monitorpixelaspect x.x* e.g.,
```
mplayer -vo aa -monitorpixelaspect 0.5 foo.ogv
```
HTH
That works in X, but it doesn't help viewing it in the virtual terminals. I'd like to be able to watch movies via SSH or in a tty. Do you know how to fix the flickering problem in the tty?

---

### Post by andrew.46 on 2009-02-20
Hi,

Can I just say that is one crazy -vo :-).

Andrew

---

### Post by Altay_H on 2009-02-21
> **andrew.46 said:**
> Can I just say that is one crazy -vo
Indeed. Unfortunately though, it's not working for me... :(

---

### Post by relztes on 2009-02-24
I'm having problems as well. If I happen to come across a solution, I'll post it here.

---

### Post by relztes on 2009-02-24
Well, I know this isn't a true solution, but aaxine from the package xine-console does the same thing and works fine for me. Also, try cacaxine from the same package for color output (just like mplayer -vo caca).

---

### Post by jgcsd on 2012-01-22
Very old thread here, so sorry about the bump, but I think it was relevant.

I was also having this problem and this thread came up on google. After another hour of work I managed to figure out the solution!

The problem is, that mplayer displays status info in the console after every frame. Normally when you're using mplayer, you're displaying video in a separate window, so the fact text is getting output into the console doesn't really matter.

But! If you're trying to play video using "-vo aa" or "-vo caca", the text modes, the status text immediately clears the screen after the frame is displayed, causing severe flickering! So the solution is to turn off the console status text, and you do that using "-quiet"

e.g. "mplayer -vo aa myvideo.flv -quiet"

Ta-dah, problem solved. You can also use "-framedrop" if you're getting sync problems. It seemed to help things for me.

Anyway, sorry for posting on such an old thread, but if this advice had existed already in this thread, it could have saved me an hour of frustration! Hope it helps anyone else whose googling for help! :)

---

