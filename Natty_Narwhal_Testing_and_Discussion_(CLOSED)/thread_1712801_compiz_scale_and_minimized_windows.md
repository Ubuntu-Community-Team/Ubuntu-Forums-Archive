---
title: "compiz scale and minimized windows?"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-03-23
I noticed recently that after years of waiting, compiz scale was displaying minimized windows (enabled via a "workarounds" option).

This has always been my biggest gripe with compiz since I use window switchers a lot and a window manager that can't handle or display minimized windows properly is seriously lacking something.
Well like I said, it has finally been working and working very well as far as I could tell.
But today I did a full natty update, which I haven't done for a few days and noticed that it is no longer showing the minimized windows again, even though the option is still checked.

Anyone know what's going on and whether or not this is likely to be working anytime soon?

As minor as it may seem, this has been one of the things keeping me on KDE for the past couple of years.

---

### Post by icek on 2011-03-24
Hi, make sure You are using command to show "All windows". You can find it in scale plugin settings...

---

### Post by SmSpillaz on 2011-03-25
> **x-shaney-x said:**
> I noticed recently that after years of waiting, compiz scale was displaying minimized windows (enabled via a "workarounds" option).

This has always been my biggest gripe with compiz since I use window switchers a lot and a window manager that can't handle or display minimized windows properly is seriously lacking something.
Well like I said, it has finally been working and working very well as far as I could tell.
But today I did a full natty update, which I haven't done for a few days and noticed that it is no longer showing the minimized windows again, even though the option is still checked.

Anyone know what's going on and whether or not this is likely to be working anytime soon?

As minor as it may seem, this has been one of the things keeping me on KDE for the past couple of years.

The workaround is being shipped however it is not enabled by default. You can get to it from ccsm -> workarounds -> Keep previews of minimized windows. This is **entirely unsupported** though.

---

### Post by mc4man on 2011-03-25
> **SmSpillaz said:**
> The workaround is being shipped however it is not enabled by default. You can get to it from ccsm -> workarounds -> Keep previews of minimized windows. This is **entirely unsupported** though.

I have fooled around w/ that here a bit in unity - there is definitely a possibility  of anomalies depending which of the numerous combos of windows it was used on and whether used from icon (currently window group) or keyboard (all windows) and which workspace it's used from,  ect, ect. ect.

Have decided not to use that workaround here.

---

### Post by x-shaney-x on 2011-03-25
Yes, that option is the one I mentioned and it was working very well for the couple of days I was using it.
However, since I posted this thread it hasn't worked at all for ANY minimized windows so one of the compiz updates seems to have altered things :(

---

### Post by mc4man on 2011-03-25
> **x-shaney-x said:**
> Yes, that option is the one I mentioned and it was working very well for the couple of days I was using it.
However, since I posted this thread it hasn't worked at all for ANY minimized windows so one of the compiz updates seems to have altered things :(
Which login are you using? It (the option) does work (somewhat) here on unity, - three ways
By default 2 keyboards -  super+w for all windows, shift+Alt+up arrow for current workspace only
1 or 2 clicks on launcher app icon for window group  from all workspaces

---

### Post by VMC on 2011-03-25
> **mc4man said:**
> Which login are you using? It (the option) does work (somewhat) here on unity, - three ways
By default 2 keyboards -  super+w for all windows, shift+Alt+up arrow for current workspace only
1 or 2 clicks on launcher app icon for window group  from all workspaces

I like that Sup+W [one less keystroke to finger about].

Also I like the export function of ccsm. I have my unity setup up the way I want it and on a new install just import the saved file.

---

### Post by x-shaney-x on 2011-03-25
> **mc4man said:**
> Which login are you using? It (the option) does work (somewhat) here on unity, - three ways
By default 2 keyboards -  super+w for all windows, shift+Alt+up arrow for current workspace only
1 or 2 clicks on launcher app icon for window group  from all workspaces
I am using it on unity and I basically I only use it to show ALL windows from ALL desktops.

I initiate it either using a shortcut (super+w) or more usually by using screen edges (top left and top right).

---

### Post by mc4man on 2011-03-25
I gave it a try using your mouse movement (used top right and bottom left as not to interfere w/ launcher lock area

It does work to a point, after a bit some windows may not be pulled or other bad behavior starts occurring
(plus there are so many diff. combos of maxed, unmaxed and min windows, I'm sure it will break down on some

Also it seems to possibly interfere with desktop based viewport switching which I use here
The super+w seems a bit more reliable, but still stopped working correctly after doing quite a number of times (with the pull min. option enabled

Not sure how you'd get this going again other than a fresh install, maybe try setting any compiz changes you've made back to defaults, a restart and try again

(while can't see being a factor here, on a couple of occasions when something went south deleting all the saved session files in ~/.compiz/sessions helped

This option appears to be more trouble than it's worth, at least as seen here on unity

---

