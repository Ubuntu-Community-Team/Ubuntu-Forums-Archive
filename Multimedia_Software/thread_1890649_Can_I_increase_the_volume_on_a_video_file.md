---
title: "Can I increase the volume on a video file?"
date: 2011-12-03
forum: Multimedia Software
---

### Post by sofasurfer on 2011-12-03
I am having problems where I do not have adequate volume available from dvds and video files. They are fine for me on my pc, but when I use them on a friends lcd tv the volume levels are not as good as when he plays a rented dvd. Can I do something to increase the available volume in my files?

---

### Post by sofasurfer on 2011-12-04
I found a thread at [http://forums.afterdawn.com/thread_view.cfm/514361](http://forums.afterdawn.com/thread_view.cfm/514361) whixh explains how to accomplish this with "windows movie editor". I installed a program called "Open Movie Editor". Can anyone explain how to increase my volume with this program?

---

### Post by inobe on 2011-12-04
usually the app that rips will have quality settings for audio.

by default most apps will extract then encode with low quality sound and video.

are you watching these files from a media server?

---

### Post by L a r r y on 2011-12-04
WinFF has the ability to change volume.  I installed winFF from my 10.04 repository and it did not work, so I had to update it from the author's ppa.

[WinFF]("http://winff.org/html_new/") is available at [http://winff.org/html_new/](http://winff.org/html_new/) with Ubuntu repositories on the right side.

Load a video, choose the desired video format, open options and under the audio tab, find the volume dialog.  Hover the mouse over the text-entry field, and get instructional tool tip for the field.  Here we use figures 128 to halve the volume, 256 to keep volume as-is (optional) and 512 to double the volume.  

Convert.

---

### Post by L a r r y on 2011-12-04
WinFF (not "Winff", wrong capitalization!) also creates a wave file in Microsoft format that is compatible with my Windows 95-vintage Syntrillium Cool Edit, which I still use after over 15 years, under Wine on Ubuntu.  The MS Wave format put out by the Sound Converter is not compatible with my editor, so I have in the past run Winamp to rip to wave output under Wine.

WinFF is a very well-done Linux app indeed.

---

### Post by L a r r y on 2011-12-04
> **sofasurfer said:**
> I found a thread at [http://forums.afterdawn.com/thread_view.cfm/514361](http://forums.afterdawn.com/thread_view.cfm/514361) whixh explains how to accomplish this with "windows movie editor". I installed a program called "Open Movie Editor". Can anyone explain how to increase my volume with this program?

From the [tutorial]("http://propirate.net/repos/openme-developers/doc/tutorial.html"):  

**Audio Automations**
Audio automations are useful, if you want to make some parts of an audio more quiet than other parts, or if you want to fade out some background music. Just click on the automations tool button as marked in the image, and click onto an audio clip to add automation points. You can drag them around with the mouse, and if you drag on outside of the clip, it will disappear. Press shift while adjusting to manipulate the volume for a whole area.

(This text is alongside a screenshot.)

It's not in my Software Center, but looks like an interesting program!

---

### Post by sofasurfer on 2011-12-05
Thanks. It appears that WinFF did the job.
Must I use multiples of 128? Is there a limit to how much I can increase the volume?

---

### Post by L a r r y on 2011-12-09
> **sofasurfer said:**
> Thanks. It appears that WinFF did the job.
Must I use multiples of 128? Is there a limit to how much I can increase the volume?

I don't think so.  Minimum is 10 and I used 1024 to 4x the volume on a YouTube MP4 music video.  Starting with 256 as keeping same volume, half of that is 128 for half volume, half again is 64 for 1/4 volume, half again is 32 for 1/8 volume.  So 128+64 should produce about 3/4 volume. 

You should be able to change volume in 1-step increments, though it would hardly be noticed if the change is less than 3dB, which is a doubling or halving.

The human ear can just barely notice a 1dB change, which is approximately 25% change.

EDIT:
Increasing volume requires a doubling of the numbers for each doubling in volume, therefore, 256 == same, 512 is double, 1024 is 4x, 2048 would go 8x.

You don't want to boost the volume too high, otherwise you go into distortion.  Digital audio is at its best when the peak audio reaches but does not exceed the maximum amplitude.  Further increase will destroy the dynamic range of the sound file, with soft passages being nearly as loud as loud passages.

---

