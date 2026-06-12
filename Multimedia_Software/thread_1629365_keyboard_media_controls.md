---
title: "keyboard media controls"
date: 2010-11-23
forum: Multimedia Software
---

### Post by resination on 2010-11-23
I have a [Microsoft Digital Media Keyboard 3000]("http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=083").  I really only use the media player controls (back/forward/play-pause/stop), and they do appear to work.  There is, however, a side effect.  Whenever I use one of the buttons, I lose the ability to use the left mouse button until I do a restart.  Right clicking appears to work, but I cannot click on anything with the left mouse button.

Has anyone see anything like this?  I can just not use the buttons, but I did buy this keyboard specifically for these buttons so that I can skip music.  Works fine in Windows 7.

I'm close to Ubuntu being a 100% replacement for Windows, but this will nag at me.

Computer:
Dell Vostro 200
Nvidia GTS 250 (w/ Nvidia driver)
MS Digital Media Keyboard 3000
Logitech G500 Mouse

Software:
Ubuntu 10.10 32bit (fully updated)
Rhythmbox 0.13.1
Also using Docky w/ Rhythmbox Controls Helper

---

### Post by Yellow Pasque on 2010-11-23
Interesting. You might want to look at this to get an idea of what;s going on (or to make a bug report).
```
sudo apt-get install x11-utils
xev
```

---

### Post by monoxide.tryst on 2010-11-23
I am having the same problem

---

### Post by resination on 2010-11-25
I tried running xev.

When I use a keyboard media button, it shows:

FocuseOut Event...
ButtonPress Event...
FocusOut Event...
FocusIn Event...
KeymapNotify Event...

There's data after each event, but i didn't write it down. (and I haven't a clue how to copy it or screenshot it without scrolling the data off the screen)

After I push a keyboard media button, xev shows nothing when I click the left mouse button.

I'm not sure how to do a bug report.  Can someone point me in the right direction?

---

