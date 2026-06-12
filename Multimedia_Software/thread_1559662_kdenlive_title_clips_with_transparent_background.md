---
title: "kdenlive: title clips with transparent background?"
date: 2010-08-23
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-08-23
Another hair-pulling WTF moment... All I wanted to do is add a title to the start of a screencast, nice words overlaying the screen vid. In kdenlive:

1. Project menu > Add title clip
2. Format text etc.
3. Set the title clip's background opacity to 0 = (should be?) fully transparent.
4. Put the clip on the timeline, on a higher track than the screen vid.
5. kdenlive obliterates the screen and displays the text with a black background.

There has got to be an easy way to do this. kdenlive.org documentation seems outdated (their screenshots look different from the version I got from synaptic). Do I *really* have to make the title in GIMP like some webpages say? I can do it, but that's idiotic. kden should be able to do it.

Ah well... everything is an epic struggle the first time.

Help? :???:

James

---

### Post by dewdrop_world on 2010-08-24
OK, got it... there's an option in one of the menus to enable the "Transition" tab. Only after enabling that could I edit the transition. Then you can set key frames and opacity levels for each; kdenlive will interpolate between those for the duration of the transition.

Mmm... hidden options...

None of this, btw, seems to be documented online anywhere. Kdenlive's docs appear to be worse even than supercollider's or pure data's!

James

---

### Post by dewdrop_world on 2010-08-24
Oh yeah, there was one other thing. Kdenlive can only composite clips if they are in adjacent layers. I had assumed (like apparently every other user) that compositing would apply all the way down. At first I had the title clip in layer 0 and the screencap in layer 2. After I moved the screencap to layer 1, I got the transparency I wanted.

My previous post was about getting the title to fade away -- "fade to transparent." That's a property of the Composite transition.

James

---

