---
title: "nm-applet not working, wireless problems"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by Hydrothrax on 2009-09-03
Hello,

The wireless doesn't work on my Ubuntu 9.04. I've been in another country for a year and was working on a wired connection the whole time, but now I'm back home and nothing works. Ubuntu can't even look for signals because the Network Manager isn't working! I keep getting this:

darkfire@Basilisk:~$ nm-applet --sm-disable

** (nm-applet:3743): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


anyone know what to do?

- Hydro

---

### Post by missirismissiris on 2009-09-18
I am having a similar problem. When I start up nm-applet loads and starts as usual, but after a while it disappears from the taskbar and wi-fi connection quits working. When I open bash and manually restart nm-applet it works again, but even then I've seen the network manager occasionally stops working:

```

iris@irisgarden:~$ nm-applet

** (nm-applet:7883): WARNING **: Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2

** (nm-applet:7883): WARNING **: Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2
** (nm-applet:7883): DEBUG: applet_common_device_state_changed
** (nm-applet:7883): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:7883): DEBUG: applet_common_device_state_changed

** (nm-applet:7883): WARNING **: Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2

** (nm-applet:7883): WARNING **: Invalid connection: 'NMSettingWireless' / 'ssid' invalid: 2
** (nm-applet:7883): DEBUG: foo_client_state_changed_cb
** (nm-applet:7883): DEBUG: applet_common_device_state_changed
** (nm-applet:7883): DEBUG: applet_common_device_state_changed
** (nm-applet:7883): DEBUG: foo_client_state_changed_cb
** Message: Caught signal 15, shutting down...


```

What is *signal 15*?

I have re-installed network-manager from the official Ubuntu repository using Synaptic, the same problem still continues. I had deleted /etc/network/interfaces file (a suggested solution found through Google), but it made little difference if any.

If the proverbial "s" hits the fan, are there any alternative to using network-manager or nm-applet -- or **can I even sniff and connect to wi-fi using terminal commands** (this would also be useful when I have to use fail-safe terminal if something goes awfully wrong with the GUI)?


This is Ubuntu 9.04

My network devices gathered from lspci
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
```

---

### Post by mikerobinson on 2011-02-03
I have the same issue as missirismissiris. Ubuntu 10.10 everything fresh out of the box. Running nm-applet fixes the problem temporarily, but it keeps crashing.

```
$ nm-applet 
** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:2021): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2021): DEBUG: foo_client_state_changed_cb
** (nm-applet:2021): DEBUG: foo_client_state_changed_cb
** Message: Caught signal 15, shutting down...
```

---

### Post by avi95 on 2011-06-27
Forget 10.10, I have the same problem with Ubuntu 11.04 !!!
I think it's high time somebody does something about this bug...

---

### Post by garvinrick4 on 2011-06-27
This is kind of an old thread here is a way to just sort of reboot the network-manager
```
sudo service network-manager stop
```
```
sudo rm /var/lib/NetworkManager/NetworkManager.state
```
```
sudo service network-manager start
```

---

### Post by garvinrick4 on 2011-06-27
> Forget 10.10, I have the same problem with Ubuntu 11.04 !!!
I think it's high time somebody does something about this bug...
It very well could be a driver problem and not network-manager at all.
Start a Thread and supply users with Network cards:
```
sudo lshw -C network
```
```
iwconfig
```

---

