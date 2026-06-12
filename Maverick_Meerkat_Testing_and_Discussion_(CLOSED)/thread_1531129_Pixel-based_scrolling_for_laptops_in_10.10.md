---
title: "Pixel-based scrolling for laptops in 10.10?"
date: 2010-07-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NoBugs! on 2010-07-14
Would it be possible for [this]("http://brainstorm.ubuntu.com/ideatorrent/idea/4849") to be done in 10.10? The jumpy scrolling makes sense for mice that have scroll-roller that "clicks" up and down, but on laptops this doesn't make sense, it should have ability to gradually scroll, like dragging the scrollbar, similar to how mac os does.

---

### Post by jpeddicord on 2010-07-14
I know someone working on this, but the impression I got is that it will take a while to be developed. Everything from the kernel and X to GTK and some end-user applications have to be modified for it to all piece together.

---

### Post by NoBugs! on 2010-07-15
Right now, when you move in the touchpad scroll region for some distance (call it D), it scrolls 3 lines. Would it be possible to set it to scroll 1 line, every D/3 distance? Combined with acceleration for fast scrolling, this could make it much better for scrolling and reading...

---

### Post by jpeddicord on 2010-07-15
Haven't found any concrete answers, but this thread may be of use:

[http://ubuntuforums.org/showthread.php?p=7416951](http://ubuntuforums.org/showthread.php?p=7416951)

---

### Post by sylvester_0 on 2010-07-15
I'm not sure if you're talking about having this system-wide, but I've pretty much managed this in firefox. I use it with the Lenovo TrackPoint middle button scroll.

1. Go to the URL about:config
2. Filter for "general.smoothScroll"
3. Double click to make it True.

I quite like this more than the default behavior. I'm not sure why the other action is the default. Some scroll wheels on mice are continuous - there's no "clicking"/stopping points.

---

### Post by crjackson on 2010-07-15
In firefox go to Edit>Preferences>Advanced and tick the option for smooth scrolling.

---

