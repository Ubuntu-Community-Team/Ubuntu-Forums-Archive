---
title: "Mplayer GUI and flv files"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Batuhan on 2007-08-26
If I doubleclick a flv file, mplayer opens only with the video window, without the gui. So If I need to go forward for example, I need to hold right arrow and that takes forever. Up arrow for 1 minute skips ain't working too.

If I first open the GUI from applications then select the file to play, it complains about not finding alsamixer for my device as my soundcard does not support software mixing.

But sound works fine, if I double click a file from nautilus.

Any clues? I want to see the Mplayer gui.

---

### Post by benerivo on 2007-08-26
I don't use mplayer anymore, but from what i remember it could be opened in both modes as you describe (1. main window only and 2. full gui) depending on how it was started.

From a terminal, the mplayer command will just open the player window, whilst the command gmplayer opens the full gui. You may want to change the file association of .flv files so that they open with gmplayer.
(Another fix, might be to rename the extension from .flv to .avi.)

You may well still get that error message you mention, but try changing a few of the sound options (if you haven't already) from within mlpayer.

---

### Post by Batuhan on 2007-08-26
Thanks, what you suggest just works but this time mplayer opens the video with wrong proportions, you have to resize the video window. And scrolling through playback is not possible.

Renaming to avi has te same result but this time video is turned 90 dgrees anticlockwise.

I'm pretty much frustrated with mplayer and totem actually.

What are you using now? I need to switch I think.

---

### Post by benerivo on 2007-08-26
I think mplayer is generally considered the best video player for linux. I have Kubuntu, so I use Kaffeine. My flv videos have a jerky playback that i haven't been able to fix, but I don't really play many of them so I'm not bothered. Your best bet is probably to continue trying mplayer.

---

### Post by benerivo on 2007-08-26
Actually, I have just tried installing KMPlayer to Kubuntu, and the flv videos play very smoothly. I had to change one of the settings inside KMPlayer to 'use mplayer' rather than xine.

Batuhan, you may have success if you tried to install KMPlayer (but keep mplayer installed) to play your flv videos.

---

