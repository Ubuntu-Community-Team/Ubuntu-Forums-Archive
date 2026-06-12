---
title: "mplayer - zooming 3:4 movie to 16:9"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by yemu on 2008-01-10
hi
is it possible to zoom 4:3 video to remove black areas on the _side_ of the screen when watching on a 16:9 monitor? i know there's pan&scan for removing black areas on the top and the bottom (i.e when watching 2,35:1 cinemascope movies on 16:9 screen), but i can't find similar function for zooming 4:3 movie. it would be really nice if it would be available from the keyboard like pan&scan.
y

---

### Post by kko1 on 2008-01-10
Hello.

I don't know of a keyboard shortcut for that (although I'm not familiar with all mplayer shortcuts). If you use the command line version of *mplayer*, there are some ways.

A working way is to crop the video. It's a bit clumsy, but gives good results. You need the *-vf crop=w:h:x:y* -option to crop as much from the top and bottom of the video as you'd like. (You'll have to calculate the "w:h:x:y" coordinates from the original (unzoomed) dimensions of the video.)

(The term "vf" stands for any of the "video filters" built-in in mplayer.) You can use *-vf rectangle=w:h:x:y* to preview the coordinates.

For more information, do *man mplayer*, and search for "-vop" under the heading "VIDEO FILTERS" for more information. Under that heading you will find the descriptions of the various video filters. (I use "-vop" (on Dapper) as the search term instead of "-vf", because that leads us directly to the right spot.)

An other way is to use for instance the *-xy* option to resize the whole video (if it's not too heavy on the machine), keep it windowed (not in full screen mode) in a window that is larger than your resolution and simply position the window appropriately, partly over the desktop borders.

For what it's worth, I hope this helps.

kko1

---

### Post by yemu on 2008-01-15
thanks for your answer,
i plan to write a bash script to suit my mplayer needs ;-) 

this script
- would detect the aspect ratio of a movie and would crop it if it's 4:3
- would detect the audio (if it's ac3 or stereo and changed audio codec to hwac3 or software)

do you have any ideas? i'd like to use cropdetect for size detection but i have no idea how to detect the type of audio stream?

i couldn's find such script on the internet, but I'm pretty sure that someone has already wrote it ;-) so if anyone saw something similar please let me know

y

---

### Post by kko1 on 2008-01-16
Hello.

Two things. One, I don't see why you'd need to detect the audio type, unless you'd be using m**encoder** to re-encode the videos. It doesn't really matter though, I assume you know why you want it, and that's enough. I'd suggest simply parsing mplayer's standard output, which you have to do anyway to get the appropriate values for the crop coordinates. I'm not an expert on codecs, but searching for "Selected audio codec:" and parsing the line appropriately for correct information should do it.

And two, since you need to do some mathematics to the coordinates anyhow, to transform them to 16:9, it doesn't really matter if you use *cropdetect* or not. It's probably simpler *without cropdetect*, because it keeps printing the values until said to stop. Instead, you could just parse the initial output for stuff like "vo config request - 640 x 480" to find the video dimensions.

I can't help you with the scripting though, except that it seems inevitable that the script has to do it in two parts. First run the video for a few frames to get the output, save/redirect the output to something temporary, parse it correctly, generate and save the new parameters, and second run the video for real, with the new parameters. So good luck with that. :KS

HTH.

kko1

---

