---
title: "wpa_supplicant[1093]: Association request to the driver failed"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by ruben_linux on 2010-12-25
yesterday i update my ubuntu 10.04 lts, and began the problens. i am using 2.6.32-24-generic, in a HP DV6 2145es do we know?
syslog saidme: wpa_supplicant[1093]: Association request to the driver failed

search in google i founded that the problem is possible that it is in wpa_supplicant.conf. my fiel is in : /etc/dbus-1/system.d/wpa_supplicant.conf and i think that is necesary be in /etc . it is truh? when i check my fiel, i founded this:

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

my fiel is diferent than otres.
why?, i need help.

sorry for my english, i am from spain. 
thanks.

---

### Post by ruben_linux on 2010-12-25
i founded it :
[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/578431](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/578431)

but i need help for solve it

---

### Post by ruben_linux on 2010-12-31
this output was when i tried connect by Wicd

> Dec 31 15:47:55 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:47:55 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:47:55 CoYoTe dhclient: All rights reserved.
Dec 31 15:47:55 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:47:55 CoYoTe dhclient: 
Dec 31 15:47:55 CoYoTe dhclient: Listening on LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:55 CoYoTe dhclient: Sending on   LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:55 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:47:55 CoYoTe dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Dec 31 15:47:55 CoYoTe dhclient: send_packet: Network is unreachable
Dec 31 15:47:55 CoYoTe dhclient: send_packet: please consult README file regarding broadcast address.
Dec 31 15:47:55 CoYoTe kernel: [ 1910.913795] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 15:47:55 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:47:55 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:47:55 CoYoTe dhclient: All rights reserved.
Dec 31 15:47:55 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:47:55 CoYoTe dhclient: 
Dec 31 15:47:56 CoYoTe dhclient: Listening on LPF/eth0/c8:0a:a9:79:d5:48
Dec 31 15:47:56 CoYoTe dhclient: Sending on   LPF/eth0/c8:0a:a9:79:d5:48
Dec 31 15:47:56 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:47:56 CoYoTe kernel: [ 1911.058047] r8169: eth0: link down
Dec 31 15:47:56 CoYoTe kernel: [ 1911.060183] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 15:47:56 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:47:56 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:47:56 CoYoTe dhclient: All rights reserved.
Dec 31 15:47:56 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:47:56 CoYoTe dhclient: 
Dec 31 15:47:56 CoYoTe dhclient: Listening on LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:56 CoYoTe dhclient: Sending on   LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:56 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:47:56 CoYoTe dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Dec 31 15:47:56 CoYoTe dhclient: send_packet: Network is unreachable
Dec 31 15:47:56 CoYoTe dhclient: send_packet: please consult README file regarding broadcast address.
Dec 31 15:47:56 CoYoTe kernel: [ 1911.314438] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 15:47:56 CoYoTe kernel: [ 1911.314539] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 31 15:47:56 CoYoTe kernel: [ 1911.512690] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 31 15:47:56 CoYoTe kernel: [ 1911.710188] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 31 15:47:56 CoYoTe kernel: [ 1911.910255] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 31 15:47:58 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:47:58 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:47:58 CoYoTe dhclient: All rights reserved.
Dec 31 15:47:58 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:47:58 CoYoTe dhclient: 
Dec 31 15:47:58 CoYoTe kernel: [ 1913.428252] type=1503 audit(1293806878.474:19):  operation="open" pid=4261 parent=4240 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
Dec 31 15:47:58 CoYoTe dhclient: Listening on LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:58 CoYoTe dhclient: Sending on   LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:47:58 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:47:58 CoYoTe kernel: [ 1913.599950] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 31 15:47:58 CoYoTe kernel: [ 1913.800936] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 31 15:47:59 CoYoTe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Dec 31 15:47:59 CoYoTe kernel: [ 1914.001037] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 31 15:47:59 CoYoTe kernel: [ 1914.200065] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out
Dec 31 15:48:06 CoYoTe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Dec 31 15:48:18 CoYoTe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Dec 31 15:48:35 CoYoTe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Dec 31 15:48:48 CoYoTe dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Dec 31 15:49:00 CoYoTe dhclient: No DHCPOFFERS received.
Dec 31 15:49:00 CoYoTe dhclient: No working leases in persistent database - sleeping.
Dec 31 15:49:00 CoYoTe avahi-autoipd(wlan0)[4280]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 110).
Dec 31 15:49:00 CoYoTe avahi-autoipd(wlan0)[4280]: Successfully called chroot().
Dec 31 15:49:00 CoYoTe avahi-autoipd(wlan0)[4280]: Successfully dropped root privileges.
Dec 31 15:49:00 CoYoTe avahi-autoipd(wlan0)[4280]: Starting with address 169.254.7.222
Dec 31 15:49:05 CoYoTe avahi-autoipd(wlan0)[4280]: Callout BIND, address 169.254.7.222 on interface wlan0
Dec 31 15:49:05 CoYoTe avahi-daemon[967]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.222.
Dec 31 15:49:05 CoYoTe avahi-daemon[967]: New relevant interface wlan0.IPv4 for mDNS.
Dec 31 15:49:05 CoYoTe avahi-daemon[967]: Registering new address record for 169.254.7.222 on wlan0.IPv4.
Dec 31 15:49:09 CoYoTe avahi-autoipd(wlan0)[4280]: Successfully claimed IP address 169.254.7.222
Dec 31 15:49:09 CoYoTe dhclient: There is already a pid file /var/run/dhclient.pid with pid 4285
Dec 31 15:49:09 CoYoTe dhclient: killed old client process, removed PID file
Dec 31 15:49:09 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:49:09 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:49:09 CoYoTe dhclient: All rights reserved.
Dec 31 15:49:09 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:49:09 CoYoTe dhclient: 
Dec 31 15:49:09 CoYoTe dhclient: Listening on LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:49:09 CoYoTe dhclient: Sending on   LPF/wlan0/78:e4:00:1c:d2:79
Dec 31 15:49:09 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:49:09 CoYoTe dhclient: DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Dec 31 15:49:09 CoYoTe dhclient: send_packet: Network is unreachable
Dec 31 15:49:09 CoYoTe dhclient: send_packet: please consult README file regarding broadcast address.
Dec 31 15:49:09 CoYoTe avahi-autoipd(wlan0)[4280]: Got SIGTERM, quitting.
Dec 31 15:49:09 CoYoTe avahi-autoipd(wlan0)[4280]: Callout STOP, address 169.254.7.222 on interface wlan0
Dec 31 15:49:09 CoYoTe avahi-daemon[967]: Withdrawing address record for 169.254.7.222 on wlan0.
Dec 31 15:49:09 CoYoTe avahi-daemon[967]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.222.
Dec 31 15:49:09 CoYoTe avahi-daemon[967]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 31 15:49:10 CoYoTe dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 31 15:49:10 CoYoTe dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 31 15:49:10 CoYoTe dhclient: All rights reserved.
Dec 31 15:49:10 CoYoTe dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 31 15:49:10 CoYoTe dhclient: 
Dec 31 15:49:10 CoYoTe kernel: [ 1984.980559] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 31 15:49:10 CoYoTe dhclient: Listening on LPF/eth0/c8:0a:a9:79:d5:48
Dec 31 15:49:10 CoYoTe dhclient: Sending on   LPF/eth0/c8:0a:a9:79:d5:48
Dec 31 15:49:10 CoYoTe dhclient: Sending on   Socket/fallback
Dec 31 15:49:10 CoYoTe kernel: [ 1985.136021] r8169: eth0: link down
Dec 31 15:49:10 CoYoTe kernel: [ 1985.138269] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 15:49:10 CoYoTe kernel: [ 1985.187573] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 1)
Dec 31 15:49:10 CoYoTe kernel: [ 1985.380161] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 2)
Dec 31 15:49:10 CoYoTe kernel: [ 1985.580147] wlan0: direct probe to AP 00:80:5a:5c:cf:4c (try 3)
Dec 31 15:49:10 CoYoTe kernel: [ 1985.780159] wlan0: direct probe to AP 00:80:5a:5c:cf:4c timed out

