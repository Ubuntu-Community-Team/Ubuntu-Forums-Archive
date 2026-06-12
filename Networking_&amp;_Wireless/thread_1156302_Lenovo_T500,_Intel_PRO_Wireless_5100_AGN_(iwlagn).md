---
title: "Lenovo T500, Intel PRO Wireless 5100 AGN (iwlagn)"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by xefialtis on 2009-05-11
I have been around the net looking for the solution to this issue, and have had no luck.

I recently got a Lenovo T500 with the Intel PRO/Wireless 5100 AGN [Shiloh] Wireless gizmo.
I copied over my etc/network/interfaces file and the /etc/wpa_supplicant/wpa_supplicant.conf files, which both worked PERFECTLY on the T43 I had previously.

However, now, the whole wireless thing just seems broken:

It won't always find the SSID, and when it does, it won't associate to the Access Point. Sometimes it will get the SSID and associate to the AP, but then it won't get an IP...and some times it won't do anything.

I have no firewall set, I have no funky or weird 3rd party programs. This is a fresh and clean Ubuntu 9.04 Jaunty install.

**/etc/network/interfaces**
> 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp
iface wlan0 inet dhcp

mapping wlan0
	script /usr/local/sbin/map-scheme
	map any any
	map work work
	map home home
	map uta uta

iface home inet dhcp
	pre-up iwconfig wlan0 txpower on
	pre-up ifconfig wlan0 up
	wireless-essid [REDACTED]
	wireless-channel 6
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
	# address 000.000.000.000
	# netmask 000.000.000.000
	# network 000.000.000.000
	# gateway 000.000.000.000
	# post-up vpnc-connect [REDACTED]
	# pre-down vpnc-disconnect
	post-down iwconfig wlan0 txpower off

iface work inet dhcp
	pre-up iwconfig wlan0 txpower on
        pre-up ifconfig wlan0 up
	wireless-essid [REDACTED]
        # wireless-channel 6
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
	# address 000.000.000.000
	# netmask 000.000.000.000
	# network 000.000.000.000
	# gateway 000.000.000.000
        # post-up vpnc-connect [REDACTED]
        # pre-down vpnc-disconnect
        post-down iwconfig wlan0 txpower off

iface uta inet dhcp
	pre-up iwconfig wlan0 txpower on
	pre-up ifconfig wlan0 up
	wireless-essid [REDACTED]
        # wireless-channel 6
	# address 000.000.000.000
	# netmask 000.000.000.000
	# network 000.000.000.000
	# gateway 000.000.000.000
	# post-up vpnc-connect [REDACTED]
	# pre-down vpnc-disconnect
	post-down iwconfig wlan0 txpower off

iface vpntun0 inet manual
	# up vpnc-connect [REDACTED]
	# down vpnc-disconnect


**/etc/wpa_supplicant/wpa_supplicant.conf**
> 
# Work Network
network={
        ssid="[REDACTED]"
        key_mgmt=WPA-EAP
        ca_cert="/etc/wpa_supplicant/ldsca.cer"
        identity="[REDACTED]"
        password="[REDACTED]"
	id_str="work"
}

# Home Network
network={
        ssid="[REDACTED]"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk=[REDACTED - Large Hex Number]
        # identity=""
        # password=""
	id_str="home"
}


