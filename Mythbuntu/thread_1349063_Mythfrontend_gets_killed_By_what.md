---
title: "Mythfrontend gets killed? By what?"
date: 2009-12-07
forum: Mythbuntu
---

### Post by pombe on 2009-12-07
My mythbox started flaking out overnight.  I woke up to it frozen, rebooted and now it stops on a login screen.  When I give my pass it gives the mythbuntu progress bar and then kicks back to the logon.  I can't login as an xfce session either.  

Attached is the mythfrontend.log bit that repeats every time I restart.  Anyone have any idea whats going on?   It was working fine for a couple days then this...

Specs:  3700+, MSI Neo2 Platinum, 1GB ram, nvidia 5200, Hauppauge, PVR-500.    

```

Starting mythfrontend.real..
2009-12-07 21:00:23.083 mythfrontend version: branches/release-0-22-fixes [2259$
2009-12-07 21:00:23.084 Using runtime prefix = /usr
2009-12-07 21:00:23.084 Using configuration directory = /home/mythbox/.mythtv
2009-12-07 21:00:23.983 Empty LocalHostName.
2009-12-07 21:00:23.983 Using localhost value of mythbox
2009-12-07 21:00:23.988 New DB connection, total: 1
2009-12-07 21:00:24.001 Connected to database 'mythconverg' at host: localhost
2009-12-07 21:00:24.002 Closing DB connection named 'DBManager0'
2009-12-07 21:00:24.049 ScreenSaverX11Private: Gnome screen saver support enabl$
No protocol specified
2009-12-07 21:00:24.049 MythXOpenDisplay() failed
2009-12-07 21:00:24.049 ScreenSaverX11Private, Error: Failed to open connection$
2009-12-07 21:00:24.049 DPMS is not supported.
mythfrontend.real: Fatal IO error: client killed

```

---

### Post by OffAxis on 2009-12-08
here's a section out of mine...
```
2009-12-07 19:22:47.590 ScreenSaverX11Private: Gnome screen saver support enabled
2009-12-07 19:22:47.592 DPMS is active.
2009-12-07 19:22:47.595 Primary screen: 0.
2009-12-07 19:22:47.596 Connected to database 'mythconverg' at host: localhost
**2009-12-07 19:22:47.599 Using screen 0, 1280x1024 at 0,0**
2009-12-07 19:22:47.635 MythUI Image Cache size set to 20971520 bytes
2009-12-07 19:22:47.679 AudioPulseUtil: Suspend Success
2009-12-07 19:22:47.683 Enabled verbose msgs:  important general
2009-12-07 19:22:47.695 Primary screen: 0.
2009-12-07 19:22:47.698 Using screen 0, 1280x1024 at 0,0
2009-12-07 19:22:47.700 Using theme base resolution of 1280x720
```
I've bolded the line in mine that's absent from yours. Looks like your screen or the (configuration for it) isn't being found properly.

---

### Post by pombe on 2009-12-08
> **OffAxis said:**
> 
I've bolded the line in mine that's absent from yours. Looks like your screen or the (configuration for it) isn't being found properly.  

Ok.  That's weird.  I haven't messed around with the display settings. TV is connected by the s-video cable to my video card.  I would think this would be "display 0" by default...

---

### Post by pombe on 2009-12-08
Ok, I can get mythtv to load if I do 
```
 sudo apt-get remove mythtv
```
and
```
 sudo apt-get install mythtv
```
while the box is stuck on the login screen...  If I reset the computer then it just gets stuck at the desktop again.

---

