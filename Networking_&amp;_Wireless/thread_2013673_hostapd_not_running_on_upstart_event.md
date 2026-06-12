---
title: "hostapd not running on upstart event"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by shemyak on 2012-07-01
Hello everyone,

I run a WLAN access point with a USB WLAN card. I can do it starting **hostapd** manually after the card is plugged in:

<card plugged in>
```
$ [COLOR="Blue"]sudo hostapd /etc/hostapd/hostapd-min.conf[/COLOR]
Configuration file: /etc/hostapd/hostapd-min.conf
Using interface wlan1 with hwaddr xx:xx:xx:xx:xx:xx and ssid 'my-wlan'
```
<access point works>

```
$ [COLOR="Blue"]cat /etc/hostapd/hostapd-min.conf[/COLOR]
interface=wlan1
ssid=my-wlan
channel=1
```

Now I want **hostapd** to start/stop automatically when the card is plugged in/out. I wrote an upstart config file:

```
$ [COLOR="Blue"]cat /etc/init/hostapd.conf[/COLOR]
description	"hostapd daemon for master mode for wlan1"
start on net-device-added IFACE=wlan1
exec /usr/sbin/hostapd /etc/hostapd/hostapd-min.conf
```

**init** has reloaded its configuration.
But nothing happens, **hostapd** does not start. Some syslog lines which I think are relevant:

<card plugged in>
```
[60547.432069] usb 1-4: new high-speed USB device number 16 using ehci_hcd
[60547.656028] rtl8192cu: MAC address: xx:xx:xx:xx:xx:xx
...
[60547.912090] init: event_new: Pending net-device-added event
[60547.912201] init: Handling net-device-added event
[60547.912484] init: job_register: Registered instance /com/ubuntu/Upstart/jobs/network_2dinterface/wlan1
[60547.912691] init: event_pending_handle_jobs: New instance network-interface (wlan1)
[60547.912730] init: network-interface (wlan1) goal changed from stop to start
[60547.912835] init: network-interface (wlan1) state changed from waiting to starting
...
[60547.923899] init: event_finished: Finished net-device-added event
```

So, although I assigned **hostapd** to run on **net-device-added** event, it does not start.

Thanks for any light on this!

---

### Post by shemyak on 2012-07-02
SOLVED. In the [upstart cookbook]("http://upstart.ubuntu.com/cookbook/"), the syntax was given
```
start on net-device-added IFACE=wlan1
```
but the working syntax appears to be
```
start on net-device-added [COLOR="Red"]INTERFACE[/COLOR]=wlan1
```
Wondering whether this is a bug of the upstart cookbook, repeated throughout all the text several times.

---

### Post by FerroPower on 2013-01-06
I know this is solved but since my problem is related I would like to ask some query. 


I also run hostapd wireless AP but I want to AUTORUN  the HostApd  script whenever the Wireless is Enabled and stop it whenever the Wireless is disabled. 

I tried many different methods using upstart but no event gets triggered when a Wireless is enabled or disabled. 

Can someone please help.

MODS. I am sorry for posting it in SOLVED thread.

---

