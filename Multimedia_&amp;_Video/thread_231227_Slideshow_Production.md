---
title: "Slideshow Production"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by indytim on 2006-08-07
First off, I am not a video expert.

I am looking for a technique in Linux (Ubuntu-Gnome) where I can produce a finished DVD playable in most players that would consist of a slide show. The slide show would be populated with a series of .jpg's (photo's).  Ideally I would also like to add audio as background music.  Last but not least, I would like to control the timing of display for each photo contained in the slide show.

I would appreciate hearing back from user(s) who have actually been able to do this rather than the "theory only" group.  Given the number of apps out there, I don't want to spend a lot of time on wild goose chase's with app checkout.  I know this will probably take more than on app to do, so I would appreciate a "sequence" of steps.  

To reiterate my opening statement, I am no expert on video formats so please keep the responses in the "simple area".

Many Thanks,

IndyTim

---

### Post by LQB on 2008-01-26
Don't know if you found what you were looking for.

Slides 2 Video does everything you want. Find it here:

[http://jslideshow.sourceforge.net/](http://jslideshow.sourceforge.net/)

It requires:
1) ImageMagick (which you probably already have installed anyway--if not, it is a simple apt-get).
2) Sun Java 6 which you can get from Sun, or install the Sun Java 6 Ubuntu package.
3) ffmpeg. This is the tough one. You need to compile from source, but instructions are included in the README file of the Slides 2 Video download (9 command line steps, including "go get a snack").

That's it. That may be more work than you were looking for, but it's worth it if you can get it to work. It's simple, has a GUI showing a preview of your slides, allows full control over the timing, etc. See some screenshots and demos at the above link.

Cheers!

---

