---
title: "How do I convert video Ogg to MPG?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by bbharatsony on 2008-06-14
I wanted to convert a video OGG file(OVG) to MPEG. I could not find anything that worked for me. So I went to Kdenlive, inserted my video OGG(OVG) file then I went to the file menu and clicked the 'Export Timeline' button and exported the file into and variety of different formats. When I played the exported file I saw everything but the last 6 seconds of the video.:confused::confused::confused: I need HELP

---

### Post by dacorr on 2008-06-14
from terminal

sudo apt-get mencoder

then

mencoder fromfile.ogg -oac lavc -ovc lavc -lavcopts abitrate=160 -o tofile.mpeg

i normally convert to avi though

Dac

---

### Post by sim-value on 2008-06-14
People who make Thread titles like you must be ignored.
No i wont help you ! Please Learn to make usefull titles ....!

---

