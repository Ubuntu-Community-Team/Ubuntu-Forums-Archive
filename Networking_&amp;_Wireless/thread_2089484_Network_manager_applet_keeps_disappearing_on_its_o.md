---
title: "Network manager applet keeps disappearing on its own"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by AdriCS on 2012-11-29
Hi!
I'm using Ubuntu 10.04 LTS with Gnome desktop. The network manager applet disappears from the task bar on its own around 15-20 minutes after starting the session. When it shuts downs, the wifi is also cut down. 
At that moment, if I open a terminal and type *nm-applet*, it reappears again and I can reconnect to the wifi. 

However this isn't permanent, as it will disappear on its own yet again.

This is the error that I get:
```

** (nm-applet:3334): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3334): DEBUG: foo_client_state_changed_cb
** (nm-applet:3334): DEBUG: foo_client_state_changed_cb
** (nm-applet:3334): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:3334): DEBUG: foo_client_state_changed_cb
** Message: Caught signal 15, shutting down...

```

I have already tried these, but with no positive result:

[LIST=1]
[*]Reinstalled these packages: network-manager, network-manager-gnome, network-manager-pptp, network-manager-pptp-gnome
[*]Modified the *nm-system-settings.conf* and changed the line *managed=false* to *managed=true*.
[/LIST]


So any idea?.

Cheers!.

PS: The *interfaces*  file contains:
```

auto lo
iface lo inet loopback

```

---

### Post by AdriCS on 2012-11-30
No one?.

Come on!. I still have faith in that this can be solved!!!

---

### Post by AdriCS on 2013-01-14
Hello!!

New info for this subject. 

First, if I use a wired connection, the network applet won't disappear. 

Also, there are times when the network manager applet will work well, without shutting down on its own even after 4 hours. Yet sometimes it will shut down right after logging in.

No one can help me?

Thanks!

---

### Post by tgalati4 on 2013-01-14
Check the log files in /var/log.  Signal 15 is the "terminate" signal, as opposed to the kill signal (9).  So something is sending the terminate signal.  It could be static electricity is momentarily shorting your wireless connection--remove your Ugg boots.  It could be some other process that needs the network, but fails and then sends the signal.  It could be a hardware problem--reseat the modem card and the antennas--typically by removing the access panel on the underside of the laptop.

The fact that a wired connection works OK, would indicate a wireless hardware problem (intermittent) that shuts down network manager because the wireless signal becomes unavailable.  Try reseating and test again.

Unfortunately, linux expects perfect hardware.  When the hardware is wonky, you end up chasing several, unhelpful software problems.

I'm going to put my money down that this is a Dell laptop.

---

### Post by AdriCS on 2013-01-15
Hi and thanks for your reply!

I'll check the logs once I get home... And is a Toshiba! :lolflag:

---

