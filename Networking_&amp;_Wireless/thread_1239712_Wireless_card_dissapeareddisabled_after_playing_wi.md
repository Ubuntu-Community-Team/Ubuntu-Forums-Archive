---
title: "Wireless card dissapeared/disabled after playing with Wifi Radar"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by earthmeLon on 2009-08-13
I was messing around on my laptop with Ubuntu and opened up a program that I thought was to see nearby routers (Wifi Radar).  When I opened it up, I only saw the router I was connected to, so I disconnected to see if I could see more.  This was the last time my laptop was connected to my router wirelessly.

I was not able to see/connect to my router with Wifi Radar, so I restarted the laptop because sudo /etc/init.d/networking restart did not solve my problem.

Upon bootup, I still had no connectivity.  I looked at my /etc/network/interfaces file and noticed it changed from something like:

```

auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid "SSID HERe"
        wpa-psk "passkeypasskeypasskeypasskeypasskeypasskey"

``` 
to
```

iface wlan0 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant.conf

```


I tried looking up wpa_supplicant.conf and editing that file to reflect my network, but I was still unable to connect.  I then reverted it back to the way I originally had it (as shown in the first code block)

On bootup, my computer hangs at Initializing network connections (not sure if that's the exact string) but will pass after 3 minutes or so of leaving it alone.


```
$sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:1f:2a:68
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:34:87:0c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.5-1 ip=10.1.2.75 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s


$sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device

```


If anybody could help me enable my wireless card again, I'd very much appreciate it.

Thanks

---

### Post by kerry_s on 2009-08-13
that's weird wifi-radar doesn't change things, it has its own /etc/wifi-radar.conf, i use wifi-radar on mine.

the new network manager won't work if theres entries in /etc/network/interfaces, try removing or commenting out the lines.

```
auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid "SSID HERe"
        wpa-psk "passkeypasskeypasskeypasskeypasskeypasskey"
```

---

### Post by earthmeLon on 2009-08-13
> **kerry_s said:**
> that's weird wifi-radar doesn't change things, it has its own /etc/wifi-radar.conf, i use wifi-radar on mine.

the new network manager won't work if theres entries in /etc/network/interfaces, try removing or commenting out the lines.

```
auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid "SSID HERe"
        wpa-psk "passkeypasskeypasskeypasskeypasskeypasskey"
```

I am not using NetworkManager to make connections.  I'd prefer to list them in /etc/network/interfaces because it seemed to be the easiest way to have two nics on two different subnets and have it work properly.

```

eth0 > 10.1.1.X
wlan0 > 10.1.2.X

```

Also, I think the problem lies elsewhere because the NIC won't even come up.  It's "disabled" but I don't know what that really means and how to enable it

---

### Post by kerry_s on 2009-08-13
then its got to be your configuration, can you post your /etc/network/interfaces & anything else you modified.

---

### Post by earthmeLon on 2009-08-14
I don't want to sound rude, but I posted my configuration in the original post.  I don't see how it's the configuration, though, since the card is disabled.  If I try to UP the card, I get an error saying the card doesnt exist.  The /etc/network/interfaces file doesnt come into play yet, as far as I can tell.

---

### Post by kerry_s on 2009-08-14
> **earthmeLon said:**
> I don't want to sound rude, but I posted my configuration in the original post.  I don't see how it's the configuration, though, since the card is disabled.  If I try to UP the card, I get an error saying the card doesnt exist.  The /etc/network/interfaces file doesnt come into play yet, as far as I can tell.

oh okay, so you already know whats wrong?
i'd like to see the whole file not just parts of it, the layout can be important as well, how you put it in the file.
for example, if you put your wireless setting before your ethernet, your wireless will be used first as the main connection.

i tell you what i'll show you mine, i don't use the ethernet so mines commented out.

---

### Post by earthmeLon on 2009-08-14
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 10.1.2.75
     netmask 255.255.0.0
     gateway 10.1.2.1

auto wlan0
iface wlan0 inet dhcp
        wpa-driver wext
        wpa-ssid "SSID NAME"
        wpa-psk "passkeypasskeypasskeypasskeypasskeypasskeypasskey"
```


Edit:
```

$ tail -f /var/log/messages
Aug 14 17:15:15 Sleipnir kernel: [90188.299892] iwl3945: Radio disabled by HW RF Kill switch

```

Hmmmm.  I have a switch on the front of my laptop to turn on/off my card.  It *IS* set to ON.

Edit2:
I just updated my kernal earlier that day with apt-get.  Wireless did not die immediately, but maybe that has something to do with it.  I really have no clue

---

### Post by earthmeLon on 2009-08-14
SOLUTION:

Somehow the switch on the front of my laptop is opposite of what it says.  I feel really dumb right now, but after putting it in the OFF position and doing **$ sudo ifconfig wlan0 up && sudo /etc/init.d/networking restart**, my network card is now activated and successfully connected to the router.

---

### Post by kerry_s on 2009-08-14
thats great, might want to file a bug on that.

---

