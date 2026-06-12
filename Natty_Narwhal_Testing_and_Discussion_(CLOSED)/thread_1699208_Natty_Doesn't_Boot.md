---
title: "Natty Doesn't Boot"
date: 2011-03-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jqdennis on 2011-03-03
Created a VM with Natty 386 ISO on Dell D630.  The VM boots, shows Ubuntu 11.04, then a dark maroon screen with a blinking cursor.  That's it.

---

### Post by jerrylamos on 2011-03-03
I've installed the 02 March CD Daily build on four test pc's so far, two run Unity 3D another is a Thinkpad T40 that won't do Unity but does classic, the fourth has intel i845 video graphics - Compiz crashes on i845 starting with Intrepid so it's blacklisted on the i845 video.  At the moment Compiz is likely to crash on all of them except the i845 where it doesn't even start.

Now on a couple of them I got a purple splotch screen with cursor. 
What I did:
Ctrl-Alt-F1
login if asked
sudo service gdm stop
sudo service gdm start

At which point after a pause it switched to the graphic screen, and a bit later the desktop showed up.

At Alpha level some various tricks are needed.

I tend to use multiple partitions on my test pc's so if one partition fails there's another to fall back on.  I don't know about VM.

Good luck, Jerry

---

