---
title: "Lucid Lynx killed the Intel PRO/Wireless 3945ABG on my Panasonic Toughbook"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by skief on 2010-12-09
I used 8.04 Hardy Heron happily for a long time, and my wireless worked fine, but after upgrading to 10.04 Lucid Lynx my wireless no longer works.

I began by trying to set up my wireless connection with NetworkManager. Nothing would work, so I finally followed someone's advice and uninstalled NetworkManager, hoping instead to configure manually.

The problem is: During manual configuration, I cannot set the WPA key.

My wireless card appears to be eth1:

```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:a3:32:91
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:26 memory:d0000000-d0000fff

```

My /etc/network/interfaces is as follows:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth2 inet dhcp
auto eth2

```

Immediately after startup, we have:

```

$ sudo iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
pan0      no wireless extensions.

```

I then set the essid (and yes, I am writing my actual essid in place of '<my_essid>' :P ):

```

$ sudo iwconfig eth1 essid <my_essid>
$ sudo iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"<my_essid>"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
pan0      no wireless extensions.


```

which works fine. However, I cannot set the key:

```

$ sudo iwconfig eth1 key s:<my_key>
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.

```

Can anybody tell me what I'm doing wrong here?
(Note: I am indeed writing my plaintext ASCII key after the 's:'.)


Now, I have also tried another /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <my_essid>

#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth2 inet dhcp
auto eth2

```

This one was produced by NetworkManager, before I uninstalled it.
The strange thing that happens with this one is that immediately
after startup we get the somewhat promising output:

```

$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"<my_essid>"  
          Mode:Managed  Frequency:2.412 GHz  Access Point:
          01:23:45:67:89:AB   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

However, if we re-execute this command a few seconds later:

```

$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point:
          Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

```

we have lost a lot! What on Earth is going on here?

In any case, even with this (improved?) /etc/network/interfaces file, I still get the very same:
```

$ sudo iwconfig eth1 key s:<my_key>
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.

```

Does anybody know what I'm doing wrong?

Thank you very much in advance for any advice you can provide.

---

### Post by chili555 on 2010-12-09
> sudo iwconfig eth1 key s:<my_key>This is appropriate for WEP; you are using WPA. Try this:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-ssid <my_essid>
wpa-psk <my_key>
```Restart networking and you should see the DHCP stanza and see it connect.

---

### Post by skief on 2010-12-10
Problem solved!!! Thanks a million for this fast and effective response! :D

---

