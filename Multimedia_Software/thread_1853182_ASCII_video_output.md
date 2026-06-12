---
title: "ASCII video output"
date: 2011-10-01
forum: Multimedia Software
---

### Post by syntheticowls on 2011-10-01
Hi,

 I am wondering how I would go about saving an ascii video output?

Example. I have an .AVI file, and using mplayer,  I go to the terminal and type...
mplayer -vo caca video.avi

It will play the .avi file in an ascii format, but how do I save the video in the newly displayed ascii format?

---

### Post by andrew.46 on 2011-10-02
I am not sure if this can actually be done but if so I would love to save the newer output of matrixview :). To see if you have access to this:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -vo help | grep matrix[/COLOR]**
	matrixview	MatrixView (OpenGL)

```

---

### Post by WasMeHere on 2011-10-02
Why do you want to save it? You can replay it from the avi file whenever you want. On my desktop it emulates a small vga window with colours. You can save screenshots with 'Alt + PrtScrn', a png picture.

But *let's play* for a while: You can write the ansi escape sequences into a text file with
[FONT="Courier New"]mplayer -vo caca movie.mp4 > output.txt[/FONT]

You can display it with
[FONT="Courier New"]cat output.txt[/FONT]
in a small 80x25 terminal window.

It will be more realistic if you enter text mode with 'Alt + Ctrl + F3'
Now you can watch and listen to the movie with 
[FONT="Courier New"]mplayer -vo caca movie.mp4[/FONT] but the 'video' was lagging for me,
or watch the video with
[FONT="Courier New"]cat output.txt[/FONT]

Return to graphics mode with 'Alt + Ctrl + F7'

---

### Post by syntheticowls on 2011-10-02
> **Olle Wiklund said:**
> Why do you want to save it? 

I would like to take the ASCII video file and upload it to a website for  display. Also I would like to use it to combine multiple ASCII file outputs  with music, and other media,  via Kdenlive,  and also create animated  .gif files from the ASCII animations. 

Text mode makes the video very choppy, so that hasn't worked well. I find that the display generated from Mplayer via ```
mplayer -vo caca video.avi

``` works well, if only I could save the output somehow. I searched thoroughly online and found some questions about combining the output with Mencoder or other similar program but no answers yet...

---

### Post by WasMeHere on 2011-10-02
Do you want it to look like played with [FONT="Courier New"]mplayer -vo caca video.avi[/FONT], when someone plays it in a web browser?

If that is possible with mencoder, it would be convenient. Otherwise you could save each frame as a picture, and then merge those pictures into a movie. But I don't know.

Another possibility would be to play it on your screen while using some kind of recording tool, that makes a movie of your screen (or of a window on your screen). I have read about such tools, and you might find it browsing on the internet, or maybe someone on this forum knows.

Have fun
Olle

---

### Post by WasMeHere on 2011-10-03
I found this recording tool, *xvidcap*, that makes a movie of your screen (or of part of your screen): _[COLOR="RoyalBlue"][http:///xvidcap.sourceforge.net/]("http:///xvidcap.sourceforge.net/")[/COLOR]_

Have fun trying it!
Olle

---

### Post by syntheticowls on 2011-10-04
Yep. I've used Xvidcap before. It's good, but crashes often and doesn't  quite capture the framerate of videos. You can change the framerate  capture speed which often results in crashing. I was able to record with  Xvidcap. The results weren't equal to the source video but I guess that  will have to do for now.

You mentioned that its possible to save each frame as a picture. Do you  know what I would type in the terminal that will let Mplayer save each  frame of the video as an ascii image? That might work better then  recording via Xvidcap.
:)

---

### Post by WasMeHere on 2011-10-04
Here it is, but I think there is a problem: both caca and jpeg are **vo** options, and I don't know how to run in sequence. Maybe you can figure that out. Cut from *man mplayer*: ```
VIDEO OUTPUT DRIVERS (MPLAYER ONLY)
       Video output drivers are interfaces to different video  output  facili&#8208;
       ties.  The syntax is:

       -vo <driver1[:suboption1[=value]:...],driver2,...[,]>
              Specify a priority list of video output drivers to be used.

       If  the  list  has a trailing ',' MPlayer will fall back on drivers not
       contained in the list.  Suboptions are optional and can mostly be omit&#8208;
       ted.
       NOTE: See -vo help for a list of compiled-in video output drivers.

       EXAMPLE:
                 -vo xmga,xv,
                      Try the Matrox X11 driver, then the Xv driver, then oth&#8208;
                      ers.
                 -vo directx:noaccel
                      Uses  the  DirectX  driver  with  acceleration  features
                      turned off.

       Available video output drivers are:
       ...

       jpeg
              Output  each  frame  into  a JPEG file in the current directory.
              Each file takes the frame number padded with  leading  zeros  as
              name.
                 [no]progressive
                      Specify  standard  or  progressive JPEG (default: nopro&#8208;
                      gressive).
                 [no]baseline
                      Specify use of baseline or not (default: baseline).
                 optimize=<0-100>
                      optimization factor (default: 100)
                 smooth=<0-100>
                      smooth factor (default: 0)
                 quality=<0-100>
                      quality factor (default: 75)
                 outdir=<dirname>
                      Specify the directory to save the  JPEG  files  to  (de&#8208;
                      fault: ./).
                 subdirs=<prefix>
                      Create numbered subdirectories with the specified prefix
                      to save the files in instead of the current directory.
                 maxfiles=<value> (subdirs only)
                      Maximum number of files to be  saved  per  subdirectory.
                      Must be equal to or larger than 1 (default: 1000).
```

---

### Post by syntheticowls on 2011-10-04
Thanks for the info. I'll look into that. Meanwhile, I've been able to get some decent output using the Xvidcap and Gimp to get an animated .gif of the text video. Had to reduce the image size to display well though. 

[IMG]http://www.weekendwastemonster.net/animatedgifs/juno.gif[/IMG]

---

