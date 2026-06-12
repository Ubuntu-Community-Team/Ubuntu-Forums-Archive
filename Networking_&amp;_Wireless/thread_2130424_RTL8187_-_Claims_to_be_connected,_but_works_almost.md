---
title: "RTL8187 - Claims to be connected, but works almost never"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by prentiz on 2013-03-29
I may be doomed here.  Have been trying for three days to make my USB Wifi adaptor work on my Myth TV box with little success.  I've tried various suggestions, with little success.  Frankly, I don't really know what I'm doing and may have made things worse, for all I know.  

The adaptor looks to be working properly, can search for wifi signals properly and claims to be connected - but it almost never sends any information.  My Windows laptop works well with the same usb device plugged in.

If anyone can point me in the right direction, it would be very much appreciated!

**lsusb** 
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
**iwconfig wlan0**
wlan0     IEEE 802.11bg  ESSID:"Bebox563156"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:62:BC:73   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1767  Invalid misc:102   Missed beacon:0

**lsmod | grep "rtl8187"**
rtl8187                56398  0 
mac80211              475546  1 rtl8187
cfg80211              181041  2 rtl8187,mac80211
eeprom_93cx6           13169  1 rtl8187



**dmesg | grep "rtl8187**" (I've stuck the full version here [http://pastebin.com/c5zSBjrg](http://pastebin.com/c5zSBjrg)
[   17.612915] rtl8187: Customer ID is 0x00
[   17.612985] Registered led device: rtl8187-phy0::radio
[   17.613390] Registered led device: rtl8187-phy0::tx
[   17.613708] Registered led device: rtl8187-phy0::rx
[   17.614264] rtl8187: wireless switch is on
[   17.614710] usbcore: registered new interface driver rtl8187



**sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:01:29:a6:58:28
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.98 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:41 memory:fddfc000-fddfffff ioport:de00(size=256) memory:fda00000-fda1ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:e0:4c:83:38:a2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-26-generic firmware=N/A ip=192.168.1.128 link=yes multicast=yes wireless=IEEE 802.11bg
(check 'iwlist --help').


**iwlist scan**
wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:62:BC:73
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Bebox563156"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001184bc4e2
                    Extra: Last beacon: 22384ms ago
                    IE: Unknown: 000B4265626F78353633313536
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180203F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


I'm using Ubuntu 12.04.2 LTS and 3.5.0-26-generic i686

**Sudo /etc/init.d/networking restart**
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by Kazi Waseef on 2013-03-29
Copy the contents of what is written after typing:
```

gedit '/etc/network/interfaces'

```

---

### Post by prentiz on 2013-03-29
> **Kazi Waseef said:**
> Copy the contents of what is written after typing:
```

gedit '/etc/network/interfaces'

```


Hi Kazi!

It says:

```

auto lo
iface lo inet loopback

```

---

### Post by Kazi Waseef on 2013-03-29
Alright, try this first,

Go to network manager dropdown on the top left corner and open Edit Connections. Then go to the wireless tab and click on the wireless network that is used for connecting to wlan0.

In it, add a letter "x" (without the quotations) to the end of the SSID value. This is a known bug for your wlan driver.

then type in terminal:
```

sudo service network-manager restart

```

Go to
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) for more details. (Can get technical)

---

### Post by prentiz on 2013-03-29
> **Kazi Waseef said:**
> Alright, try this first,

Go to network manager dropdown on the top left corner and open Edit Connections. Then go to the wireless tab and click on the wireless network that is used for connecting to wlan0.

In it, add a letter "x" (without the quotations) to the end of the SSID value. This is a known bug for your wlan driver.

then type in terminal:
```

sudo service network-manager restart

```

Go to
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) for more details. (Can get technical)

Thanks Kazi - I've tried that, but I'm a bit confused.  If I do as you say, once I reset NM, it won't connect to the router with the saved profile, because it has a different SSID.  If I set up a new profile (put the WEP key in again etc), it connects, but as before it won't work - can't ping anything, for example.  Thanks for your help so far!

---

### Post by Kazi Waseef on 2013-03-30
Is your device shown on the network manager dropdown. Does it say something like device not managed?

In that case type
```

gksudo gedit '/etc/NetworkManager/NetworkManager.conf'

```

There you will find:
managed=false

change that to:
managed=true

then restart network manager...

---

### Post by prentiz on 2013-03-30
> **Kazi Waseef said:**
> Is your device shown on the network manager dropdown. Does it say something like device not managed?

In that case type
```

gksudo gedit '/etc/NetworkManager/NetworkManager.conf'

```

There you will find:
managed=false

change that to:
managed=true

then restart network manager...

Thanks Kazi - tried as you suggested, but still has no effect.  Tried putting the X into SSID as well, but this just means it doesn't know which access point to connect to.  Any help much appreciated!

---

### Post by Kazi Waseef on 2013-03-30
Please give some more details as to what the dropdown tab for network manager shows for your device.

Meanwhile try a manual un-encrypted connection

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid xxxxxx
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

---

### Post by Kazi Waseef on 2013-03-30
You can also try this

Copy '/etc/network/interfaces' to the desktop as backup

```

cp '/etc/network/interfaces' '/home/kaziwaseef/Desktop/'

```

Then open '/etc/network/interfaces' as super user

```

gksudo gedit '/etc/network/interfaces'

```

Replace everything with:
```

auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf

```
Close it.

Now open '/etc/wpa_supplicant.conf'
```

gksudo gedit '/etc/wpa_supplicant.conf'

```
Replace anything (if there is anything) with:
```

network={
        ssid="ADD-YOUR-SSID-HERE"
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        psk="ADD-YOUR-WPA-PASSWORD-HERE"
}

```
Restart Network.

---

### Post by prentiz on 2013-04-02
Kazi - thanks very much for your help so far.  I've tried both of those suggestions with no improvement.  In the second case, I had to re-enter WPA passwords etc, it did eventually reconnect, but still with no ability to ping etc.  Any more suggestions from you, or anyone else much appreciated!

---

### Post by Kazi Waseef on 2013-04-06
Hmmm.... I'm dry.... Sorry.

---

### Post by prentiz on 2013-04-06
> **Kazi Waseef said:**
> Hmmm.... I'm dry.... Sorry.

Thanks for your help Kazi - anyone else got any ideas?

---

