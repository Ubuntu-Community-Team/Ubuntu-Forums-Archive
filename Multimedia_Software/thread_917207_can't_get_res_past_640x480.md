---
title: "can't get res past 640x480"
date: 2008-09-11
forum: Multimedia Software
---

### Post by TheVirtualMember on 2008-09-11
Hey. I was using Ubuntu for a while with a 19" LCD I had. It worked fine. Then I moved the LCD to somewhere else, and used a CRT with my computer. With the CRT in Ubuntu, the highest res I can go up to is 640x480. I've used the same monitor, same video card (and same machine) on Windows (different partition), and the res has been well past 640x480. Anyone know why it only happens with Ubuntu? Could it be an issue with drivers?

---

### Post by TheVirtualMember on 2008-09-12
Anyone have any idea why I can't go past 640x480 only on Ubuntu? (sorry if i broke a bumping rule...)

---

### Post by xc3RnbFO8P on 2008-09-12
try
atl+f2
gksudo displayconfig-gtk
Choose Generic
and resolution that your monitor supports.

---

### Post by TheVirtualMember on 2008-09-12
Okay, I sort of found the problem. Ubuntu thought that the CRT was still the old LCD. I changed that, and now it works well in my user, but for the log in screen, I think i"m only seeing a portion of the screen. I can log in, but I can't see the the shut down buttons from there. Anyone have an idea to fix that? Not a huge issue, but still annoying.

---

### Post by bobwalters on 2008-09-17
It seems odd that config utilites are not available from a menu; is there a place that documents how to bring up those types of configuration applications? I have looked through the documentation but I have not found them.  It would be real handy do have a list along with how to access them.

I've done some further thinking on this and I have a suggestion.  Afterall it is supposed to be open source.  It seems to me it would make sense for there to be a configuration menu that would show all the various configuration items. It could be made available as a password protected option.  This would be an enormous help to those of us, who may be familar with computer hardware but are new to Linux.  As it is there are way too may items that have to be accessed from command line.

Bob

---

