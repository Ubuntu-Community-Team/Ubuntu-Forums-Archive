---
title: "Gnome Panel Icons Animation"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by rogeriovinhal on 2007-04-08
Hello, I recently installed Beryl in my Ubuntu Edgy with XGL, but I am having some issues with that icon animation on gnome-panel.

I am talking about that animation, that even in metacity, comes up when you click in any icon on the gnome-panel. It is like a border that starts rising untill it fills the screen.

With XGL it seems to rise really slow, and it slows down the computer while it is rising. Icons from the Application menu run fine, just this animation is messing things up.

I couldn't find where I can disable it, is there a way to disable? Or even is there a way to make it work with XGL/Beryl?

Nevermind, just found it.

To whom might interest, this and other tips I found at:
[http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl](http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl)

---

### Post by Doc Horn on 2007-04-18
to complete this:
this is from beryl-project.org:
> You need to disable panel animations. Press Alt+F2 to get the "Run Application" dialog and enter "gconf-editor". From the gconf-editor browser, navigate your way to apps -> panel -> global. Uncheck enable animations. Close gconf-editor window; panel animation shall bother you no more.

---

