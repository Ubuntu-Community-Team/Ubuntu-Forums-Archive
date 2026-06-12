---
title: "Ad-hoc network doesn't survive a reboot"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by legege on 2011-03-01
Hi,

I'm configuring an HP Mini 110 (wireless BCM4313) to use it as a small Access Point (ad-hoc mode).

I want to make my configuration reboot friendly. With what I have right now, as soon as I reboot the laptop, the wireless interface configuration isn't correctly setup. I have to do "ifdown eth1; ifup eth1" manually.

Here is what I have in /etc/network/interfaces for the wireless interface:

```

auto eth1
iface eth1 inet static
  address 192.168.30.1
  netmask 255.255.255.0
  wireless-mode ad-hoc
  wireless-essid HOME-ADHOC
  wireless-channel 6
  wireless-key 1234567890

```

When I reboot, my iwconfig is:

```

lo     no wireless extensions.

eth0   no wireless extensions.

eth1  IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.437GHz  Access Point: Not-Associated
          Bit Rate:8 Mb/s   Tx-Power: 24 dBm
          Retry min limit:7   RTS thr:off    Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5   Signal level=0 dBm  Noise level=-86dBm
          Rx invalid nwid:0  Rx invalid crypt:0   Rx invalid frag:0
          Tx excessive retries:4   Invalid misc:0   Missed beacon:0

```

And the interface the static IP.

After my "ifdown eth1; ifup eth0", iwconfig looks like:

```

lo     no wireless extensions.

eth0   no wireless extensions.

eth1  IEEE 802.11  ESSID:"HOME-ADHOC"
          Mode:Ad-Hoc  Frequency:2.437GHz  Cell: 02:2C:3C:93:9D:89
          Bit Rate=11 Mb/s   Tx-Power:24 dBm
          Retry min limit:7   RTS thr:off    Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5   Signal level=0 dBm  Noise level=-86dBm
          Rx invalid nwid:0  Rx invalid crypt:0   Rx invalid frag:0
          Tx excessive retries:4   Invalid misc:0   Missed beacon:0

```

Here is what I installed to make the BCM4313 working: bcmwl-kernel-source wireless-tools wpasupplicant

So the question is how can I avoid having to bring down and up the interface?

Thanks!

---

### Post by legege on 2011-03-01
It looks like the same problem is described here:

[Post #336975: I need to restart wireless-network once after boot]("http://ubuntuforums.org/showthread.php?t=336975")

Any solution?

---

