---
title: "Wireless Network woes in Kubuntu 9.10"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by packmule on 2010-02-23
I have installed Kubuntu 9.10 recently, and have been able to initially connect to several unsecure wireless networks without any problems. However, after approximately 20-30 minutes, I completely lose the network connection and it is impossible to reconnect. I tried shutting down knetworkmanager and restarting it, and this did not work. I thought there might be a problem with knetworkmanager, so I installed nm-applet, the Gnome network manager program, and I had the exact same problem; I lose the network connection after 20-30 minutes and can't get it back until I reboot the system. As soon as I reboot the system, however, I am able to once again reconnect to a network.

I am running an Acer notebook computer.

I'd appreciate any input.

-Jack

---

### Post by Joe Ker1086 on 2010-02-23
what wireless card are you using.

---

### Post by packmule on 2010-02-24
It says Atheros AR5B93 for my Wireless hardware. I had another laptop with KDE Mandriva 2008 on it that also had Atheros Wireless hardware, and it also had some wireless networking glitches (though not this particular problem). I'm still having the same problem today, although my network connection has been lasting a little bit longer before losing it (as much as an hour).

Some more background info: I ran nm-applet in a konsole to see what data it might show about my problem and I got the following readout on the konsole around the time I lost my network connection:

** (nm-applet:2037): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:2037): DEBUG: foo_client_state_changed_cb
** (nm-applet:2037): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:2037): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:2037): DEBUG: foo_client_state_changed_cb
** (nm-applet:2037): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:2037): DEBUG: going for offline with icon: notification-network-wireless-disconnected

I'm not sure if that helps, but I thought I'd throw it out there.

---

### Post by Greenwidth on 2010-02-24
Installing backport modules seems to fix it for some:

linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

---

### Post by packmule on 2010-02-25
Thank you, Greenwidth from the UK, I just downloaded the backports a few minutes ago, I'll have to let time tell the rest of the story. I'll let you know how it works.

---

### Post by packmule on 2010-02-26
Installing the backports seems to solve the problem; I spent two hours yesterday on the internet without losing my wireless connection, and am at two consecutive hours and counting for today. I appreciate the help, and I'm going to mark this one as solved.

---

