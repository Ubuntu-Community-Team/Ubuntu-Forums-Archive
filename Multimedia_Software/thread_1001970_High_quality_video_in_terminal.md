---
title: "High quality video in terminal ???"
date: 2008-12-04
forum: Multimedia Software
---

### Post by bebox on 2008-12-04
can somebody tell me if you can watch high quality video in terminal?

---

### Post by bebox on 2008-12-04
please???anybody?

---

### Post by stefangr1 on 2008-12-04
Can you explain what you mean by "in terminal"?

---

### Post by bebox on 2008-12-04
without x i think...without gnome or any other desktop.just with terminal....because i just managed to watch with ascii.

---

### Post by terminator14 on 2009-03-28
I realize that this thread is a few months old, but since I just ran into the same problem and had to spend about an hour trying to figure it out, with no luck finding a solution online, I though I'd post my results for anyone who may be faced with this in the future. 

My main computer just died so I had to take my motherboard back for warranty. Meanwhile I pulled out my old toshiba laptop, and since its video card can't handle running gnome and a movie at the same time, I was looking for how to do just that: play a movie in terminal without needing gnome...

I ended up installing mplayer with

```
sudo apt-get install mplayer
```

and through terminal I run

```
sudo mplayer -vo svga -ao sdl movie.avi
```

which seems to work just fine.

---

### Post by joey-elijah on 2009-03-28
I appreciate that it can be fun watching a movie in the terminal... but.. seriously? 

if your hardware isn't up to scratch to handle gnome AND a video playing it might be time to start saving!

---

### Post by binbash on 2009-03-29
> **joey-elijah said:**
> I appreciate that it can be fun watching a movie in the terminal... but.. seriously? 

if your hardware isn't up to scratch to handle gnome AND a video playing it might be time to start saving!

This is not a hardware case since sometimes you may need to view a video on terminal especially when you are dealing with 10+ boxes.

---

### Post by nikefalcon on 2011-10-03
> **bebox said:**
> can somebody tell me if you can watch high quality video in terminal?
You could use the linux framebuffer. Try: 
```
 mplayer -vo fbdev -fs <videofile.ext>  
```to play it in fullscreen mode in the console.(Alt+F[1-6]) :)

---

### Post by nothingspecial on 2011-10-03
Please don't bump old threads to the top.

Closed.

---

