---
title: "D-Link DWA-140 Wireless USB - Drivers, Ping Spikes, and Log Spam"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by Wulfrunner on 2010-06-03
I've had a D-Link DWA-140 Wireless USB dongle for a couple of years. It uses the Ralink RT2870 chipset and every time a new distribution comes out, this thing breaks and I have to fix it again. Of course, every time I forget how I did it. The three main problems that come up are:

[LIST=1]
[*]The drivers are not installed or simply do not work (e.g. lights but no connection, no lights at all, connection drops, computer hangs, etc.)
[*]There is a periodic lag spike or loss of connection. It usually happens every 1-2 minutes and is horrible for VoIP or games.
[*]Three or four log files are spammed with meaningless error messages
[/LIST]

**Drivers**
The best way to fix the driver problem is to use the drivers from Ralink: 
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

You can find a fairly straightforward set of instructions on how to do that here:
[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

**Error Messages**
The debug / error messages usually say something like:
```
wpa_supplicant[1213]: CTRL-EVENT-SCAN-RESULTS 
kernel: [ 2993.865942] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 515

```
They appear in syslog, messages, kern.log, and daemon.log by the tens of thousands. For me, these messages are related to the periodic connection loss (below).

**Lag Spikes**
The culprit is NetworkManager. The roaming features cause a periodic scan for new networks and that just doesn't agree with the rt2870. You can find a complete description of the technical aspects of the log spam and connection loss here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)

Oh, it also contains **[COLOR="Green"]a simple workaround by Wagner Volanin[/COLOR]** for those of you who just want the nightmare to end.

---

