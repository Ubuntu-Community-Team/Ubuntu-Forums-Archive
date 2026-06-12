---
title: "vlc won't play videos"
date: 2009-10-15
forum: Multimedia Software
---

### Post by snakeman21 on 2009-10-15
I have used vlc as my main media player for a while now, and until now, it has never given me any problems.  I recently reinstalled (Karmic) and now vlc refuses to play videos.  I installed with sudo apt-get install, and when it didn't work, I removed it and reinstalled via the Ubuntu Software Center.  It worked fine before, and I was running Karmic then as well.

It plays music files just fine, but when I try to open a video, the interface pops up only for a split second, then disappears.  There is no crash report when this happens.

I have tried .avi, .mp4, .wmv, .mpg, .flv, .rm, and DVD .iso's.

---

### Post by mc4man on 2009-10-16
It could be your video output module which by default is set to 'default', usually meaning Xv.

If you open vlc -> tools -> preferences and click on the video icon you can set the output in the dropdown.
you could try XVideo directly, though your best bet may be X11 or OpenGl 

Remember to click save or press enter on keyboard after changing. ( sometimes also better to close and re-open vlc.

If the vo is the issue and it used to work with the default (Xv) setting or none of the 3 work then you may want to look at the state of your video drivers ( intel and ati display adapters seem to be a bit of hit or miss

running vlc from the terminal as such could provide relevant info ( and a wee bit more

```
vlc -vv
```

If you think you need to reset vlc from any adjustments then this will return to install defaults

```
vlc --reset-config --reset-plugins-cache
```

---

### Post by snakeman21 on 2009-10-16
mc4man: 

Thanks a lot, setting it to OpenGL did the trick.

I appreciate the help!

---

### Post by mickie.kext on 2009-12-16
Um... I have exact same problem, but setting output to X11 and OpenGL did not help. I had that problem right from day one with Karmic, but I just used another player. Now I installed Ubuntu to friends computer, and he wants VLC. So I want to fix this both for me and for friend... hopefully with your help:D.

[Here is]("http://pastebin.com/m3107dd49") full terminal output from my computer. When VLC is started, I try to load video from hard drive via Media --> Open file command, and video just does not start. When I click play nothing happens. From terminal output, I can say that it wants Qt libraries... but I had KDE 'till couple of weeks ago when I reinstalled Ubuntu. When I had KDE, VLC worked just from KDE, for GNOME was same like now - non working. So I am not sure if installing KDE will actually help, since I do not intend to use it and sure not intend to install it to a friend who have 56k dial-up and 768MB of RAM.

Any thoughts?

---

### Post by snakeman21 on 2009-12-16
Sorry dude... I actually reinstalled about a week ago, and had the same issue again.  But as before, setting the output to OpenGL fixed it.  I'm not very savvy in this particular area of ubuntu, so you're gonna be better off creating your own thread.  Maybe you'll get some helpful advice there.  Good luck :)

---

