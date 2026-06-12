---
title: "Cannot restart X server and/or KDM Display Manager"
date: 2008-04-22
forum: Multimedia Software
---

### Post by snorkytheweasel on 2008-04-22
Kubuntu 7.1
The screen resolution changed - lowered the res - without my help. 

To fix that, I went into the screen where I could view/change display settings.
[LIST]
[*]I selected my monitor: Viewsonic E790.
[*]There a few possible settings, so I looked up my monitor specs at Viewsonic's web site.
[*]According to the web site, there are a lot of possible refresh rates & resolutions.
[*]At Kubuntu's screen where I could view/change settings, [LIST]
[*]I selected a refresh rate that was "in the middle" of the range of possible rates. 
Once set, that gave me a range of resolutions. [*]Then I selected a resolution that was "in the middle" of the range of possible resolutions. [*]When I clicked the "Apply" button, it advised  that I had to restart(?) the system and restart x server.
[/LIST]
[/LIST]
No problemo, dude.

However, I can't get xserver to restart. I've tried
[LIST]
[*]sudo /etc/init.d/kdm start
[*]startx
[/LIST]
Each of those gives me screens full of errors. The I tried
[LIST]
[*]xinit
 [ followed by ] 
[*]startkde
The system returned "Starting K Display Manager: kdm is already running"
[/LIST]
Then it drops me back to the BASH prompt.

If I reboot, the initialization process says (among other things) "Starting KDE Display Manager KDM". Then the graphical Kubuntu startup screen displays as if the GUI was going to kick in. However, it drops me to the shell to log in. At that point the visible error messages are
[LIST]
[*]fatal server error
[*]no screens found
[*]XIO: error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
[/LIST]
Then it taunts me to try something else at the BASH prompt.

WTF???

---

