---
title: "fullscreen tv-out"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by zoryn on 2006-08-14
I have ATI tv-out working, but the resolution in the TV is smaller, so when I watch a full-screen video, it never shows the entire video, if you know what I mean (the TV is 1024x768, the monitor is 1280x800, so the TV only shows 1024x768 portions of the monitor).
Is there any way to do the same thing the windows ATI drivers do, which displays the video fullscreen in the TV, with the right resolution, even if the player is not fullscreen?...
Even if it's not possible, I would be happy with the video only displaying in the TV, but with the right resolution.

---

### Post by zoryn on 2006-08-15
bump?

---

### Post by isharra on 2006-08-15
It sounds like you are running in clone mode, so you're limited to a "viewport" which is a section of the monitor's display.

Set up the display as a dual head. then set the resolution for the tv using the screen resolution utility.
 
see 'aticonfig --help' for more info :)

---

### Post by zoryn on 2006-08-15
Exactly. I guess there's no way to use a video player to display only in tv-out, and in full-screen...?

---

### Post by isharra on 2006-08-17
To clarify. Using the ati drivers (fglrx) I have set up my desktop with video display on both screens (dual head). The tv is properly scaled and I can display full screen video on it.

The setup was done using the aticonfig command. Type the command 'aticonfig --help' to see the available options.

---

