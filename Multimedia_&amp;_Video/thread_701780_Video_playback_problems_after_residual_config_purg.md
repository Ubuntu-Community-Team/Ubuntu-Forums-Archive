---
title: "Video playback problems after residual config purge"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by Thorir Mar on 2008-02-19
Hi all!

I was running short on space on / so after a quick search on the forums I found that I could free a few megabytes by cleaning up residual config packages in Synaptic.  This was apparently not as harmless as I thought, and now I am having video and DVD playback problems as well as being unable to start skype.

When I put a DVD in the drive Totem fires up automatically and starts playing the dvd.  The audio sounds fine, but there is no video.  If I manually start Totem and select DVD I get the following error message:

> Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Xine plays the DVD but the colors are all wrong, only red and blue and very dark, again the sound is alright.

Any pointers in the right direction would be much appreciated.

---

### Post by koleoptero on 2008-02-19
Have you tried reinstalling the plugins needed? I believe that reinstalling them would help. Although I've done the purging thing too and I have no problems with anything. But I use VLC.

Try in a terminal:

sudo apt-get update
sudo apt-get check

to see if you have missing dependencies. If you do install them. If not, or if this doesn't fix your problem search in synaptic for the ugly and bad gstreamer plugins, and install them.

---

### Post by Thorir Mar on 2008-02-20
I tried *]apt-get check*, but to no avail.  I then tried removing all the gstreamer plugins and installing them again, again without success.  I then tried installing the VLC player, it works, but has the same color problem as Totem (very dark, red-blue image).

Anybody have any further ideas?

---

### Post by thechilipepper0 on 2008-02-20
I had a very similar problem, although i didn't remove anything. i just tried *many* different options to get video. i thought it was just dvds that wouldn't play video but it turns out video doesn't work in any format.

anyway someone suggested I turn off compiz fusion. when i did that, VOILA! everything worked.
sadly, i don't know how to make them work together. so give that a try, see if that does anything.

---

### Post by koleoptero on 2008-02-20
Then probably it's your graphics card configuration that has the problem. I had a similar problem when I tried to tamper with my graphics card drivers. Unfortunately I'm not that knowledgable in this area :(, but probably someone else is.

---

