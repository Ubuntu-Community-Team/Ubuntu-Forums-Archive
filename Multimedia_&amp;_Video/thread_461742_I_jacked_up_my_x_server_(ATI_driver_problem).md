---
title: "I jacked up my x server (ATI driver problem)"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by orbilius on 2007-06-02
Hello.  I am trying to get two things done in Ubuntu.  First, get either 1280x720 or 1360x768 resolution working, second I am trying to get the ati driver working for my Radeon 9600.

I ran:   sudo dpkg-reconfigure xserver-xorg      and selected ATI and the default settings for everything else.  Restarted x server and get a blue screen.  Cant log in.  Anyone know how to undo the damage I have done?  Thanks!

---

### Post by orbilius on 2007-06-02
I found out how to boot in to the terminal, but not sure what to do after that.  just a lame bump here.

---

### Post by marchar on 2007-06-03
I'm also working on getting my ATI 9600 driver working..

try choosing VESA instead of ATI from the video list in the xserver-xorg reconfiguring routine.

Worked for me to get my desktop back..

---

### Post by orbilius on 2007-06-03
Update: I removed my Radeon 9600 Pro and reinstalled my Radeon 7000.  Much slower card, but the ATI driver works.  I can run it in 1024x768 max right now.  I would like to get it to output 1280x70@60hz to my monitor but do not know how.

---

### Post by orbilius on 2007-06-04
Got windows working at 1360x768 with the following timings (see attached pic)

---

