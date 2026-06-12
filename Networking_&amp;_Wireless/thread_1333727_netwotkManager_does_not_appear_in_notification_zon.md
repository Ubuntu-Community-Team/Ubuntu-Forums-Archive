---
title: "netwotkManager does not appear in notification zone"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by yvesg on 2009-11-21
Hello,

I cannot see any icon for NetworkManager, despite the following:
1) network-manager, network-manager-gnome and network-manager-pptp are installed,
2) there is a notification zone
3) the service "nm-applet --sm-disable" belongs to the list of applications to launch at startup
4) a process nm-applet is visible with "ps -el"
5) /etc/network/interfaces only contains the two lines concerning interface lo

How could I see the icon and manage a pptp connection?

I am using Hardy Heron.

---

### Post by LukonLinux on 2009-11-26
I think I have a related issue.  I am running a fresh 64-bit karmic install, and I use my usb connection to tether my phone.  It used to have a notification in the taskbar and a brief window telling me usb0 connected.  Both notifications have gone away.  Thankfully the connection still works, I just get no feedback.  I'd like to set it back, so I get the notification.

Does your connection work despite having no notification?

---

### Post by yvesg on 2010-01-25
Sorry for answering so late.

Yes, my connexion works. network-manager works, only the applet is invisible.

---

