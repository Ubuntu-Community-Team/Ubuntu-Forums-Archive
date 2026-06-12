---
title: "Broadcom BCM4318 suddenly stopped working with WPA"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2009-05-10
I have a Dell running 8.04 LTS server that has been updated regularly with a BCM4318 wireless card that has worked flawlessly for almost over a year.  Recently, I did a reboot after I purged out bind9 (don't know if that affects anything) but can not get the wireless card to work with WPA Personal correctly again.

I am able to connect to my router with an unencrypted connection using the following commands

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid “matthewboh”
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

Here are the results from the machine after a reboot

Results from lspci
```
05:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

Results from ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:18:39:15:1c:11  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Results from iwconfig
```

wlan0     Link encap:Ethernet  HWaddr 00:18:39:15:1c:11  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Results from lsmod | grep -e b43 -e wlan0
```

b43                   114976  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    32132  1 b43
```

Results from dmesg | grep -e b43 -e wlan0
```
[   27.001373] b43-phy0: Broadcom 4318 WLAN found
[   28.474942] input: b43-phy0 as /devices/virtual/input/input6
[   30.166888] Registered led device: b43-phy0:tx
[   30.166912] Registered led device: b43-phy0:rx
[   30.166933] Registered led device: b43-phy0:radio
[   31.870525] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Results from sudo lshw -C Network
```
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:05:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=66 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:39:15:1c:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11g
```

Results from iwlist scan - Cell 02 is mine
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:3A:8B:10:8E
                    ESSID:"08FX03006780"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/100  Signal level=-80 dBm  Noise level=-72 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000177f908d275
          Cell 02 - Address: 00:0C:41:D0:46:A0
                    ESSID:"matthewboh"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level=-75 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000000a766c012
```

Results from lsb_release -d
```
Description:	Ubuntu 8.04.2
```

Results from uname -mr
```
2.6.24-16-server i686
```

Results from sudo /etc/init.d/networking restart
```
* Reconfiguring network interfaces...                 [OK]

```

If I try to set any of the WPA values like sudo iwpriv wlan0 set AuthMode=WPAPSK, it says ```
wlan0     No private ioctls.
```

Any help would be greatly appreciated.  I hate to have to reinstall

---

### Post by matthewboh on 2009-05-11
Ok - I'm able to now connect with the following:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf &
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

and my /etc/wpa_supplicant.conf contains

```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="matthewboh"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="---my supersecret password---"
        pairwise=TKIP
        group=TKIP
}
```

but I read that wpa_supplicant is getting phased out and the powers that
be want you to use wext and to add in your information to
your /etc/network/interfaces file 

So that looks like

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo wlan0
iface lo inet loopback

# The primary network interface
iface wlan0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1
        wpa-driver wext
        wpa-ssid matthewboh
        wpa-ap-scan 2
        wpa-proto WPA
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk
c43ae013621f4aa1db2d1127664349f425a2852c352c2c1d6913bfb056736b8d

```

and when I reboot - nothing still.  Any ideas where I should be looking?

---

### Post by matthewboh on 2009-05-12
I had to completely remove wpasupplicant and then followed [this set of instructions]("http://ubuntuforums.org/showthread.php?t=571188&highlight=hardy+server+wireless+wpa"), repopulate the /etc/resolv.conf with the dns servers from my isp because I wanted a static ip address.  Is there a way to get that information from my router?

---

