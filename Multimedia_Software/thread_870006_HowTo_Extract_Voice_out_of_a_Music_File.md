---
title: "HowTo: Extract Voice out of a Music File?"
date: 2008-07-25
forum: Multimedia Software
---

### Post by eHobayyeb on 2008-07-25
The subject explained it.

I have a music file and want to extract the voice only with out the music.

Linux or Windows does not matter.
Thanks

---

### Post by Jose Catre-Vandis on 2008-07-25
It'll never be perfect but Audacity can help you to acheive this with time and effort

---

### Post by eHobayyeb on 2008-07-27
How?

---

### Post by Jose Catre-Vandis on 2008-07-27
This guy explains it well
```
http://virtualturntable.fourstones.net/isolating-vocals-from-background-music-part-3
```

You may need Windows only plugins for some of it, and £'s

---

### Post by albert ozzy on 2009-07-25
It's an old thread but i've just found the solution so im writing it:

Step 1: 
Open the music file with Audacity. It'll show you 2 graphics which means the song is in stereo.

Step 2: 
To the left of the graphics there's a section which has the file details like this:
> Left, 44100Hz 32-bit float

It doesn't have to be the exact values but sth. similar to this format. On top of this info there's a bar which has the song name on it and a black triangle. Click the triangle to open up the drop-down menu. And in the menu select: "Split Stereo Track". Now both of the tracks have that menu.

Step 3:
Select the second (below) track and on the top menu select Effect > Invert. After that using the same dropdown menu we used to split the tracks,  select "mono" for both of the tracks.

That's it. Now you can play the song.

Although this is a very basic technique it should work on most of the songs. You'll hear a deep voice in most of the songs. And in some of them this'll not work at all.

But give it a try

---