**/var/log/syslog**
> 
May 11 13:19:03 [REDACTED] kernel: [15074.253335] Registered led device: iwl-phy0:radio
May 11 13:19:03 [REDACTED] kernel: [15074.253349] Registered led device: iwl-phy0:assoc
May 11 13:19:03 [REDACTED] kernel: [15074.253362] Registered led device: iwl-phy0:RX
May 11 13:19:03 [REDACTED] kernel: [15074.253376] Registered led device: iwl-phy0:TX
May 11 13:19:03 [REDACTED] kernel: [15074.331285] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:04 [REDACTED] dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 11 13:19:04 [REDACTED] dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 11 13:19:04 [REDACTED] dhclient: All rights reserved.
May 11 13:19:04 [REDACTED] dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
May 11 13:19:04 [REDACTED] dhclient: 
May 11 13:19:04 [REDACTED] dhclient: wmaster0: unknown hardware address type 801
May 11 13:19:04 [REDACTED] kernel: [15075.296321] eth0: no IPv6 routers present
May 11 13:19:05 [REDACTED] dhclient: wmaster0: unknown hardware address type 801
May 11 13:19:05 [REDACTED] dhclient: Listening on LPF/wlan0/[REDACTED]
May 11 13:19:05 [REDACTED] dhclient: Sending on   LPF/wlan0/[REDACTED]
May 11 13:19:05 [REDACTED] dhclient: Sending on   Socket/fallback
May 11 13:19:05 [REDACTED] kernel: [15075.617900] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:05 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May 11 13:19:06 [REDACTED] kernel: [15076.917550] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:08 [REDACTED] kernel: [15079.222960] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:11 [REDACTED] kernel: [15081.514137] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:12 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May 11 13:19:13 [REDACTED] kernel: [15083.911898] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:15 [REDACTED] kernel: [15086.177307] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:18 [REDACTED] kernel: [15088.458252] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:19 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May 11 13:19:20 [REDACTED] kernel: [15090.737907] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:22 [REDACTED] kernel: [15093.085814] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:24 [REDACTED] kernel: [15095.354341] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:27 [REDACTED] kernel: [15097.705394] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:29 [REDACTED] kernel: [15100.010374] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:30 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May 11 13:19:32 [REDACTED] kernel: [15102.402786] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:34 [REDACTED] kernel: [15104.711634] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:36 [REDACTED] kernel: [15107.079639] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:38 [REDACTED] kernel: [15109.374129] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:41 [REDACTED] kernel: [15111.693680] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:42 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May 11 13:19:43 [REDACTED] kernel: [15113.960782] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:45 [REDACTED] kernel: [15116.353851] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:48 [REDACTED] kernel: [15118.726883] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:50 [REDACTED] kernel: [15121.077345] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:52 [REDACTED] kernel: [15123.329508] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:55 [REDACTED] kernel: [15125.722909] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:57 [REDACTED] dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May 11 13:19:57 [REDACTED] kernel: [15128.013233] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:19:59 [REDACTED] kernel: [15130.270546] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:01 [REDACTED] /USR/SBIN/CRON[1498]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 11 13:20:02 [REDACTED] kernel: [15132.572984] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:04 [REDACTED] kernel: [15134.872460] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:06 [REDACTED] kernel: [15137.172988] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:07 [REDACTED] dhclient: No DHCPOFFERS received.
May 11 13:20:07 [REDACTED] dhclient: No working leases in persistent database - sleeping.
May 11 13:20:07 [REDACTED] avahi-autoipd(wlan0)[1641]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
May 11 13:20:07 [REDACTED] avahi-autoipd(wlan0)[1641]: Successfully called chroot().
May 11 13:20:07 [REDACTED] avahi-autoipd(wlan0)[1641]: Successfully dropped root privileges.
May 11 13:20:07 [REDACTED] avahi-autoipd(wlan0)[1641]: Starting with address [REDACTED]
May 11 13:20:09 [REDACTED] kernel: [15139.437814] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:11 [REDACTED] kernel: [15141.734332] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:12 [REDACTED] avahi-autoipd(wlan0)[1641]: Callout BIND, address [REDACTED] on interface wlan0
May 11 13:20:12 [REDACTED] avahi-daemon[3118]: Joining mDNS multicast group on interface wlan0.IPv4 with address [REDACTED].
May 11 13:20:12 [REDACTED] avahi-daemon[3118]: New relevant interface wlan0.IPv4 for mDNS.
May 11 13:20:12 [REDACTED] avahi-daemon[3118]: Registering new address record for [REDACTED] on wlan0.IPv4.
May 11 13:20:13 [REDACTED] kernel: [15144.003102] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:15 [REDACTED] kernel: [15146.282515] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:16 [REDACTED] avahi-autoipd(wlan0)[1641]: Successfully claimed IP address [REDACTED]
May 11 13:20:18 [REDACTED] kernel: [15148.581133] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:20 [REDACTED] kernel: [15150.882225] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:22 [REDACTED] kernel: [15153.217411] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:25 [REDACTED] kernel: [15155.592969] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:27 [REDACTED] kernel: [15157.882237] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:29 [REDACTED] kernel: [15160.174305] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:32 [REDACTED] kernel: [15162.499489] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:34 [REDACTED] kernel: [15164.818585] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:36 [REDACTED] kernel: [15167.134709] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:39 [REDACTED] kernel: [15169.412591] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:41 [REDACTED] kernel: [15171.719372] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:43 [REDACTED] kernel: [15174.074830] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:45 [REDACTED] kernel: [15176.377082] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:48 [REDACTED] kernel: [15178.635297] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:50 [REDACTED] kernel: [15180.926075] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:52 [REDACTED] kernel: [15183.217199] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:55 [REDACTED] kernel: [15185.548827] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:56 [REDACTED] ntpdate[1725]: can't find host ntp.ubuntu.com 
May 11 13:20:56 [REDACTED] ntpdate[1725]: no servers can be used, exiting
May 11 13:20:57 [REDACTED] kernel: [15187.851431] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:20:59 [REDACTED] kernel: [15190.158844] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:02 [REDACTED] kernel: [15192.469627] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:04 [REDACTED] kernel: [15194.771013] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:06 [REDACTED] kernel: [15197.007802] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:08 [REDACTED] kernel: [15199.342541] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:11 [REDACTED] kernel: [15201.616676] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:13 [REDACTED] kernel: [15204.032913] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:15 [REDACTED] kernel: [15206.330935] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:18 [REDACTED] kernel: [15208.613415] iwlagn: Requested user TXPOWER 15 below limit.
May 11 13:21:20 [REDACTED] kernel: [15210.912911] iwlagn: Requested user TXPOWER 15 below limit.

