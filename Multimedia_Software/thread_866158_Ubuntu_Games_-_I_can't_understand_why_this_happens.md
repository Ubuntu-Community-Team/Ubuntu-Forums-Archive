---
title: "Ubuntu Games - I can't understand why this happens."
date: 2008-07-21
forum: Multimedia Software
---

### Post by Krazeel on 2008-07-21
Hello,

I'm sorry for the non specificity of this thread's title, I guess it's hard for me to explain this problem. I'll give it a try:

What happens is that I installed some 3d ubuntu native games and a few that can run fullscreen -such as Wormux- and all of them give me a similar problem: after almost 5 minutes running the application, the window resizes automatically, showing part of the desktop and nothing responds. The only thing left to do in this situation is to restart. 
I've tried configuring every game to the lower settings and different screen resolutions, as well as figuring out what makes the screen pop out and I don't find what it can be.

I have a Geforce 7200 card and runs pretty well many modern games on medium settings.

What do you think I could do to solve this issue?:confused:

Thanks a lot for your time.

---

### Post by Lesouteneur on 2008-08-24
I have this exact same issue. It has happened with Tuxracer and Urban Terror. I always just log out and in again but it is extremely annoying. I have no idea what could be causing this.

---

### Post by brian mcgee on 2008-08-24
Try disabling visual effects.

rt click on desktop -> change desktop bkgrnd -> visual effects -> none -> close

Then play the game. I've had some trouble with visual effects and a couple games.

---

### Post by Krazeel on 2008-09-01
Thanks, I'll post again after I try that.

---

### Post by Lesouteneur on 2008-09-01
It worked for me :)

---

### Post by Krazeel on 2008-10-23
Hey thanks! It worked.
Long time has past but I haven't forgotten - I blame my ISP provider.

---

### Post by Ryan450 on 2008-11-01
> **brian mcgee said:**
> Try disabling visual effects.

rt click on desktop -> change desktop bkgrnd -> visual effects -> none -> close

Then play the game. I've had some trouble with visual effects and a couple games.

Yes disabling the visual effects does the trick for me to, however I like to have a bunch of compiz's plugins enabled and i've configured them via the compiz-settings-manager.

when i disable the visual effects, it restores the defaults to these plugins, so when i turn them back on I have to reconfigure them. Is there anyway i can save my compiz config to a file or something so i dont lose them when I re-enable it?

---

### Post by brian mcgee on 2008-11-02
> **Ryan450 said:**
> Yes disabling the visual effects does the trick for me to, however I like to have a bunch of compiz's plugins enabled and i've configured them via the compiz-settings-manager.

when i disable the visual effects, it restores the defaults to these plugins, so when i turn them back on I have to reconfigure them. Is there anyway i can save my compiz config to a file or something so i dont lose them when I re-enable it?  You might be able to restore your compiz settings from a profile. Check out the Preferences section of CompizConfig Settings Manager. Probably the easiest thing to do would be write a script to restore compiz after the game closes.    

If you select flat-file backend from CompizConfig Settings Manager, you might be able to script a restore from settings stored in /home/user/.config/compiz/compizconfig -- not real sure though.

Check out:
[http://ubuntuforums.org/showthread.php?t=604973](http://ubuntuforums.org/showthread.php?t=604973) 
[http://forum.compiz-fusion.org/showthread.php?t=6511](http://forum.compiz-fusion.org/showthread.php?t=6511)

---

### Post by eenofonn on 2008-11-03
compiz switch is the best option imo [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

