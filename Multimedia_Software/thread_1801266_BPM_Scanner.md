---
title: "BPM Scanner?"
date: 2011-07-10
forum: Multimedia Software
---

### Post by moore.bryan on 2011-07-10
I'm looking to find-out the beats per minute (BPM) for each of the songs in my music collection to put together various playlists and thought it would be as simple as adding that column of information to Rhythmbox or Clementine, but that fields shows-up as blank. Am I doing something wrong or do I need a scanner to add that meta information first? If so, do you fine folks know of a good one out there for a large collection?

Thanks, in-advance...

EDIT: So, I installed Banshee because I've read it has a BPM scanner; however, it runs *insanely* slowly. It took from when I last posted this to now to scan my music collection and only has about two dozens songs' BPM computed. Is Banshee supposed to be that slow? Seems useless...

---

### Post by daniel_w93 on 2011-07-28
Sadly it renders itself even more useless when you realize that 90% of the calculated BPM are false. For example some fast paced Anti-Flag song was tagged to have only 40 BPM...

I made the effort ( :P ) and posted this problem to the banshee mailing list and got the following response:

> To do the BPM detection, we use the bpmdetect element wich is part of 
a GStreamer plugin called soundtouch. 
So any problem with the detection algorithm is probably happening in there. 

You might want to discuss your issue with them : 
[http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)

-- 
Bertrand Lorentz 

so I guess one has to wait for updates :/

---

### Post by moore.bryan on 2011-08-02
Hmm... perhaps that's also where the slow scanning speed is having the issue. I wonder why it could be so far off... I also wonder why that isn't a piece of information already in the meta-data.

---

