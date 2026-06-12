---
title: "sort of replacement for the gnome panel system monitor in gnome unity?"
date: 2011-03-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Bazon on 2011-03-06
I liked having my computer status in the upper gnome panel (system monitor with CPU and network + temperatures) to see what's going on with my hardware, is there some kind of replacement for this?

---

### Post by cariboo on 2011-03-06
Unless someone comes up with an indicator applet, there is no way to to add anything to the panel at this time.

---

### Post by MacUntu on 2011-03-06
I guess as long as the indicator API only allows you to draw text and icons (don't know if that's still the case), a system monitor clone is not going to happen.

One thing I tried some months ago was to create and replace a new icon on every update. It worked, but had some major downsides: a lot of I/O from creating the new icons, laggy under CPU or I/O load, and it's generally a pretty bad way to implement it. :D

That said, yeah, I do hope we get a replacement for the system and the sensor applets.

---

### Post by eltama on 2011-03-19
I'm missing the system monitor too.
Could it be implemented as a special icon in Unity (like in Docky) or the entries in Unity are just plain icons?

---

### Post by cariboo on 2011-03-19
Appindicators can be active icons, just use brasero to burn a cd to see an example. As an alternative for now the only choices seem to be conky or desklets.

---

### Post by thaDM on 2011-03-20
I hope there'll be an indicator for this too; I miss the system monitor in the panel.

---

### Post by jerrylamos on 2011-03-20
> **cariboo907 said:**
> Unless someone comes up with an indicator applet, there is no way to to add anything to the panel at this time.

From my standpoint, that's a "loss of function" or "regression" in Natty Unity vs. Maverick.  I had a row of applets at the top of Gnome of things I usually use.

Now I might just be willing to take that as far as launching applications goes.  In this Unity 2D the launchers are easy to reach if a bit slower because of the hiding and exposing launcher dock on the left.

And I can get system and preferences by selecting the top corner and starting to type the name in the search box.  A bit slower than gnome but it does work.

However I do use the "system monitor" applet on a couple of my installations which isn't available in Unity 2D or 3D that I can find.

For all this grumping, on my two pc's that won't use Unity 3D I do find myself using Natty Unity 2D vs. gnome desktop....

Jerry

---

### Post by jennybrew on 2011-03-20
I suspect Ubuntu may revisit this at sometime in the future as they put a lot of work into it.
In the meantime Conky is fun and really enhances your desktop.
Maybe not the best thing to do during an alpha phase ..but a few weeks down the line maybe :)

---

### Post by MacUntu on 2011-03-20
Conky is no replacement for me. I want that information in the panel, where I can see it _all the time_.

---

### Post by mc4man on 2011-03-20
The only applet missed here is the weather applet, there is a replacement for it (indicator-weather) which is ok but not quite as good  - no radar, otherwise atm about the same

---

### Post by lancest on 2011-03-23
Mixed feelings about this. 

On my machines I've seen many occasions where indicators loaded improperly or got moved around (during projection).   

So I was fed up with seeing that. 
On my testing 11.04 doesn't suffer from this.

---

### Post by eltama on 2011-03-25
Have a look at this system monitor indicator [http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html](http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html)
It's not the sane, but better than nothing.

---

### Post by kansasnoob on 2011-03-25
Personally I'm more concerned about temperature, which is also an indicator of how hard the CPU is working, so I always install either 'computertemp' or 'sensors-applet'.

Another one I miss is the power manager inhibit applet. It's just so easy to click on that if I'm going to watch a video and don't want the screensaver to activate at all :)

---

### Post by Bazon on 2011-03-26
> **eltama said:**
> Have a look at this system monitor indicator [http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html](http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html)
It's not the sane, but better than nothing.

Thanks, that's at least something...

---

### Post by Anduu on 2011-03-26
> **eltama said:**
> Have a look at this system monitor indicator [http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html](http://www.webupd8.org/2011/03/system-monitor-indicator-puts-cpu-and.html)
It's not the sane, but better than nothing.

Doesn't load for me :(

---

### Post by lancest on 2011-03-26
> **Chauncellor said:**
> That's a bug with gnome-panel and the murrine-based themes. This bug will not appear in natty because the buggy panels are gone.

Yes and I'm quite pleased with that. :)

---

### Post by squee on 2011-04-02
I do like the unity bar at the top but yes it is drastically missing the notifications and applets we had before. I only installed last night but this missing is tempting me to roll back already.

I shall persevere for now, and I've added things to my Docky menu. I miss being able to glance and know my CPU/ram/network load, weather, mounted drives, dropbox action.

---

### Post by kansasnoob on 2011-04-02
> **squee said:**
> I do like the unity bar at the top but yes it is drastically missing the notifications and applets we had before. I only installed last night but this missing is tempting me to roll back already.

I shall persevere for now, and I've added things to my Docky menu. I miss being able to glance and know my CPU/ram/network load, weather, mounted drives, dropbox action.

I plan on trying different docks myself at the bottom of the screen. Would you share a screenshot of what your desktop looks like with Docky?

---

### Post by squee on 2011-04-06
Wouldnt bother with putting Docky/Gnome Do on top of unity. Still quiet slow and buggy.

I know that this is probably really really really obvious but I only figured it out yesterday, that you can set the session on the log in screen. I know have the original set as the default and all is back to normal but with 11.04 back end.

Win!

---

### Post by cariboo on 2011-04-06
> **kansasnoob said:**
> I plan on trying different docks myself at the bottom of the screen. Would you share a screenshot of what your desktop looks like with Docky?

I've had docky installed almost from the start of testing, and haven't any major problems.

---

