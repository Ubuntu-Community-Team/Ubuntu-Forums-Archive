---
title: "FireFox flash video fault"
date: 2009-12-20
forum: Multimedia Software
---

### Post by georgemcbaingage on 2009-12-20
This is a bit odd but it's beginning to annoy me, so if anybody can help I'd be grateful
I'm using 64 bit 9.10 on a laptop, all works well no problem,but.. In firefox if I visit the BBC site which I do, in the news sections I can watch flash video only if it auto-plays, if a “click here to play” button appears it will not work, very odd. Now as well as this when they auto-play I can watch them but the menu bar underneath fails to work so no pause or full screen. In Opera which I have also installed all works perfectly so must be firefox but I've spent ages looking and am stumped
Thanks in advance

---

### Post by madverb on 2009-12-20
This is a common problem. Do a quick search on the forums. There are quite simple fixes for this.

---

### Post by saltmore on 2009-12-20
Edit /usr/lib/nspluginwrapper/i386/linux/npviewer
add the following line BEFORE the last line of text
export GDK_NATIVE_WINDOWS=1
Save.
Restart any applications using flash.

---

