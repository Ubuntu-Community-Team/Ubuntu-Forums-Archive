---
title: "Some Video Player Problems, Please Help!"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by SpikeRazorshards on 2007-06-09
Hey guys, maybe you can help me out here, I'm using ubuntu 7.04 Feisty Fawn and I have it all set up just the way I want it.  However, I'm having a problem with this version that I never had in other versions.  
While watching any video through Totem, there's always a layer of dots all over the video.  I'm not a very advanced user, so if anybody can help, I would like those dots to be gone.  I can see the video and all, but it's just not very crisp with the dot-grid patter like here: 
::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::
::::::::::::::::::::::::::::::
(except the dots are completely even throughout the video).  

When I try to use VLC to play video, the video is crisp, but the program is very unstable.  If I click on anything, the video blacks out.  So I can't zoom, or drag the window, or seek through the video or anything.  Oftentimes, it goes black after a split second of playing regarless of me doing anything.  

If possible, I would rather use VLC player for everything, unless of course there's a better program to use.  The video on VLC is crisper and the color is better.  When I load a video file into Totem, it is really bright and ugly.  Even when I mess with the display settings, it still sucks compared to VLC.  

I have MPlayer installed, and I heard that is a pretty reliable program, but nothing ever loads in my MPlayer for some reason.  When I try loading, an error comes up and I gotta shut down the program.

---

### Post by blackened on 2007-06-09
You may need to change the video decoder preference in Mplayer to stop getting those error messages. Open Mplayer without an actively playing file (Applications -> Sound & Video -> Mplayer or alt+F2 -> gmplayer) right click on the main window and choose preferences, then go to the video tab and try the different listed decoders. One will likely work after some trial and error. GL works best for me, the others are either choppy or don't play at all. 

Maybe one of the resident AV experts will grace us with some insight into this particular weirdness.

---

### Post by SpikeRazorshards on 2007-06-09
Cool, now at least Mplayer works a little, though it's still very choppy throughout all the videos I've tried.  Any suggestions for fixing my VLC player?

---

### Post by Pathian on 2007-06-14
I don't know much about configuring VLC, but as far as that matrix of dots goes, I had the same problem after I enabled the new Desktop Effects. It stopped after I disabled them.

---

