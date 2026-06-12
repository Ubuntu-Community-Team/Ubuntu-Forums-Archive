---
title: "Why are videos on Ubuntu Jerky?"
date: 2009-09-27
forum: Multimedia Software
---

### Post by SteveDee on 2009-09-27
Don't worry, I'm not asking for help, I just wanted to share this with you.

I was recently given three old Compaq D510 USDT computers. These are very well built, small footprint, fan-less processor machines based on a Pentium 4 running at 1.7GHz.

They are very quiet and tick along drawing only 30-40Watts. So I thought one of these would be ideal connected to my TV to play videos previously recorded via MeTV. But running various MPlayer derivatives on Ubuntu 9.04 always resulted in frame-drop, not dreadful but enough to be very irritating, especially when the scene included people walking or cars driving across the screen.

I tried various "fixes" including doubling the amount of RAM and switching from Ubuntu to Xubuntu (both of these options helped a little). But the greatest improvement came from running mplayer from the terminal with a command line something like:-
mplayer -fs WhateverFile.mpeg

I don't know why this should be better than a GUI version of MPlayer, like SMPlayer or Gnome MPlayer. But it was good enough that I even wrote a simple GUI (in Gambas) so a casual user can select a video file and launch MPlayer in a shell. Now I rarely notice a dropped frame or a jerk (maybe once or twice an hour), so long as the pc is not running other apps at the same time.

As a final test, I reduced the RAM back to 512MB and booted the system into Puppy Linux from a memory stick. After installing MPlayer, I sat back and watched "The Lake House" without a single glitch (..apart from every half hour when Puppy saves RAM to a file on the memory stick, but I think this is easily fixed).

However, what I think this proves is that MPlayer and the hardware are adequate for the task, and that there is still room for improvement with Ubuntu...maybe 9.10 will perform better.

---

### Post by Huufarted on 2009-09-28
The major culprit in your issues is the video chipset.  Sounds like it's an intel 915 or something.  Confirm/deny?

---

### Post by arnab_das on 2009-09-28
even i face this "jerky" videos issue but only whe it comes to watching flash streaming videos in full screen.

---

### Post by SteveDee on 2009-09-28
> **Huufarted said:**
> The major culprit in your issues is the video chipset.  Sounds like it's an intel 915 or something.  Confirm/deny?

Well, according to Device Manager its an Intel 82845G/GL/GE, but I can't bring myself to blame it. After all, it copes just fine when "driven" by Puppy Linux.

According to stickies like this one: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) there are issues with Jaunty. Elsewhere on the forum there are reports that graphics performance took a knock with the introduction of Hardy, and that Intrepid is better than Jaunty.

My own view is that this is a compound problem created by many issues. The fact that Xubuntu is noticably better than Ubuntu may indicate that Gnome is playing a major role in this. However, while I can see that when I force cpu usage to 100% frames are dropped, playing a video on Ubuntu normally shows a fairly steady cpu% of 65-75%, while Xubuntu is typically no more than 10% lower.

It has been suggested that modifications to xorg, the Intel driver, the kernel, and the intro of Karmic will improve some of these video issues. And with less than 5 weeks until release, I guess I don't have too long to wait!

---

