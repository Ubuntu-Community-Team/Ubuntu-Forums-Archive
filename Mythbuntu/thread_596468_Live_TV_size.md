---
title: "Live TV size"
date: 2007-10-29
forum: Mythbuntu
---

### Post by ghostwalker50 on 2007-10-29
how do i make my live tv to stay at 16/9. i tryed the apperence and set it their but no change. even tryed a restart of the system.

---

### Post by superm1 on 2007-10-29
First, make sure that you are using a 16:9 resolution.  You may need a proprietary driver to do this.

Next make sure that you have a 16:9 video source.  Typically these are HD sources or digital sources only.

Lastly, if you need to, you can force the type of monitor that is recognized in mythfrontend's setup->appearance section.

---

### Post by ghostwalker50 on 2007-10-29
> **superm1 said:**
> First, make sure that you are using a 16:9 resolution.  You may need a proprietary driver to do this.

Next make sure that you have a 16:9 video source.  Typically these are HD sources or digital sources only.

Lastly, if you need to, you can force the type of monitor that is recognized in mythfrontend's setup->appearance section.

my tv is a widescreen, and i know my video source is not HD or 16/9, but in the alfa verson it was full screen. im just the tuner. i go in to athe appearance section and tell it to use 16/9 and use same for live tv as gui. it does notton. is their and config file i can edit.

---

### Post by superm1 on 2007-10-29
> **ghostwalker50 said:**
> my tv is a widescreen, and i know my video source is not HD or 16/9, but in the alfa verson it was full screen. im just the tuner. i go in to athe appearance section and tell it to use 16/9 and use same for live tv as gui. it does notton. is their and config file i can edit.

This was the bug of the alpha version that you were encountering.  Odds are it was running at 1024x768, and consequently stretching the picture across the screen.  I'd be betting the final version is taking up the full resolution that your display can actually do.  Because of this, a video that is typically a 4:3 aspect ratio is being displayed *properly.  *Follow what I said and query the resolution of your display and follow up from there.

---

### Post by ghostwalker50 on 2007-10-30
thanks you for all the help :)

---

