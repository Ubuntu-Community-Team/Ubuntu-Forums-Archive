---
title: "Matlab figure fonts: broken in 11.04"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rgbrown on 2011-04-14
I would love to post a bug report, but I have no idea what the package in question is.

Basically, in 11.04, Matlab doesn't render fonts correctly in figures, it just uses some default (Java I think) font. In 10.10 this doesn't happen. This is a big deal for me; I'm a mathematics lecturer, and I need to be able to create graphics using Matlab. If I have no control over figure fonts then I can't afford to upgrade.

Screenshots of the same figure in 10.10 and 11.04 are attached. If anyone has any idea where the bug is, I'd like to post a bug report.

edit: I should mention it's the same Matlab version (R2010b) - in fact I copied the directory across directly from 10.10 to 11.04. Also, Matlab comes with its own Java.

---

### Post by aljazek on 2011-04-14
Wow, really? I have to try this, because I also use MATLAB every now and then.

---

### Post by dienalsmith444 on 2011-04-14
it should be the size of the screen. I tried setting the figure's  position property to the value returned by get(0, 'ScreenSize').

---

### Post by shafin on 2011-04-14
You can try [this solution]("http://www.mathworks.com/support/solutions/en/data/1-12NHPX/index.html?product=ML&solution=1-12NHPX"), by changing the matlab plot's font. To make it parmanent, add it to startup.m file.

---

### Post by rgbrown on 2011-04-14
Thanks, but that wasn't it. I can't get it to display *anything* other than the small font in my 11.04 screenshot. Changing the font, changing the font size, etc. all make no difference.

---

### Post by rgbrown on 2011-04-21
Marking thread as solved (although it only sort-of is)

I couldn't fix the problem in 11.04, so what I did was upgraded a 10.10 distribution which had a properly functioning Matlab to 11.04, and lo and behold, found that the fonts still worked. Still no idea why the problem occurred in the first place.

---

