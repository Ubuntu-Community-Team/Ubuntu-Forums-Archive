---
title: "Flickering black line after sleep"
date: 2015-03-31
forum: Multimedia Software
---

### Post by Bucky Ball on 2015-03-31
Hi all,

Purchased a 24" Benq GL2460HM monitor yesterday. I love it, but this bit I don't love. 

I have the monitor attached to my Toshiba Satellite Pro laptop. When I shut the laptop lid and put the system to sleep, on waking (lifting the laptop lid) the new monitor has a flicking black line in random positions on the screen whenever there is any activity (window scroll, scroll wheel, keyboard action). The laptop screen is fine. This only effects the new monitor. The resolution is at 1920 x 1080, as it should be, but when I set it to 1920 x 1080i, everything 'jitters' (visibly shakes). Not much, but enough. 

Can't take a screen shot as the line just flashes up the full width of the screen and then disappears. Seems to be a reaction to any input on any hardware attached to the machine (and even happens occasionally when the machine is 'thinking', i.e. updating via a terminal). 

I've scoured the interwebs with no success. I haven't found any issues that are exactly like mine and the fixes for other things don't seem to apply here. The only thing that does sound promising was a fix for another screen problem which instructed to 'unity --replace', from memory. I am using a minimal install with lightdm and xfce4, so no Unity. Would replacing lightdm have the same effect? I have no power manager or screensaver installed (and no lightlocker, nothing) so none of these are causing the problem.

Before anyone raises a hand to exclaim 'Hardware!', everything works fine in Win7. No flicker to be seen. It only happens when I bring the machine out of sleep in my minimal xfce4 install. Maybe I'm missing something (it is pretty slim install). If I reboot the machine (and usually when I logout/login again), it is fine again, no flicker.

Any suggestions? Tnx in advance. ;)

PS: Using the opensource vid drivers. No proprietary installed.

---

### Post by dino99 on 2015-03-31
i've no clue about xfce, but reading your post i'm thinking of a possible related compiz plugin trouble. Is there some non mandatory compiz plugin(s) installed ?
can you also check an other installation not using xfce, and try to reproduce that issue ?

---

### Post by Bucky Ball on 2015-03-31
Have never used Compiz so no, not that. Nothing installed there. Mini install with xfce4 is what I've used for years, so no, I don't have any other flavours to try, unless it's in virtualbox, which may have totally different results not related to this, so won't go there, but I will try another kernel and see if I get the same. Using 14.04 LTS BTW.

---

### Post by Bucky Ball on 2015-03-31
* Update: Not exactly a fix, but I've discovered something. I have been using the 3.13.0-48-lowlatency kernel. That's where I'm getting the issue. Tried the 3.13.0-44-lowlatency kernel. Same. So thought I'd give the 3.13.0-48-generic kernel a try and bingo. Problem disappeared. The problem of the black lines at least. Problem remains that I occasionally do some audio recording on this machine, which is why I am using the low latency kernel, but the flickering after sleep seems to be isolated to that kernel (in 3.13.0-48-generic now and not a peep of a problem).

Not sure if this is bug-worthy, or maybe it already is one. I'll have a sniff around later. The workaround for now is to do day to day in -generic kernel and boot to the -lowlatency kernel for audio recording (a drag as the audio recording tends to happen somewhat spontaneously), remembering NOT to close the laptop lid when using the lowlatency kernel (which drives me nuts as I have what borders on an OCD regarding energy wastage!). ;)

If someone can throw some light on why the low latency kernel has the issue but the generic one doesn't, shine on.

---

### Post by Bucky Ball on 2015-03-31
* Further update: I take it back. Just went off to do something else for awhile (oddly enough, set up a dual-monitor system with the old external monitor from the laptop), wake out of sleep, and exactly the same as the lowlatency kernel. The black line is back. It also jerks the screen down when I type. Really odd and hard to explain. Line starts somewhere across the screen, then works its way down as I type until it reaches the bottom of the screen, then cycles back to the top.

Hard to put into words. Might look into making a screencast of it tomorrow night. :-k

---

### Post by dino99 on 2015-03-31
thinking about the processes priorities, maybe you can check with higher priority for some of them (system-monitor)

---

### Post by Bucky Ball on 2015-03-31
> **9d9 said:**
> thinking about the processes priorities, maybe you can check with higher priority for some of them (system-monitor)

Sorry, don't know what you mean or how to do what you're saying. Please explain. ;)

---

### Post by Bucky Ball on 2015-04-01
Well, looking in Synaptics I discovered I have both xfwm4 and openbox installed. Was wondering if that is causing the issue as they are both window managers. I don't remember installing openbox as I've never intentionally used it. Could it possibly have been dragged in with something else (xfce4 desktop environment)?

Anyways, I tried:

```
openbox --replace
```

... hoping a change of window manager might stop the flickering, but to no avail. It gave me openbox windows, but not joy. So I:

```

xfwm4 --replace
```

... and I am no further along with this frustrating issue. Wouldn't be such a problem but I'm studying and need to have a heap of apps and windows open at the same time. To close and save everything, reboot to kill the flickering and then open everything to where I was is particularly annoying. :|

Guess I can just switch the monitor off instead of closing the laptop lid. Some of the way there with a clumsy workaround.

* Update: On a more positive note ... a not-so-clumsy workaround and possibly a clue to what is at the root of this issue. I have arandr installed. If I launch that, deactivate the monitor screen, reactivate the monitor screen, no more flickering screen. At least I don't need to close all app and files if I close the laptop lid. Getting there ... slowly. The penny might drop for me eventually as to what this development means. 

If I switch the monitor off and back on via the power switch (on the monitor, not the wall socket!), the flickering remains. It is only deactivating/reactivating in arandr (where the power isn't switched off manually) that kills the flickering, shuddering screen problem. ;)

---

### Post by Bucky Ball on 2015-04-10
Any further takers on this? Still deactivating monitor with arandr and then enabling it again as a workaround, but getting mighty tedious. Anyone have any idea what arandr is actually doing when I disable/enable? If I knew the commands its using perhaps I could sneak a script in to run when the machine comes out of sleep to do the same thing (and save me some time). 

All offers accepted! ;)

---

### Post by Bucky Ball on 2015-04-16
* Update in the hope this further clue can inspire ideas: When the monitor is flickering, if I open arandr, switch off the laptop screen, the flickering stops. If I then switch the laptop screen on again with arandr, the flickering is still stopped. :-k

So, I can switch off and then on either the laptop screen or the external monitor and it fixes the flickering. Living with this annoyance for now and having a quick look for a fix now and then when it finally gets to me. :|

---

### Post by Bucky Ball on 2015-04-21
Yet another update to my annoying issue. Just noticed something else. When I open the laptop and the flickering black line is happening, if I open arandr and switch off the laptop screen, the flickering stops on the external monitor. If I then switch on the laptop screen again, the flickering stays stopped. :-k

To sum up:

* Open laptop lid, external monitor has flashing, twitching black line when computer activity;
* Open arandr and deactivate the external monitor then activate it again, flickering stops;
* Open arandr and deactivate the laptop monitor, flickering stops on external monitor (and stays stopped if I switch laptop monitor back on again).

This bugs me! ;)

---

