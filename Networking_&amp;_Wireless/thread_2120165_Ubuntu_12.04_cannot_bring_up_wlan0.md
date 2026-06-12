---
title: "Ubuntu 12.04 cannot bring up wlan0"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by quan1992 on 2013-02-25
When I run command "sudo ifconfig wlan0 up", this shows up:
SIOCSIFFLAGS: Device or resource busy

This is what in /etc/network/interfaces:

auto lo
iface lo inet loopback
-----------------------------------------------------------------------------------------------
These are some output related to wlan0:

adrian@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.
wmx0      Interface doesn't support scanning.
wlan0     Failed to read scan data : Network is down
eth0      Interface doesn't support scanning.

adrian@ubuntu:~$ sudo lshw -C network
[sudo] password for adrian: 
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:dc:ad:70
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-3 ip=130.215.23.104 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:50 memory:f4a00000-f4a1ffff memory:f4a2b000-f4a2bfff ioport:6080(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 5e
       serial: 64:80:99:3a:83:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-29-generic-pae firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:52 memory:f4900000-f4901fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.3
       logical name: wmx0
       serial: 00:1d:e1:49:a9:1d
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

adrian@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: i2400m-usb:2-1.3:1.0: WiMAX
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

adrian@ubuntu:~$ dmesg | grep iwl
[    5.522710] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.522741] iwlwifi 0000:03:00.0: setting latency timer to 64
[    5.522783] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    5.522785] iwlwifi 0000:03:00.0: pci_resource_base = f8540000
[    5.522787] iwlwifi 0000:03:00.0: HW Revision ID = 0x5E
[    5.523266] iwlwifi 0000:03:00.0: irq 53 for MSI/MSI-X
[    5.523399] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[    5.523530] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    5.534106] iwlwifi 0000:03:00.0: device EEPROM VER=0x540, CALIB=0x6
[    5.534109] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[    5.536337] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    5.585176] iwlwifi 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
[    5.587817] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.344593] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    6.344783] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    6.589745] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[    6.589923] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
-----------------------------------------------------------------------------------------------------------------------
Can anyone help me to solve this problem?
Thanks in advance!

---

### Post by chili555 on 2013-02-25
May we see:```
rfkill list all
```Thanks.

---

### Post by quan1992 on 2013-02-25
> **chili555 said:**
> May we see:```
rfkill list all
```Thanks.
Hi, chili555, I updated the question. Thanks for your reply!!!

---

### Post by chili555 on 2013-02-26
If it's not the wireless switch, we wonder why the wireless is disabled:> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: Centrino Advanced-N + WiMAX 6250
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0Network Manager is designed to disallow wireless if you have wired, and you do. Please temporarily detach the ethernet and then run and post:```
dmesg | grep iwl
```Thanks.

---

### Post by quan1992 on 2013-02-26
Hi, I updated the output of dmesg | grep iwl

I found that I can connect with infrastructure, but I cannot connect with ad-hoc wireless.

---

### Post by chili555 on 2013-02-27
> I found that I can connect with infrastructure, but I cannot connect with ad-hoc wireless.'Infrastructure' is for computer-to-router or other access point. 'Ad hoc' is for computer-to-computer. Isn't Infrastructure what you want? Aren't you trying to connect to a router and through it, to the internet?

---

### Post by quan1992 on 2013-02-27
> **chili555 said:**
> 'Infrastructure' is for computer-to-router or other access point. 'Ad hoc' is for computer-to-computer. Isn't Infrastructure what you want? Aren't you trying to connect to a router and through it, to the internet?

For some reason, my single board computer can only create ad-hoc wirelss right now. So I want my laptop to connect to this ad-hoc network. Does driver of Ubuntu12.04 has the ability to connect to ad-hoc network? My friends computer running on Ubuntu11.04 can connect to it.

---

### Post by chili555 on 2013-02-27
> Does driver of Ubuntu12.04 has the ability to connect to ad-hoc network? Usually, yes. Edit connections in Network Manager and select Ad Hoc. You'll need to specify the BSSID of the station you are connecting to.

---

### Post by quan1992 on 2013-02-27
> **chili555 said:**
> Usually, yes. Edit connections in Network Manager and select Ad Hoc. You'll need to specify the BSSID of the station you are connecting to.

Is BSSID the MAC address of the single board computer showed by "iwconfig"? I tried to select Ad Hoc in network connections and type the MAC address of wlan1 of single board computer. Unfortunately, it still doesn't work. 

