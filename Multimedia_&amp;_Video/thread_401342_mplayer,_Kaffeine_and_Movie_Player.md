---
title: "mplayer, Kaffeine and Movie Player"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Campingman on 2007-04-04
I am having many woes with video playback.
On Mplayer I am constantly getting the error initializing selected VO, I have tried all VO codes listed and no change, I have an ati 9250 card and previously had mplayer working with VO = X11 no problem (this was on the fglrx driver, I am now on Radeon to get Beryl working)
The twist is that if I play from the terminal mplayer plays the file just fine!!!!, the script tells me it has selected VO = VX, if I select this in conf it will not play the file in GUI.  My mplayer firefox plug in works just fine also VO= VX,X11. 
I cannot play all files in the terminal as if they have a space in the file name it cannot locate the file.
Confused Iam!!

On Movie Player and Kaffeine if I try to open a wmv file it crashes with an audio sharing violation (the audio is already in use), no other applications are running and nothing is using the audio, it works fine for any other file type.

I have had all these applications running previously using the fglrx driver but I cannot get beryl to run with the fglrx driver.  I do not really want to switch back to the other driver as I quite like Beryl.

Any suggestions?

---

### Post by sisco311 on 2007-04-04
> I cannot play all files in the terminal as if they have a space in the file name it cannot locate the file.
ex. to play: velvet revolver - fall to pieces.mpg
```
mplayer velvet\ revolver\ -\ fall\ to\ pieces.mpg
```

---

### Post by Campingman on 2007-04-04
Thanks sisco311, I knew there was a way to do it but could not drag it from the depths.
Mplayer plays all files from the terminal but not gui?

---

### Post by blueboy4 on 2007-08-24
I have a problem with Mplayer. I cannot change the size of the movie even if I specify "Aspect Ratio - 4:3". It's still widescreen. Does anyone know how to make it full screen like you see on tv? :confused:

---

