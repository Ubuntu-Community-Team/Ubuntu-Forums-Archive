---
title: "Cisco Pix vpnc connection"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by ldarby on 2010-12-09
We use CISCO PIX vpn.
I have been wrestling with vpnc with and without network manager for months and I finally got it working.
I made three changes, none of which should have made a difference, but now it is working great, does not time out, and does not mess up name resolution or routing.
1. I changed Dbus permissions to permit service to run as ordinary user.  this does not make sense since it has to run as root to change network settings, (and in fact the service runs as root).  If I take this out, it quits working.
Added below to  /etc/dbus-1/system.d/nm-vpnc-service.conf
	<policy user="loyd">
		<allow own="org.freedesktop.NetworkManager.vpnc"/>
		<allow send_destination="org.freedesktop.NetworkManager.vpnc"/>
	</policy>
2. I disabled dead peer connection which previously had no impact.
3. I enabled xauth with blank password even though we do not use xauth. First run of vpnc prompted for password.  I typed in junk and it connected. after that it does not prompt any more.
I hope you find this helpful.

---

