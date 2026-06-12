---
title: "Nvidia twinview dual screen different resolution"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by holr on 2008-03-17
Hi,
   I have ubuntu 7.10 32 bit installed with the latest nvidia drivers 169.12 running on a 3rd gen macbook pro (the one with a 256mb nvidia 8600). Using the nvidia-settings (the gui control panel) I can easily get a large desktop across two monitors, using twinview. The problem Im having is this (it may be more of a configuration issue):

The macbook screen is running at 1440x900 and the external screen at 1280x1024. It seems that, using the gui tool, i end up with a desktop effectively 2720x1024 (1440 + 1280 = 2720). This is fine, but as the vertical resolution of the one screen is 900, there is effectively a section at the bottom that I cannot see as it is extended to 1024. 

I remember in the past being able to use something like panning to get the screen to virtually "scroll" down so I can access this lower part, but even playing with the advanced options in the gui tool, this doesnt seem to help.

Im very much working in a mobile environment so I don't want to set any settings permanently in my xorg.conf, I am happy to have the single 1440x900 screen initially then use the gui tool to enable twinview.

Any ideas would be much appreciated!

---

### Post by askreet on 2008-03-17
I dont know if you will find this helpful but I use an external 20" monitor at work with my Dell D610.  I wrote a script to invoke xrandr for dual-screen configurations:

Here is the code:
```
#!/bin/bash
xrandr --output TMDS-1 --mode 1680x1050
xrandr --output TMDS-1 --right-of LVDS

```

TMDS-1 is the name of my external DVI port, you may have to invoke 'xrandr' from a command-line to get the correct output name for your external monitor.

---

### Post by holr on 2008-03-18
I feel a bit silly now, the option I needed was in the nvidia-settings all along. I just wasnt using it right. I went back into X Server Display Configuration, selected the shorter of the two screens (i.e. the 1440x900 apple laptop lcd) hit Advanced, and changed panning from 1440x900 to 1440x1024 (to match the Y axis of the other screen) and hit ENTER. This was what I wasn't doing before, was pressing enter. I was using the mouse to click elsewhere, so the setting wasn't activated, as it were. All's well that ends well!

---

