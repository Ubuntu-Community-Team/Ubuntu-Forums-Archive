---
title: "nintendo ds access point"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by olithered on 2009-07-20
I struggled all last night to get this working, finding bits of the puzzle all over the place. So I wanted to record the procedure in one place for others to follow.

AIM: Share the (wired) internet connection by emulating a wifi access point in WEP mode for use by a nintendo ds (not WPA capable).

PLATFORM: Ubuntu 9.04 (32bit), Netgear WAG511 PCMCIA.

PRE-REQ: Ensure no wireless connections are auto connecting.

METHOD: Switch from ath5k to madwifi. Ensure network device is created in AP mode. Manually setup wifi essid/key. Tweak wifi parameters. Configure port forwarding and nat. Manually configure nintendo.

COMMAND HISTORY:
====
v@lop:~$ sudo -i
[sudo] password for v: 
root@lop:~# modprobe -r ath5k
root@lop:~# modprobe ath_pci
root@lop:~# wlanconfig ath0 destroy
root@lop:~# wlanconfig ath0 create wlandev wifi0 wlanmode ap
ath0
root@lop:~# iwconfig ath0 essid n key 1234567890
root@lop:~# ifconfig ath0 192.168.43.51  netmask 255.255.255.0
root@lop:~# echo 1 > /proc/sys/net/ipv4/ip_forward
root@lop:~# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
root@lop:~# iwpriv ath0 authmode 2
====

NINTENDO CONFIG:
====
ssid: n
WEP (40bit): 1234567890
ip/netmask: 192.168.43.62/255.255.255.0
gateway: 192.168.43.51
dns: <isp dns>
====

TODO: Script/Automate PC setup. Add DHCP.

COMMENTS/QUESTIONS/SUGGESTIONS: Welcome!

---

