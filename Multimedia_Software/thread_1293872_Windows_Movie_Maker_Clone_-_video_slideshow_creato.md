---
title: "Windows Movie Maker Clone - video slideshow creator"
date: 2009-10-17
forum: Multimedia Software
---

### Post by hitekwaiter on 2009-10-17
I currently am forced to use Windows Movie maker on my ....uh..Windows machine to create video slide shows consisting of stills, music and titles. I'm a still photographer and I post the "videos" on you tube. I don't want to use windows, but I have not found an application in Ubuntu that works like Windows Movie Maker, Kino and all the other ones seem to want to capture raw video or import existing video files only.

Any suggestions?

---

### Post by vinutux on 2009-10-17
Check out **[smile]("http://smile.tuxfamily.org/")**

install from here **[[COLOR="Olive"]http://www.getdeb.net/app/Smile[/COLOR]]("http://www.getdeb.net/app/Smile")**

Home page [http://smile.tuxfamily.org/]("http://smile.tuxfamily.org/")

[IMG]http://www.getdeb.net/media.php?id=663&type=screens&w=425&h=350[/IMG]

[IMG]http://download.tuxfamily.org/smiletool/smile1.jpg[/IMG]

---

### Post by lovesrugers on 2009-10-17
Kdenlive which can be found in the repository should do what you want.  Here is an example video with a titles, a slideshow, music and video all done using Kdenlive on my Kubuntu 9.04 system.  

[http://www.youtube.com/watch?v=L5ffcJJiFCA](http://www.youtube.com/watch?v=L5ffcJJiFCA)
Jerry

---

### Post by ArielEnter on 2009-12-09
Hi. A few days ago I was looking for a good replacement for that video creator included with windows. I wanted to create a photo presentation like I do it in that software.

I found Kdenlive, and I think is the best choice between all the other options I tried because of it similarities with Movie Make to establish the the default duration of Still Pictures.

In MM you go to tool>options and to the Advance Tab. Then you just change the value in Picture Duration. Very similar, in Kdenlive you go to Settings>Configure Kdenlive and you change the field that says: “Default duration, image clips”. You do the exact same thing for transitions in both programs.

You import pictures, videos and sound the same way you do it in MM.

Another great similarity between them is their time line. Kdenlive doesn't have a Story Board, but its time line looks very similar to MM´s.

Kdenlive doesn't have a Auto Movie yet, but I´m sure they are going to implement it soon. Until then you could use this script [http://www.kdenlive.org/forum/photo-slider-random-effects-script](http://www.kdenlive.org/forum/photo-slider-random-effects-script). It needs to be change a little by replacing “prm” with “prm.png” in the code to work with the current version (0.7.6), but it works.

Kdenlive 0.7.5 available at Ubuntu's repositories is an OLD RELEASE, NOT SUPPORTED ANY MORE!
To installed the newest release you will have to do the following:
   1. go to System Menu > Software Sources > Third-Party Software;
   2. click add and paste this line in:
      ppa:sunab/ppa
   3. close software source and click reload.
   4. Find and install Kdenlive newest version.

If you got problems with the way the program is display, you may be having the same problem I got in this thread:
[http://ubuntuforums.org/showthread.php?t=1343142](http://ubuntuforums.org/showthread.php?t=1343142) it´s easy to solve.

You can mimic many MM's title and credit functions with the use of a text slide and a picture to picture transition. Even MM's “moving title”. An example of picture to picture transition can be found in the following video: [http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video](http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video)
Many other tutorials are found here as well:
[http://www.kdenlive.org/tutorial](http://www.kdenlive.org/tutorial)

I´ll make a template of a “moving title” in kdenlive very soon.

You will find that at the end, Kdenlive lets you do a lot more things than MM.

---

