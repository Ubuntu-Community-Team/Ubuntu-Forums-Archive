---
title: "Acer Wifi Issues - 11.10"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by volksy on 2012-02-13
I tacked on to the end of another thread, but thought I would start an new one as it wasn't exactly relevent to the PC involved.
 
Summary of the fault:
 
On boot up, wireless works fine, after an indeterminate amount of time, the WIFI will disconnect and nothing apart from a reboot will bring it back online again. Clicking on the WIFI icon on the desktop shows "Wifi Disabled by Hardware Switch" and most options are greyed out.
 
After installing Ubuntu, the WIFI (Hardware) switch is inoperative, (no LED, no reponse) so I can't see it being the switch. 
 
Once the fault occurs an RFkill shows 'Hardblocked' and performing an 'unblock all' does nothing.
 
I did notice that the other evening, moving the laptop can cause the fault to occur, coinsidence maybe, but I'm not too sure.
 
Any ideas to help would be great..
 
Thanks on Advance.
 
Chris

---

### Post by volksy on 2012-02-15
Anyone?

---

### Post by TBABill on 2012-02-15
I would start looking at power settings. I'm wondering if something is enabled for power control that disables your wireless in a certain condition, such as when the battery gets to a certain % of charge or when the lid is closed or some other function of the machine that triggers the power control to kick off the wireless. I normally disable power control except on extreme low battery conditions, which I never hit. I just use a screensaver to blank my screen after a few minutes and that keeps the wireless from disengaging. 
 
Not sure if that's your problem, but something is triggering the "off" command and power save features of the wireless or the machine are where I'd start looking.

---

