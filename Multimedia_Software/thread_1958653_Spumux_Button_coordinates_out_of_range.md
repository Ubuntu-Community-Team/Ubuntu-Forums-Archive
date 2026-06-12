---
title: "Spumux: Button coordinates out of range"
date: 2012-04-14
forum: Multimedia Software
---

### Post by Lallitus on 2012-04-14
Spumux: I always get the error message
 
"ERR: Button coordinates out of range: (304, 330) - (326,360)",
 
when I use the command line
 
spumux buttons.xml < menuNoButtons.mpg > menuWithButtons.mpg
 
while trying to create a dvd menu for dvdauthor. Here is the file buttons.xml:
 
<subpictures> 
<stream>
<spu force="yes" start="00:00:00.00" select="1.png" highlight="2.png" >
<button x0="304" y0="330" x1="326" y1="360" />
<button x0="304" y0="362" x1="326" y1="392" />
</spu>
</stream>
</subpictures> 
 
Pictures 1.png and 2.png have the resolution 22x30 (Windows/DVDAuthorGui accepts them).
 
To create the file menuNoButtons.mpg I did the following:
 
(first try: )
jpeg2yuv -n 1100 -I p -f 25 -j picture.jpg | mpeg2enc -n p -f 8 -a 3 -o menuNoMusic.m2v
mplex -f 8 -o menuNoButtons.mpg menuNoMusic.m2v music.ac3
 
(second try: )
jpeg2yuv -n 1100 -I p -f 25 -j picture.jpg > 1.yuv
ffmpeg -i 1.yuv -target pal-dvd -aspect 16:9 -f mpeg2video menuNoMusic.m2v
mplex -f 8 -o menuNoButtons.mpg menuNoMusic.m2v music.ac3
 
In both cases menuNoButtons.mpg plays nice, 44 s with background music, but spumux can't insert the buttons.
 
With some senseless numbers, for example
<button x0="304" y0="330" x1="304" y1="330" />
<button x0="304" y0="362" x1="304" y1="362" />
there will be no error, but then I see one button in point (0,0) .

---

### Post by Lallitus on 2012-04-15
Solved.
 
Pictures 1.png and 2.png should be 720 x 576 (then the button coordinates tells the area in the png picture where the buttons really are). 

(So 1.png and 2.png are not the buttons as I thought.)
 
No the dvd builds up nicely.

---

