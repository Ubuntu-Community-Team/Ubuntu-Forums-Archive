---
title: "Hotkeys Startup"
date: 2008-06-08
forum: Multimedia Software
---

### Post by Eazy© on 2008-06-08
Hi!

I want to use "Hotkeys" (installed from repository) but I have a a problem starting it from Autostart. I made a start-script like this:
```
#!/bin/bash
hotkeys -t itouch 
``` and putted it in .kde/Autostart. The Hotkeys-splash-screen comes up but the buttons don't work. There seems to be another hotkey-app overriding Hotkeys. 

If I start Hotkeys manually from console, or double-click on my script it does work, but I really would like it to start automatic

---

### Post by abhiroopb on 2008-06-08
In gnome you can go to system>preferences>sessions and add a command there to start automatically. Try it out....

---

### Post by Eazy© on 2008-06-08
I'm using Kubuntu. Adding a start-script in ./kde/Autostart is the same thing.

---

### Post by Eazy© on 2008-06-08
no one knows?

---

### Post by Eazy© on 2008-07-31
I was just googeling on this problem just now, and found my own thread. So I'm bumping it again :)

The reason I want "Hotkeys" (stupid name, makes it impossible to google on) is that when I play ut2004 I can change tunes on Amarok and change the master volume. UT2004 overrides the kde build in hotkeys support  and "Hotkeys" overrides UT2004 :P

Well, now you know why I want this :)

---

### Post by abhiroopb on 2008-07-31
I just got this, sorry for not responding before. Basically I was thinking, why don't you try looking for a "sessions" app instead of manually putting it into the scripts folder. I mean the script seems simple enough but there are always little problems with it.

Have you for example made the script executable?

---

### Post by Eazy© on 2008-07-31
"chmod a+x hotkeys" I guess make it executable. 

"Hotkeys" starts when KDE start if I put the script in ./kde/autostart, but KDE's built in hotkeys overrides it somehow. 

Strange thing is, if I do "killall hotkeys" and then just do a normal double-click directly on the script, it does work. I wonder if it will work if I put the script in /etc/init.d instead (but I rather not do that)?

---

