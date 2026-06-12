---
title: "nm-applet equivalent for WM?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by rawlyn on 2010-02-19
Hi all,

I have recently installed Window Maker on my EeePC, so I have a lightweight alternative to Gnome available.

Everything I want to work seems to work, except I'm not getting a network connection. I'm not too familiar with setting up networks (in the past I've always relied on the fact that Ubuntu just makes everything work on it's own), so I don't really know how to approach this problem.

Is there an easy (GUI-based maybe?) way to get connected wirelessly within WM?

Thanks in advance for any help.

---

### Post by m_duck on 2010-02-19
You can use nm-applet in WM's as well. I'm not familiar with window maker specifically, but if it has an autostart file, add the following to start nm-applet:```
nm-applet --sm-disable &
```You could also just run **nm-applet --sm-disable** from a run dialog or run the above from a terminal window I should think.

EDIT
It looks like WM doesn't have a system tray so what I've written above will not be much use. Another alternative would be to install [wicd]("http://wicd.sourceforge.net/") though I think it conflicts with network manager and will remove it if installed. That aside, the wicd daemon should then run on boot, and from within window maker, you can then run **wicd-client -n**, with the ***-n*** switch being used to start the client without a tray icon.

This will open the wireless settings window, similar to that of nm-applet (ish). Once configured and connected you can close that window and have your connection. Simply run it again to join a new network or whatever.

---

### Post by chaanakya_chiraag on 2010-02-19
I'm using fluxbox, but for me, just ```
nm-applet &
``` works.  What exactly does the --sm-disable do?

---

### Post by m_duck on 2010-02-19
As far as I am aware, the ***--sm-disable*** stops multiple instances of nm-applet loading. Most of the tutorials and whatnot lying around seem to use it (and I think Ubuntu's autostarted nm-applet instance also uses it) so I tend to follow. It is probably not strictly necessary though.

---

### Post by chaanakya_chiraag on 2010-02-19
I just gave up using nm-applet and directly configured /etc/network/interfaces and /etc/resolv.conf because I wanted to get rid of most bloat on my comp.  This means only stuff I want started get started.  I even got rid of a graphical login :D

---

### Post by rawlyn on 2010-02-19
That works perfectly - I'm replying from a WM session right now! :D

Thank you ever so much!

---

### Post by chaanakya_chiraag on 2010-02-19
By the way, does WM include tabbed windows?  Sorry if it's off-topic :P

---