Above, it bound to a 169.x.x.x address, not in my address space of 10.x.x.x...

If you have any ideas, I am all ears...

---

### Post by Crafty Kisses on 2009-05-11
Let's try a couple of simple things here. What happens when you try to find your wireless network through the Terminal, does it give you any error messages? You can try this by running the following:
```
iwlist wlan0 scan
```
If you can't see your wireless network, then you can try running the following commands and then try to search again and see if it recognizes your wireless network, so try running the following:
```
ifconfig wlan0 down
ifconfig wlan0 up
```
Then once you have done that, try to search again by obviously running the following:
```
iwlist wlan0 scan
```
Try that first, and see if that works. Now upon further research on your wireless card, you can get some new drivers for the Intel PRO Wireless 5100, and you might want to see this thread for more information: [http://ubuntuforums.org/showpost.php?p=5754065&postcount=62](http://ubuntuforums.org/showpost.php?p=5754065&postcount=62). I also wouldn't mind seeing the results of the following output:
```
dmesg
```

---

### Post by trent1980 on 2009-08-16
i have a w500 with the 5100 agn wireless card ...

I just upgraded from Hardy to Intrepid (64 bit). The wireless did not work at all in Hardy and I was on Jaunty before but it was just too slow (I think video issues). The issue with my wireless is strange. It seems to take a really long time to connect and then it fails on getting an IP 9 times out of 10. But then I finally connect and all is fine.

When it fails, it posts something like this:

Aug 15 20:03:17 t-ubu804 dhclient: Internet Systems Consortium DHCP Client V3.1.1
Aug 15 20:03:17 t-ubu804 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Aug 15 20:03:17 t-ubu804 dhclient: All rights reserved.
Aug 15 20:03:17 t-ubu804 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 15 20:03:17 t-ubu804 dhclient: 
Aug 15 20:03:17 t-ubu804 dhclient: wmaster0: unknown hardware address type 801
Aug 15 20:03:18 t-ubu804 dhclient: wmaster0: unknown hardware address type 801
Aug 15 20:03:18 t-ubu804 dhclient: Listening on LPF/wlan0/00:21:5d:b8:70:8a
Aug 15 20:03:18 t-ubu804 dhclient: Sending on   LPF/wlan0/00:21:5d:b8:70:8a
Aug 15 20:03:18 t-ubu804 dhclient: Sending on   Socket/fallback
Aug 15 20:03:22 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Aug 15 20:03:26 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Aug 15 20:03:32 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Aug 15 20:03:46 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Aug 15 20:03:54 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Aug 15 20:04:12 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug 15 20:04:23 t-ubu804 dhclient: No DHCPOFFERS received.
Aug 15 20:04:23 t-ubu804 dhclient: No working leases in persistent database - sleeping.

When is succeeds, it posts this to logs:

Aug 15 20:27:23 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Aug 15 20:27:27 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 15 20:27:32 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Aug 15 20:27:45 t-ubu804 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Aug 15 20:27:45 t-ubu804 dhclient: DHCPOFFER of 192.168.0.188 from 192.168.0.1
Aug 15 20:27:45 t-ubu804 dhclient: DHCPREQUEST of 192.168.0.188 on wlan0 to 255.255.255.255 port 67
Aug 15 20:27:45 t-ubu804 dhclient: DHCPACK of 192.168.0.188 from 192.168.0.1
Aug 15 20:27:45 t-ubu804 avahi-autoipd(wlan0)[14195]: Got SIGTERM, quitting.
Aug 15 20:27:45 t-ubu804 avahi-autoipd(wlan0)[14195]: Callout STOP, address 169.254.7.118 on interface wlan0
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: Withdrawing address record for 169.254.7.118 on wlan0.
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.118.
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 15 20:27:45 t-ubu804 avahi-autoipd(wlan0)[14196]: client: RTNETLINK answers: No such process
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.188.
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: New relevant interface wlan0.IPv4 for mDNS.
Aug 15 20:27:45 t-ubu804 avahi-daemon[5224]: Registering new address record for 192.168.0.188 on wlan0.IPv4.
Aug 15 20:27:45 t-ubu804 dhclient: bound to 192.168.0.188 -- renewal in 32542 seconds.
Aug 15 20:57:48 t-ubu804 avahi-daemon[5224]: Registering new address record for fe80::21c:25ff:fe97:c612 on eth0.*.



On a side note, I installed Wicd because I found that on another forum post. No luck.

Just wondering what you did Xefialtis or if you ever got yours fixed. I haven't tried the ndsiwrapper (but I've had to use that before with other installations of hardy)

---

