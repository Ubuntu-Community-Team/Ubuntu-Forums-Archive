---
title: "VPN Connections menu blank"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by Kurtosis on 2013-01-09
I have about 20 VPN connections configured and available in my top right systray VPN Connections menu (Ubuntu 12.04 x64).  

Occasionally they all disappear and the menu is completely blank (I even lose the 'Disconnect from VPN' option).  This can happen after regular use, or after Suspending and reactivating the system.  

When this happens while I'm connected to one of the VPNs in the list, the connection remains with no problems.  Viewing htop, I can see the OpenVPN service with the connection still running, it's just the systray menu that fails/crashes/whatever.

I'd screenshot it, but apparently the screenshot function doesn't work with that menu open.

Anyone know how to restore this menu without relogging/restarting?

---

### Post by ahallubuntu on 2013-01-09
Yes.  It's a known bug with Network Manager I've been recently annoyed with, too.  I'm not sure why such an annoying bug has persisted so long.  (This is the kind of frustrating bug that makes new users less likely to stick with Ubuntu IMO.)  I think the fix will finally be rotated in (forgive me, I don't have the link to the bug report on Launchpad anymore) with 12.04.2 LTS release (which means it should make it into the repositories at that time).

It doesn't affect just the VPN menu; it affects other items in the Network Manager menu as well.

The work-around is quite simple if a pain: kill nm-applet and re-start it.  You don't even need to be root to do this.  Dump into  terminal and type:

```
ps -afe | grep nm-applet 
```

to find the process number - then:

```
kill -9 nnnn
```

where "nnnn" is the process number (first column after username).

Then - launch a new nm-applet:

```
nm-applet &
```

and you're done.

When I get around to it, I'm simply going to kill/restart nm-applet in the resume script because I too see this issue a lot on a laptop where I'm sleeping/resuming often.

---

### Post by Kurtosis on 2013-01-10
Thank you!  Exactly what I was looking for.  I figured I could restart it, just wasn't sure the process name.  Much appreciated!

---

### Post by RomanIvanov on 2013-06-26
I got the same problem on my Ubuntu 12.04 on Dell Latitude 6550, out of the blue user's VPN connections disappear or whole submenu items are missed.

For "only user VPN connections disappear" - you can restore them by click on "Configure VPN", do any changes, and press Close.
For "whole submenu items are missed" - just do nm-applet restart, as sugested above.

---

### Post by matteus_blanc2 on 2014-06-13
> **ahallubuntu said:**
> Yes.  It's a known bug with Network Manager I've been recently annoyed with, too.  I'm not sure why such an annoying bug has persisted so long.  (This is the kind of frustrating bug that makes new users less likely to stick with Ubuntu IMO.)  I think the fix will finally be rotated in (forgive me, I don't have the link to the bug report on Launchpad anymore) with 12.04.2 LTS release (which means it should make it into the repositories at that time).

It doesn't affect just the VPN menu; it affects other items in the Network Manager menu as well.

The work-around is quite simple if a pain: kill nm-applet and re-start it.  You don't even need to be root to do this.  Dump into  terminal and type:

```
ps -afe | grep nm-applet 
```

to find the process number - then:

```
kill -9 nnnn
```

where "nnnn" is the process number (first column after username).

Then - launch a new nm-applet:

```
nm-applet &
```

and you're done.

When I get around to it, I'm simply going to kill/restart nm-applet in the resume script because I too see this issue a lot on a laptop where I'm sleeping/resuming often.


You can alias this command:
```

kill -9 $(ps -afe | grep nm-applet$ | head -2 | tail -1 | cut -d" " -f5) && nm-applet &

```

in the ~/.bash_alias file as follows:
```

alias fix-nm-applet='kill -9 $(ps -afe | grep nm-applet$ | head -2 | tail -1 | cut -d" " -f5) && nm-applet &'

```

Takes some of the pain out of it...

---

