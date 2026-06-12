---
title: "How Do I Play Video Through HDMI In ubuntu 12.04"
date: 2012-09-16
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2012-09-16
How Do I Play Video Through HDMI In ubuntu 12.04?

Thanks Hannibal:popcorn:

---

### Post by afulldeck on 2012-09-16
> **coljohnhannibalsmith said:**
> How Do I Play Video Through HDMI In ubuntu 12.04?

Thanks Hannibal:popcorn:

Once you've plugged into the HDMI port, you need to go to sounds and select HDMI as your sound device. I'm not sure why this doesn't happen automatically.

---

### Post by micahpage on 2012-09-16
if you want to have multiple displays, being one as HDMI:
system settings -> Displays 
mirror displays for the same output for both displays, turn on display for HDMI and apply and you should have an extended monitor going between the two

The sound on HDMI in 12.04 is however more difficult. IT seems the current kernel for ubuntu 12.04 is using 3.2 and have problems with HDMI sound. I think the newer kernel has fixed this problem.

---

### Post by coljohnhannibalsmith on 2012-09-16
Does the video have to be in a specific format or played with a certain player such as VLC?

Thanks Hannibal

---

### Post by micahpage on 2012-09-16
> Does the video have to be in a specific format or played with a certain player such as VLC?


vlc should be able to play most formats

What kind of format are you trying to play with vlc that doesn't work?

EDIT:
playing video through HDMI, it does not matter what format it is. At least I have never had any problems with any format.

---

### Post by coljohnhannibalsmith on 2012-09-17
I think I'm getting the idea; mirror the monitors, change the sound to HDMI, and play the video.  Seems to work.

However, I have another wrinkle.  Having to watch the video on both monitors is just annoying, and I loaded the xscreensaver because GNOME3 doesn't have one.  The screensaver works well enough, but I have to set it to blank the screen for a period that's longer than the movie.  I also changed the power settings to do nothing when I close the lid.  The hope was that the movie would still play and I'd only have to look at one screen.  Well it still blanked the screen anyway when I closed the lid.  My intermediate solution was to put a piece of paper over the laptop screen and try to ignore it, hardly an elegant solution.  Can any of you think of some settings I may have overlooked so that the movie will play with the lid closed.  This would be ideal!

Thanks Hannibal

---

