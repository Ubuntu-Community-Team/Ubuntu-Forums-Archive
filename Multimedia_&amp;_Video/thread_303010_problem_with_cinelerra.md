---
title: "problem with cinelerra"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by black_rob on 2006-11-19
Hi.  I installed Cinelerra from the debs listed in the "install cinelerra" post, and for the life of me I can't get it to do what I want. 

I have a short video I made in front of a green screen.  I used the chromakey effect to eliminate the green color, and added a jpeg image as a new track.  The background image only shows up on one frame --I understand this, and expected it from reading [this]("http://robfisher.net/video/cinelerra3.html") :
"If you drag an image file onto a video track you will notice that it is only one frame long. You can make it longer by zooming into it on the timeline and dragging the edges with the middle mouse button. You can also position it at the correct point in time using this method."

But that doesn't work for me, the clicking and stretching part.  I've been trying different things and googling about for at least four hours now, and everywhere just says, "click and drag it".  Cinellera will not let me click and drag it.  I can sometimes click and move it --it seems very tempermental about that, too-- but my background image always remains one frame long.  

Is there some secret setting I'm missing?  

Help!

---

### Post by movil on 2007-12-11
Same here, it's just one frame and I cannot make it bigger. 
Also it's not appearing in the timeline, is this normal ?
Anyone has some hint about this ?

---

### Post by val67 on 2007-12-11
maybe some help can come form here.

[http://www.freenet.org.nz/misc/cintitles/](http://www.freenet.org.nz/misc/cintitles/)


They also use an image on the track, you can play with their already done cinelerra project (xml)

---

### Post by movil on 2007-12-12
Thanks for the link val.

# create new video track, set the track width to the width of the gimp image, arm this track and disarm all others
# import the png file and place it on the new video track
***# stretch it along the timeline to required length***
That is the part I don't get.

I see he PNG in the composer view, but I don't see it in the timeline!
So I don't see any way to drag it and make it longer. It remains one unique frame.

---

