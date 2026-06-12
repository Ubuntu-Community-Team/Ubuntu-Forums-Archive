---
title: "MythTV - ATI - video playback"
date: 2008-09-02
forum: Multimedia Software
---

### Post by tmeitner on 2008-09-02
OK, so I installed MythTV on my Toshiba Satellite laptop running an ATI Radeon Xpress video card and a USB Hauppage WinTV-HVR 950Q capture card. Everything ran smoothly, and I could watch and record HDTV and everything on my laptop. I wanted to connect the display to my LCD TV so that I could play back recorded shows from the comfort of my recliner.

I've finally gotten to a point where I have everything hooked up and working properly, but now the video playback on my system is terrible, and that includes MythTV (both recorded shows and live TV). The video seems to bounce up and down, sometimes there is a big pink bar on the right side of the screen in MythTV, and other media players (i.e. VLC, Mplayer) have "bouncy" videos too.

I'm more than willing to provide whatever information would be necessary, please help! Thank you!

---

### Post by TheKorn2 on 2008-09-05
> **tmeitner said:**
> I've finally gotten to a point where I have everything hooked up and working properly, but now the video playback on my system is terrible, and that includes MythTV (both recorded shows and live TV). The video seems to bounce up and down, sometimes there is a big pink bar on the right side of the screen in MythTV, and other media players (i.e. VLC, Mplayer) have "bouncy" videos too.

Make sure you've set the ati driver for a video overlay.  That made a ton of difference on my system.  ( sudo aticonfig --overlay-type=Xv )

Unfortunately, I too am suffering the pink bar syndrome *only* when playing back 1080i content.  720p is fine, but 1080 has a vertical pink bar on the right.  Quite annoying, really!

I'm using the driver version available that's available on ati.com right now...  2.1.7873, which is lots later than the one packed with hardy, though that version did the pink bar garbage as well.  (use fglrxinfo to check your version)

Radeon xpress 200 is my chipset, FWIW.  (More than likely a few steps behind yours!)

---

### Post by tmeitner on 2008-09-05
Actually, I figured it out: the video rendering was set to xV, and I changed it to something else - guess and check till you get it.

---

