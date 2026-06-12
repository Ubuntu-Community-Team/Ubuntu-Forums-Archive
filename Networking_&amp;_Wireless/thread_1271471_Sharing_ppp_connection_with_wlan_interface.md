---
title: "Sharing ppp connection with wlan interface"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by viniciusandre on 2009-09-20
Dear all.

I'm on Debian Sid, and as Ubuntu community is being really kind helping me I'm trying to find out what's happening around here.

I've been trying to serve a ppp0 internet connection through a wireless network. I made a small script to be ran when i want to do that:

ifdown wlan0
iwconfig wlan0 essid "VinaNET" mode Ad-Hoc
ifconfig wlan0 192.168.0.254
echo 1 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/dnsmasq stop
/etc/init.d/dnsmasq start
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

The script goes just fine and the client computer can see the wireless network but can't connect, it only keeps trying:

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval x

Here's my dnsmasq.conf file:

domain-needed
bogus-priv
interface=wlan0
dhcp-range=192.168.0.1,192.169.0.100,12h

And my syslog on the router computer.

Sep 20 23:46:48 vinicius kernel: [ 3349.172165] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
Sep 20 23:46:51 vinicius kernel: [ 3351.704879] wlan0: Selected IBSS BSSID 0e:45:9e:94:06:07 based on configured SSID

The above goes like that forever.

I'm not quite sure if that's an iptables or a dnsmasq problem.

Thanks!

---

