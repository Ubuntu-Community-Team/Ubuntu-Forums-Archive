---
title: "[SOLVED] How to determine display where program windows open?"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by thepanu on 2007-08-27
I have dual screen setup with nvidia 6800 which is working fine except for one thing.

Some programs open their window at my secondary display (tv), which is annoying cause I don't keep it on at all times. So how can I set programs to open only in my primary screen?


**Solution (For KDE):**
> Left click on program icon on upper left corner of window -> Advanced -> Special Window Setting

And from there Geometry tab check Position and select Remember from drop down menu.


---

### Post by ddrichardson on 2007-08-27
Which window manager are you using - is it the default (Metacity) or one of the super all singing all dancing compositing ones?

---

### Post by thepanu on 2007-08-27
Just plain KDE from Kubuntu. Nothing added to it.

---

### Post by ddrichardson on 2007-08-27
It's just the metacity doesn't support window placement options. I'm sure KDE has an option to remember window positions with apps when they exit. You could change shortcuts to specify the position they are loaded at but I'm sure someone has a simpler, more elegant solution.

---

### Post by thepanu on 2007-08-28
Most of the programs do remember thei preference when exiting. Biggest problem are firefox popups opened with javascript.

---

### Post by ddrichardson on 2007-08-28
You can disable javascripts ability to move and resize windows from preferences/content

---

### Post by thepanu on 2007-08-28
Didn't help. I thin it would help if it were existing window that is moving. But this problem occurs when opening popup-window. 

When I start firefox normally it does open in correct screen, problem occurs only with popups.

---

### Post by ddrichardson on 2007-08-28
There's a Firefox extension you can try:
[https://addons.mozilla.org/en-US/firefox/addon/4073](https://addons.mozilla.org/en-US/firefox/addon/4073)

---

### Post by thepanu on 2007-09-04
That extension doesn't solve the problem. And now, after I installed Google earth I noticed that it also opens new windows in secondary display and it doesn't remember last place said windows was closed.

So problem summary:
-Firefox popups open in secondary display
-Google earth settings windows open in secondary display (Atleast Flightsimulator windows)
-New Firefox windows open correctly in primary display (ie those that aren't forced into certain size)

Is it really so, that no one else has similar problem with me?

---

### Post by eentonig on 2007-09-04
You could try to investigate devilspie. It allows you to create rules which specify how to handle certain windows.

---

### Post by thepanu on 2007-09-04
Problem solved. ddrichardson was correct in his assumption that there is elegant solution to this problem in KDE.

Left click on program icon on upper left corner of window -> Advanced -> Special Window Setting
 
And from there Geometry tab check Position and select Remember from drop down menu. 

Really simple and works flawlessly.

Found solution from here: [http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

When trying to figure out how devilspie works. So thanks eentonig for that tip.

---

### Post by ddrichardson on 2007-09-04
Great, well we all learned something new! Can you mark the thread as solved?

---

