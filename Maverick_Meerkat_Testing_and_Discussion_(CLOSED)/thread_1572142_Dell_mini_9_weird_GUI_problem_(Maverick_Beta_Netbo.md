---
title: "Dell mini 9 weird GUI problem (Maverick Beta Netbook Remix)"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by FadeOUT on 2010-09-10
Hey Guys,

I've just upgraded to Maverick Netbook Remix on a Dell Mini 9 (910) and I'm having a problem with the GUI; after booting, the background dims, then undims repeatedly and nothing else appears apart from a couple of big arrows in the top left and, after a while, an X-style cursor.

Any ideas??

---

### Post by cariboo on 2010-09-10
It sounds like you have a graphics driver problem. Can you start a normal gnome session from the login screen?

---

### Post by FadeOUT on 2010-09-10
> **cariboo907 said:**
> It sounds like you have a graphics driver problem. Can you start a normal gnome session from the login screen?

It was set up to log in automatically, so it may have made it past the login screen. I can right-click on the desktop and change the background image, for instance (although I have to do it during the non-greyed out periods).

---

### Post by cariboo on 2010-09-10
You should be able to get to a console by pressing Ctrl-ALt-F1, once logged in, you should be able to navigate to /etc/gdm. You should see a file in that directory called custom.conf, just remove it and reboot. Once you have rebooted you should see the login screen, select your name and select gnome session at the bottom of the screen

---

### Post by FadeOUT on 2010-09-11
> **cariboo907 said:**
> You should be able to get to a console by pressing Ctrl-ALt-F1, once logged in, you should be able to navigate to /etc/gdm. You should see a file in that directory called custom.conf, just remove it and reboot. Once you have rebooted you should see the login screen, select your name and select gnome session at the bottom of the screen
Thanks, that's an improvement - I can now log in as usual. However, the menu on the left does not respond to mouse clicks. The icons at the top work as usual. Any ideas?

---

