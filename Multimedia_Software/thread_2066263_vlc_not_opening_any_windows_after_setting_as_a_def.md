---
title: "vlc not opening any windows after setting as a default application"
date: 2012-10-04
forum: Multimedia Software
---

### Post by Elwro on 2012-10-04
12.04 64bit.

I set vlc as a default application for mkv files using Nautilus.

Now vlc does not work at all. If I open any video file, simply nothing happens. If I run it from the terminal, a vlc icon appears on the taskbar, and vlc menu is visible at the top of the screen. However, none of the options do anything - I can click e.g. "open file" and just nothing happens.
Even quitting does not work - I have to kill the process.

What's more, I already reinstalled vlc (removed it using the software center and reinstalled using "sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc"). The problem persists.

I'd really appreciate any pointers!

---

### Post by Elwro on 2012-10-06
Let me just add that doing "aptitude purge vlc" and reinstalling vlc did not help at all!

---

### Post by Elwro on 2012-10-06
Doing the purge, and then deleting the hidden $HOME/.config/vlc directory did the trick at least partially: the program now works, but sound is garbled.

---

