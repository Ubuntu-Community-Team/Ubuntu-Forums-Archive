---
title: "Network manager not auto-connecting"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by carrett on 2012-03-13
Hi, I"m on amd64 Oneric. This happened for me in Debian wheezy as well. The only fix I could find there was to use KDE (for some reason KDE+NetworkManager didn't have this problem). On a different install of Oneric on the same system (recently), this wasn't a problem.

When I add a connection with Network Manager (always checking the available to all users and connect automatically boxes), it creates the correct file in /etc/NetworkManager/system-connections HOWEVER on reboot my passphrase is not being utilized and the "auto-connect" does not work. Instead, when I click the wireless menu and select my AP, NM again asks for the passphrase and ANOTHER file is created in /etc/NM/s-c. So now I have "Auto Sobotka" #s 1-11 with none of them auto-connecting me at boot.

Once I select my AP and enter my passphrase, it works totally fine (am posting from it now).

Happy to post any needed info! Thanks in advance.

---

### Post by carrett on 2012-03-13
Bump!

---

### Post by carrett on 2012-03-15
Third time's a charm?

---

### Post by carrett on 2012-03-16
OK I've come up with some log stuff that hopefully will help.

So, here's what I did. I reinstalled NM, tried connecting, setting connection available to all and to auto-connect, rebooted. Auto-connection didn't happen, when I selected my router, it did not use the saved password in /etc/NetworkManager/system-connections, instead it asked me again and created another file in that folder. Here is the syslog output (grepping wlan) from the reboot after initial connection saving:

```
Mar 16 16:44:03 colebear NetworkManager[1019]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.6/0000:08:00.0/0000:09:02.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): new 802.11 WiFi device (driver: 'rt61pci' ifindex: 3)
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): now managed
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): bringing up device.
Mar 16 16:44:03 colebear kernel: [   43.807559] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): preparing device.
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): deactivating device (reason 'managed') [2]
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): supplicant interface state: starting -> ready
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar 16 16:44:03 colebear NetworkManager[1019]: <info> (wlan1): supplicant interface state: ready -> inactive
```

and here is some log from when I selected my router (and it asked me AGAIN for the password):

```
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) starting connection 'Sobotka 2'
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> (wlan1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> (wlan1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1/wireless): access point 'Sobotka 2' has security, but secrets are required.
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> (wlan1): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar 16 16:46:33 colebear NetworkManager[1019]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.

```

(Keep in mind, "Sobotka" and "Sobotka 1," both containing the password and settings to be available to all and auto-connect, already existed in /etc/NetworkManager/system-connections.

I know it's not a driver issue because auto-connect works just great with wicd and straight up editing /etc/network/interfaces. I want to get NM working though cause it just looks so nice and shiny in my menu. Also I don't want to have to question every default software choice that Ubuntu makes.

---

### Post by carrett on 2012-03-23
One last, sad, desperate bump... then it's on to just using /etc/network/interfaces, no more connection managers.

---

