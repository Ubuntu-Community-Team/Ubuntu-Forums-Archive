---
title: "Dual monitor setup"
date: 2007-03-13
forum: Multimedia &amp; Video
---

### Post by special on 2007-03-13
I have a nvidia Geforce 4 mx440 and am trying to have two monitors(one a lcd monitor and the other a TV) showing the same thing at the right resolution. I can get the both monitors working but can get the resolution on both to work properly. LCD 1280x1024 and TV 1024x768. Please help fairly new to linux.

---

### Post by veloce on 2007-03-13
are you using twinview?  This is supposed to make dual monitors easier for nvidia.

I can't quite understand what you are trying to achieve. How can you have the same thing on each monitor if they are at different resolutions?

---

### Post by special on 2007-03-14
When I ran my computer as a windows based media center I was able to have both monitors showing the mirroring each other and both have the resolution set so that there was no distortion on either. But when I try to set it up i linux eather my lcd looks fine and the tv does not show the whole screen or the tv looks fine and the resolution on the lcd is horrible.

---

### Post by fenian on 2007-03-14
Make sure you have the latest Nvidia drivers (info on how to is [here]("http://www.albertomilone.com/latest_nvidia_udsf_edgy.html")).
After you have the latest drivers open a terminal and enter...

> gksudo nvidia-settings

In the window that opens there is a section 'X Server Configuration' where you can set all the settings for twin view.

---

