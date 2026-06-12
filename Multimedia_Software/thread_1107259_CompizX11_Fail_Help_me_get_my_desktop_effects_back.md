---
title: "Compiz/X11 Fail? Help me get my desktop effects back on!"
date: 2009-03-26
forum: Multimedia Software
---

### Post by antipuls3 on 2009-03-26
Hey guys! New, enthusiastic Ubuntu 8.10 user here! I just jumped on this past Satuday, and it's been pretty fun getting everything working. But then this afternoon something happened. My compiz stuff is gone and I can't turn on any more effects (suddenly) than the basic of basic desktop effects.

I hit Ctrl-Alt-Backspace because I wanted to know what it did. That shuts down X11, right? What do I do to turn it back on?

In the console, I try to start "compiz"

and get:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

{edit}Back from a fresh reboot. After running "compiz" above, my minimize, expand, and exit buttons on the upper right of all my windows disappeared, and I had to reboot. What the heck... I really with I hadn't hit Ctrl-Alt-Backspace. Haha..

Fail.

What am I doing wrong/what can I do to get on the right track? Thanks to all who can help me! :-)

---

### Post by LordHypnos on 2009-03-28
> **antipuls3 said:**
> I hit Ctrl-Alt-Backspace because I wanted to know what it did. That shuts down X11, right? What do I do to turn it back on?

That would terminate the currently running X *session*, yes. Should return you to the X11 login screen. 
If you really want to kill X, you'd have to login via console (Ctrl+Alt+F1) and type "sudo killall gdm" (gnome) or "sudo killall kdm" (kde). You can start the x again, by typing "startx" to the console.

> **antipuls3 said:**
> 
What am I doing wrong/what can I do to get on the right track?


I suspect you might have updated the kernel of your ubuntu. I had the same problem this morning, when I booted up. I had to recompile the NVIDIA display driver module to get the eye-candy working again.

---

### Post by antipuls3 on 2009-03-28
> **LordHypnos said:**
> That would terminate the currently running X *session*, yes. Should return you to the X11 login screen. 
If you really want to kill X, you'd have to login via console (Ctrl+Alt+F1) and type "sudo killall gdm" (gnome) or "sudo killall kdm" (kde). You can start the x again, by typing "startx" to the console.



I suspect you might have updated the kernel of your ubuntu. I had the same problem this morning, when I booted up. I had to recompile the NVIDIA display driver module to get the eye-candy working again.

Ahhhh.... I did have updates. That's probably what the problem was. >_< So much to learn.

---

