---
title: "ATI Gutsy HDTV VGA out"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by hebetude on 2007-11-11
I just bought a refurb Olevia 32'' HDTV (model 232V).  The first thing I noticed is that it just plain didn't work.  Well adding the native resolution to xorg.conf (1360x768 ) and restarting X (ctrl+alt+backspace) fixed that right up.

The bigger problem was the poor colors.  Movies looked fine, but websites like Gmail that abuse the pastel colors looked terrible or washed out.  The text on the big reply buttons here was completely unreadable.  First I thought, well I got hosed on this TV.  But the PS3 looks perfect on it and I notice no problems with movies so.... I went to fix this issue.

Well when I switched form the freebie ati drivers to FGLRX it fixed this problem completely.  All I did was install it through the restricted driver manager, which obviously is the easiest and least likely way for it to work :P.   Nothing else changed, always used 24bit color, same resolution, HZ etc.

I did lose 3d acceleration in the switch and compiz won't load says composite extension missing.  I'm about to try out envy to see if that will correct the problem.  Easy video driver installations?? not possible!

Just my 2cents, this issue seems to not be a problem for others or no other discussion going on so I added my experience.  I thought I was going to go blind reading ubuntu on this big *** TV, fglrx to the rescue :)

---

### Post by hebetude on 2007-11-11
Update: Envy DOES NOT WORK, don't use it!  Not sure what it did (a lot), but uninstall was successful in fubaring my system.

Before you do anything uninstall your current drivers.  I know, I know you will be stuck in 800x600 or less.  Rest assure you are in linux and not windows, you can always alt click a window to drag it around and get to those buttons that are off the screen.  I installed the ATI binary from the instructions on their site with one addition.  I used automatic install, gurus can use custom or write their own I dont know.

**To fix 3d effects:**
Go into /etc/X11/xorg.conf at the bottom
and turn
```

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "disable"
EndSection


```
into
```

Section "ServerFlags"
        Option      "AIGLX" "on"
EndSection

Section "Extensions"
        Option "Composite" "enable"
EndSection


```

Good luck

---

### Post by JBAlaska on 2007-11-12
Glad to here you got it working, and thank you for bringing this TV to my attention.

I was ready to buy a 22" monitor for this price ($459.99 new egg), the specs are fantastic for a unit of this price range, 1600:1 Contrast Ratio..WOW!

One does have to wonder why they have so many refurbished units available though. The bad news for me is they say "Not available in Alaska", but I can work around that.

This will be sweet with my new (to me) 6800GT that I bought from my neighbor  for $30.00! this is shaping up to be a good Christmas for me lol.

Enjoy your new monitor!

---

### Post by hebetude on 2007-11-12
Good to hear that ubuntu is warming a home in alaska :P.

The one drawback of fglrx, at least for me, is that I have to disable compiz to play movies (any movies).  This is quite simple to do
```

metacity --replace

```

---

