---
title: "Wifi does not Re-connect (unless i unplug it..)"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by fasti on 2009-04-23
Shalom and Hi to everybody,

I post this plea for help after spending a few days trying to write a shell script that would (and almost does) re-connect my WiFi at home when it periodically disconnects.
The reason for the disconnections might have something to do with a torrent sharing SW I have running 24/7, or it might be a bad router issue.

My Question-
The wireless connection will NOT re-connect (after it drops connection about once a day) unless I unplug the wifi dongle (adapter), and plug it back in.
WHY?????    :)
I tried "sudo /etc/init.d/networking restart", and it fails before unplugging the adapter and WORKS after the unplugging+replugging.
pleeease... HELP ME !

Here is the output of the "sudo /etc/init.d/networking restart"
when it fails (before I unplug the wifi):

#user@Host:~$ sudo /etc/init.d/networking restart
# * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
#There is already a pid file /var/run/dhclient.wlan0.pid with pid 134612120
#Internet Systems Consortium DHCP Client V3.0.5
#Copyright 2004-2006 Internet Systems Consortium.
#All rights reserved.
#For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

#wmaster0: unknown hardware address type 801
#wmaster0: unknown hardware address type 801
#Listening on LPF/wlan0/00:21:27:cb:71:a3
#Sending on   LPF/wlan0/00:21:27:cb:71:a3
#Sending on   Socket/fallback
#DHCPRELEASE on wlan0 to 192.168.50.1 port 67
#send_packet: Network is unreachable
#send_packet: please consult README file regarding broadcast address.
#SIOCSIFFLAGS: Input/output error
#SIOCSIFFLAGS: Input/output error
#There is already a pid file /var/run/dhclient.wlan0.pid with pid 134612120
#Internet Systems Consortium DHCP Client V3.0.5
#Copyright 2004-2006 Internet Systems Consortium.
#All rights reserved.
#For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

#wmaster0: unknown hardware address type 801
#SIOCSIFFLAGS: Input/output error
#SIOCSIFFLAGS: Input/output error
#wmaster0: unknown hardware address type 801
#Listening on LPF/wlan0/00:21:27:cb:71:a3
#Sending on   LPF/wlan0/00:21:27:cb:71:a3
#Sending on   Socket/fallback
#receive_packet failed on wlan0: Network is down
#DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
#send_packet: Network is down
#DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
#send_packet: Network is down
#DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
#send_packet: Network is down
#DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
#send_packet: Network is down
#No DHCPOFFERS received.
#No working leases in persistent database - sleeping.
#RTNETLINK answers: Network is down
#run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
#                                                                         [ OK ]


if it helps, I can post the output of this command AFTER the unplugging+replugging, when it works and reconnect to the network.

Any help would be much appreciated.

---

### Post by fasti on 2009-04-24
bump...

---

### Post by rlzyoner on 2009-04-24
Hmmmm, thats a strange one.
Off the top of my head, why not bang together a script like this

```

#!/bin/bash

ifconfig wlan0 down
ifconfig wlan0 up
iwconfig wlan0 essid YOUR_ESSID
iwconfig wlan0 mode managed
iwconfig wlan0 key YOUR_KEY
dhclient3
```

Save it as whatever.sh
chmod a+x whatever.sh

Then run ./whatever.sh whenever the wifi drops.

---

### Post by fasti on 2009-04-24
I tried that, same thing - it only works after unplugging+replugging the usb dongel (wifi adapter).

Could it be that the usb port itself goes into some idle mode?
Or it could have something to do with initializing the network..?

I noticed that when reconnection works, the output does not have these lines (in comparison to when it fails as I posted above):
.
.
.
#send_packet: Network is unreachable
#send_packet: please consult README file regarding broadcast address.
.
.
#SIOCSIFFLAGS: Input/output error
#SIOCSIFFLAGS: Input/output error
.
.
#receive_packet failed on wlan0: Network is down
.
.
.

---

### Post by rlzyoner on 2009-04-24
I'm not sure mate.
Its definately a strange one.
If I get a solution or an idea, I'll pass it on.

---

### Post by Neosano on 2010-05-09
It's a necro, but I have exactly the same problem. :-S

---

### Post by eltonw on 2010-05-09
You didn't post what type of wireless / network card is on your system. Have you tried installing newer drivers? There are serious issues with connectivity in the (current) kernel. Rather than re-compile the drivers at each update, I have chosen to use the unofficial newer kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/")

\\:D/sometimes _[COLOR="Olive"][FONT="Comic Sans MS"]it pays to do a SEARCH[/FONT][/COLOR]_:
[http://swiss.ubuntuforums.org/showthread.php?p=8580879]("http://swiss.ubuntuforums.org/showthread.php?p=8580879")

Perhaps this may also interest you:
[http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922") [#136]

HTH....

---

### Post by Neosano on 2010-05-10
> **eltonw said:**
> You didn't post what type of wireless / network card is on your system. Have you tried installing newer drivers? There are serious issues with connectivity in the (current) kernel. Rather than re-compile the drivers at each update, I have chosen to use the unofficial newer kernel:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.3-lucid/")

\\:D/sometimes _[COLOR=Olive][FONT=Comic Sans MS]it pays to do a SEARCH[/FONT][/COLOR]_:
[http://swiss.ubuntuforums.org/showthread.php?p=8580879](http://swiss.ubuntuforums.org/showthread.php?p=8580879)

Perhaps this may also interest you:
[http://ubuntuforums.org/showthread.php?p=9203922#post9203922](http://ubuntuforums.org/showthread.php?p=9203922#post9203922) [#136]

HTH....

Not sure which wireless adapter I have, but it's something with zd1211rw chipset.
Using Wicd, and it's not just not reconnecting. It can't even obtain the list of visible networks. The light on the adapter is blinking slowly.
Here's the kern.log on disconnecting
```

May 10 23:11:11 Anna kernel: [52611.505021] No probe response from AP 1c:af:f7:1b:54:92 after 500ms, disconnecting.
May 10 23:11:11 Anna kernel: [52611.568042] cfg80211: All devices are disconnected, going to restore regulatory settings
May 10 23:11:11 Anna kernel: [52611.568048] cfg80211: Restoring regulatory settings
May 10 23:11:11 Anna kernel: [52611.568051] cfg80211: Calling CRDA to update world regulatory domain
May 10 23:11:11 Anna kernel: [52611.570813] cfg80211: World regulatory domain updated:
May 10 23:11:11 Anna kernel: [52611.570816]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 10 23:11:11 Anna kernel: [52611.570819]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 23:11:11 Anna kernel: [52611.570822]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 23:11:11 Anna kernel: [52611.570825]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 10 23:11:11 Anna kernel: [52611.570828]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 23:11:11 Anna kernel: [52611.570830]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 10 23:11:15 Anna kernel: [52615.194108] ADDRCONF(NETDEV_UP): wlan3: link is not ready
May 10 23:11:15 Anna kernel: [52615.360879] ATL1E 0000:02:00.0: irq 28 for MSI/MSI-X
May 10 23:11:15 Anna kernel: [52615.361152] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 23:11:20 Anna kernel: [52620.025401] ADDRCONF(NETDEV_UP): wlan3: link is not ready
```

---

