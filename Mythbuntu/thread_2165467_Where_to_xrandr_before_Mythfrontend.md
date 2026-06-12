---
title: "Where to xrandr before Mythfrontend?"
date: 2013-08-05
forum: Mythbuntu
---

### Post by otoh on 2013-08-05
Got Mythbuntu running nicely - a new 12.04/0.26 install after running 10.04 for a few years. My main problem being that of my older TV with non-square pixels, requiring some adjustment to get MythTV to play videos full screen. After various experiments with xorg.conf - all of which refused to take - I eventually discovered **xrandr --fbmm 935x535** - this seems to set the different DPIs in xdpyinfo (whereas setting them directly with **xrandr --dpi 28x36** won't take - it just uses one or the other DPI but not both).

Anyway - problem solved, although I need to run this on login and can't figure out where best to do it. After some searching, adding it in ~/.xsession doesn't seem to work; nor does adding a new entry to the session & startup GUI with that code in it - even if it did, not sure how I could be sure it would run before launching Mythfrontend. Any ideas how best to ensure this runs?

---

### Post by ajgreeny on 2013-08-05
Try turning the command into a shell script ```
#!/bin/bash
xrandr --fbmm 935x535
``` make it executable, and then run the script at session login by adding it to the list of apps that autostart.

---

### Post by otoh on 2013-08-05
> **ajgreeny said:**
> Try turning the command into a shell script

Many thanks for the reply - a good idea that I hadn't thought to try. Unfortunately, I think I'm still missing something. I saved the script - exactly as you noted - in ~/screensize.sh and made it executable. When I manually run it from within my home dir:

```
./screensize.sh
```

It runs as expected and the correct DPI reports. But when I add the script to my startup items, it does not change - the DPI remains the default 96x96. I thought there was something wrong with how I added it to my autostart apps. So I altered the script to:

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]mkdir ~/scripttest[/FONT][/COLOR]
```

Then restarted - the directory was created in my home directory as expected. So it seems my script is working, and is autostarting - the problem specifically with the xrandr command running in the context of my autostart apps. Any ideas?

---

### Post by ajgreeny on 2013-08-06
I wonder if the shell script is running a bit too early, before the GUI of the DE is properly up and running (if that matters; I don't know!) so try adding a sleep option to the command ```
#!/bin/bash
sleep 10; xrandr --fbmm 935x535
```

---

### Post by otoh on 2013-08-08
> **ajgreeny said:**
> I wonder if the shell script is running a bit too early, before the GUI of the DE is properly up and running (if that matters; I don't know!) so try adding a sleep option to the command ```
#!/bin/bash
sleep 10; xrandr --fbmm 935x535
```

Aha! It seems it does matter - you are right :) I experimented with the sleep and it seems just 2 is enough to get it working. Even then, though, it was out of sync with the front end starting up - it does so first so does not read the correct DPI until quit and restarted... so I just turned off auto-start and added *mythfrontend --service* to the script.

Problem solved - many thanks for your time to help!

---

### Post by ajgreeny on 2013-08-08
Wonderful!!

---

