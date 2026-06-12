---
title: "WLAN after suspend-to-ram"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Afteroid on 2010-01-30
Hi everybody,

I'm using Ubuntu 9.10.

I've got no problems with my WLAN, but sometimes after awaking from suspend-to-ram, which was triggered by the command: 
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:1
```my WLAN doesn't work anymore. The problem only occurs, if my computer is at least 5 hours in suspend. 

Restarting *networking* or *NetworkManager*:
```
sudo /etc/init.d/networking restart 

or 

sudo /etc/init.d/network-manager restart
```didn't help. Finally I found out, that *dhclient* crashes. So I tried to restart *dhclient*:
```
sudo /sbin/dhclient
```As an output, I got:
```
[...]
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
No working leases in persistent database - sleeping
```I noticed, that normally *dhclient* is started as:
```
sudo /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-4ec7cc61-6835-471d-921e-f486ea52627c-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
```so I tried that. Then I got:
```
[...]
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
```The problem can easily be solved by reboot, but that not really a solution for me. Can anyone help? 

Thanks in advance.

Edit: I'm not able to reproduce the error anytime I want. How could I kill dhclient in a normal (working) system, that it doesn't restart itself. And how can change the title *gobuntu *in *Ubuntu. *Sorry, I'm quite new in this forum.

---

### Post by jc66 on 2011-03-12
I am going to bump this because I have got exactly the same problem.

My system is Lucid on an eeePC netbook, and wakeup after suspend worked fine until a couple of weeks ago when suddenly after restart there was no internet connection.

The symptons are very similar as in the origional post, other than it happens after every suspend restart, no matter how short the time interval is.

My router is acting as the dhcp server. If I run ifconfig after suspend/restart, then the ip address given is not valid (it is out of the range of my subnet.)

If anyone can suggest anything I would appreciate it.

---

