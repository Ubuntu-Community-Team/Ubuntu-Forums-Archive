---
title: "hdmi video output problem"
date: 2012-07-03
forum: Multimedia Software
---

### Post by nhyrum on 2012-07-03
so when i plug in an hdmi cable, what happens is my laptop screen freezes, and a fresh screen pops up on my v, then i have to go to what i want to watch using my tv screen, if that makes sense. what im worried about, is when i watch a movie, is the movie plays o my tv, but my laptop has a still screen, and will most likely burn the image on the screen. how can i get it so either the laptop display turns off, but the output still goes, or the laptop follows what is going on on the tv?

basically the two screens act independetly of one another and i want them to run the same.

---

### Post by gschoper on 2012-07-03
I use Disper.

[http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)

There is a PPA at:

[https://launchpad.net/~disper-dev/+archive/ppa](https://launchpad.net/~disper-dev/+archive/ppa)

HTH,,,

---

### Post by cipherboy_loc on 2012-07-03
The display preferences utility should have options about mirroring the displays. 


Cipherboy

---

### Post by jonnyboysmithy on 2012-07-03
Look under Administration->Preferences->Screensaver 
There you can set the time till the screen turns off. If you are using 11.04 or later, just search for screensaver in dash.
 
Alternatively you could run the command this command in the terminal (ctrl+alt+T)
 ```
gnome-screensaver-command -a
```

To quote wikipedia:
> [Plasma displays]("http://en.wikipedia.org/wiki/Plasma_displays") are highly susceptible to burn-in, while [LCD]("http://en.wikipedia.org/wiki/LCD")-type displays are generally less so.  Now a days all laptop screens are LCD or LED. Screen burn will not happen on these type of screens so don't worry about it.

---

### Post by nhyrum on 2012-07-03
> **cipherboy_loc said:**
> The display preferences utility should have options about mirroring the displays. 


Cipherboy

thanks, got it!

---

