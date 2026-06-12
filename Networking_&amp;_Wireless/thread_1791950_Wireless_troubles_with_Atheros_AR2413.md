---
title: "Wireless troubles with Atheros AR2413"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by aph216 on 2011-06-27
Hello

I'm running Natty on Acer Aspire 3690 (Atheros AR2413) and I've encountered weird issues with Wi-Fi. I'm using Linksys WAG120-N router that works well with mobile devices and worked well with this laptop and Windows XP. On Ubuntu however it takes a long time for Wi-Fi to connect after booting (1-30 minutes). Last wireless related messages in syslog when it waits to connect are

```
Jun 27 20:27:08 laptop NetworkManager[790]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:06:01.0/ssb0:0/net
/eth0
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): now managed
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): bringing up device.
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): preparing device.
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): deactivating device (reason: 2).
Jun 27 20:27:08 laptop NetworkManager[790]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jun 27 20:27:08 laptop kernel: [   15.610779] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 27 20:27:08 laptop NetworkManager[790]: <info> modem-manager is now available
Jun 27 20:27:08 laptop NetworkManager[790]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 27 20:27:08 laptop NetworkManager[790]: <info> Trying to start the supplicant...
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): supplicant manager state:  down -> idle
Jun 27 20:27:08 laptop NetworkManager[790]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Jun 27 20:27:08 laptop gdm-simple-slave[890]: WARNING: Unable to load file '/etc/gdm/custom.conf': Nie ma takiego pliku ani katalogu
Jun 27 20:27:09 laptop NetworkManager[790]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun 27 20:27:09 laptop wpa_supplicant[895]: Failed to initiate AP scan.
```

During this time "iwlist wlan0 scanning" doesn't find any devices.

I found out though that when I start an ad hoc hotspot on my phone, Ubuntu immediately starts to scan for networks, finds my router and connects.

Full relevant syslog here: [http://pastebin.com/e0kURhpX](http://pastebin.com/e0kURhpX)
Notice that I started the hotspot at 20:29.

The router is running a WPA2 mixed B/G network, but I've tried turning the encryption off with no effect.

---

### Post by aph216 on 2011-06-28
Solved by installing madwifi from SVN.

---

### Post by JadeLinux on 2011-07-20
how do you install that driver is you cannot get a inet connection?

---

