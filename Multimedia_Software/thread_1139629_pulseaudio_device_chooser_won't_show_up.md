---
title: "pulseaudio device chooser won't show up"
date: 2009-04-27
forum: Multimedia Software
---

### Post by kristensson.jonas on 2009-04-27
Hi!
Im using Jaunty 9.04 and when I try to start pulseaudio device chooser the icon wont show up on the upper bar? Is there a bug or whats the problem? Can I try to force start it in the terminal or something?

/Jonas

---

### Post by valadil on 2009-04-27
If your pulse-session is frozen or crashed (not so uncommon in jaunty), apps that connect to pulse are also likely to freeze.  padevchooser in the console might tell you something.  Alternatively ps ax | grep pulse, followed by killing each pulseaudio process should let you start up a new pulseaudio.

---

### Post by kristensson.jonas on 2009-04-27
Hi!
Yes but is strange because the volume control works perfectly. I tried running the command and got this error:

> 
** (padevchooser:4400): WARNING **: pa_browser_new() failed.


/Jonas

---

### Post by kristensson.jonas on 2009-04-28
Maybe it could be a problem with avahi? I dont really know but when I start ubuntu I get a notification saying that i have a .local adress and avahi seems to have some problem with it. How do I fix that?

---

### Post by duanedesign on 2009-08-26
Did you ever find a resolution to this problem. I am experiencing the exact same thing?

---

### Post by lancerocke on 2010-05-07
bump. same here

---

### Post by Daryth on 2010-05-22
bump

---

### Post by rukna on 2010-12-07
Same here. Although, padevchooser loads on my Kubuntu's taskbar with a blank icon with a question mark. Clicking on it gives the usual options, and among them, I can bring up pavucontrol without any problem.

So, I guess the problem is having the correct icon configured for my padevchooser.

---

