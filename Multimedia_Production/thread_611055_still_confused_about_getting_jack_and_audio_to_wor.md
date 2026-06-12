---
title: "still confused about getting jack and audio to work"
date: 2007-11-12
forum: Multimedia Production
---

### Post by Bubs on 2007-11-12
ok anyone have some good N00B resources for getting this stuff to connect and work?  

is it even possible for Ardour to record sounds from zynAddSubfx?  if not what can.  I've read some posts about this and some people talked about using patchage.  the program seems easy enough but what do I patch?  I'm not sure where the things get dragged to.I uploaded a screen of what it looks like now.

seriously I don't want to be a big time techno geek, I just want to make some music for a cartoon.

bubs

---

### Post by Stochastic on 2007-11-12
it sounds like you want to patch the out 1 and out 2 of zynaddsubfx to the audio 1 in of ardour.  then within ardour select the record function on track 1 (the little small record button on track 1), select the overall record function at the top of the screen (the big record button next to stop), then hit the play button.  At this point, anything that comes out of zynaddsubfx will be recorded as audio in ardour.

I may also suggest creating a stereo track in ardour (and then patch ou1 and out 2 to in 1 and in 2 of the respective channel) thus keeping the left and right signals of zynaddsubfx separate.

---

### Post by Bubs on 2007-11-12
well that worked.

but still is there any info you know of to get newbs to linux sound up and running?

---

### Post by Stochastic on 2007-11-12
yeah, try browsing through [https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia) the 'Sound' section of that page [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) contains the documentation that was the original UbuntuStudio project before it morphed into a distro.

---

### Post by Drunky on 2007-11-14
[Here]("http://www.linuxformat.co.uk/pdfs/LXF63.tut_audio.pdf") is an old Linux Format article that describes using and connecting Jack and ZynAddSubFX in PDF format... 

The [same article]("http://www.linuxformat.co.uk/wiki/index.php/Audio_production_-_JACK") but non-PDF format and without any graphics.


[Ubuntu Help: HowToJACKConfiguration]("https://help.ubuntu.com/community/HowToJACKConfiguration?highlight=%28jack%29") wiki page.

[Ubuntu Help: HowToQjackCtlConnections]("https://help.ubuntu.com/community/HowToQjackCtlConnections?highlight=%28jack%29") wiki page.

I thought I had some pages from Dave Phillips but I can't find them right now.  Dave is really worth reading in general for Linux audio.

---

