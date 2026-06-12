---
title: "Jaunty openvpn security bug - Survival Guide"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by drplix on 2009-04-25
Migrated to Jaunty from Hardy.  Rely on openvpn to get into the office network when on the road.  Didn't anticipate any problems since this has been rock solid.  Problem - get a weird warning about trust/security - don't even see an attempt to call the vpn server.

Found this bug report...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818)

And this comment...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818/comments/3](https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818/comments/3)

Turns out this is a dbus privileges setting bug in Jaunty.

To give the openvpn module permission to access dbus you need to edit...

/etc/dbus-1/system.d/nm-openvpn-service.conf  

And add these lines...

<policy user="at_console">
		<allow own="org.freedesktop.NetworkManager.openvpn"/>
		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
	</policy>

Reboot to ensure dbus gets these new settings.  Voila openvpn works again just like it did on Hardy!

Hope this helps someone.

---

