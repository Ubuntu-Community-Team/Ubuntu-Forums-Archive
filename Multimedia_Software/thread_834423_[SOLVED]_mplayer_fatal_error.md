---
title: "[SOLVED] mplayer fatal error"
date: 2008-06-19
forum: Multimedia Software
---

### Post by chillyair on 2008-06-19
I receive the following fatal error message when attempting to run a video in mplayer.

Error opening/initializing the selected video_out (-vo) device.

Anyone know whats wrong or how to fix this?

---

### Post by hypocratus on 2008-06-19
You can try changing to ~/.mplayer. There should be a file called config in that directory. Open that file and see if there is a line with vo=. If there isn't try adding the line vo=xv . If the line is there with something else, try commenting it out by putting a # in front of that line. Save the file and try mplayer again.

---

### Post by chillyair on 2008-06-20
> **hypocratus said:**
> You can try changing to ~/.mplayer. There should be a file called config in that directory. Open that file and see if there is a line with vo=. If there isn't try adding the line vo=xv . If the line is there with something else, try commenting it out by putting a # in front of that line. Save the file and try mplayer again.

I'm assuming this is all done in the command line. If that is the case could you provide a little more explanation cuz i'm kind of a novice with it. 
Thanks

---

### Post by logos34 on 2008-06-20
in your home directory look for folder .mplayer.  Click on file named gui-conf.  It should open in text editor so you can edit it.  Or open mplayer config/preferences and change the video driver there

---

### Post by chillyair on 2008-06-26
OK found the gui.config file. There is a lot of jibberish code in it and i'm still not sure exactly what part im supposed to edit. Here is the top part of whats in the file


enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "-1"
v_ni = "no"
v_idx = "-1"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"

---

### Post by logos34 on 2008-06-26
> **chillyair said:**
> vo_driver = "xv"

try "x11" or "gl" instead

---

### Post by chillyair on 2008-06-26
> **logos34 said:**
> try "x11" or "gl" instead


Tried them and they both worked. 

Thanks

---

### Post by logos34 on 2008-06-26
cool. enjoy

---

### Post by geezerone on 2008-08-28
> **chillyair said:**
> I receive the following fatal error message when attempting to run a video in mplayer.

Error opening/initializing the selected video_out (-vo) device.

Anyone know whats wrong or how to fix this?

Getting same error. I changed to x11 and no error but playback is only displayed in a window 2 inches square regardless of how I change view.:confused:

---

