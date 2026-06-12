---
title: "Unity and 2 monitors"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by osarusan on 2011-04-02
I have a dual monitor setup and am currently using Unity 2d (until I can figure out how to fix Compiz...)

My question is, the Unity panels always show up on the leftmost monitor, but my primary monitor is the right one.

How can I change this so that the right monitor gets the panels and the left monitor does not??

---

### Post by sanderd17 on 2011-04-02
install and run the grandr app:

```

sudo apt-get install grandr 
grandr

```

There you should find it (grandr is just a gnome frontend to randr, there are other frontends too).

---

### Post by osarusan on 2011-04-03
I've already got grandr installed. My monitors are set up correctly, but the problem is that the Unity panels show up only on the leftmost panel, never on the one which I use as my main display.

Is there a way to change which monitor the Unity panels load on?

---

### Post by osarusan on 2011-04-03
Ahh I think I worded it poorly.

The global menu goes across both screens, but the Launcher is stuck on the left screen. This is exceptionally awkward for my setup. Is there any way to make the Launcher appear on the right monitor and not the leftmost one by default?

---

### Post by taojian on 2011-04-03
I think that's also in the Catalyst Control Center: with two monitors plugged in I can have it label them 1 and 2, and then drag them back and forth to set which one is left and which one's right.

Can't get any of this to stick though: each logout/restart disables my left monitor and dumps everything on the right. Restarts are coming fast and thick these days, so I'm just going single monitor until this is all sorted out.

---

### Post by osarusan on 2011-04-03
It doesn't seem to matter which monitor is set to 1 or 2 in CCC, Unity always forces the launcher to load on the leftmost windows as far as I can see... I don't know if there's a way around it, given the other complaints I'm seeing about Unity's inability to customize anything at all... :( bad decision on the designers' parts... How could they assume that everyone uses their desktop in the exact same manner??

---

### Post by davepoth on 2011-04-03
To be fair putting the bar where you want it is a bit of a "minority pursuit" but I can't see any reason why you shouldn't be allowed to do it.  This is Linux after all. At least I *think* it still is.

---

### Post by osarusan on 2011-04-03
Maybe moving the bar is, but how about using your primary monitor as your primary monitor? Because that's essentially what this is about.

In regular Gnome you can set which is your "primary" monitor, and the panels etc. appear on that monitor. In Unity, it is forcing you to accept that your leftmost monitor is primary, no matter what your setup is. I hardly call deciding which is your primary monitor a minor pursuit.

---

### Post by mstrelan on 2011-04-08
I have the same issue. I have installed Docky to run on my right monitor, which is my primary monitor. I have set the Unity Launcher to autohide so I never really see it. Problem is when I unplug the external monitor my laptop screen now has docky AND the Unity launcher :(

I am largely unimpressed with Unity, but sticking with it to see if there is any real benefit over Gnome 2. I miss being able to see information at a glance, I now have to think about what information I want to see.

---

### Post by The Yump on 2011-04-09
The Unity launcher appears on whichever is the primary monitor.  You can change the primary monitor thus: ```
xrandr
```  to get a list of your video outputs, then:  ```
xrandr --output $monitor_you_want_from_previous_step --primary
```

---

### Post by osarusan on 2011-04-10
That did it!
Thank you so much, The Yump!
It was such a simple solution, yet so hard to come by. It's too bad the GUI versions of xrandr don't have that option.

---

### Post by mstrelan on 2011-04-10
Thank you! Now I just need to learn how to not hate it. It seems so in-your-face when you turn off hiding, but you can't tell what else you're doing when it hides.

---

### Post by osarusan on 2011-04-10
So now my question is, short of making a script to run this command every time I log in, is there a way to make it remember this setting?? Currently I have to re-enter it every time I log in.

---

### Post by Tich666 on 2011-04-14
> **The Yump said:**
> The Unity launcher appears on whichever is the primary monitor.  You can change the primary monitor thus: ```
xrandr
```  to get a list of your video outputs, then:  ```
xrandr --output $monitor_you_want_from_previous_step --primary
```

Thank you a thousand times! Now I can finally use unity with my dual monitor setup! :D
If somehow it would be possible to disable the information (indicator) area on the secondary monitor panel this would be perfect, but as it is now it is finally usable for me! Hooray :D

---

