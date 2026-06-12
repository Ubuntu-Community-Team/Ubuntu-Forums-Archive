---
title: "Bizarre VNC issue in 10.10 - unable to click sidebar"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Cerdito on 2010-11-02
Hi all,

Got a really strange one here. Can connect fine to my 10.10 Netbook Remix desktop over OpenSSH & x11VNC.

However, I cannot left-click on the sidebar (Unity). For example, if I click on one of the icons (say Firefox), nothing happens. 

Clicking anywhere else on the desktop is fine.

Clicking on the sidebar icons when at the netbook is fine.

Furthermore, over VNC I can click on one of the sidebar icons and drag it, but can't click to open!

Any help is appreciated...

---

### Post by tobid on 2010-11-02
can confirm this behavior/error. a complete fresh installation of ubuntu netbook 10.10 plus vino/vinagrae results in not being able to leftclick on sidebaricons. tooltips are shown ... strange - even more stranger: right click events are recoginzed!!! i can view the context sensitive menu to remove entries from the sidebar. as the menu is displayed outside the sidebar, leftclick events are recognized. 

but there is a seconde are where left click events are ignored: the new taskbar. but only the stuff which counts to the window on left side (min/max buttons, menue, etc.). the stuff on the right hand side (network connections, power, etc.) can be controlled.

to make things even more bizarre: the ubuntu icon on the top left can be left clicked ...

server
ubuntu netbook 10.10 
vino 2.30.2

client
ubuntu 10.10
vinagre 2.30.2

both with all available updates.

i hope someone can help solving this problem. especially, i intend to use the netbook primarly via vnc/vino remote control ...

thx, tobias

---

### Post by Cerdito on 2010-11-02
You have the identical problem that I have, can also click the top left "Ubuntu" icon. Very frustrating as have to go the long way round to access things.

Tried changing round a number of the x11vnc properties to no avail.

Can anyone help?

---

### Post by krunge on 2010-11-02
Could this problem be due to window manager / desktop?  Does it only happen in gnome?  Or does it happen in kde and simpler ones like xfce or twm or failsafe X session with no window manager?

---

### Post by Keilaron on 2011-05-06
I have this problem as well, and it only seems to happen with Unity. If, for example, I select the option "Ubuntu Netbook Remix 2D" instead of the default "Ubuntu Netbook Remix", I get a different WM and such, and they work fine in VNC. That option has its own host of issues, however.

---

