---
title: "Wireless never connects Edimax/10.04 LTS/PC"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by p0is0n on 2010-06-01
Hi,
I am trying to get my wireless networking up and running.
The network list is shown from the network manager, I select my router and the strength bars (icon) flashes up and down signalling that it is connecting, then after a while it asks me again for my details (password and security type (triple checked btw)). Again I click connect and then again it asks me for my details (just a circle or events click connect, wait, box pops up, click connect etc...)

I am running Ubuntu 10.04 LTS 64-bit with an Edimak RaLink wireless card.
The disk that comes with the wireless card has a linux driver for it (however I have no idea how to install it, or if I even need to)

As outlined in the HOWTO post a wireless issue thread the information is below.
**lspci -v | less**
```
0c:01.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
        Subsystem: Edimax Computer Co. Device 7727
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta
```**iwconfig**
```
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:22:69:34:0E:2A   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-60 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**lsmod**
```
rt2860sta             542482  1 
```**dmesg | grep rt2860**
```
[    8.685571] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[    8.687912] rt2860 0000:0c:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
```[B]
lshw -C network[/B]
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:95:cb:f2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:56 ioport:e800(size=256) memory:fbcff000-fbcfffff memory:f2ef0000-f2efffff(prefetchable) memory:fbcc0000-fbcdffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 1
       bus info: pci@0000:0c:01.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:49:54:fd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:fbef0000-fbefffff
```**iwlist scan**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:22:69:34:0E:2A
                    Protocol:802.11b/g/n
                    ESSID:"BTHomeHub2-PS8Z"
                    Mode:Managed
                    Channel:1
                    Quality:81/100  Signal level:-58 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:8B:5D:81:93:4A
                    Protocol:802.11b/g/n
                    ESSID:"BTHomeHub2-376P"
                    Mode:Managed
                    Channel:6
                    Quality:34/100  Signal level:-76 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```[B]
lsb_release -d[/B]
```
Description:    Ubuntu 10.04 LTS
```**uname -mr**
```
2.6.32-22-generic x86_64
```**sudo /etc/init.d/networking restart**
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

Any help on this would be much appreciated.
Also I am still fairly new to linux so explanations would be invaluable.
Thanks!

---

### Post by p0is0n on 2010-06-03
Still not sure how to proceed with this wireless card.

The wireless shows the networks, I can select my network and pass it the login details but it just won't connect :confused:

---

### Post by p0is0n on 2010-06-11
Does anyone have any idea what the problem is here.

My wired connection to the BT HomeHub router works just fine, but I can't keep the cable in there forever (the other computer needs it).
The router is set to use WPA & WPA2 as I indicate in my wireless authentication box.

The wireless networks available are displayed, I select mine, then it starts trying to connect (indicated by the wireless icon) then it comes up with a box saying authentication required.

The only security option is WPA &WPA2 Personal so I select that and enter the password and click connect.

Then it goes back to connecting (as indicated by the wireless icon).

Then it comes up with the authentication required box again, check the details - all is set, click connect.

And then a third time.

Then finally a little black semi transparent box comes up in the top-right corner of the screen saying wireless disconnected.


I don't have any idea what the actual problem is here. All I know is that my wireless will not connect.

Any help would be appreciated.
Thanks.

---

### Post by maxxjr on 2010-08-01
I have the same issue.  Did you ever get this resolved?

---

### Post by p0is0n on 2010-08-01
> **maxxjr said:**
> I have the same issue.  Did you ever get this resolved?

No, sorry, still using my wired connection.
Kinda gave up with having no idea how to fix it and getting no replies lol.

---

### Post by midea on 2010-08-04
Hi,

I have also card with the same chipset. I use the following configuration for wpa_supplicant:

ctrl_interface=/var/run/wpa_supplicant GROUP=netdev
ap_scan=2
fast_reauth=1
eapol_version=1
network={
    ssid="MyNetworksEssid"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP
    group=TKIP
    #psk="Your passphrase in can go here in plaintext, which should work too."
    psk=01234567..89abcdef ## << can be generated using wpa_passphrase
}

And it's working. 

Regards,
Marcin

---

### Post by p0is0n on 2010-08-04
> **midea said:**
> Hi,

I have also card with the same chipset. I use the following configuration for wpa_supplicant:

ctrl_interface=/var/run/wpa_supplicant GROUP=netdev
ap_scan=2
fast_reauth=1
eapol_version=1
network={
    ssid="MyNetworksEssid"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP
    group=TKIP
    #psk="Your passphrase in can go here in plaintext, which should work too."
    psk=01234567..89abcdef ## << can be generated using wpa_passphrase
}

And it's working. 

Regards,
Marcin

Hi,
Would you please be able to explain the steps taken to configure the card.
I have tried reading through this post :
[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)
to get things running with the details you have listed with no success.

In /etc/wpa_supplicant.conf I have :
ctrl_interface=/var/run/wpa_supplicant GROUP=netdev
ap_scan=2
fast_reauth=1
eapol_version=1

network={
    ssid="BTHomeHub2-PS8Z"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP
    group=TKIP
    psk=3ebb804caf442424b957205011404c238e32649098ab552005ae4abfc45f7273
}

In /etc/network/interfaces I have :
auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.15
netmask 255.255.255.0
wireless-essid BTHomeHub2-PS8Z
gateway 192.168.1.254
pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

The wireless connected a couple of times for a second or so before disconnecting again :-S

---

### Post by Charly85551 on 2010-08-04
Hi,
just looked at the last contribution. That is clearly a WPA1 connection using TKIP as the protocol. If this is working with you guys then it is indicating that your router/access point is not set up/working for WPA2 but for working under WPA1:p.
cheers - charly85551

---

### Post by p0is0n on 2010-08-04
Mine isn't working, maybe due to a setting or something somewhere.

My wireless router settings are limited :(
The encryption is set as:
Use WPA & WPA2
And uses a WPA-PSK Encryption Key.

As far as setting up networks/wireless cards on linux goes my knowledge is non existent.
I have no idea how to get it working and am just trying things posted that are probably not doing anything useful for me lol.

I created those files, so the information in them may be completely wrong.

---

