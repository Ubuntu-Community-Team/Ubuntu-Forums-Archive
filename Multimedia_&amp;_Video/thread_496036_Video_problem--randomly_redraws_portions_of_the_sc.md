---
title: "Video problem--randomly redraws portions of the screen"
date: 2007-07-08
forum: Multimedia &amp; Video
---

### Post by sohanley on 2007-07-08
I have a new and strange problem occurring on my Feisty computer. Starting yesterday, the screen will suddenly, randomly (though sometimes coincident with me clicking the mouse or moving the mouse over a particular portion of the screen) redraw sections of the desktop (or whatever application I have open) with either all black, or strange colored lines across a black background, or sometimes with a different portion of the screen. For example, one thing that seems to happen often is that the desktop toolbar will be replaced by the titlebar of Firefox.

Often, when I wave the mouse over the affected portion, it will redraw what is supposed to be there; but this doesn't always happen. In addition, I've found that, sometimes, if I leave the PC alone for fifteen minutes and let the monitor go to sleep, when I come back and move the mouse, the monitor turns back on but is completely blank. I've tried switiching consoles using Ctrl+Alt+F1, but it doesn't do anything (I'm guessing maybe the graphics driver is hanging the system or something?).

I have an nVidia GeForce FX 5200 video card (I think). I'm using the nVidia accelerated graphics driver found the in the System-->Admin-->Restricted Drivers Manager menu option.

Here is the output of uname -a:
Linux izzo 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux

Please help! This is severely impacting my ability to get any work done at all, and I've scoured the forums looking for a similar problem with no success.

---

### Post by guitard00d on 2007-07-09
I would try using the basic Nvidia driver rather than the restricted version and see if the problem persists. If it does, then I would have to assume an error in your xorg configuration file, or the video card itself is faulty. If you can boot up and run off the Live CD without this problem occurring, then its an xorg configuration error or your video card just isn't compatible with the restricted Nvidia driver.

---

### Post by sohanley on 2007-07-11
I am now unable to even boot the desktop so that I could try disabling the restricted driver. Now, when I turn on the PC, the initial video card boot screen (which just has four lines of text, the first of which is "PNY Verto GeForce FX5400") is garbled--every other letter is missing or replaced by a random character, and there are random characters sprinkled across the entire screen-- @ symbols, smiley faces, and accented letters. The PC hangs on this screen and does not continue the boot process.

I'm doubtful that this would be a driver problem--it seems to me that if it's hapening right when it begins to boot up, it must be a virus of some kind. But I'm no expert on these kinds of things. Again, any help anyone could provide would be much appreciated.

---

