---
title: "[SOLVED] Sometimes videos are mostly in black and white when I play them"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by mahasmb on 2007-11-09
My video playback seems to be messed up most of the time. I use VLC and Totem.

The video is mostly black and white, with a thick neon green line at the bottom and lines of varied colours running diagonally across the video. I'd take a picture of it, but the picture comes out fine weirdly enough.

Also, for some files I get a dialog box popping up saying "An error occurred" "Internal data stream error." And the video won't play, unless I open it with terminal by typing

```

mplayer *thefile I want to play*

```

This is all very odd and annoying. 

Also sometimes the video does seem to work better with VLC, sometimes not.

I use an integrated video card. What's wrong and how can I fix this??

---

### Post by Amon_Re on 2007-11-12
I just had it happen to me too, after i enabled YUY2 support or whatever it was called (needed for TVTime) i also use integrated video.

I'm going to remove the options i added for TvTime from my xorg.conf file & see if it happens again

---

### Post by mahasmb on 2007-11-13
Any clues or tips from anyone?

---

### Post by walkerk on 2007-11-17
same issue... no one? i'll dig....

---

### Post by mahasmb on 2007-11-19
I've also tried the following command to no avail:

> sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine


It's supposed to remove the '*totem-gstreamer*' package and replace it with the "*totem-xine*" package.

I managed to take some pictures with my phone to show just how bad this problem is.

Here they are:

---

### Post by Elenion on 2007-11-19
I've the same issue that started to happen after I used automatix2 to install all the codecs to play DVD and Firefox plugins

---

### Post by Elenion on 2007-11-19
I have found a fix that worked for me.

Close Totem and remove ~/.gconf/apps/totem/ 
with "rm -r ~/.gconf/apps/totem" and then logout and login again. After that it should work.
Of course all Totem settings are gone.

Check it [here]("https://bugs.launchpad.net/ubuntu/+bug/149791").

---

### Post by mahasmb on 2007-11-21
>  Carlos Parra Camargo wrote on 2007-11-17: (permalink) 
dpkg.log (778.1 KiB, text/plain) 

Same problem here.

> "rm -r ~/.gconf/apps/totem" and then logout and login again. 

Also works for me.

**> Workaround: launch gstreamer-properties -> Video -> Output -> X Window System (No Xv) **

Also works for me (no need to logout/login).

I'm in a fresh install of gutsy (installed on 2007-11-14) and i've updated the system daily. Since yesterday (2007-11-16) i've the black & white problem, i attach my dpkg.log.

I followed your link, Elenion, and what the person above suggested ( in bold ) seemed to work though not at first... I don't seem to have any problems playing any of my videos after I've restarted though.

So this is GREAT NEWS!

Thank you! ^_^

I'm going to make sure I have no video problems for the next few days first before I mark this thread as resolved though.

---

### Post by eXwin on 2008-02-13
am a newbee(three days) to linux but had same problem my solution was to go to to video preferences and re ajust colour saturation

---

### Post by tanas on 2008-04-29
> Workaround: launch gstreamer-properties -> Video -> Output -> X Window System (No Xv) 

Wow! That solved my problems. 
Just for reference, after upgrading to Hardy, all video playback programs had strange colors (due to strange saturation and contrast settings). So it was not a totem-xine vs totem-gstreamer thing (MPlayer and VLC also had the problem).

Now it's solved

---

### Post by NastyT23 on 2008-06-25
> **tanas said:**
> > Workaround: launch gstreamer-properties -> Video -> Output -> X Window System (No Xv) 

Wow! That solved my problems. 
Just for reference, after upgrading to Hardy, all video playback programs had strange colors (due to strange saturation and contrast settings). So it was not a totem-xine vs totem-gstreamer thing (MPlayer and VLC also had the problem).

Now it's solved

How do you get to gstreamer properties?

---

### Post by alecz20 on 2008-07-21
How to get to gstremer properties?

Open terminal and type: "gstreamer-properties" a window will open up.

Strange as it may seem selecting the option "X Window System (No Xv)" fixed totem but not VLC.

I can't believe I watched 2 movies in black and white!!!:confused:

---

