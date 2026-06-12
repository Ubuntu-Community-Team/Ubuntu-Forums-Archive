---
title: "VLC won't go to full screen properly"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-02-25
Hi,

Can anyone help me with this minor annoyance?  I installed vlc and it plays all my files, but when I put it in full screen display mode it won't cover the ubuntu task bars and the top bar with the min, max, exit buttons doesn't go away either.

I don't think this is a general video playing problem, because I also have democracy player and it goes to fullscreen perfectly.

Any suggestions for fixing?

Thanks,
Douglas

---

### Post by louis_nichols on 2007-02-26
VLC has a setting for video output module (in preferences - make sure you check the option for advanced settings). I suggest you change the module there to another. Just try them all until you find one that works better. At least, that;s what I do when I have suh problems.

---

### Post by djrobthaman on 2007-02-26
Thanks,

Tried a few of those but figured it was a bigger problem.  Will keep messing with it then.

Douglas

---

### Post by Engnome on 2007-05-07
I had the same problem and I found that checking "Alternate full screen method" in whatever module you are using solves the problem. If you are unsure which module you are using either select one or check "Alternate full screen method" in all of the modules.

Don't know if you've solved it but maybe someone will find this and benefit. :D

ps. don't forget to select "Advanced options" in preferences or else you won't see the Alternate full screen method checkboxes.

---

### Post by djrobthaman on 2007-05-09
Thanks,

I actually had got it to work, but still don't really know how.  Installed beryl and since then it goes to fullscreen fine.  So, I don't know if it was something that beryl or xgl did to the settings, but it works so I'm happy.

---

### Post by almalaci on 2007-05-10
> **Engnome said:**
> I had the same problem and I found that checking "Alternate full screen method" in whatever module you are using solves the problem. If you are unsure which module you are using either select one or check "Alternate full screen method" in all of the modules.

Don't know if you've solved it but maybe someone will find this and benefit. :D

ps. don't forget to select "Advanced options" in preferences or else you won't see the Alternate full screen method checkboxes.

Engnome, 
Thanks, checking the alternate full screen under X11 finally solved my same problem in a 64bit Feisty install. VLC has had various bugs in 64bit mode, but never in 32 bit. However it only had the full screen issue lately which is now solved!
Thanks a lot!

---

### Post by fakie_flip on 2007-06-06
I get a green line going across the screen horizontally when watching a movie in full screen. I checked the same movie with totem-xine, and the green line wasn't there. Has this happened to anyone else?

---

### Post by Pragmatist on 2007-09-05
> **fakie_flip said:**
> I get a green line going across the screen horizontally when watching a movie in full screen. I checked the same movie with totem-xine, and the green line wasn't there. Has this happened to anyone else?
I have the same problem.

---

### Post by Pragmatist on 2007-09-05
I followed this suggestion:
[http://ubuntuforums.org/showthread.php?t=447900](http://ubuntuforums.org/showthread.php?t=447900)

and "X11 video output" worked for me.  Now there is no green line.  However, now I have these little white brackets on all four corners!  I traded one obnoxious defect for another! :(

---

### Post by Pragmatist on 2007-09-05
Success! I made two changes in VLC Preferences:

1.) **Video-->Output Modules** and set "Video Output Module" to "X11 Video Output"

2.) **Video-->Output Modules-->X11**  and checked "Alternate Fullscreen Method"

Now there is no green line and no white things in the corners.  Finally! :)

---

### Post by djrobthaman on 2007-09-07
I used that alternate method for a while but foudn a better way to do it.  If you have the same problem as me (some keyboard shortcuts don't work all the time in full screen) then you could try it.

This only works if you're running compiz fusion though.  You just go into the settings and check the legacy fullscreen output checkbox and it works fine.  (Actually there's no need to do this with Trevino's latest build... just finished watching something in vlc fullscreen not 5 minutes ago no hacks necessary).

---

