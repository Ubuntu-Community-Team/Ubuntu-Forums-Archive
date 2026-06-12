---
title: "Play DVD internal, main menu selector not scaled right"
date: 2009-04-16
forum: Mythbuntu
---

### Post by mathog on 2009-04-16
Playing a DVD on screen 1, which is TV-out (NTSC analog, 640x480).  When the DVD's menu comes up the selector (highlight, cursor, whatever you want to call it) is offset considerably from its target.  For instance, in the movie the "Last Samurai" the main menu looks sort of like this (sorry, I could not get Gimp running in Screen 0 to take a screen capture of Screen 1):

```
play movie        languages
scene selections  special features

----------
==========

```

These options are placed very low on the screen in this movie, they are centered about 1/4 of the way up the screen (the whole screen, they are only about 1/8 of the way up the letterbox area). Here the ---- position is where the selector line is for "play movie", and the ===== position is where the it falls for "scene selections".  For "play movie" selected it should instead look something like this:

 ```
_play movie_        languages
scene selections  special features


```


The appearance wizard shows the size of the display set at 589x449 with offset 11 x 8.  It sort of looks like this scaling is being applied to the image containing the menu items, but not the selector (or vice versa).

Not all programs do this, for instance:

(export DISPLAY=:0.1; xine -B -G 589x449+11+8 --no-splash dvd:/ )

had the cursor in the right place relative to the menu items.  Although Xine is not centered properly with that geometry, being well to the left and not extending all the way to the right side of the screen.  To center Xine I have to use: 604x456+18+12 instead. Naively I would have expected the same geometry to work in both programs.

Anybody else seen this?  Is this a configuration problem on my part, or a bug?

Version details:

Mythbuntu 8.10
Mythtv 0.21.0+fixes20277-openglvdpau-0ubuntu3
Nvidia 180.44
256MB 8400GS card

Thanks.

---

