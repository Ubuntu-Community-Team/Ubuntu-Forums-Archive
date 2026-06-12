---
title: "display issues"
date: 2010-08-03
forum: Mythbuntu
---

### Post by itlarson on 2010-08-03
I am having a few issues with an ion based mythbox and a 26" HDTV.  The TV has a native resolution of 1366x768, and I am running it via hdmi at  1360x768, the closest resolution which nvidia-settings provides.  Despite having a VGA input, I don't think the TV was built with computer input over hdmi in mind, as there is no hardware overscan correction.  I am living with this,though because of the 20' cable run between the tv and computer, but am wondering if maybe the tv doesn't properly identify itself when hooked up this way. 

The main problem I would like to deal with seems to be dpi related.  First, the font sizes don't seem right for the theme.  Long items like "record on this channel every week" are cut off, so you cant tell if it is every week, or every day.  Playback initially was squashed vertically.  I worked  around this by setting the default aspect ratio to 4:3 in the frontend settings, but now it looks like it is squashed horizontally, albeit much less so.

Does anyone know the proper way to set dpi for nvidia graphics?

---

### Post by LowSky on 2010-08-03
I had a similar issue. In nvidia-setting there is an option for overscan if your using HDMI, but it isn't called that, and I'm drawing a blank.

If you can try using 1280×720 for your resolution. Since its the standard for 16x9 resolution and the resolution of 720p video should look much better.
Or try using 1920x1080, if your TV can play 1080i it may work, but look a bit grainy on menu text.

change the font size in mythtv if your having issues reading the fonts, just shrink the size a bit. this can be done from the setup menu on the frontend

---

### Post by newlinux on 2010-08-03
Just echoing LowSky - if you are running through HDMI, I'd go with 1280x720 or 1920x1080 especially if you can't get 1:1 pixel mapping. Your TV is probably optimized to handle these resolutions through HDMI because that's what set top boxes will send it. If you are only worried about overscan with mythtv playback  you can correct for that in the TV Settings under playback. If you are worried about overscan with the desktop the nvidia-settings tool is the way to go.

---

### Post by itlarson on 2010-08-03
I found this: [http://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards](http://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards)  and will try it before giving up on the native resolution.  I feel that up/downscaling causes more pronounced artifacts when the camera pans over sharp lines.  I thought that font sizes should automatically be right if the dpi was right?

---

### Post by newlinux on 2010-08-03
Keep in mind your signals will be scaled by the CPU/GPU anyway (because they aren't going to be 1366x768, they are going to be 1280x720 or 1980x1020 if they are from standard hdtv broadcasts. Your computer will have to scale them to 1366x768. If you set your resolution to 1280x720 or 1980x1020 your TV will do more of the scaling, which it should be pretty good at.

---

### Post by itlarson on 2010-08-08
The info in the wiki which I found after my first post worked perfectly.  I simply added the following to the "Monitor"  section of xorg:

Option    "UseEdidDpi"  "FALSE"
  Option    "DPI"  "100 x 100"

I notice that monitor is listed as "unknown" in xorg.  I don't think the tv is identifying itself properly over hdmi, but with this tweak it works as it should.

---

