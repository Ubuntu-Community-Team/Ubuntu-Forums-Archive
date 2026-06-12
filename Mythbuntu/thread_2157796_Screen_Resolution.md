---
title: "Screen Resolution"
date: 2013-06-26
forum: Mythbuntu
---

### Post by drewdin on 2013-06-26
Im running mythbuntu .26, through an hdmi cable to a pioneer tv. Both picture and sound work well, the issue I am having is that the screen resolution is bigger than my monitor.  im not really sure how to fix the issue, I went into the NVIDIA setup an dtried adjusting the sliders and although i was able to shrink the screen to fit, it didnt fit right. It gave me black lines that were unusable on the sides. 

oes anyone have any instructions on what I should look at to fix the issue? Thanks

---

### Post by papibe on 2013-06-26
That looks like an [Overscan]("http://en.wikipedia.org/wiki/Overscan") problem. In other words, a setting on the TV itself not in the computer.

For instance: in my Sony Bravia the settings is under the screen menu, the value "Full Pixel". In my brother's Samsung is something like Picture Options -> Screen Size ->  P.size to 'Full Scan'.

I'd start navigating into your TV's menu for a similar option, and checking the TV's manual.

Let us know how it goes.
Regards.

---

### Post by drewdin on 2013-06-26
I just went through my TV setup, I dont have any settings labeled Screen size or P Size or anything size. In the manual for my TV, I have the following resolutions for the HDMI Inputs. 1920x1080, 720x480p, 1280x720p, 720x480 and 1920x1080p. Using the VGA input I would have 1024x768 and 1360x768 all at 60Hz.

I ran a xrandr and got the following settings:
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 952mm x 536mm
   1920x1080      30.0*+   24.0     30.0  
   1440x480       30.0  
   1280x720       60.0     59.9  
   720x480        59.9     30.0  
   640x480        59.9  


Any Suggestions? Thanks

---

### Post by grunge09 on 2013-06-26
in Mythtv, goto Utilities/Setup, then Setup, then Screen Setup Wizards and you can adjust the picture form there.  May have to save and exit mythtv frontend for changes to take effect.

---

