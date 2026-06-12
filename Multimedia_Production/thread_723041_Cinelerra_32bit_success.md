---
title: "Cinelerra 32bit success?"
date: 2008-03-13
forum: Multimedia Production
---

### Post by holmes85 on 2008-03-13
Hi

I'm looking to start using Cinelerra for my short films and I am eager to learn cinelerra. One thing i noticed though was that it crashed A LOT. I know its not meant for 32 bit systems, but I was wondering if anyone had any success using cinelerra on a 32 bit system for their projects?

did you just deal with the crashes?

your installation method fixed it?

*oh and no LIVES, AVIDMUX, KINO are not great alternatives,  maybe for youtube, but not for film makers.

---

### Post by eye208 on 2008-03-13
> **holmes85 said:**
> *oh and no LIVES, AVIDMUX, KINO are not great alternatives,  maybe for youtube, but not for film makers.
Try Blender.

---

### Post by cotcot on 2008-03-13
I am using cinelerra in 64 bit and 32 mbit, both complied from source. You can read how i did this and also how others did in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911").
The only crashes I had were due to a full disk.
I am also learning blender for the moment.

---

### Post by holmes85 on 2008-03-13
thanks i'll try it. and get back to you.

---

### Post by Shlomir on 2008-03-14
The problem with Conelerra is there is no built-in Capture option which makes it kinda rubbishy...

I've been using KdenLive which is OK, but video editing in Ubuntu is clunky, unstable and risky..I know the idea on paper - yay! lets make TRULY OPEN SOURCE CINEMA - sounds great to yr typical marxist indie film-maker, but until some genius writes some stable code, it's all a bit of a pipe-dream!

---

### Post by eye208 on 2008-03-15
> **Shlomir said:**
> yay! lets make TRULY OPEN SOURCE CINEMA - sounds great to yr typical marxist indie film-maker, but until some genius writes some stable code, it's all a bit of a pipe-dream!
[http://www.elephantsdream.org/](http://www.elephantsdream.org/)
[http://www.plumiferos.com/](http://www.plumiferos.com/)
[http://peach.blender.org/](http://peach.blender.org/)

Open source cinema is alive and kicking, but for obvious reasons Cinelerra is not a part of it.

Sure, Blender is not iMovie. In terms of functionality it is closer to Adobe After Effects. It requires a week of learning, but unlike many other video editors on Linux it gets the job done.

---

### Post by IsawSp4rks on 2008-03-15
> **Shlomir said:**
> The problem with Conelerra is there is no built-in Capture option which makes it kinda rubbishy...

While I can't speak for Cinelerra, most professional apps do not include video capture.  In the professional world a lot of people use apps like Flame (and it's derivatives) and AfterFX to mix and process their offline video into broadcast quality output.

---

### Post by holmes85 on 2008-03-16
yea i didn't know a non linear video editor that doesn't degrade the quality and had a decent GUI could be that hard to create. Then again I'm not a programmer. by the way i just used cinerella from the medibuntu repository seems fine so far.... we'll see.

anyone know if its possible to get final cut pro working on ubuntu?
or adobe premiere?

---

### Post by cotcot on 2008-03-16
> **Shlomir said:**
> The problem with Conelerra is there is no built-in Capture option which makes it kinda rubbishy...

I've been using KdenLive which is OK, but video editing in Ubuntu is clunky, unstable and risky..I know the idea on paper - yay! lets make TRULY OPEN SOURCE CINEMA - sounds great to yr typical marxist indie film-maker, but until some genius writes some stable code, it's all a bit of a pipe-dream!

Cinelerra has capture functions (see manual). However most users do not get it working properly and use dvgrab or kino to do the capturing. But this does not make the whole program rubbish. It is more advanced in features than most other editors. The cinelerra learning curve is worth to do if you want more than a set of standard features you find in most editors.

---

### Post by homy06 on 2008-03-16
for the record,

I followed the directions on the cv cinelerra which used the arkicad repo, and it worked, seems pretty stable for now we'll see.
thanks all

---

### Post by keykero on 2008-03-17
I would just like to echo that 32-bit Cinelerra can be very stable.  As a video editor it is very precise with great output, and is great at editing audio.  You just have to learn it and get used to the interface, which actually does not take long.

For capturing Standard Definition footage from a tape-based camcorder, use Kino and save everything as DV AVI Type 2 (choose it in the Preferences > Capture section of Kino).  Cinelerra will have no problem with this format.

---

