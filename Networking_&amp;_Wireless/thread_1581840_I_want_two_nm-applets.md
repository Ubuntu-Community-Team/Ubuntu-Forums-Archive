---
title: "I want two nm-applets"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by complience on 2010-09-25
I'm running dual monitors, each with their own desktops.

I want to have the wifi icon showing on both, but whenever I startup I get an error message saying the applet is already running so it won't be started up again.

I've searched the forum and it seems alot of people had a problem of multiple icons showing in the taskbar when not wanted.

I'm thinking theres been some code added to the nm-applet to only allow one instance in the notification area. 

Can anyone confirm this and tell me how to turn it off?

---

### Post by termin on 2010-09-25
you just plainly cant, its just not possibe within the gnome settings. although you could play around with the gonf editor to run it go to the terminal and then type:
gconf-editor

and just look around the folders and then find something, but i doubt its there

---

### Post by complience on 2010-09-26
okay as termin spelt it out so clearly for me, i decided to force the nm-applet to use my main screen by putting --screen="1" in the command.

I find it strange that I need too although.. why does it default to screen 2?

---

