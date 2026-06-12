---
title: "RT73 Wireless USB network adapter: works, but poor performance"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by dpapathanasiou on 2011-09-04
I'm running the latest version of mythbuntu (11.04) with an Edimax USB network adapter (model EW-7318USg, RT73 chipset).

Since this is a DVR, I don't have my keyboard plugged in at all times, and to avoid the keyring password input that the gui requires, I tried getting networking started with edits to /etc/network/interfaces instead.

The machine recognizes the adapter as wlan0 automatically, so I first tried editing /etc/network/interfaces by adding these lines:

```

auto wlan0
iface wlan0 inet dhcp
wireless-essid [essid]
wireless-key [hex key]

```But it didn't work, since the network manager gui seemed to override or ignore those settings.

I then removed the network gui with this command:

```
sudo apt-get purge network-manager-gnome
```It still didn't work, but when I tried connecting via the command line, using the steps outlined here -- [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) -- I established a connection.

So to get that to work on boot, I added these lines to /etc/rc.local

```

iwconfig wlan0 essid '[essid]'
iwconfig wlan0 key [hex key]
ip link set wlan0 up
dhclient wlan0
service network-manager start

```I thought I wouldn't need that last line -- service network-manager start -- since the service should already be running by the time rc.local is invoked, but without it, the connection didn't work.

So that combination (updates to both /etc/network/interfaces and /etc/rc.local) gives me a connection on boot, and without needing to type a password for the keyring.

The only problem is, the perform of the adapter is poor; it's a noticeable slow connection, and running a trace, I see 70% packet loss or more.

Is there anything I can do to improve this?

---

### Post by praseodym on 2011-09-04
Do you have several drivers loaded? Namely rt73usb and rt2500usb? Check with

```
lsmod

```
In that case, blacklist the wrong one:

```
echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

---

### Post by dpapathanasiou on 2011-09-05
> **praseodym said:**
> Do you have several drivers loaded? Namely rt73usb and rt2500usb? Check with

```
lsmod

```In that case, blacklist the wrong one:

```
echo "blacklist rt2500usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```and reboot.

Yes, I did have rt2500usb loaded in addition to rt73usb, and blacklisting it solved the problem.

I also found that I do not need the entries in /etc/rc.local -- the extra lines in /etc/network/interfaces are enough.

Thank you for your help.

---

