---
title: "resizing mplayer subtittle fonts"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by renators on 2007-04-01
ok, noob question:

how can i change the size of the mplayer subtitles? and there's any way to put them on the bottom black bar like in bsplayer? (my monitor isn't widescreen so the vids plays with black bars at bottom and top.)

ps: sorry for possible errors, but english isn't my primary language.

thanks :D

---

### Post by garybrlow on 2007-04-01
Right click on Mplayer and click on Preferences then go to Subtitles and OSD tab. In this section find the Subtitle Position slider, the values of which represent 0-100 (leftmost of the slider is 0 and rightmost is 100).  Setting the slider to 0 places the subtitles on the top most part of the screen and 100 on the bottom most part of the screen irregardless of whether you have wide screen or not. To add margins you can check the SAA/*** Subtitle Rendering option on the bottom part of the section and set margins for use with the subtitles.

To customize the font display (size, face etc.) Click on the Font Tab. Click on the No Autoscale option to enable customized size.  Use Blur slider for font display transparency, Outline Slider for Black line around the font/text display and use Text Scale to adjust the font display size. Click OK and you're good to go.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by renators on 2007-04-01
ok, i also have another problem:

i can't play any videos using the graphic mode, the only way i can play anything is using the terminal. i really don't know why.

i get an error saying: 

"error opening/initializing the selected video_out (+vo) device."

---

### Post by LudoA on 2007-04-05
> **garybrlow said:**
> Right click on Mplayer and click on Preferences then go to Subtitles and OSD tab. In this section find the Subtitle Position slider, the values of which represent 0-100 (leftmost of the slider is 0 and rightmost is 100).  Setting the slider to 0 places the subtitles on the top most part of the screen and 100 on the bottom most part of the screen irregardless of whether you have wide screen or not. To add margins you can check the SAA/*** Subtitle Rendering option on the bottom part of the section and set margins for use with the subtitles.

I had the exact same problem as the OP. Your suggestion for the font size worked like a charm, thanks.
About the position of the subtitles, my slider is already at position 100, but it's still not displayed in the black corner at the bottom. It still shows the subtitles on the video itself, on the border of the black bar.
Same if I move the slider to 0, it'll be on top of the video, not of the window.

As for "error opening/initializing the selected video_out (+vo) device.": you should try out all video output devices, e.g. x11, xv, gl, gl2,... until you find one which works for you. AFAIK xv is the best, but also the most unlikely to work. Chances are x11 will work for you. Go to preferences -> video to select the video out device.
Running "mplayer -vo help" should also show you the video output devices available to you.

---

### Post by Arjunanda on 2007-05-26
I find no effect using the text scale option. No matter what I do, the text size wont change. Weird.

---

### Post by Vajk on 2007-06-09
> **renators said:**
> ok, noob question:

how can i change the size of the mplayer subtitles? and there's any way to put them on the bottom black bar like in bsplayer? (my monitor isn't widescreen so the vids plays with black bars at bottom and top.)

ps: sorry for possible errors, but english isn't my primary language.

thanks :D

I've been looking how to resolve this thing and I've found in numerous threads that linux doesn't have good video players. I was using Bsplayer too on win but I can really say now that I've found the solution for my needs. There's a great player - [Smplayer]("http://smplayer.sourceforge.net/linux/index_en.php") wich is based on Mplayer but the gui is much more user friendly. 
As for having subtitles on the black bottom check this thread [http://www.phpbbplanet.com/smplayer/viewtopic.php?t=91&highlight=subtitles+black&mforum=smplayer](http://www.phpbbplanet.com/smplayer/viewtopic.php?t=91&highlight=subtitles+black&mforum=smplayer) it worked for me. 

If you still have problems there's an Smplayer thread in this forum somewhere, I just can't remember where, but I'm sure you can find it.

---

