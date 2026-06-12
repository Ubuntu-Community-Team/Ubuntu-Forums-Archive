---
title: "NMCLI works in script when I run it, but not in CRON"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by wandrson on 2012-02-24
This is under Ubuntu 11.10

I have a script that starts a pptp vpn connection fetches a couple of files, then closes the connection.  When I run this script from a terminal prompt it works perfectly; however, when I schedule it to run with CRON the nmcli commands in the script generate errors.  The VPN connections are configured to be used by any user, not just my account.

Here is the relevant line of the script

/usr/bin/nmcli con up id MyVPN

and here is the errors that generate when using it in CRON

** (process:6360): WARNING **: _nm_object_get_property: Error getting 'WirelessHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.624" (uid=1000 pid=6360 comm="/usr/bin/nmcli con up id MyVPN ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1029 comm="NetworkManager ")   ** (process:6360): WARNING **: 

_nm_object_get_property: Error getting 'WwanHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.624" (uid=1000 pid=6360 comm="/usr/bin/nmcli con up id MyVPN ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1029 comm="NetworkManager ")   ** (process:6360): WARNING **: 

_nm_object_get_property: Error getting 'WimaxHardwareEnabled' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.624" (uid=1000 pid=6360 comm="/usr/bin/nmcli con up id MyVPN ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1029 comm="NetworkManager ")   ** (process:6360): WARNING **: 

_nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager: (9) Rejected send message, 2 matched rules; type="method_call", sender=":1.624" (uid=1000 pid=6360 comm="/usr/bin/nmcli con up id MyVPN ") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1029 comm="NetworkManager ")


Any ideas would be appreciated!

---

