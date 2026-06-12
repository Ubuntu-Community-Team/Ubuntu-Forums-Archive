---
title: "Rosegarden Saving Problem"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by Affrikka on 2008-02-18
Okay i have been running Rosegarden on my dad's computer for a long time, and finally installed it on mine.
I write a big long piece, probably one of my best, and i try to save it.
 I get this message:

[B]Could not save document at /usr/share/apps/rosegarden/examples/fasd.rg
Error was : Could not open file '/usr/share/apps/rosegarden/examples/fasd.rg' for writing[/B]

my dad is on this whole "i am not going to help you anymore" thing and he also said that he honestly doesn't know what is wrong.
My dad and my computers are identical exept for the proccessor and the case that they are in. We both got it from Synaptic, I have tried uninstalling then reinstalling it a few times, and I get the same problem

thanks,

-Mathieu


**EDIT: I just tried saving it in my desktop, and it worked** but I would still like to be able to save it into the examples folder so I don't muck up my desktop with songs.

---

### Post by fredbird67 on 2008-02-25
This is nothing more than a permissions issue and is actually quite simple to fix.

All directories on your computer other than "/home/yourusername" require root-level access.  To access them using Gnome (I'm going to assume here that that's your GUI), you open a terminal, type "gksudo nautilus", enter your password, and a nautilus window will open up that you have root access in, and from there, you can save your work in /usr/share/apps/rosegarden/whatever.

Hope this helps!

Fred in St. Louis

---

### Post by Affrikka on 2008-02-25
thanks so much!

---

