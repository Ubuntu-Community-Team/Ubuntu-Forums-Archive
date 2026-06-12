---
title: "Unreliable Broadcom BCM43224 wireless"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by rivode on 2011-06-13
Hi

I'm having all sorts of problems with my wireless connections in an HP Pavilion DM1.  I'm sure it was working last week...

I have two access points, one with WPA, one unsecured.  It's not working with either.  I can connect to both of them fine with a wifi USB adapter.

I've tried:

[LIST]
[*]Using Wicd instead of networkmanager
[*]Using the proprietary driver
[*]Installing the linux-firmware package from Oneric (version 1.54)
[*]Changing the frequencies the AP runs on
[/LIST]

I haven't tried ndiswrapper yet.

I used to use this with Lucid, with no problems (except I had to use wicd with it).

Does anyone have any other suggetions?

The relevant "lspci -v" follows:

```

02:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
	Subsystem: Hewlett-Packard Company Device 1510
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 93500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: brcm80211
	Kernel modules: brcm80211

```

and part of /var/log/syslog, while connecting to the unsecured AP (I hope it's the relevant bit):

```

Jun 13 20:29:36 kite NetworkManager[1331]: user_connection_updated_cb: assertion `old_connection != NULL' failed
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) starting connection 'Auto unsecured-ap'
Jun 13 20:29:36 kite NetworkManager[1331]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 13 20:29:36 kite NetworkManager[1331]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0/wireless): connection 'Auto unsecured-ap' requires no security.  No secrets needed.
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Config: added 'ssid' value 'unsecured-ap'
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Config: added 'scan_ssid' value '1'
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 13 20:29:36 kite NetworkManager[1331]: <info> Config: set interface ap_scan to 1
Jun 13 20:29:36 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 13 20:29:39 kite wpa_supplicant[1522]: Trying to associate with 00:11:22:33:44:55 (SSID='unsecured-ap' freq=2472 MHz)
Jun 13 20:29:39 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 13 20:29:39 kite kernel: [  224.944465] wlan0: direct probe to 00:11:22:33:44:55 (try 1/3)
Jun 13 20:29:40 kite kernel: [  225.144053] wlan0: direct probe to 00:11:22:33:44:55 (try 2/3)
Jun 13 20:29:40 kite kernel: [  225.344040] wlan0: direct probe to 00:11:22:33:44:55 (try 3/3)
Jun 13 20:29:40 kite kernel: [  225.544032] wlan0: direct probe to 00:11:22:33:44:55 timed out
Jun 13 20:29:49 kite wpa_supplicant[1522]: Authentication with 00:11:22:33:44:55 timed out.
Jun 13 20:29:49 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 13 20:29:49 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 13 20:29:52 kite wpa_supplicant[1522]: Trying to associate with 00:11:22:33:44:55 (SSID='unsecured-ap' freq=2472 MHz)
Jun 13 20:29:52 kite kernel: [  238.043557] wlan0: direct probe to 00:11:22:33:44:55 (try 1/3)
Jun 13 20:29:52 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 13 20:29:53 kite kernel: [  238.240041] wlan0: direct probe to 00:11:22:33:44:55 (try 2/3)
Jun 13 20:29:53 kite kernel: [  238.440050] wlan0: direct probe to 00:11:22:33:44:55 (try 3/3)
Jun 13 20:29:53 kite kernel: [  238.640036] wlan0: direct probe to 00:11:22:33:44:55 timed out
Jun 13 20:30:02 kite wpa_supplicant[1522]: Authentication with 00:11:22:33:44:55 timed out.
Jun 13 20:30:02 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun 13 20:30:02 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 13 20:30:06 kite wpa_supplicant[1522]: Trying to associate with 00:11:22:33:44:55 (SSID='unsecured-ap' freq=2472 MHz)
Jun 13 20:30:06 kite NetworkManager[1331]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun 13 20:30:06 kite kernel: [  251.155402] wlan0: direct probe to 00:11:22:33:44:55 (try 1/3)
Jun 13 20:30:06 kite kernel: [  251.352062] wlan0: direct probe to 00:11:22:33:44:55 (try 2/3)
Jun 13 20:30:06 kite kernel: [  251.552064] wlan0: direct probe to 00:11:22:33:44:55 (try 3/3)
Jun 13 20:30:06 kite kernel: [  251.752065] wlan0: direct probe to 00:11:22:33:44:55 timed out
Jun 13 20:30:12 kite NetworkManager[1331]: <info> (wlan0): device state change: 5 -> 3 (reason 39)
Jun 13 20:30:12 kite NetworkManager[1331]: <info> (wlan0): deactivating device (reason: 39).
Jun 13 20:30:12 kite NetworkManager[1331]: <info> Policy set 'Auto NETCOMM808zvbo' (wlan1) as default for IPv4 routing and DNS.

```

---

### Post by superduperlinuxperson on 2011-06-13
i have had similar problems, and reinstalling the b43 drivers seems too have fixed it:
step 1: download these two things from here:[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
step 2: extract the second one to your home folder, and copy the other one their too
step 3: download b43-fwcutter from the software center
step 4: execute these steps too get it working:

~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

---

### Post by rivode on 2011-06-13
I'll give that a shot tonight.  I notice though that it seems to be using the "brcm80211" driver, not b43 (perhaps they're the same?), so perhaps that's the problem.

---

### Post by rivode on 2011-06-14
It seems to be working... for now.  I used the restricted driver:

[LIST=1]
[*]Install the restricted driver via System/Administration/Additional drivers
[*]Add to /etc/modprobe.d/broadcom-sta-common.conf:
[INDENT]```
blacklist brcm80211
```[/INDENT]
[*]Update the initramfs:
[INDENT]```
# update-initramfs -u -k $(uname -r)
```[/INDENT]
[*]Reboot
[/LIST]

I restarted, then "iwconfig" showed the network card under a different device.  Last time I didn't add the blacklist line, nor did I update the initramfs.

Somewhere along the line I also installed [the firmwares from oneiric]("https://launchpad.net/ubuntu/oneiric/+source/linux-firmware/1.54").

As a bonus, the wireless light turns blue again when it's enabled!

Part of the instructions came from [the Debian wiki]("http://wiki.debian.org/wl").

---

### Post by wildmanne39 on 2013-04-06
Thread closed. Please do not post in old threads.

---

