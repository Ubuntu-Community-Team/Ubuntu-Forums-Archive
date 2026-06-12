---
title: "[SOLVED] External Monitor initially shows videos with blue screen..."
date: 2008-05-22
forum: Multimedia Software
---

### Post by ipsi on 2008-05-22
I've recently set up Ubuntu 7.10 to use an external monitor, using xrandr and a virtual screen entry in xorg.conf.

This is all fine and good, and everything works (laptop screen is at the correct res, external is too), except when I try and play videos.

When I load one up, it starts playing with a blue screen. There's sound, but no picture - just blue. I'm using VLC for this, but it happens with MoviePlayer and MPlayer too, so it must be one of the libraries. The weird thing is, it only does this on the external monitor. If I move it to the internal one, everything plays fine. If I put half on the internal, half on the external, the half on the external is blue, but the half on the internal monitor displays fine. Though on a second look, it only works if less than (or equal to? Not sure) half is on the external monitor. Otherwise it displays the last frame, but keeps playing the audio.

If I open a second instance of VLC (which actually opens two more, for a total of three - probably a VLC bug?) by double-clicking on the file, it plays just fine on both internal and external monitors. If I close the currently running instance, then open a new one, it does the same thing - I have to open the movie again while there's an instance of VLC already running.

Anyone know what's going on here? It's technically the same desktop across both, they're just on different monitors. Could that be the problem? I don't know if I want to hack around with my xorg.conf file to get two proper desktops - that seems like a lot of work, and what I have now basically works, except for this.

---

### Post by ipsi on 2008-05-24
Bump - Any suggestions?

---

### Post by prshah on 2008-05-26
> **ipsi said:**
> 
When I load one up, it starts playing with a blue screen. There's sound, but no picture - just blue.

When you load VLC, can you check Settings-Preferences-Video-Output modules and post the selection for "Video Output Module"?

I can't understand why it shouldn't affect the second time round, though.. unless the first VLC blocks one mode and the second/third instance "fallsback" on another mode...

---

### Post by ipsi on 2008-06-01
Sorry about the late reply, got kinda busy this week...

Anyway,

Default
Dummy video output function
XVideo extension video output
OpenGL video output
ASCII-art video output
Image video output
X11 video output
Color ASCII art video output.

Having played around with them for a bit, it seems that only OpenGL and X11 work, and OpenGL doesn't work well at all - seems to stutter quite a bit, not very nice. So X11 is the only choice for me, though OpenGL seems to look better.

Though it's a bit strange the others don't work right off the bat.

---

### Post by prshah on 2008-06-01
> **ipsi said:**
> 
Default
Dummy video output function
XVideo extension video output
OpenGL video output
ASCII-art video output
Image video output
X11 video output
Color ASCII art video output.

Having played around with them for a bit, it seems that only OpenGL and X11 work, So X11 is the only choice for me, though OpenGL seems to look better.

Though it's a bit strange the others don't work right off the bat.

I'm sorry, I'm a little confused. Is the problem solved? If not, can you tell me which of the above options is selected in the dropdown box? (It should be default).

---

### Post by ipsi on 2008-06-01
Right, sorry - the issue is solved *provided* I select either of OpenGL or X11 - Default *does not* work, and it was the one that was originally selected.

---

### Post by prshah on 2008-06-01
> **ipsi said:**
> the issue is solved *provided* 

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