in this output there isnt: "wpa_supplicant[1171]: Association request to the driver failed"

Why?

---

### Post by ruben_linux on 2010-12-31
will be necesary install this?

ruben@CoYoTe:~$ aptitude search wireless-lucid-generic
p   linux-backports-modules-wireless-lucid-generic         - Backported wireless drivers for generic kernel image            
p   linux-backports-modules-wireless-lucid-generic-pae     - Backported wireless drivers for generic-pae kernel image 

before updating network-manager running without this packets

---

### Post by ruben_linux on 2010-12-31
will be necesary install this?

ruben@CoYoTe:~$ aptitude search wireless-lucid-generic
p   linux-backports-modules-wireless-lucid-generic         - Backported wireless drivers for generic kernel image            
p   linux-backports-modules-wireless-lucid-generic-pae     - Backported wireless drivers for generic-pae kernel image 

before updating network-manager running without this packets

---

### Post by ruben_linux on 2011-01-01
aptitude show wpasupplicant

Paquete: wpasupplicant
Estado: instalado
Instalado automáticamente: no
Versión: 0.6.10-2
Prioridad: opcional
Sección: net
Desarrollador: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Tamaño sin comprimir: 971k
Depende de: libc6 (>= 2.4), libdbus-1-3 (>= 1.1.1), libnl1 (>= 1.1), libpcsclite1 (>= 1.5.3), libreadline6 (>= 6.0), libssl0.9.8 (>= 0.9.8m-1), lsb-base (>= 3.0-6),
            adduser
