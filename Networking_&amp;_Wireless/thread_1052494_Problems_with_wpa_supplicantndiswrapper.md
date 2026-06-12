---
title: "Problems with wpa_supplicant/ndiswrapper"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by ittiam on 2009-01-27
I have been using wpa_supplicant with ndiswrapper for quite sometime now. But recently I had to use a dsl-connection so I used pppoeconf and it went through successfully. But when I returned to use wifi it doesn't work. 

So I removed dsl configuration from /etc/network/interfaces file. 

Then I found the following from dmesg

```

ittiam@Inspiron-e1505:~$ dmesg | grep ndiswrapper
[   22.525866] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   22.577890] usbcore: registered new interface driver ndiswrapper
[  114.013972] usbcore: deregistering interface driver ndiswrapper
[  114.058935] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  114.116588] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  114.117651] ndiswrapper 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  114.117735] ndiswrapper 0000:0b:00.0: setting latency timer to 64
[  114.124297] ndiswrapper: using IRQ 16
[  114.530419] usbcore: registered new interface driver ndiswrapper
[  114.536657] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  524.857209] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)

```

```

[  191.566405] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  194.069554] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  204.703137] eth1: no IPv6 routers present
[  242.675324] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  243.101032] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  253.332055] eth1: no IPv6 routers present
[  314.195795] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  524.857209] ndiswrapper (iw_set_freq:325): setting configuration failed (00010003)

```

But I am able get wireless up successfully using knetworkmanager.

---

### Post by ittiam on 2009-01-27
Some more information to share. When i ran wpa_supplicant in verbose mode I found the following,

It is scanning for my essid but it says it is skipping it because it is blacklisted. 

I mean is there even a way to blacklist an essid?

---

### Post by kevdog on 2009-01-27
What are the commands you are passing to wpa_supplicant and how are you invoking the wpa_supplicant statement on the command line?

---

### Post by ittiam on 2009-01-28
Command

```
sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf
```

my /etc/network/interfaces file

```
auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -B
post-down killall -q wpa_supplicant

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
wpa_supplicant.conf

```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="essid"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       group=CCMP TKIP
       pairwise=CCMP TKIP
       psk=passphrase
}

```

As I said things were working fine but when I configured for a dsl connection using pppoeconf and then removed dsl entry from interfaces file, i face this problem. But weird that knetworkmanager works.

---

### Post by ittiam on 2009-01-28
Ok I made some progress

i found 2 processes running on boot up

```

/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
wpa_sypplicant -ieth1 -Dwext -c/etc/wpa_supplicant.conf -B

```

I killed these and tried again voila wpa_supplicant works.

Any idea what is going on?

---

### Post by ittiam on 2009-01-30
I found /sbin/NetworkManager running during startup. Well I removed it using update-rc.d and now the wpa_supplicant works at startup.

I was thinking that pppoeconf made the NetworkManager come up during startup and when I disabled wired and enabled wireless connection, even the Network manager was trying to set up wireless and wpa_supplicant was also trying to set up wireless and that created the problem.

The NetworkManager was spawning a wpa_supplicant process and apart from that I had my own wpa_supplicant process at startup. That explains two processes as well.

---

