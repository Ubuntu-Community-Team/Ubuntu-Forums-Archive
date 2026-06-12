---
title: "GeForce 6200 - too slow"
date: 2010-07-07
forum: Multimedia Software
---

### Post by rabby_ on 2010-07-07
Hello,

Some weeks ago, I read a post about an ubuntu user who was wondering why his system had shown films and animations very slowly although high-end cpu, ram and a very new video card, whenever using two monitors (twinview). Some ubuntu experts found out that the reason had been some xorg.conf or nvidia-specific settings which made the X switching from display0 to another displayN and the other way round within a second, so fast that the user cannot see it, but slowing down the machine/output, of course.

My video card is not that new, it's a good, old GeForce 6200 and it is running with the latest nvidia driver that comes with ubuntu. First I thought, the video card is too slow for serving two monitors, but after booting Ms Windows on the same machine, I know that the geforce should be able to serve both monitors much (!) faster than it does currently at ubuntu.
Whenever i watch a film in fullscreen or even when watching a youtube clip or an animation, the display output slows down and even lags :-( No matter if it is some flash, .ogg or .avi. At least when switching into fullscreen mode, it's losing performance. Doing the same with Windows (not in vbox! but real booting...), runs properly.

If only one monitor is switched in, the performance is fine with ubuntu, too; but i'd really enjoy using both monitors without a such a loss of performance.

Is there a solution or is there someone who knows this problem already?

Thanks a lot for advice!

---

### Post by rabby_ on 2010-07-07
Btw. when trying to record the screen with istanbul, for an area of 200px*200px it looks like every 2nd frame is a black frame. So in the video with highest frame rate, it is obviously flipping between empty/black frames and the shown output.

/etc/X11/xorg.conf: [http://nopaste.info/7fb9b27845.html](http://nopaste.info/7fb9b27845.html)

---

