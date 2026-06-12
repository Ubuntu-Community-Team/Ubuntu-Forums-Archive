---
title: "Banner/logo over the top of video"
date: 2013-06-14
forum: Multimedia Software
---

### Post by Mr_Vile on 2013-06-14
Hi all,

We are installing a plasma screen in work that will be showing BBC News 24 (or similar news service). The problem is that as the plasma screen has been funded by a donation, we need to display a thank-you message acknowledging the donation. Ideally this would be either a rolling banner across the bottom/top of the screen, or a static image overlaid on the video feed. 

Does anyone have any suggestions as to where I should start on this, or what potential routes I could take? I'm happy with either a simple solution or something more involved (I took this "project" on as I thought it would be a good opportunity to develop my knowledge).

All the best,
MV

---

### Post by FakeOutdoorsman on 2013-06-14
You can use the [drawtext](http://ffmpeg.org/ffmpeg-filters.html#drawtext-1) video filter in ffmpeg to create text-in-a-box:
```
ffmpeg -i input -vf drawtext="fontfile=/usr/share/fonts/TTF/Vera.ttf: text='TV donated by Mr_Vile': fontsize=18: fontcolor=black@0.4: box=1: boxcolor=white@0.6: x=5: y=5" output
```

Preview it in ffplay before encoding: 
```
ffplay input -vf drawtext="fontfile=/usr/share/fonts/TTF/Vera.ttf: text='TV donated by Mr_Vile': fontsize=18: fontcolor=black@0.4: box=1: boxcolor=white@0.6: x=5: y=5"
```

Same as above but is intermittent. Displays for 30 seconds every 120 seconds:
```
ffplay input -vf drawtext="fontfile=/usr/share/fonts/TTF/Vera.ttf: text='TV donated by Mr_Vile': fontsize=18: fontcolor=black@0.4: box=1: boxcolor=white@0.6: x=5: y=5: draw=lt(mod(t\,120)\,30)"
```

Or you can use the [overlay](http://ffmpeg.org/ffmpeg-filters.html#overlay-1) video filter to place an image over the video:
```
ffmpeg -i video -i image.png -filter_complex overlay output
```

I'm not sure how you're going to feed the input to your computer and then back out to the TV though. Or you could print the info on a piece of paper and tape it to the TV but where's the challenge in that?

I don't use the so-called "ffmpeg" from the repository, so I'm unsure if these examples will work with it. If not you can use a [static ffmpeg build](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453), just download, extract, and run, or you can follow a step-by-step guide to [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

---

