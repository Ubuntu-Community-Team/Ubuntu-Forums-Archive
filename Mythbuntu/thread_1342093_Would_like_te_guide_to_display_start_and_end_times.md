---
title: "Would like te guide to display start and end times"
date: 2009-11-30
forum: Mythbuntu
---

### Post by My Name on 2009-11-30
i have noticed in 9.10 that the tv guide doesn't show the start and end times of programmes any more. It now requires you to press the info button to get that kind of detail.
It's fine if a programme starts on the hour or half past but when a programme starts at an odd time, there is no easy way to see when it starts.

Is this fixable?

---

### Post by My Name on 2010-01-12
Does anyone have this as an issue
Seems odd that I am the only one that uses this info.
Just to be clear, this is the info I'm missing...
[IMG]http://img229.imageshack.us/img229/1447/mythtvcopy.jpg[/IMG]

---

### Post by azmyth on 2010-01-12
You'll need to edit the schedule-ui.xml of the theme you're using or if not found look for the one in the default-wide.

Look for the section that says template and you'll see stuff like %LONGREPEAT%. You'll need to add what you want by looking at

[http://www.mythtv.org/wiki/Schedule-ui.xml](http://www.mythtv.org/wiki/Schedule-ui.xml)

Look at the Generic Attributes for example

%STARTTIME%

---

