---
title: "jaunty - vlc / mplayer / totem disappearing when playing video"
date: 2009-04-20
forum: Multimedia Software
---

### Post by knapps on 2009-04-20
Hey guys
New to the forums but not new to Ubuntu...been drinking the goodness since 7.04.

Installed the Jaunty RC this weekend and was greatly impressed by its speed.

Followed the instructions in the sticky thread to get all codecs working and whatnot and that seemed to go well.

Problem is - whenever I use anything to play any video (AVI encoded in DIVX or DVD VOB's), the program seems to crash and unload itself.  Tried mplayer, Totem and VLC.

Anyone else come across this ???
TIA
Knapps

---

### Post by VMC on 2009-04-20
You must have an Intel chip. There's a problem with either xorg 1.61 and/or Intel driver.

There's several bug reports and a couple of topics on the issue. 

Someone has tried to consolidate the issue found [here]("http://ubuntuforums.org/showthread.php?t=1130582").

Edit: If it's in Intel ingetraged video chip, try this [LINK]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") first.

---