Sugiere: wpagui, libengine-pkcs11-openssl
Descripción: client support for WPA and WPA2 (IEEE 802.11i)
 WPA and WPA2 are methods for securing wireless networks, the former using IEEE 802.1X, and the latter using IEEE 802.11i. This software provides key negotiation with
 the WPA Authenticator, and controls association with IEEE 802.11i networks.
Página de inicio: [http://w1.fi/wpa_supplicant/](http://w1.fi/wpa_supplicant/)

when i read this output, i found that i dont have installed "libdbus-1-3". when i search in ubuntu i didnt found. i download by web debian and install without a problem, now i will reboot and then post my result

---

### Post by idachev on 2011-01-13
Did you manage to fix this problem? I also updated ubuntu on two of my desktops and on both of them wireless stop working.

---

### Post by idachev on 2011-01-13
I manage to fix the problem by removing the network manager and created this script:

```

#!/bin/bash

if [ "$(whoami)" != "root" ]; then
    echo "Requires sudo to start me.";
    exit 1;
fi

INTERFACE="wlan0"
DEVICE="wext"
CONFIG="/etc/wpa_supplicant/my_ap.conf"

if [ "$1" = "-stop" ]; then
    echo
    echo "Disconnect from access point..."
    killall -v wpa_supplicant
    exit 0
fi

echo
echo -e "In order to work this script you should disable\nthe wireless network from GNOME/KDE network manager."
echo
echo -e "To change the access point use this config:\n$CONFIG"
echo
echo -e "To scan for access points use this command:\niwlist scan"
echo
echo -e "To disconnect from the access point use this command:\nsudo killall wpa_supplicant"
echo -e "or just call this script with -stop argument:\n$0 -stop"
echo

# give a second to read the messages
sleep 1

# This should be the content of config file:
#
# ap_scan=1
# ctrl_interface=/var/run/wpa_supplicant 
# 
# network={
#         ssid="SSID_NAME"
#         scan_ssid=0
#         proto=WPA
#         key_mgmt=WPA-PSK
#         psk="PASSWORD"
#         pairwise=TKIP
#         group=TKIP
# }

# In order to scan for access points use this:
# iwlist scan

# make temp log file
TMP_LOG="$( mktemp /tmp/wpa_connect_log.XXXXXXXXXX)"

# first disable the wlan interface
ifconfig $INTERFACE down

# remove the dhcp client IPs for this address
dhclient -r $INTERFACE

# call wpa_supplicant in daemon mode -B
echo
echo
echo "Starting wpa_supplicant check log file: $TMP_LOG"
wpa_supplicant -B "-D$DEVICE" "-i$INTERFACE" "-c$CONFIG" -dd -t -foutput $TMP_LOG

# up the wireless interface
ifconfig $INTERFACE up

# some wireless configuration
iwconfig $INTERFACE mode Managed

# this one will try to obtain new IP from DHCP
dhclient $INTERFACE

```You should configure the config file and set correct interface name.
You could get the interface name and the SSID by scanning with this:
iwlist scan

---

