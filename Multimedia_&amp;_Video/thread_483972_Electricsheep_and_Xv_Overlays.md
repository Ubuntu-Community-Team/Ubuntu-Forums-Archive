---
title: "Electricsheep and Xv Overlays"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by EReckase on 2007-06-25
I'm working on getting the next 'generation' of electricsheep client working for multiple Linux distros (Ubuntu, OpenSUSE, etc) and I've run into a problem with my Ubuntu laptop.  I've managed to figure out how to get electricsheep installed appropriately as a screensaver, and how to set everything to make it work...and it does, the first time I start my machine.  I've actually been starting it on the command line since that simplifies testing (I can see any errors that might be taking place.)  

The problem isn't getting it to display video the first time...that works fine.  But if I play a video using mplayer, and then start the screensaver, the popped-up window is empty - not black, but empty, invisible, transparent.  If I then use gstreamer-properties to set the overlay mode, it'll start up again, but mplayer 'resets' the video somehow to prevent the overlay from properly displaying.

Does anyone have any ideas about this?  I'm afraid I'm not particularly knowledgable about video, but I'll help all I can.  I'm using Feisty on a laptop with ATI Xpress 200m graphics, latest ATI drivers.

Thanks!

---

