---
title: "ATI Radeon X1600 page tearing / vsync issues"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by krazyd on 2006-07-05
I've been having terrible trouble trying to get rid of page tearing on my lappy with its ATI Radeon X1600 graphics card. The problem is especially noticeable when trying to watch a video, or when an Open GL screensaver is running. I have tried the Open GL outputs of both mplayer and gxine.

My screen is 60Hz / 1200x800. Driver is the 8.25.xx fglrx ATI proprietry driver from the repo. (not sure of the exact number right now, in windows.. :()

I have tried installing driconf and playing with the options, but the problem remains. Can anyone suggest anything else I can try? I need my vids in Ubuntu!! 

Cheers!

---

### Post by Eversmann on 2006-07-05
Maybe trying to run official ati drivers? latest is 8.26.xx.

More information: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by krazyd on 2006-07-05
I tried that too, doesn't help! :( 
Is there anyone with the same card who has vsync working?

---

### Post by TheTroll on 2007-04-20
Has any solution been found yet ?

---

### Post by legzelda on 2007-06-06
I'm having the same annoying problem with my X1400 card in my Dell E1505.  I've tried running

```
sudo aticonfig --sync-video=on
```

and

```
sudo aticonfig --vs=on
```

This is supposed to removed tearing during 3D rendering, according to aticonfig's manual.  I've also tried turning off these options, all to no avail.  Maybe they will give you some luck?  I kind of doubt it, but it's worth a shot.  Please let me know if you find a fix.

---

### Post by tartley on 2008-07-01
bump.

I have the same problem using Ubuntu 8.04, Thinkpad T60.

direct rendering: Yes
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

Doesn't matter if I'm using Compiz or MetaCity.

Any clues?

---

