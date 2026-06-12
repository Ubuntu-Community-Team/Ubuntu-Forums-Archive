---
title: "Video Skips - Please Help"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by mendahu on 2007-05-13
Hey all,

I've got a new Compaq Presario V6305 that I've finally got up and running (not a Linux-friendly laptop) with Fiesty.  I'm having some issues with viedo playback that I can't seem to resolve.  Playing through .avi files causes the video to pause every so often (random intervals, for about 1-2 seconds) before continuing again.  The audio does not pause along with it (eventually syncs back up).  The error occurs in both mplayer and totem, and across many different files (all .avi).  Running totem in a terminal tells me nothing (just using the command "totem file.avi") but mplayer gives me an error when the file is finished.  

Cannot sync MAD frame

The error is repeated over and over with different number jargon afterwards.  Plugging the error into Google yielded little, though I believe it is the audio telling me that the video is skipping.  Is there a codec I'm missing? Are the files all corrupted? Is it just my system? Any help is appreciated; some stats below to help out.

-Jake

AMD Turion 64 X2
nVidia Geforce Go 6150
Fiesty 32-bit version

---

### Post by crispy_420 on 2007-05-14
My first guess would be that maybe your video is not setup right. This is just a guess, but maybe you're stalling do to a lack of resources. Maybe a change in how the video is displayed (system -> preferences -> multimedia system selector) or maybe a switch to a "lighter" desktop like xfce.

---

### Post by mendahu on 2007-05-14
That's a thought.  It's not a particularly high end laptop, and I am running Ubuntu along with compiz.  I've also noticed that when the video skips, so does any other program that's running simultaneously.  I'll try disabling compiz and cutting back on resource-eaters and see how it goes.  Thanks!

-Jake

---

### Post by jcrow on 2007-05-14
I am a fairly new Ubuntu user and I recently found a similar problem playing WMV files.  I experienced slow playback on several WMV files, but everything else was ok. I searched the forum and found a suggestion to use mplayer. I had used it in SuSE, but I had problems getting the codecs to work. I installed Mplayer through synaptic and ran into a problem trying to run mplayer because it was telling me there was no output or something. I again searched the forum and found that I had to edit a file and then I was faced with trying to get the correct codecs. I did another search and installed the w32codecs through the terminal. It seemed a little tricky, but I am very happy with the results. Mplayer seems to work a lot better than totem. It fast forwards without delay and the video seems a little more clear. The only thing I don't like is that the controls are not docked to the player window like I am used to.

---

### Post by mendahu on 2007-05-14
Yea, mplayer does work pretty well most of the time, as far as playback goes.  I really hate the gui on it, but I tend not to use it to often so its ok.  i've installed all the codecs and the same problem occured, so I tried using the other poster's suggestions.

I disabled compiz to see if it would run well in a metacity environment, and it did; no skipping occurred.  However, I noticed something when I turned off compiz; I had left all my workgroups active from when I wasn't using compiz, so when I had the cube running it was rendering three other cubes which I wasn't even using.  Turning them off, I returned to compiz and the video ran fine.  So, I'm running it down to just not enough resources to run everything at once.  Luckily, I'm not gaming on this system.

Thanks for everyone's help!

-Jake

---

