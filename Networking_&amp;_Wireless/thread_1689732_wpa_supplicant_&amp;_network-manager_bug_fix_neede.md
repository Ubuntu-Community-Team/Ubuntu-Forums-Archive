---
title: "wpa_supplicant &amp; network-manager bug fix needed"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by elbanaan on 2011-02-17
Hi all,

I'm am looking for a fix of a known bug, being this one:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128)

in short, I get this error:

Could not request DBus service name: org.freedesktop.DBus.Error.AccessDenied Connection ":1.85" is not allowed to own the service "fi.epitest.hostap.WPASupplicant" due to security policies in the configuration file.
wpa_supplicant[3477]: Failed to initialize wpa_supplicant

Wireless was working fine before an upgrade, and is still working fine (i'm using Wicd now).

However, the fix mentioned in the link (reinstalling wpasupplicant) did not work, and the error persists.

Could someone be so kind to help me out?


further info (possibly just changing one of these files should work)

ubuntu 10.04 lucid
network-manager 0.8
wpa_supplicant v0.6.9

--------------------------------
/etc/dbus-1/system.d/wpa_supplicant.conf

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="fi.epitest.hostap.WPASupplicant"/>

                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy group="netdev">
                <allow send_destination="fi.epitest.hostap.WPASupplicant"/>
                <allow send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
        <policy context="default">
                <deny own="fi.epitest.hostap.WPASupplicant"/>
                <deny send_destination="fi.epitest.hostap.WPASupplicant"/>
                <deny send_interface="fi.epitest.hostap.WPASupplicant"/>
        </policy>
</busconfig>
network={
 ## my network info, not relevant I guess :)
}
---------------------------------------
/usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service

[D-BUS Service]
Name=fi.epitest.hostap.WPASupplicant
Exec=/sbin/wpa_supplicant -u -s
User=root
----------------------------------------
/etc/dbus-1/system.d/NetworkManager.conf

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="org.freedesktop.NetworkManager"/>
                <allow own="org.freedesktop.NetworkManagerSystemSettings"/>

                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManagerSystemSettings"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>
        <policy user="haldaemon">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <policy at_console="true">
                <allow send_destination="org.freedesktop.NetworkManager"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.DBus.Introspectable"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.DBus.Properties"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.AccessPoint"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Connection.Active"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device.Cdma"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device.Wired"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device.Gsm"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device.Serial"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device.Wireless"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.Device"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.DHCP4Config"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.IP4Config"/>

                <allow send_destination="org.freedesktop.NetworkManager"
                       send_interface="org.freedesktop.NetworkManager.VPN.Connection"/>
        </policy>
        <policy context="default">
                <deny own="org.freedesktop.NetworkManager"/>
                <deny own="org.freedesktop.NetworkManagerSystemSettings"/>

                <deny send_destination="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManagerSystemSettings"/>

                <!-- The org.freedesktop.NetworkManagerSettings.Connection.Secrets
                     interface is secured via PolicyKit.
                  -->
        </policy>

        <limit name="max_replies_per_connection">512</limit>
</busconfig>

---

