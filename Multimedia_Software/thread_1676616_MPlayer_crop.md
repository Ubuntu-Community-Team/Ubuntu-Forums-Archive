---
title: "MPlayer crop"
date: 2011-01-27
forum: Multimedia Software
---

### Post by jonnybarnes on 2011-01-27
Hi, I'm trying to rip The Wire from DVD. Season 1 must be from a while ago, its in 4:3, though when playing the dumped VOB file, th default cropping by MPlayer gives this horrible bit at the top of the screen. How would I change the -vf crop option to get rid of it?

Cheers

Here's a screenshot of what I mean.

[IMG]http://i53.tinypic.com/2e5odp5.jpg[/IMG]

---

### Post by cchhrriiss121212 on 2011-01-27
Might be able to remove it with an automatic crop:
mplayer -vf cropdetect file.vob

Any reason you are ripping VOBs instead of something smaller? I ask because Handbrake has a good feature for setting up a crop as well as having h264 output which will be basically the same as the VOB in terms of quality.

---

### Post by andrew.46 on 2011-01-27
Sounds a bit odd, by *default* MPlayer does not crop at all but I can see some cropping parameters have been passed in your example. Are you using a frontend of some sort for MPlayer? A description of the FFmpeg port of MPlayer's crop filter [here]("http://www.andrews-corner.org/fist.html#video") may be useful.

---

### Post by jonnybarnes on 2011-01-27
I've got the VOB because I'm going to use MEncoder to convert it to a smaller format. I just want to work out what crop parameters to pass to it in order to get rid of the stuff at the top.

EDIT: I've worked out the second two numbers, so to stop a fatal error for the "cropped area outside the original!" I crop a smaller height and start several pixels down. That is if I pass the following to MPlayer I don't get the wierd stuff at the top:
```
-vf crop=672:570:8:6
```

---

### Post by m_yates on 2011-01-27
This command will give recommended crop as numbers scrolling down the terminal:

```
mencoder filename.vob -oac mp3lame -lameopts cbr:br=128:vol=9 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000:autoaspect -vf cropdetect -ffourcc DX50 -ss 00:10:00 -endpos 00:00:30 -o filename.avi
```

kill it with ctrl+c, then enter the crop values XXX:XXX:X:X that it gives:

```
mencoder filename.vob -oac mp3lame -lameopts cbr:br=128:vol=9 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000:autoaspect -vf crop=XXX:XXX:X:X -ffourcc DX50 -ss 00:10:00 -endpos 00:00:30 -o filename.avi
```

The above command will encode 30 seconds of video starting 10 minutes into the vob file "filename.vob".  It will create the 30 second divx5-compatible avi file "filename.avi", with 2000 kbps video, 128 kbps mp3 audio, with audio level raised to 9 (from 1-10 allowed).  Play this test file to see if you like the audio, video quality, and if it is cropped in the right location:

```
mplayer filename.avi
```

If "cropdetect" doesn't give you good crop values, you can manually crop.  Try running:

```
mplayer -vf rectangle XXX:XXX:X:X filename.vob
```

using the crop values XXX:XXX:X:X from mencoder.  It will display a rectangle overlay on the video to show where the crop is.  The crop is in the form "w : h : x : y".  You can adjust the numbers a little to move the rectangle where you like.  Once you have the crop where you like, plug those numbers into mencoder and test encode another small section of video.  The width and height should be multiples of 16.  You should crop enough to remove all black borders.

Also, since this is an old TV show, you might want to add "lb" to the video filters to deinterlace.  To encode the entire vob file with deinterlacing:

```
mencoder filename.vob -oac mp3lame -lameopts cbr:br=128:vol=9 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000:autoaspect -vf crop=XXX:XXX:X:X:pp=lb -ffourcc DX50 -o filename.avi
```

You can try with and without deinterlacing to see what works best.  Good luck.

---

