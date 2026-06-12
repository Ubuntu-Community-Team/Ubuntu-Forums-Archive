---
title: "Excessive Wireless Password Popups"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by R3M3 on 2012-08-25
I recently updated to Xubuntu 12.04, and have run across an issue where occasionally (it's happened a couple of times, but it can go for days/weeks without the issue) I'll leave my computer running for a while, and when I come back, there will be an extremely excessive number of "Wireless Network Authentication Required" popup boxes prompting for my wireless password. 

And when I say "extremely excessive", I'm not exaggerating. The last time this happened, there was over 100 of them*. It was to the point where the subtle drop shadow that surrounds the popup overlaid with itself so many times that there was a solid black band surrounding the dialog in the middle of the screen.

Of course, to add insult to injury, the boxes are completely superfluous. I didn't even have to press "connect" to reconnect - Xubuntu was able to automatically reconnect to my wireless network. Although when reconnected, the popups don't disappear and I have to manually exit out of each one, waiting several seconds as there's a flurry of disk activity before the next one disappears (or I have to kill the nm-applet program).

Anyone have a clue as to what's going on here - why I'm getting multiple wireless password popups, instead of Xubuntu being smart enough to recognize that there's already one open? By the way, I'm completely fine with turning these popups off entirely if that's a fix. So long as there's an easy way to check my wireless network status and manually reconnect if I need to manually reconnect.

*)I stopped counting when I got smart and killed the nm-applet process in the terminal - I knew that was the one to kill as it was using 50+% of my memory. Unfortunately, it did not go gentle into that good night, as a simple "kill" causes my disk to thrash for 15+ min, with memory usage actually going up to 66%. I had to "kill -HUP" to get any results.

---

### Post by beboylips on 2012-08-26
Probably a bug in Xfce. I find that the releases of Ubuntu not running their default Unity/GNOME combos are given much less care and have silly bugs like that. 

I would try storing your wireless password in the keyring (the application for storing system-related passwords and other passwords in general) so that every time the system needs the password, it would fetch it from there. 

Maybe make the connection "available to all users" in the connection set-up, so the password gets stored in the system.

---

### Post by Bucky Ball on 2012-08-26
*Moved to **Networking ******& Wireless. ***

---

### Post by xyzzyman on 2012-08-26
This happens in Ubuntu 12.04 running Unity also.

---

### Post by fiklein on 2012-08-27
I am having the same problem on an ACER laptop. It works well with ethernet. It seems to disconnect and request "Authentication," accepts it then drops the connection and asks again for the WEP address in about 40 seconds. 
The computer worked well in Xubuntu 11.04 and 11.10, but failed after an uptdate to Xubuntu 12.04.
Help!! I am trying to set this up for a friend who is leaving the country for 3 months in about 30 hours. I would rather not have to reinstall the whole operating system.

---

### Post by evilpenguinj on 2012-11-29
I am having this issue as well.  Has anyone found a fix for it?

It's very annoying!

Jason

---

