---
title: "Network Manager dissapeared"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by snkngshps on 2008-12-13
I just restarted my computer and when it came back on the network manager never loaded. I thought it was odd, so I restarted again.. still no network manager. I have no idea what happened, I haven't even installed any update recently. I tried manually running *nm-applet --sm-disable* and I'm getting this error:

```
** (nm-applet:9868): WARNING **: <WARN> applet_dbus_manager_start_service(): Could not aquire the NetworkManagerUserSettings service as it is already taken.
Return 3.

(nm-applet:9698): GLib-GObject-CRITICAL ** g-objet_unref: assertion 'G_IS_OBJECT (object)' failed
```

I can't connect to anything at all or get online (this is typed from another computer). If anyone could help, I would appreciate it.

---

### Post by The Cog on 2008-12-13
You could try Completely Removing network manager and reinstalling, or try installing wicd instead. I find wicd much better behaved. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by iponeverything on 2008-12-13
the wireless card does not show disabled when you do -- does it:

lshw -c network

also do a killall nm-applet and try to restart it again from the command line.

---

### Post by snkngshps on 2008-12-13
> **iponeverything said:**
> the wireless card does not show disabled when you do -- does it:

lshw -c network

also do a killall nm-applet and try to restart it again from the command line.

It doesn't say it's disabled. I tried the killall command as well but it says that no processes were killed :-/

---

### Post by snkngshps on 2008-12-13
> **The Cog said:**
> You could try Completely Removing network manager and reinstalling, or try installing wicd instead. I find wicd much better behaved. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I'm not able to connect to the internet at all, wirelessly or wired, so I'm not able to install anything at this time :-/

---

