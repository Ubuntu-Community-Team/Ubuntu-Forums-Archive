---
title: "Ralink USB wifi dongle wont work"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by h2sammo on 2012-01-27
I have installed the correct driver (i believe) but cannot get any wireless network interfaces to work. Any ideas? This is Hardy Heron i believe.

```
atv@Crystalbuntu:~$ uname -a
Linux Crystalbuntu 2.6.24-28-generic #1 SMP Sat Oct 16 17:46:03 UTC 2010 i686 GNU/Linux
```
```

atv@Crystalbuntu:~$ lsusb | grep Ralink
Bus 002 Device 004: ID 148f:2770 Ralink Technology, Corp.
```

```
atv@Crystalbuntu:~$ sudo lsmod | grep rt2x
rt2x00usb              12800  0 
rt2x00lib              22528  1 rt2x00usb
rfkill                  8596  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165780  2 rt2x00usb,rt2x00lib
usbcore               146412  6 rt2x00usb,usbhid,ehci_hcd,uhci_hcd
```

```
atv@Crystalbuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Wireless
auto eth2
iface eth2 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf


auto eth0
iface eth0 inet dhcp
```

```
atv@Crystalbuntu:~$ cat /etc/wpa_supplicant.conf
network={
ssid="TRENDnet652"
proto=WPA
key_mgmt=WPA-PSK
psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
}
```

```
atv@Crystalbuntu:~$ sudo ifup eth2
[sudo] password for atv: 
eth2: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth2' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
Failed to disable WPA in the driver.
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.eth2.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
```

---

### Post by Bucky Ball on 2012-01-27
Hardy is no longer supported. I suggest the current long term support release, 10.04 LTS, supported until April 2013. You should be able to upgrade via the update manager or by tweaking your software source settings to 'Display Long Term Support releases' or something along those lines.

---

### Post by h2sammo on 2012-01-28
cannot upgrade, this is a special distribution called crystalbuntu for appletv. can you help me troubleshoot?

---

