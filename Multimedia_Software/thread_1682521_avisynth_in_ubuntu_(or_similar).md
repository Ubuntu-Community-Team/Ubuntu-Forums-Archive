---
title: "avisynth in ubuntu (or similar)"
date: 2011-02-06
forum: Multimedia Software
---

### Post by arsci on 2011-02-06
So first off, I'm not sure if I posted this in the right forum so if not, sorry.

I'm looking for a program of some kind that I can combine 4 (if not 2 minimum) streams of video into one file. The only program so far that I've found that does this is avisynth but I can't seem to make it work at all. Does it even work under ubuntu? I've tried numerous guides and how to's but nothing seems to be working.

Basically I just need something that will take a video file, from several different sources (cameras placed around a car) and be able to place them in a grid form into one file. basically in a format like this, where each letter is a different video file:

a b
c d

Thanks!

Ryan

---

### Post by newbie2 on 2011-02-25
It's a shame that this cool app isn't getting more 'traction' on linux :
[http://forum.doom9.org/showthread.php?t=118035](http://forum.doom9.org/showthread.php?t=118035)

because here are some great examples of what you can do with it :
[http://vimeo.com/2823934](http://vimeo.com/2823934)
[http://vimeo.com/2827387](http://vimeo.com/2827387)

:cool:

---

### Post by FakeOutdoorsman on 2011-02-25
You can use AviSynth in Linux: [HOWTO: AviSynth video processing with WINE](http://ubuntuforums.org/showthread.php?t=1333264).

---

### Post by newbie2 on 2011-02-27
> **FakeOutdoorsman said:**
> You can use AviSynth in Linux: [HOWTO: AviSynth video processing with WINE](http://ubuntuforums.org/showthread.php?t=1333264).
Thanks doorsman, i found also this linux sub-forum, that is still 'in use' :
[http://forum.doom9.org/forumdisplay.php?f=63](http://forum.doom9.org/forumdisplay.php?f=63)
;-)

---

### Post by inobe on 2011-02-27
openshot is also a non linear editor.

[http://www.openshot.org/features/](http://www.openshot.org/features/)

some of the features

> OpenShot's Features include:

    * Support for many video, audio, and image formats (based on FFmpeg )
    * Gnome integration (drag and drop support)
    * Multiple tracks
    * Clip resizing, trimming, snapping, and cutting
    * Video transitions with real-time previews
    * Compositing, image overlays, watermarks
    * 3D Animated Titles
    * Title templates, title creation, sub-titles
    * SVG friendly, to create and include titles and credits
    * Scrolling motion picture credits
    * Solid color clips (including alpha compositing )
    * Support for Rotoscoping / Image sequences
    * Drag and drop timeline
    * Frame stepping, key-mappings: J,K, and L keys
    * Video encoding (based on FFmpeg )
    * Key Frame animation
    * Digital zooming of video clips
    * Speed changes on clips (slow motion etc)
    * Custom transition lumas and masks
    * Re-sizing of clips (frame size)
    * Audio mixing and editing
    * Presets for key frame animations and layout
    * Ken Burns effect (making video by panning over an image)
    * Digital video effects , including brightness, gamma, hue, greyscale, chroma key (bluescreen / greenscreen) , and over 20 other video effects
    * OpenShot provides extensive editing and compositing features, and has been designed as a practical tool for working with high-definition video including HDV and AVCHD .


it seems to do very well with avi formats, not so good with high byte rate formats from the start, although the end results are fantastic.

---

### Post by cotcot on 2011-02-27
I have done this with blender, cinelerra and kdenlive.
In blender : start with a black image on the lowest track; put the video tracks upon each other above the black image; downsize and relocate them with the transform tool. Alpha over the tracks on the black image.
Cinelerra : I have done this with cinerella but is too long ago to remember how I did this exactly. It was similar to blender.
Kdenlive : look for the PIP (picture in picture) tool.

---

