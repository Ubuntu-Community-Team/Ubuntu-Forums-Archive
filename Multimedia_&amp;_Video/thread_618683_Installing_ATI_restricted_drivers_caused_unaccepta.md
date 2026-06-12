---
title: "Installing ATI restricted drivers caused unacceptable mouse lag"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by MeanStreak on 2007-11-20
Hi,

I recently installed Ubuntu 7.10 and have been running it now for the last three days. It is my desire to replace my instance of XP in time. 

However, I've been experiencing unacceptable system freezes on a regular basis - mousing over a dropdown menu, for example, sometimes results in a freeze - the only solution being a system restart (on the plus side Ubuntu boots nearly six times as quickly as my bloated Windows installation).

Assuming this was a graphics card issue, I enabled the Restricted Drivers and installed the ATI drviers (from memory I am running an ATI 8300 graphics card) and restarted. It was then I noticed my mouse (basic Logitech wireless) movement lagging terribly and the left click not even registering at times. 

I've tried tweaking the mouse settings but to no avail. Note that upon load-up, the mouse appears to work fine (i.e moving mouse around the screen responds as expected) on the Ubuntu username/password screen but the lag then sets in once Ubuntu desktop loads up.   

I desperately want to resolve this lest I end up back in Windows-land. Any help is much appreciated.

---

### Post by stunner on 2007-11-20
If things work fine in GDM but not upon login, I would assume that there's something in your session that conflicts with your mouse.  You can look in System -> Preferences -> Sessions and look in the 'startup programs' and 'current session' tab for anything that looks like it might conflict.

Do other mice cause this as well?

---

### Post by MeanStreak on 2007-11-21
I have not yet tested this with another mouse. 

Regarding the session conflicts - could you be more specific as to what I am looking for that may be in conflict? I am surprised that Ubuntu would allow a conflict that affects the basic control of the mouse.

---

### Post by stunner on 2007-11-21
A few things:

1) what is the cpu usage like after you log in?  Hit alt+f2, run 'gnome-terminal' and inside there run 'top' and look at the %CPU column.

2) what is the exact model of the mouse?  I'm not too familiar with logitech mice, but I have read that they can be finicky with linux.

3) I would strongly urge that you try a simple, wired mouse (that is confirmed working on another system) - a $5 cheapie will do - just for diagnostic purposes.

---

### Post by stunner on 2007-11-21
Regarding the session conflicts - I'm thinking (a) a startup program that eats up a lot of cpu (not a conflict per se, but more or less the same effect), or (b) a mouse-related program that you placed yourself in the startup programs tab.  Power management can also interfere with mice, or so I've heard, but that doesn't seem like something you'd want to disable willy-nilly.

---

### Post by MeanStreak on 2007-11-21
Thanks for the suggestions. I have a wired mouse at home which I'll try tonight, however I should point out that the wireless mouse was working perfectly before I installed the restricted ATI drivers, also the fact that it works during login screen would indicate some other sort of problem. I'm going to try using VESA instead and see if that fixes the problem.

---

### Post by stunner on 2007-11-21
Good point - but if another mouse worked fine both pre- and post-login, I imagine that it would be useful info.

Decided to google around and found this - [http://ubuntuforums.org/showthread.php?t=214946]("http://ubuntuforums.org/showthread.php?t=214946") - kind of old and doesn't have much of a solution.  Hope vesa works out for you.

---

### Post by MeanStreak on 2007-11-22
Thanks for all your help once again. 

In a follow up: when I booted up Ubuntu last night, before the log in screen loaded, Ubuntu advised there was a configuration problem with the graphics and display and would therefore boot into low graphics mode (basically meaning VESA is applied by default). Low graphics mode results in no mouse lag and the problem seems to be solved. 

Of course it would be nice to use the 1024*768 settings - which my monitor supports and Windows provides out of the box - but beggars can't be choosers.

My graphics card is ATI Radeon X300SE.

---

### Post by stunner on 2007-11-23
Spent some time googling and searching the forums...it doesn't look like there's much I can say except maybe to recommend a new video card.  If 1024x768 is your standard resolution you may be pleasantly surprised by what a $30 videocard can do for you :)

---

### Post by MeanStreak on 2007-11-26
Might just have to take your advice on that! Thanks again! :)

---

### Post by Yellow Pasque on 2007-11-27
You shouldn't have to spend any money to get an X300SE working. I had one in my old box and it worked just fine with Feisty and Gutsy.

This doesn't sound like a video driver issue to me.

---

### Post by MeanStreak on 2007-11-28
Perhaps I haven't configured Ubuntu Gutsy correctly for the ATi Radeon X300SE - could you post your monitor settings?

---

