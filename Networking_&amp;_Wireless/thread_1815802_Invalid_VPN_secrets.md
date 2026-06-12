---
title: "Invalid VPN secrets"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by Deathmoon on 2011-07-31
I'm running Ubuntu 11.04 and recently wanted to start using a VPN service ([https://www.tunnelr.com/](https://www.tunnelr.com/)).  I configured everything as per the website and now when I attempt to connect I get the error "...invalid VPN secrets.".  I looked in the forums and attempted the simply reboot and restarting network-manager and that did not work.  

I also edited the nm-vpnc-service.conf file in /etc/dbus-1/system.d/ (see below) and it didn't work.

```
[SIZE="1"]<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
	<policy user="root">
		<allow own="org.freedesktop.NetworkManager.vpnc"/>
		<allow send_destination="org.freedesktop.NetworkManager.vpnc"/>
	</policy>
	<policy context="default">
		<deny own="org.freedesktop.NetworkManager.vpnc"/>
		<deny send_destination="org.freedesktop.NetworkManager.vpnc"/>
	</policy>
	<policy user="at_console">
		<allow own="org.freedesktop.NetworkManager.vpnc"/>
		<allow send_destination="org.freedesktop.NetworkManager.vpnc"/>
	</policy>
</busconfig>[/SIZE]
```

That said, it's still not working.  Any clue?

---

### Post by Deathmoon on 2011-08-01
I reset my password on the vendors website, downloaded my keys and tried again.  This time it worked.  Furthermore, I'm not sure if this had anything to do with it but my username maybe case sensitive.  

No changes to config files where needed to resolve the issue.

---

