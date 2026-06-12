---
title: "Not so smooth playback on totem."
date: 2010-11-14
forum: Multimedia Software
---

### Post by me.translucent on 2010-11-14
My totem media player hangs a lot. The video playback is not smooth ..as if i am on a very old computer and believe me i am not :P . though everything runs smooth on vlc . but i'd still prefer totem if it can be fixed . any ideas ? 

PS :  i running ubuntu 10.10 , the graphic card i have is Nvidea 8600GTM

---

### Post by no2498 on 2010-11-15
this helps me
ah and i think i had to restart my computer to make it work

this comes from the program cheese help faq's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you too

---

### Post by SeijiSensei on 2010-11-15
> **me.translucent said:**
> i running ubuntu 10.10 , the graphic card i have is Nvidea 8600GTM

Use the "Additional Drivers" application to install the proprietary Nvidia driver, then tell totem to use VDPAU for its video output.  It should hand the task of decoding the files over to the Nvidia GPU.

Personally I prefer smplayer over all other media player options; it works flawlessly with VDPAU.

---

### Post by petran79 on 2010-11-15
it may also have to do with the  sound driver. Have you tried to play the video with sound disabled?

---

### Post by me.translucent on 2010-11-15
> **no2498 said:**
> this helps me
ah and i think i had to restart my computer to make it work

this comes from the program cheese help faq's

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    


hope it helps you too

yes i had set it to ximagesink instead of xvimagesink but the reason i did so is that xviimagesink gives me negative colors in the videos :(

---

### Post by me.translucent on 2010-11-15
thought using ```
videobalance hue=-1 ! autovideosink
``` with custom setting also solves the problem but i am not sure whether above option is using my CPU or Graphic Card.

---

### Post by no2498 on 2010-11-16
try changing the saturation in totem to 0
after it plays good reset to default 

hope that helps

---

### Post by wojox on 2010-11-16
Did you download all the drivers for Totem?

---

### Post by me.translucent on 2010-11-16
> **no2498 said:**
> try changing the saturation in totem to 0
after it plays good reset to default 
Qualification : Masters degree in Statistics / Economics / Commerce / MBA (Finance) / Econometrics with minimum 55% marks (50% for SC/ PWD). Candidates with a doctorate in topics related to the above subjects will be given preference

hope that helps

The problem of negative colors is with all the media players not just Totem.

---

