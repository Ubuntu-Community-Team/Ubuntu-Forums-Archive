---
title: "Network Manager Applet Menu not Showing (Unity)"
date: 2011-08-20
forum: Networking &amp; Wireless
---

### Post by MaccyDG on 2011-08-20
Hi all,

I seem to have a little problem with the Network Manager applet - it works vaguely OK, even if it takes a bit long to find my connection, but when I click on the icon, the menu doesn't show.  I've Googled for the answer, but so far I can't find any help - can any of you help, please?

I have these packages installed:
network-manager-gnome
network-manager-pptp
network-manager-pptp-gnome
network-manager

I have also installed the applet through the Ubuntu Software Centre.

Just to clarify, the icon appears fine in my panel, and the notifications appear when I am connected, it's just that the menu doesn't appear at all.

Thanks for any help.

Liam

---

### Post by Basher101 on 2011-08-20
type ```
nm-applet
``` and see if the menu shows then. The terminal must remain open during that tho. Try that and if it does not function post your outcome

---

### Post by MaccyDG on 2011-08-20
Hi Basher,

Thanks for helping.

This is what I get:
```
An instance of nm-applet is already running.

** (nm-applet:1619): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

```

---

### Post by MaccyDG on 2011-08-20
OK, I've got a bit more info.

I can't click to get the volume menu, either.  The volume icon is right next to the Network Manager icon.

However, if I click on the mail icon, its menu shows up just fine, and I can then hover over both the volume and Network Manager icons, and their menus will show.  This is really strange!  Any idea what's happening here?

---

### Post by dixfranke on 2011-09-14
Hmm, I'm having the same problem right now (running Ubuntu 10.04 for Netbooks on a EEE 1000H). As a result, when my computer doesn't connect to the internet I just have to restart it...

---

### Post by MrWylbur on 2011-09-16
Exact same issue for me.  Also can't access the power applet and the display applet.  Help!

---

