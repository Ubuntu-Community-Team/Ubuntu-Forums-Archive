---
title: "HP2133 Graphics issue"
date: 2008-08-21
forum: Multimedia Software
---

### Post by LonelyMoai on 2008-08-21
Howdy all. I'm extremely new to the linux scene so you'll pardon my ignorance if my question seems silly: generally when you have your graphics drivers installed correctly, do you see images(some)/buttons(all)/banners(all) distorted? Pictures look great, but the video is a bit choppy. Any input would be greatly appreciated.

---

### Post by jtappin on 2008-08-26
Quick answer: No

There are a number of issue that can arise, and I think we need some more information to determine which it is.

Most important: Which graphics drivers are you using? There is a known issue with the basic vesa driver trying to display at 1280x720 instead of 1280x768 (this is usually most obvious in text displays, where there are horizontal lines of distorted letters where the extra pixels are being filled in).

Also if you have transferred your home directory over from a non-widescreen machine, you may actually be forcing something like 1024x768 on the display, in KDE this can be rectified with the system settings tool (monitor & display) [not in administrator mode], I assume Gnome has an equivalent.

---