I noticed that before I try to connect to ad-hoc created by single board computer, I can see wlan0 by typing "ifconfig". But after I try to connect to ad-hoc(doesn't succeed), wlan0 simply disappear in output of "ifconfig".

Do you know why that happened?

---

### Post by chili555 on 2013-02-27
> Is BSSID the MAC address of the single board computer showed by "iwconfig"? BSSID is the station name. If, from your laptop, you scan:```
sudo iwlist wlan0 scan
```Do you see the single-board advertising its network?> Cell 02 - Address: 8x:1B:5E:42:75:xx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    BSSID:"[COLOR="Red"]rweathers[/COLOR]"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad Hoc
In this example, the BSSID you need to fill in is rweathers.

---

### Post by quan1992 on 2013-02-27
> **chili555 said:**
> BSSID is the station name. If, from your laptop, you scan:```
sudo iwlist wlan0 scan
```Do you see the single-board advertising its network?In this example, the BSSID you need to fill in is rweathers.

This is what I got:

Cell 01 - Address: 02:22:62:C8:4A:C8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:off
                    ESSID:"murover"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000000018b294a8
                    Extra: Last beacon: 2852ms ago
                    IE: Unknown: 00076D75726F766572
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

There is no BSSID, only ESSID(SSID). I tried the address 02:22:62:C8:4A:C8. It doesn't work.

---

### Post by chili555 on 2013-02-27
I'm sorry if I didn't make myself clear. It is not the MAC address you want; it is the name. Did you try *murover*?

---

### Post by quan1992 on 2013-02-28
> **chili555 said:**
> I'm sorry if I didn't make myself clear. It is not the MAC address you want; it is the name. Did you try *murover*?

I tried the murover, however I even cannot save the edit because it seems "murover" doesn't fit the format of BSSID.
Following is what I read from wikipedia
"[COLOR=#000000][FONT=sans-serif]For a BSS operating in infrastructure mode, the BSSID is the [/FONT][/COLOR][MAC address]("http://en.wikipedia.org/wiki/MAC_address")[COLOR=#000000][FONT=sans-serif] of the [/FONT][/COLOR][wireless access point]("http://en.wikipedia.org/wiki/Wireless_access_point")[COLOR=#000000][FONT=sans-serif] (WAP) generated by combining the Organization Unique Identifier (the manufacturer's identity), 24 bits, and the manufacturer's assigned 24 bit identifier for the radio chipset in the WAP[/FONT][/COLOR]"

---

### Post by chili555 on 2013-03-01
You are perfectly correct and I am wrong. I made a regrettable mistake and I apologize. What could I have been thinking or drinking?

So does putting the MAC address in the BSSID space, the SSID of murover and selecting band B and G allow you to connect? Are there any clues here?```
cat /var/log/syslog | grep etwork | tail -n20
```We will likely not see significant results unless the ethernet is detached.

---

### Post by quan1992 on 2013-03-02
> **chili555 said:**
> You are perfectly correct and I am wrong. I made a regrettable mistake and I apologize. What could I have been thinking or drinking?

So does putting the MAC address in the BSSID space, the SSID of murover and selecting band B and G allow you to connect? Are there any clues here?```
cat /var/log/syslog | grep etwork | tail -n20
```We will likely not see significant results unless the ethernet is detached.

[IMG]/home/adrian/Pictures/Screenshot from 2013-03-02 16:03:21.png[/IMG]

---

### Post by quan1992 on 2013-03-02
> **chili555 said:**
> You are perfectly correct and I am wrong. I made a regrettable mistake and I apologize. What could I have been thinking or drinking?

So does putting the MAC address in the BSSID space, the SSID of murover and selecting band B and G allow you to connect? Are there any clues here?```
cat /var/log/syslog | grep etwork | tail -n20
```We will likely not see significant results unless the ethernet is detached.

Lol, that's fine. I did put the MAC address in BSSID space, SSID of "murover", band B/G and I manually set IP address to 192.168.1.30 because gumstix Overo don't have DHCP. BUt it still doesn't work.

adrian@ubuntu:~$ cat /var/log/syslog | grep etwork | tail -n20
Mar  2 16:12:14 ubuntu NetworkManager[869]: <warn> Activation (wlan0/wireless): Ad-Hoc network creation took too long, failing activation.
Mar  2 16:12:14 ubuntu NetworkManager[869]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Mar  2 16:12:14 ubuntu NetworkManager[869]: <warn> Activation (wlan0) failed for access point (murover)
Mar  2 16:12:14 ubuntu NetworkManager[869]: <warn> Activation (wlan0) failed.
Mar  2 16:12:14 ubuntu NetworkManager[869]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  2 16:12:14 ubuntu NetworkManager[869]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  2 16:12:14 ubuntu NetworkManager[869]: <info> (wlan0): supplicant interface state: associating -> disconnected
Mar  2 16:12:14 ubuntu NetworkManager[869]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Mar  2 16:12:51 ubuntu NetworkManager[869]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Mar  2 16:12:51 ubuntu NetworkManager[869]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  2 16:12:51 ubuntu NetworkManager[869]: <info> WiFi hardware radio set disabled
Mar  2 16:12:51 ubuntu NetworkManager[869]: <info> WiFi now disabled by radio killswitch
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> (wlan0): bringing up device.
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> WiFi hardware radio set enabled
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> WiFi now enabled by radio killswitch
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> (wlan0): bringing up device.
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> (wlan0): supplicant interface state: starting -> ready
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar  2 16:12:54 ubuntu NetworkManager[869]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar  2 16:12:54 ubuntu NetworkManager[869]: <warn> Trying to remove a non-existant call id.

---

### Post by chili555 on 2013-03-02
> and I manually set IP address to 192.168.1.30 because gumstix Overo don't have DHCPI'm not sure that's correct. Usually ad-hoc networks are in the 10.42.43.xx range in Ubuntu. I'm not at all sure about gumstix, but I suspect it's 10.something.

Do you ssh into the gumstix? What does it say its IP is?```
ifconfig
```

---

