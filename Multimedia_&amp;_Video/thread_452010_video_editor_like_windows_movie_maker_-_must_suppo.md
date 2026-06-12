---
title: "video editor like windows movie maker - must support still images"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by mpgarate on 2007-05-22
I have been playing around with ubuntu's video editing capabilities, and found some things lacking, including a video editor that supports still images (with music playing in the background). Is there anything anyone can suggest? Am I just not using Kino right?

---

### Post by reclusivemonkey on 2007-05-23
> **mpgarate said:**
> Am I just not using Kino right?

That's correct. Kino supports still images with music playing in the background.

---

### Post by mpgarate on 2007-05-23
how would I go about doing that? Its weird

---

### Post by reclusivemonkey on 2007-05-23
Go to the FX tab. Select the "Create" tab on the left. Choose "Create from file" from the drop down list. Choose your number of frames (its 25 frames per second in Kino, so 250 frames = 10 seconds, etc). Click on the browse button. Select your picture. Click on "Render".

Ok now you have a still image at your required length (this will most likely be the length of the sound you have). Next, again on the FX tab, choose "Overwrite" on the left, and then on the right choose "Audio Transition", and "Dub" from the drop down menu. Click on "Browse" and select your audio track. Again click on "Render" (don't worry about the sound not being smooth on the preview).

Go to the "Edit" tab on the left and watch your results, you're all done.

---

### Post by mpgarate on 2007-05-25
thanks for the help.. is there a program that could do it easier? im trying to make a slideshow type video

---

### Post by billstei on 2007-05-25
Kdenlive is the one to watch (ha) [http://www.kdenlive.org](http://www.kdenlive.org) but is still in development, so might be a bit unstable.

---

### Post by mpgarate on 2007-05-25
thanks! I installed it, and it crashed when I put a picture in :(... but ill keep my eye on it!

---

### Post by billstei on 2007-05-26
You might have better results with the bleeding edge SVN versions of kdenlive, mlt, and ffmpeg.  You could compile them yourself, but I also found that adding the [http://www.debian-multimedia.org](http://www.debian-multimedia.org) repository(s) (I used testing: [http://www.debian-multimedia.org/mirrors-testing.html](http://www.debian-multimedia.org/mirrors-testing.html) ) will keep you reasonably up to date - use at your own risk, but I don't seem to have any conflicts with Ubuntu that I can tell.

---

### Post by mpgarate on 2007-06-04
kdenlive is exactly what I was looking for. Install mlt, mlt++, and kdenlive (in that order) packages from 

[http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html)

then its very similar to windows movie maker from there!

---

### Post by Killtown on 2007-07-23
Problem with importing images.  Does Kdenlive only stretch the images to fit, or is there a way to make it keep the image's regular size without stretching?

---

### Post by Shay Stephens on 2007-07-23
Right now the only thing that works for me in creating slideshows with music is, oddly, a windows program called [MemoriesOnTV 3.1.8]("http://www.codejam.com/").  It runs very well in wine .9.38 or later.  You have to pay for it, but it works.

My slideshows get put onto DVD, and for that I am using QDVDAuthor (available in synaptic), it works, but crashes like mad.  But it is the only authoring program that works for me right right now.

---

### Post by mpgarate on 2007-07-23
yeah. making slideshows is the ONLY reason I ever switch to my windows machine. kdenlive has worked fairly well.. but I wouldnt bother if you are using more than 20 pictures or so, as it crashes often too.

there are links to recent .debs of kdenlive in my other post in this thread

---

