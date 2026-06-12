---
title: "Changing screen size(not resolution)"
date: 2008-10-12
forum: Multimedia Software
---

### Post by jomacintosh on 2008-10-12
Hi gang!  Here is an interesting question - can I change the size of my display so it only uses about 10" by 10" or so.
Here is the reason:
I'm building a projector using a overhead projector(like the kind used in math class, etc.) and a 17" LCD monitor that I stripped for the LCD panel.  I'm sure you have heard of these projects, so hopefully you understand the concept.
The problem I have now is the overhead has a display area of about 10" square, while my LCD is 17".
What I would like to do is have a way to tell the display to shrink down to about 10" or so without loosing resolution.

I'm sure some of you think I'm nuts, but it would be great to watch movies, etc on a 96" screen!
Thanks for any help you can give me!
Jo

---

### Post by sillyxone on 2008-10-12
couldn't you play the movie in a window instead of fullscreen, and resize the movie window to fit into that 10"?

Let's say your LCD monitor is 14"x10" at 1680x1260 resolution. Then if your movie is in a 10"x10" window, it would have the resolution of 1260x1260 or less (movie is usually not in square ratio)

With the same reasoning, if you can find a way to tell Ubuntu that your screen is 10"x10", it will display the resolution in that square at 1260x1260 resolution.

---

### Post by aeiah on 2008-10-12
there are several ways to do it. the best but most complicated way is to create a 'resolution within a resolution' using xorg.conf settings. have a look at what people are saying about overscanning and such.

the easier method involves putting blank gnome-panels around all edges so when you maximise windows, they just fill up to the edge of the panels, not the edge of the screen. combine this with settings in your video player of choice that allow you to underscan the image so it fits nicely. something like vlc or mplayer shouldnt have a problem with it.

here's the mplayer command option you'd use. im sure you can throw it in the config file or something
```

mplayer -fs -vf expand=-140:-140 movie.avi
```

-fs is fullscreen, the -vf expand bit will add 140px black bars around it.

ps: ive always wanted to do the same thing, but ive never had the time or space. looks fun though. be sure to use a fan to keep things from melting :p

---

### Post by jomacintosh on 2008-10-12
> **aeiah said:**
> there are several ways to do it. the best but most complicated way is to create a 'resolution within a resolution' using xorg.conf settings. have a look at what people are saying about overscanning and such.

the easier method involves putting blank gnome-panels around all edges so when you maximise windows, they just fill up to the edge of the panels, not the edge of the screen. combine this with settings in your video player of choice that allow you to underscan the image so it fits nicely. something like vlc or mplayer shouldnt have a problem with it.

here's the mplayer command option you'd use. im sure you can throw it in the config file or something
```

mplayer -fs -vf expand=-140:-140 movie.avi
```

-fs is fullscreen, the -vf expand bit will add 140px black bars around it.

ps: ive always wanted to do the same thing, but ive never had the time or space. looks fun though. be sure to use a fan to keep things from melting :p

I think that is what I'm looking for.  I know I could just open the movie in a sized window, but my problem is since the screen is 17" and the light source is 10", i can't see things like my top and bottom bars without looking directly at the projector.


Thanks for the response.  I've talked about doing this for the longest time, and finally found a good projector for 40 bucks bulbs and all.

The ultimate goal is to hook the projector up to a computer I'm building to run as a MythTV.

---

