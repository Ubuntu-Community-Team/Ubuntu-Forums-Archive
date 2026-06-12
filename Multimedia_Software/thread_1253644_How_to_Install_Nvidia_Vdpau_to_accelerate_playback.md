---
title: "How to Install Nvidia Vdpau to accelerate playback of Mpeg2/VC1/WMV3/H.264"
date: 2009-08-30
forum: Multimedia Software
---

### Post by Wanas on 2009-08-30
I have troubles playing H.264 videos which is played slowly on my computer, the only option to play them smoother is to play them with VLC and enable something called (skip the loop filter for H.264 decoding) which makes playing H.264 videos work much better.

After a while I have seen this page [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa) 
and this description 
[QUOTE=NVidia]
This PPA contains updated mplayer/smplayer builds geared towards use with Nvidia's VDPAU hardware accelerated playback of Mpeg2/VC1/WMV3/H.264.

Turn off Post-Processing and multithreading.[/QUOTE]

I have uptaded my mplayer and smplayer to the latest in this PPA and installed the Nvidia's VDPAU package but the H.264 still slow when you play them with smplayer :(

any suggestion in how to make this work and make all my players play H.264 and high-definition videos smoothly ?  

My computer specs:
- NVidia 6200 LE
- Core 2 due 3.00 GHZ
- 3 GB ram

---

### Post by bilder on 2009-08-30
Believe you need an 8600 or better with the required hardware to run VDPAU and the appropriate drivers, which should be in the Ubuntu repository.

---

### Post by Wanas on 2009-11-30
any other suggestions plz ?

---

### Post by Wanas on 2010-01-12
bump

---

### Post by Wanas on 2010-01-12
The problem is its working more better on windows XP and the H.264 720p vidoes works fast and dont take that much cpu ?
Is there a way to test my vidoe driver is it working fine or not ?

---

### Post by engti on 2010-03-27
I've been tearing my hair out on this one also.... did you manage to find a solution?

I found this page [http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

Its titled How to --- but it goes on to say its not for a newbie..... I've been wondering what is the point of this.....

---

### Post by cchhrriiss121212 on 2010-03-27
> Its titled How to --- but it goes on to say its not for a newbie..... I've been wondering what is the point of this..... 	

Just click on the link for the ppa and follow the instructions. If you have been using Ubuntu for more than a week you should be fine with it.
Better check you have a supported card first though.

---

### Post by AdrianVeidt on 2010-03-27
> NVidia 6200 LE

Not good enough, sir. You need at least the VP2 generation to make vdpau work, and that means a Geforce 8000 or newer. However, the rest of the hardware on that system looks great to me, so go out and get a GT 220/230/240 for about $100 and you'll be in great shape (those cards also come with HDMI ports so you can connect the system directly to your HDTV).

Here's the page that has the purevideo chart. As you can see, the Geforce 6 series doesn't make it:

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

> Its titled How to --- but it goes on to say its not for a newbie..... I've been wondering what is the point of this.....

At the time I originally wrote that, there was no vdpau PPA, and it was all about compiling things yourself. The instructions were completely different and much more difficult. The "newbie" sentence really no longer applies.

---

### Post by salemboot on 2010-09-12
The 6200 plays h264 fine in Windows XP on VLC.

Turn off compiz.

Options are numerous but try a different video player first.   KMplayer will let you tweak the video out.   Try using GL instead of auto.  Xine has always been a great player too.


Another option,
I'd actually suggest re-encoding the video to XVid.  
Use AcidRip and instead of the /dev/dvd path put in the actual path to the video.

Hit Queue and you can go to the other tab to make note of the command-line it uses.

Make a script for all your videos and re-encode them to a less cpu intensive codec.

---

