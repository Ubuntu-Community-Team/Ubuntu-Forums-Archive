---
title: "ifupdown entry in network manager causing issues"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by evilc1 on 2011-02-21
I am making a development web server using ubuntu server and virtualbox.

I wanted gnome desktop as I want things like copy/paste and other niceties, plus an artist will be using the machine so I need everything to be configurable by a GUI if possible.

I did NOT install ubuntu-desktop (As apparently this switches you to desktop kernel not server), I executed:

```
  [FONT=Calibri]sudo apt-get install xorg gnome-core gdm gnome-applets gnome-system-tools gnome-utils ubuntu-artwork compiz-gnome firefox sysv-rc-conf[/FONT]
   
```This worked, but there appeared to be no way to configure the NIC. When I went from virtualbox's NAT setting to Bridge setting, the box lost network connection.

So I installed the NetworkManager package.
Still no joy (NetworkManager did not appear in any menus or toolbars)

So I manually edited /etc/network/interfaces and set it to static IP in there, all seemed to work.

Later on, I got DHCP working properly, so I re-edited /etc/network/interfaces and set it to dhcp.

I then stumbled on [this]("http://www.ubuntugeek.com/how-to-fix-network-manager-applet-missing-from-notification-area-in-ubuntu-10-04.html") which enabled me to get network manager to show in the menu / on the taskbar.

So now I have things working OK, with a GUI interface, but just one problem:

There are two entries in Network Manager: "LAN" (The one I created) and "ifupdown".
ifupdown cannot be edited. It is set to DHCP and cannot be changed or removed.

However, when the machine boots, it is set to "ifupdown". I can click the tray icon and switch to "LAN" no problem, but how do I set it to default to LAN (or make ifupdown editable) ???

TIA

---

### Post by evilc1 on 2011-02-21
Hmm, typical, I think I found a solution just after posting

I followed [this]("http://ubuntuforums.org/showpost.php?p=8275776&postcount=6") and ended up with only one entry in Network Manager ("Auto eth0") which I can edit and set to static if needed.

---

