---
title: "square playback"
date: 2009-01-23
forum: Mythbuntu
---

### Post by rusty0101 on 2009-01-23
for some reason playback is showing up as a square in the middle of the screen. Cycling through 'w' options the display stays 'square' until Stretch where I get a full screen view of the middle of the screen.

Video that would be 4:3 appears to be closer to 2:3, 16:9 letterboxed stuff ends up looking like 3:3. Both are with everything stretched vertically and squeezed horizontally.

I don't recall having this problem in the past. I was having database problems on a HD that had gotten a bit warm, and re-installed from scratch with the 8.10 mythbuntu cd.

This is actually a problem in both live TV and in TV recordings. It is not a problem in playback of movies (mythvideo) or with most of the visualizations I've seen in mythmusic (not sure on the lib variety of visualizations.)

Using an intel video card at 1600x1280 (not the desired mode, but 1920x540i ends up as 1920x270 which is a really bad way to try even using the ui.

UI itself seems to be handling the playback modes in stride. Text in the OSD is not distorted vertically, though there is definately not as much as you would expect to see. For example if a channel is 4_1, I get to see 4_ instead. 

Suggestions would be appreciated. I have tried setting up different video modes for playback, to no effect.

Not sure if this will help, but to somewhat visualize what this looks like, if I should see:
```

+------------------+
|                  |
|                  |
|                  |
+==================+

```
where the picture takes up the full screen, I currently get:
```

+------------------+
|######      ######|
|######      ######|
|######      ######|
+------------------+

```
where the '#' is blank screen.

Thank you,

-Rusty

|Resolution|
For me the issue was resolved by setting the aspect ration on page 3 of 9 of the Appearance setting pages.

---

### Post by singedwings on 2009-01-24
Is it that your recordings are having the edges of the screen chopped off? On my fresh install of mythbuntu I found that the recording profiles are set to 720x576 where as PAL should be 768x576. But beware my changing these settings has stopped livetv working on my system see [http://ubuntuforums.org/showthread.php?t=1033447]("http://ubuntuforums.org/showthread.php?t=1033447")

---

### Post by rusty0101 on 2009-01-24
Not cut off, squeezed in. Overweight people look fit. (sort of.) Another way of looking at it is that someone fit a 4:3 screen in dimension, in a 2:3 latout, with 1:3 pains fo black on either side..

---

### Post by rusty0101 on 2009-01-24
Using a remote front end playback of recorded video is fine. Likewise watching live TV though the remote front end works.

This would not be a problem if it were not for the fact that I would prefer to watch TV etc, on the primary front end.

---

### Post by rusty0101 on 2009-01-25
Have tried changing the pvr-x50 capture resolution to 480x480, no change.

It's almost as if the internal media player thinks it should only be using the center third of the screen, unless the "zoom" is set to Stretch, at which point the entire screen is used, but then the edges and top and bottom of the image are clipped. 

Still looking for any ideas.

There was an update to xorg something intel, which didn't do anything for me.

One thought might be to see if I can use mplayer instead of the internal player for watching recorded TV, but I suspect that would cause no end to problems with such things as editing commercials, etc.

---

### Post by rusty0101 on 2009-01-25
Setting 'horizontal scaling' simply expands the size of the image within the part of the screen where I am seeing video. In this case if I set the horizontal scaling to 25% I still see the same amount of the screen being used, but I also see that I've lost the left and right edges of the show. (easiest way to recognize this is that credits that are visible at 0 are clipped at 25)

So that's not going to be it.

---

### Post by rusty0101 on 2009-01-26
created bug 6177 in hopes of getting some useful attention to the issue. May have to migrate to 9.4 beta to get past the problem.

---

### Post by rusty0101 on 2009-01-27
it appears that the issue is that in 8.10, on my system xinerama is enabled by default. Setting the aspect ratio to 16:9 or 4:3 on the Appearance configurations sett screen resolutions page (3/9) resolves the issue.

I have not the alternative which would be to use 'option xinerama=off' in the appropriate location (with the appropriate syntax) in xorg.conf as well.

So issue is currently resolved for me. Setting subject appropriately.

---

