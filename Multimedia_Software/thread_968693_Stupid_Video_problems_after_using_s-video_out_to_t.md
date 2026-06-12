---
title: "Stupid Video problems after using s-video out to tv"
date: 2008-11-02
forum: Multimedia Software
---

### Post by mooney79 on 2008-11-02
Ok, this is kind of a stupid problem and I must've spent an hour trying to figure this out to no avail. I had been using my laptop with ubuntu 8.10 and the s-video out to watch a movie on my tv. I adjusted the display settings in System-Preferences-Screen Resolution. I was able to get it sort-of working how I wanted to, but everything was popping up on the tv and not my laptop. I think it was using my laptop as the secondary display. So, my laptop only shows the desktop with no panel or taskbar at the bottom. My TV had everything in it. After I watched the movie, I disconnected the s-video cable and shutdown my computer. I took my laptop to my office, and when I turned it back on, my laptop was still my secondary display, meaning everything i tried to open from "alt-f2" would open in the primary display which i presume is the tv, which is no longer connected. I need to know how to get my panel and regular desktop back. When I go between desktops, I can see the panel flash across the top as I switch to the other desktop, but it's not actually in either. Any help would be appreciated.:confused:

---

### Post by hairyharry7 on 2008-11-13
I've been having similar problems with the display settings and outputting video to my tv through s video...the output works fine but if i disconnect it i have to logout and log back in (or completely restart) to reconnect it...any fixes for this? and yeah like mooney79 asked - how can you make the output monitor the secondary so that when the screens aren't mirrored my laptop screen has my menu bars

@mooney79 - try running "gnome-display-properties" in the alt-f2 window...see if that pops up on your laptop screen-not sure if it'll work but worth a try...

---

### Post by mooney79 on 2008-11-15
> **hairyharry7 said:**
> I've been having similar problems with the display settings and outputting video to my tv through s video...the output works fine but if i disconnect it i have to logout and log back in (or completely restart) to reconnect it...any fixes for this? and yeah like mooney79 asked - how can you make the output monitor the secondary so that when the screens aren't mirrored my laptop screen has my menu bars

@mooney79 - try running "gnome-display-properties" in the alt-f2 window...see if that pops up on your laptop screen-not sure if it'll work but worth a try...


I had tried doing that, but since my laptop was my secondary display, the properties window showed up on the tv display (which was no longer connected). So I was pretty much stuck. I ended up installing intrepid ibex as a fresh install anyways. But I'd still like to figure out how to get it to work so i can use my ubuntu partition to watch movies on my tv.

---

### Post by killer_d76 on 2008-11-15
i had this same problem as well, i plugged in an external LCD monitor screen on my laptop.. tested dual monitor and it worked flawlessly.. but when i unplugged the monitor, i was not able to get the resolution back to normal not until i reboot and try fixing X settings.. then everything went back to normal.. i almost come to the part where i was about to re-install intrepid!.

---

### Post by blackened on 2008-11-15
Even though the dialog is offscreen, you should be able to use alt+F2
```
xrandr --auto
```
to disable the s-video and bring your panels and desktop back to your laptop screen.

---

### Post by hairyharry7 on 2008-11-15
> **killer_d76 said:**
> i had this same problem as well, i plugged in an external LCD monitor screen on my laptop.. tested dual monitor and it worked flawlessly.. but when i unplugged the monitor, i was not able to get the resolution back to normal not until i reboot and try fixing X settings.. then everything went back to normal.. i almost come to the part where i was about to re-install intrepid!.

yea how can this be fixed...i have no problem hooking up the s-video and using my tv but when i unplug it and try again it doesn't work...i have to reboot for it to work again-in my monitor resolution settings the "detect displays" button doesn't seem to work

---

### Post by DDRao on 2010-07-15
> **blackened said:**
> Even though the dialog is offscreen, you should be able to use alt+F2
```
xrandr --auto
```
to disable the s-video and bring your panels and desktop back to your laptop screen.
Tried the solution mentioned by you, but still the problem continues. Screen resolution is completely distorted on my laptop after connecting my laptop to lcd tv using s-video output. kindly help resolving this issue.

---

