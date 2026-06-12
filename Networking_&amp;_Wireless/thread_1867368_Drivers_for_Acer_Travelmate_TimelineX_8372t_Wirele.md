---
title: "Drivers for Acer Travelmate TimelineX 8372t Wireless Switch?"
date: 2011-10-22
forum: Networking &amp; Wireless
---

### Post by clappboard on 2011-10-22
I'm currently running Ubuntu 11.10 on my laptop, and had a good deal of trouble getting the Broadcom wireless card to work properly.  I previously had 11.04 on it, and everything worked fine; the light on the wireless button lit up, and pressing it switched the wifi on/off.  Then I upgraded to 11.10, and had issues even getting the darn thing to be detected.  The light doesn't light up anymore, and pressing the button has no effect.  Also, the Fn+F3 command (which is supposed to turn all wireless services (BlueTooth+WiFi) off/on) now does this:

Press 1:  Nothing.
Press 2:  BlueTooth ON.
Press 3:  WiFi and BlueTooth OFF.
Press 4:  BlueTooth ON.
Press 5:  BlueTooth OFF.
Press 6:  WiFi ON.
(Repeat)

I can't make heads nor tails of it.  As it is, the wireless works fine (relatively speaking), but this is really just bugging the hell out of me.
If ANYONE has a clue how to solve this problem, please let me know.

Additional Info:
I've tried disabling acer_wmi module, then enabling the additional drivers, and vice versa, which both work.  They won't work together though... ??

---

### Post by clappboard on 2011-10-24
For anyone who stumbles across this, after much web surfing and trial-and-error, I finally procured a solution:

After a fresh install, enable the additional drivers, then add a few lines to your modprobe blacklist file:

```
sudo nano /etc/modprobe.d/blacklist.conf
```...then add these lines at the end of the file:

```
blacklist bcma 
blacklist brcmsmac
blacklist acer-wmi

```...reboot, then you're done!!
(WiFi light even works! :D )

---

