---
title: "Animated GIF with Fillings/Transition"
date: 2015-01-10
forum: Multimedia Software
---

### Post by Cedar_Ren on 2015-01-10
Environment: Ubuntu 14.04

You might have seen mutli-frame GIFs created from only a few images, with software-added blending/fading/other transition effects in between.

I'm new to linux and want to process two or three images to become such GIFs.

My question is, how do I do that under linux?
Is there some kind of Photoshop-like software with such capabilities?
Or is there a command-line tool (preferred)?
How do I find the software? How do I use them?

---

### Post by coldraven on 2015-01-11
Gimp is the nearest thing to Photoshop. It is in the Ubuntu Software Centre or use the command
```
sudo apt-get install gimp
```

For command line stuff install imagemagick, the convert utility will make animated gifs. Convert is part of the imagemagick package.
[http://www.imagemagick.org/](http://www.imagemagick.org/)
```
sudo apt-get install imagemagick
```

Edit: Another link [http://www.imagemagick.org/Usage/anim_basics/#gif_anim](http://www.imagemagick.org/Usage/anim_basics/#gif_anim)

---

### Post by SeijiSensei on 2015-01-11
I've made many animated GIFs using GIMP, but I've never been able to make one that interpolates between frames with effects like fading.  I think it's possible, but it wasn't obvious to me.

Depending on the source material, you may not need any such effects.  I make anime avatars and grab adjacent frames from a show to craft an avatar.  You'll be amazed how much motion can be conveyed in just a few frames since your eyes and brain fill in the rest.  Here's one example:
[IMG]http://www.takinganimeseriously.com/images/avatars/chiko-in-chains-bordered.gif[/IMG]
That consists of just eight frames yet has a lot of motion.

---

### Post by coldraven on 2015-01-11
Maybe you need to create the extra "fading" frames with Gimp and then add them to the animation. Just a guess :)

---

### Post by SeijiSensei on 2015-01-11
Well, yes, that could work if I could figure out what tools to use in GIMP.  There's something called "[Dissolve Mode]("http://docs.gimp.org/en/gimp-concepts-layer-modes.html")" for multi-layered images, but I don't see how to make it create the intermediate frames.  I'll admit I haven't looked really deeply into this question.

---

