---
title: "dhclient can't get ip in &quot;recovery mode&quot; for wireless"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2008-12-14
On occasion, it is necessary to start in recovery mode in Ubuntu.

Using wireless ralink device ra0

Once I bring up the interface, "sudo dhclient" gives 5 or 6 lines lof "listening to port XX" then "found no persistent leases in database" occurs.

If I boot all the way into the desktop, Knetworkmanager has NO problems connecting... so I need to know what might be reconfigured/reset or how to do this via command line so that I can get my wireless to be assigned an IP address.  If I hard wire to the router, eth0 has no issue getting an IP.

If I drop to command line from the desktop, it works fine.

---

### Post by iponeverything on 2008-12-14
in recovery mode if the access point is not encrypted you should just able to do:

iwconfig <netdev> essid <youressid>
dhclient <netdev>

If it is encrypted you can still do it from the cli but it slightly more involved. Remember that you have to undo the below, for network manager to pick up the interface again.

```
nano /etc/network/interfaces

```
add:

```
iface wlan0_rename inet dhcp
  wpa-conf /etc/wpa_supplicant.conf

```

for my /etc/wpa_supplicant.conf

```
# home network; allow all valid ciphers

ctrl_interface=/var/run/wpa_supplicant

network={
     ssid="KabulWobble"
     proto=WPA
     group=TKIP
     scan_ssid=1
     key_mgmt=WPA-PSK
     psk="Close enough to get this signal and not get shot, congrats"
}

```

---

### Post by maestrobwh1 on 2008-12-14
That is what is odd... it is not encrypted, and I have been using ubuntu since dapper.

dhclient is just "stuck" for some odd reason.  I do the 

ifconfig ra0 inet up
iwconfig ra0 linksys
dhclient ra0 

**And it just listens to ports, times out, then sleeps**

In /var/lib/dhclient3/dhclient.leases

the only persistent file is for eth0

---

