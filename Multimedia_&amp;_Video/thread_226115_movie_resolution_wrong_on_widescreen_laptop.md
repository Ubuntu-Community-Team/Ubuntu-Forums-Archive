---
title: "movie resolution wrong on widescreen laptop"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by hotani on 2006-07-30
I have a laptop with screen resolution of 1680x1050. Every movie player I have is showing the videos "squished" - as in slightly too short vertically, so circles become ovals, people look a little chubbier than they should, etc...

I have mplayer set to do 16:9, but it is no different. All players from Totem to VLC are doing this.

---

### Post by hotani on 2006-08-15
Bump!

Still having this problem on my laptop. Tried changing the resolution to 1280x768 but still no go. 16:9 videos are looking more like 16:5... :(

---

### Post by jazzmuzik on 2006-08-15
I adjust aspect ratio thusly:

mplayer -x 160 -y 90 movie.avi

If it's still off I'll escape out of the movie and adjust the x or y values until I get it looking good. (Press 'f' to get full screen because 160 x 90 is too tiny for anything except setting the ratio.)

---

### Post by hotani on 2006-08-15
thanks - that seems to work with mplayer. 

I used "mplayer -fs -x 160 -y 110 movie.avi" and it looks like it should. I had to throw the 'fs' in there because hitting the 'f' button wasn't working from the mini player for some reason. It would try to go fullscreen but then end up showing a tiny window in the corner.

---

### Post by jazzmuzik on 2006-08-15
"tiny window"

You might try different -vo <option> options on the command line and see if you can correct that. There's of bunch to try. Type 'man mplayer' and look at the VIDEO OUTPUT DRIVERS (MPLAYER ONLY) section. I'd try them all until you get it working.

For example, you could try gl2, xv, x11, and vesa (e.g., -vo xv).

---

