---
title: "Make VLC My Default DVD Player"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by rpainter on 2008-03-24
OK. I have searched these forums. I have searched Google. Nothing that is suggested works.

I am running 8.04. I currently have VLC set as my default player for AVI files. I want it set as the default for DVDs. Right now, when I insert a DVD in to the drive, it opens with Totem.

I have gone to System>Preferences>Removable Drives and Media, and there is no "Multimedia" tab. 

I have tried setting VLC as the default in the Preferred Applications...no luck...still opens with Totem.

I also tried something in the configuration editor (though I can't remember what).

Please help me. This really should not be so freakin difficult!!!

Thanks.

---

### Post by rwpritchett on 2008-03-24
Try this thread:

[How can I set the default dvd player to VideoLan? ]("http://ubuntuforums.org/showthread.php?t=333714&highlight=set+default+media+player+VLC")

---

### Post by rainwalker on 2008-03-25
You have no "Multimedia" tab? That's very odd...
Anyway, I guess it wouldn't be much help, but I attached a screenshot of my multimedia settings window if you need it

---

### Post by rpainter on 2008-03-25
> **rainwalker said:**
> You have no "Multimedia" tab? That's very odd...
Anyway, I guess it wouldn't be much help, but I attached a screenshot of my multimedia settings window if you need it

Nope...no Multimedia tab. Is this a bug with 8.04? Attached is a screenshot of what I have.

---

### Post by xc3RnbFO8P on 2008-03-25
Here is mc4man solution:
[http://ubuntuforums.org/showpost.php?p=4555475&postcount=19]("http://ubuntuforums.org/showpost.php?p=4555475&postcount=19")
and here is about missing tab (in same thread):
[http://http://ubuntuforums.org/showthread.php?p=4474243]("http://http://ubuntuforums.org/showthread.php?p=4474243")

---

### Post by mc4man on 2008-03-25
The link redirect was a  temporary fool around solution  - here is a better way - take care though if you have previously edited defaults.list  except as suggested or have edited mimeapps.cache or .list.
Just retested from fresh install - works very well. no issues
Basically 3 steps - edit default.list , edit 1st. vlc.desktop, edit 2nd vlc.desktop
To access media default settings - edit menus>preferences> check box for file management
[http://ubuntuforums.org/showthread.php?t=733559](http://ubuntuforums.org/showthread.php?t=733559)   #8

---

### Post by rpainter on 2008-03-25
Cool. Thanks. I will try give that a try in the morning.

---

### Post by djben75 on 2008-05-26
I have a strange problem! Cant get vlc to autostart because it is not an option in my media tab! I only have open folder, do nothing or open with media player!

---

