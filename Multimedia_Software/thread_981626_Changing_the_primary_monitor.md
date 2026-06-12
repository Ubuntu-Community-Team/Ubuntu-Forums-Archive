---
title: "Changing the primary monitor"
date: 2008-11-13
forum: Multimedia Software
---

### Post by mssever on 2008-11-13
With the release of Intrepid, dual monitor setups finally work mostly. However, for the setup to be usable, I need a workaround for Intel's dumb default.

My laptop has Intel graphics (Mobile GM965/GL960 according to lshw). When I plug in an external monitor, the external monitor becomes the primary monitor (where the panels live, etc.). This is actually the case in Windows, as well, and I've seen it on several laptops with Intel graphics. Of course, setting the external monitor as primary is stupid. Why would anyone want that? Imagine this: I'm giving a presentation, so I plug in a projector and start the presentation software. The presentation shows on my laptop while the presenter notes show up on the screen. Huh? What were the folks at Intel smoking?

Anyway, the Windows Intel drivers provide a hidden way to fix the primary monitor. But I can't find anything like that in Linux. Is there a way to make my laptop screen my primary monitor?

EDIT: Google didn't turn up anything relevant and recent, and [this thread]("http://ubuntuforums.org/showthread.php?t=975473") only deals with tools specific to ATI and nVidia. I'm hoping that a tool exists which is independent of the driver in question.

---

### Post by mssever on 2008-11-16
bump

---

### Post by Genogp on 2008-11-17
I am in the exact same spot as u are. There must be someone out that that can help?

---

### Post by mssever on 2008-11-21
Another bump

---

### Post by BrandonR on 2008-11-28
I am also having the same issue, I have a LCD TV connected to the VGA-out on my laptop (HP pavilion) as a second monitor (primarily for video playback). Unfortunately it always ends up as the primary monitor.  Obviously I can drag the menus over to the laptop LCD but all new programs open on the TV instead of the laptop LCD.

---

### Post by sleepitoff on 2008-12-01
BUMP again

Same question as the rest... How do I get fullscreen to show up in the external monitor and not on the laptop? Same graphics as mssever.

---

### Post by Genogp on 2008-12-02
Bump

---

### Post by sleepitoff on 2008-12-02
Woo! I figured out a workaround! 

Now, this might not be in the best interest of everyone with this problem, but this will work, but you'll loose access to your laptop for the time. 

Next time you log in, drag your main panel over from your notebook's screen to your external monitor's screen. Next, click System -> Preferences -> Screen Resolution. Notice your notebook's icon on the window? Select, and under the drop-down box for resolution, click 'off.' Now *log out and log back in and your notebook's screen will be black and you'll only have access to you external monitor. Now simply open FireFox and goto the flash video site you want and when you'll be able to watch the video in fullscreen on that monitor. 

*You have to log out and login after disabling your notebook's monitor. I didn't log out first and the fullscreen video didn't show,  even though it was off. 

Like I said, you'll loose access to your notebook's screen for the time being, but this is a workaround that'll work. 

When you want your notebook's screen back, go back to the Screen Resolution preferences and re-enable it.

---

### Post by mssever on 2008-12-02
@sleepitoff:
I'm glad you found a workaround for your problem--which is quite different from mine. In my case, the external monitor is always primary. I could, of course, disable it, but that would defeat the purpose of having an external monitor (or more specifically, projector). So I need both enabled simultaneously with the laptop being primary.

@everyone:
Given that this thread is two weeks old and no one's given a workable suggestion, I'm thinking that there might not be any existing software to accomplish this. I'm considering writing a program to fix this when I get the time. However, I really don't know right now what would be involved in such a project or whether it would be a feasible project for my skillset and available time. Even though sleepitoff and I have opposite needs, a reasonable solution would be general enough to meet both our needs and work at a high enough level to be hardware-independent.

EDIT: I've started a [thread]("http://ubuntuforums.org/showthread.php?p=6294390") in Programming Talk specifically about the possibility of writing something to solve this problem. Of course, if someone can point out a solution that won't require so much time, I'd prefer that.

---

### Post by bctechnzl on 2008-12-07
Same things have happened here with an HP 6730b laptop, intel graphics and CPU. It seems there needs to be a way of setting the primary display in the GUI. "Make this my primary display"
Anyway, where does one go to edit this stuff by hand now?  Once upon a time I could edit xorg, but this is not the goal anymore.

Is there a launchpad bug devoted to this yet?

---

### Post by mssever on 2008-12-07
> **bctechnzl said:**
> Same things have happened here with an HP 6730b laptop, intel graphics and CPU. It seems there needs to be a way of setting the primary display in the GUI. "Make this my primary display"
Anyway, where does one go to edit this stuff by hand now?  Once upon a time I could edit xorg, but this is not the goal anymore.See the thread I linked to in post 9.

> Is there a launchpad bug devoted to this yet?
Not that I know of. I don't think I have enough information to file a useful bug report. For example, which component is defective? The video driver? Xorg? gnome-panel? Metacity? Compiz? All of the above? None of the above?

---

