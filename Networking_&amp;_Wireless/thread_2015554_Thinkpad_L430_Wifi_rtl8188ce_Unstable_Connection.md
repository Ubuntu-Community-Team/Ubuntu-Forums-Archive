---
title: "Thinkpad L430: Wifi rtl8188ce Unstable Connection"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by simon002 on 2012-07-03
Hi, I've been reading several threads on the forums and askubuntu about people having the same issue as me, which is unstable and slow wifi with the Realtek rtl8188ce wifi adapter. None of the threads have helped. 
I am new to Linux, so I can't tell if you in words what I've tried, but if you suggest a terminal command I may recognize it! I can tell you that I've tried the latest official Realtek driver, and it didn't change a thing.

The router I am connected to only supports g and b, not N.


Please let me know if you need more info than this, thanks:

**Laptop:**
```
Lenovo Thinkpad L430 L2N36MD
Ubuntu 12.04 LTS 64-bit
```

**Kernel/architecture (including 32 vs. 64 bit):** 
$ uname -mr
```
3.2.0-26-generic x86_64
```

**Wireless Brand, Model and Wireless Chipset:**
$ lspci | grep Network
```
06:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

**Interface:**
$ iwconfig wlan0
```
wlan0     IEEE 802.11bgn  ESSID:"Fullrate"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:E7:09:C5   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0

```

**Modules:**
$ lsmod | grep 8192
```
rtl8192ce             137448  0 
rtlwifi               118718  1 rtl8192ce
mac80211              506816  2 rtl8192ce,rtlwifi
```

**Kernel boot messages:**
$ dmesg | grep 8192
```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011f200000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    2.923992] rtl8192ce 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.924006] rtl8192ce 0000:06:00.0: setting latency timer to 64

```

**Network configuration:**
$ sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 7c:e9:d3:f3:b0:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-26-generic firmware=N/A ip=192.168.1.40 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:f1d00000-f1d03fff
```
  
**Scan for networks:**
$ iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:19:CB:E7:09:C5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"Fullrate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000014db49d1b6
                    Extra: Last beacon: 12368ms ago
                    IE: Unknown: 000846756C6C72617465
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
```

---

### Post by simon002 on 2012-07-06
Bump

---

### Post by wildmanne39 on 2012-07-06
Hi, please copy and paste all commands and do the following:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```

A new empty file will open, paste this one line into the file.

```
options rtl8192ce swenc=1
```

Proofread, save and close gedit.

Set your wireless settings in network manager to match the screenshots.
Reboot

If still having issues post the output of:
```
nm-tool
```
Thanks

---

### Post by simon002 on 2012-07-06
Hi wildmanne39, thank you for helping. 

I recall reading a post where you suggested the same, and I ended up trying wicd which didn't change my situation. Ultimately I made a fresh Ubuntu install to revert any changes. 

I have added the line to rtl8192ce.conf and the issue persists.

This is the output of nm-tool:

```
NetworkManager Tool

State: connected (global)

- Device: ttyACM0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:FF:17:1A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Fullrate] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        7C:E9:D3:F3:B0:E7

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Fullrate:       Infra, 00:19:CB:E7:09:C5, Freq 2437 MHz, Rate 54 Mb/s, Strength 63

  IPv4 Settings:
    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            cdc_ncm
  State:             unavailable
  Default:           no
  HW Address:        02:15:E0:EC:01:00

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

---

### Post by wildmanne39 on 2012-07-06
Hi, post the output of:
```
Cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```
Thanks

---

### Post by simon002 on 2012-07-06
Output:
```

minstrel_ht

```

---

### Post by wildmanne39 on 2012-07-06
Hi, post the contents of:
```
gksudo gedit /etc/modprobe.d/rtl8192ce.conf
```
output of:
```
dmesg | grep 819
```
what kind of router are you using is it real old?
Thanks

---

### Post by simon002 on 2012-07-06
Hi!

Contents of gksudo gedit /etc/modprobe.d/rtl8192ce.conf:
```
options rtl8192ce swenc=1
```

$ dmesg | grep 819:
```
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88011f200000 s83072 r8192 d23424 u262144
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u262144 alloc=1*2097152
[    1.208194] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.047890] rtl8192ce 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.047901] rtl8192ce 0000:06:00.0: setting latency timer to 64
[    3.198190] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    3.198193] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.198195] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    3.198198] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    3.246724] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[    3.698441] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   27.830410] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   31.153593] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
```

```
what kind of router are you using is it real old?
```
It is quite old :p Unfortunately it's the only one I have available. It's a Zyxel P-2602HW-D1A. 
Before I installed Ubuntu on this laptop, Windows 7 had no problems keeping a stable connection. Thanks.

---

### Post by wildmanne39 on 2012-07-06
Hi, post the output of:
```
sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e etork wlan | tail -n55
```

Also change your channel to 1 or 11 in the router.
Thanks

---

### Post by simon002 on 2012-07-06
Hey man, the command didn't work :confused: So I added -e in front of wlan and this is what came out :KS (working on the channel shift):

simon@sbl:~$ sudo cat /var/log/syslog | grep -e 819 -e firmware -e wpa -e etork -e wlan | tail -n55
```
Jul  6 21:13:28 sbl dhclient: receive_packet failed on wlan0: Network is down
Jul  6 21:13:28 sbl NetworkManager[865]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Jul  6 21:13:28 sbl NetworkManager[865]: <info> (wlan0): deactivating device (reason 'none') [0]
Jul  6 21:13:28 sbl wpa_supplicant[1133]: Failed to initiate AP scan.
Jul  6 21:13:28 sbl NetworkManager[865]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1612
Jul  6 21:13:28 sbl kernel: [  865.883437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  6 21:13:28 sbl NetworkManager[865]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jul  6 21:13:33 sbl NetworkManager[865]: <info> (wlan0): bringing up device.
Jul  6 21:13:33 sbl kernel: [  870.321762] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jul  6 21:13:33 sbl kernel: [  870.667396] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  6 21:13:33 sbl NetworkManager[865]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  6 21:13:33 sbl NetworkManager[865]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  6 21:13:33 sbl NetworkManager[865]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) starting connection 'Fullrate'
Jul  6 21:13:35 sbl NetworkManager[865]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  6 21:13:35 sbl NetworkManager[865]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0/wireless): connection 'Fullrate' requires no security.  No secrets needed.
Jul  6 21:13:35 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  6 21:13:35 sbl NetworkManager[865]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul  6 21:13:36 sbl wpa_supplicant[1133]: Trying to authenticate with 00:19:cb:e7:09:c5 (SSID='Fullrate' freq=2437 MHz)
Jul  6 21:13:36 sbl NetworkManager[865]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul  6 21:13:36 sbl wpa_supplicant[1133]: Trying to associate with 00:19:cb:e7:09:c5 (SSID='Fullrate' freq=2437 MHz)
Jul  6 21:13:36 sbl kernel: [  873.323913] wlan0: authenticate with 00:19:cb:e7:09:c5 (try 1)
Jul  6 21:13:36 sbl kernel: [  873.325420] wlan0: authenticated
Jul  6 21:13:36 sbl wpa_supplicant[1133]: Associated with 00:19:cb:e7:09:c5
Jul  6 21:13:36 sbl wpa_supplicant[1133]: CTRL-EVENT-CONNECTED - Connection to 00:19:cb:e7:09:c5 completed (auth) [id=0 id_str=]
Jul  6 21:13:36 sbl kernel: [  873.325622] wlan0: associate with 00:19:cb:e7:09:c5 (try 1)
Jul  6 21:13:36 sbl kernel: [  873.327692] wlan0: RX AssocResp from 00:19:cb:e7:09:c5 (capab=0x461 status=0 aid=2)
Jul  6 21:13:36 sbl kernel: [  873.327698] wlan0: associated
Jul  6 21:13:36 sbl kernel: [  873.328667] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  6 21:13:36 sbl NetworkManager[865]: <info> (wlan0): supplicant interface state: authenticating -> completed
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Fullrate'.
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul  6 21:13:36 sbl NetworkManager[865]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul  6 21:13:36 sbl NetworkManager[865]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul  6 21:13:36 sbl dhclient: Listening on LPF/wlan0/7c:e9:d3:f3:b0:e7
Jul  6 21:13:36 sbl dhclient: Sending on   LPF/wlan0/7c:e9:d3:f3:b0:e7
Jul  6 21:13:36 sbl dhclient: DHCPREQUEST of 192.168.1.37 on wlan0 to 255.255.255.255 port 67
Jul  6 21:13:36 sbl NetworkManager[865]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  6 21:13:36 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul  6 21:13:37 sbl NetworkManager[865]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jul  6 21:13:37 sbl NetworkManager[865]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul  6 21:13:37 sbl NetworkManager[865]: <info> Policy set 'Fullrate' (wlan0) as default for IPv4 routing and DNS.
Jul  6 21:13:37 sbl NetworkManager[865]: <info> Activation (wlan0) successful, device activated.
Jul  6 21:13:37 sbl NetworkManager[865]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  6 21:13:46 sbl kernel: [  883.540620] wlan0: no IPv6 routers present
```

---

### Post by simon002 on 2012-07-07
Hi again, I just ran the command again, straight after boot. Looks a bit cleaner, but the problem is still there.


```
Jul  7 10:25:35 sbl NetworkManager[933]: <info> wpa_supplicant started
Jul  7 10:25:35 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: starting -> ready
Jul  7 10:25:35 sbl NetworkManager[933]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul  7 10:25:35 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: ready -> inactive
Jul  7 10:25:35 sbl kernel: [    3.754694] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) starting connection 'Fullrate'
Jul  7 10:25:37 sbl NetworkManager[933]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul  7 10:25:37 sbl NetworkManager[933]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0/wireless): connection 'Fullrate' requires no security.  No secrets needed.
Jul  7 10:25:37 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul  7 10:25:37 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jul  7 10:25:38 sbl wpa_supplicant[1100]: Trying to authenticate with 00:19:cb:e7:09:c5 (SSID='Fullrate' freq=2437 MHz)
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul  7 10:25:38 sbl wpa_supplicant[1100]: Trying to associate with 00:19:cb:e7:09:c5 (SSID='Fullrate' freq=2437 MHz)
Jul  7 10:25:38 sbl kernel: [    6.701202] wlan0: authenticate with 00:19:cb:e7:09:c5 (try 1)
Jul  7 10:25:38 sbl kernel: [    6.702782] wlan0: authenticated
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul  7 10:25:38 sbl kernel: [    6.723063] wlan0: associate with 00:19:cb:e7:09:c5 (try 1)
Jul  7 10:25:38 sbl wpa_supplicant[1100]: Associated with 00:19:cb:e7:09:c5
Jul  7 10:25:38 sbl wpa_supplicant[1100]: CTRL-EVENT-CONNECTED - Connection to 00:19:cb:e7:09:c5 completed (auth) [id=0 id_str=]
Jul  7 10:25:38 sbl kernel: [    6.729084] wlan0: RX AssocResp from 00:19:cb:e7:09:c5 (capab=0x461 status=0 aid=1)
Jul  7 10:25:38 sbl kernel: [    6.729086] wlan0: associated
Jul  7 10:25:38 sbl kernel: [    6.729567] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): supplicant interface state: associating -> completed
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Fullrate'.
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul  7 10:25:38 sbl dhclient: Listening on LPF/wlan0/7c:e9:d3:f3:b0:e7
Jul  7 10:25:38 sbl dhclient: Sending on   LPF/wlan0/7c:e9:d3:f3:b0:e7
Jul  7 10:25:38 sbl dhclient: DHCPREQUEST of 192.168.1.37 on wlan0 to 255.255.255.255 port 67
Jul  7 10:25:38 sbl NetworkManager[933]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul  7 10:25:38 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul  7 10:25:38 sbl avahi-daemon[950]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.37.
Jul  7 10:25:38 sbl avahi-daemon[950]: New relevant interface wlan0.IPv4 for mDNS.
Jul  7 10:25:38 sbl avahi-daemon[950]: Registering new address record for 192.168.1.37 on wlan0.IPv4.
Jul  7 10:25:39 sbl avahi-daemon[950]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::7ee9:d3ff:fef3:b0e7.
Jul  7 10:25:39 sbl avahi-daemon[950]: New relevant interface wlan0.IPv6 for mDNS.
Jul  7 10:25:39 sbl avahi-daemon[950]: Registering new address record for fe80::7ee9:d3ff:fef3:b0e7 on wlan0.*.
Jul  7 10:25:39 sbl NetworkManager[933]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jul  7 10:25:39 sbl NetworkManager[933]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul  7 10:25:39 sbl NetworkManager[933]: <info> Policy set 'Fullrate' (wlan0) as default for IPv4 routing and DNS.
Jul  7 10:25:39 sbl NetworkManager[933]: <info> Activation (wlan0) successful, device activated.
Jul  7 10:25:39 sbl NetworkManager[933]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul  7 10:25:39 sbl kernel: [    7.981961] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input12
Jul  7 10:25:48 sbl kernel: [   16.755733] wlan0: no IPv6 routers present
```

---

### Post by simon002 on 2012-07-07
I just discovered that by pinging my router I can create a stable connection.

---

### Post by kurt18947 on 2012-07-07
> **simon002 said:**
> I just discovered that by pinging my router I can create a stable connection.

Good deal! :).  I found when using RealTek's driver that I had to blacklist the 'built-in' one on some distros.  I didn't have to blacklist on Ubuntu12.04, did have to blacklist on Mint Maya which is based on 12.04.  Some things are a mystery.

---

### Post by simon002 on 2012-07-07
Hi Kurt, this is a very annoying mystery :D 
I tried blacklisting earlier, but it didn't change anything. And that is weirdly a recurring result. Whatever I try, my situation doesn't change. Not for the better and not for the worse :confused:

Maybe wildmanne39 was onto something when he asked me if my router is really old, hehe.   

Still looking for a solution.

---

### Post by wildmanne39 on 2012-07-07
Hi, please post the output of:
```
ndiswrapper -l
```
just want to make sure it is not installed.
Thanks

---

### Post by simon002 on 2012-07-08
Hey, I think the only driver installed at the moment is the one which came with Ubuntu. 
Can you help me find out which driver is in use?

Output:
```
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
```

This is lsmod:

```
$ lsmod
Module                  Size  Used by
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
arc4                   12529  2 
thinkpad_acpi          81819  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
psmouse                87692  0 
cdc_wdm                17581  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
cdc_acm                26858  0 
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
cdc_ncm                17399  0 
usbnet                 26212  1 cdc_ncm
snd_hda_intel          33773  3 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41616  0 
cfg80211              205544  2 rtlwifi,mac80211
snd_timer              29990  2 snd_seq,snd_pcm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468737  3 
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,thinkpad_acpi,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_device,snd_pcm,snd_timer
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
wmi                    19256  0 
soundcore              15091  1 snd
nvram                  14413  1 thinkpad_acpi
tpm_tis                18804  0 
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0
```

---

### Post by simon002 on 2012-07-08
Pinging the router no longer works. It creates a more consistent connection, but I don't think the router likes it, because it stops responding after a while. I'm not getting disconnected but traffic is delayed.

Also as an aside my system froze earlier today. Not sure why.

---

### Post by wildmanne39 on 2012-07-08
Hi, while it is connected can you browse the internet?
Thanks

---

### Post by simon002 on 2012-07-09
Hi, yes, but it is mostly unresponsive, sometimes I am able to load a webpage.

---

### Post by wildmanne39 on 2012-07-09
Hi, please post the output of:
```

lspci -nnk | grep -iA2 net
iwconfig
rfkill list all

```
Thanks

---

### Post by simon002 on 2012-07-09
$ lspci -nnk | grep -iA2 net
```
06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce
--
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:21f7]
	Kernel driver in use: r8169
```

$ iwconfig
```
lo        no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Fullrate"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:E7:09:C5   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```


$ rfkill list all
```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

The laptop supports GSM WAN, but I don't use it.

---

### Post by wildmanne39 on 2012-07-09
Hi, go into your router settings and change 802.11bgn to 802.11bg.
Thanks

---

### Post by kurt18947 on 2012-07-09
While adjusting router settings, would it be worthwhile to check for new router firmware?  I've had that help with connection problems.

---

### Post by wildmanne39 on 2012-07-09
Hi, no I prefer he not do that at this time but it is his choice.
Thanks

---

### Post by simon002 on 2012-07-10
My router does not support n. It is setup to broadcast b or g. I set it to g only, but it didn't help.

Also changing channel to 1 or 11 didn't help.

Can I set the Ubuntu driver to only use g?

I will wait with firmware update :)

---

### Post by wildmanne39 on 2012-07-10
Hi, according to the information you posted you are having issues with wpa_supplicant which usually can be gotten around by using wicd now that you have set the parameter on the driver.

In your router do you see an option like the one in the screenshot? If not that is okay.

Please do [COLOR="Red"]in this order[/COLOR]:
```
sudo apt-get install wicd
```
Then:
```
sudo apt-get purge network-manager network-manager-gnome
```
I believe you have to set a static ip and for dhcp use dhclient for wicd to work unless it has changed in the latest release.
Thanks

---

### Post by szbab on 2012-07-17
Hello
Sorry for my English (translated with google)
Here is the latest realtek driver from the month of May to compile:

[http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ](http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ)

---

### Post by R. McC on 2012-07-19
> **szbab said:**
> Hello
Sorry for my English (translated with google)
Here is the latest realtek driver from the month of May to compile:

[http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ](http://ubuntuone.com/2BDt3O2YqZv8QDqQWoZshQ)
Tried these, but am still encountering the same frequent deauthentication errors as ever. The connection quality seems higher while it's up, but the frequency of disconnect is the same.

```

Jul 19 17:13:13 SilverSurfer kernel: [ 1104.650013] wlan0: deauthenticated from 00:46:9a:02:17:01 (Reason: 6)
Jul 19 17:13:13 SilverSurfer wpa_supplicant[997] CTRL-EVENT-DISCONNECTED bssid=00:46:9a:02:17:01 reason=6
```

If I set*ping google.com* going, I see this message approximately every 10 seconds or so. 

Network Manager or Wicd; I've encountered the same sorts of messages with both. Happens in 2/3 routers (the only router that works is the one *at* work; the wireless on the train and at home exhibit this problem), does not happen on another Lenovo ThinkPad Ubuntu 12.04 64-bit machine using an Intel chip.

Launchpad bug: [https://bugs.launchpad.net/bugs/902557](https://bugs.launchpad.net/bugs/902557)

Would really love it if someone knew how to fix this. :confused:

---

### Post by pingadam on 2012-07-25
Hi,

Unfortunately I have exactly the same problem with a Realtek RTL8188CE WiFi Card in my Lenovo ThinkPad X121e (with AMD E-350 APU), intermittant / poor connection (but apparently strong signal) in Ubuntu 12.04 LTS (64-bit). It works superbly in Windows 7.

So I consider the Realtek RTL8188CE incompatible with the latest versions of Linux (including Ubuntu 12.04), there seems little progress in the bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557")), so I see 2 available options:

1. Purchase another WiFi card that is compatible (and that's not easy for Lenovo Thinkpads, as the BIOS is locked and you can only install certain "whitelisted" cards, which are more expensive than standard mini-PCI-e WiFi cards).

2. Wipe Ubuntu and revert to Windows 7.

Looks like I'm going to have to choose Option 2! :(

Kind regards,

Adam.

---

### Post by R. McC on 2012-07-25
Can everyone experiencing issues with the wireless card check their syslogs for the reason 6 line I quoted a few posts back? I'd like to make sure that this is a common thread for everyone.

---

### Post by dboonz on 2012-08-24
Hi,

I am thinking about buying a thinkpad L430, but I don't want the network problems you're describing. Do you know which network card  you are using?  There are a few available if you buy the laptop. Especially: Do you know if it is the centrino wireless 2200, or something else?

regards,

Dirk Boonzajer

---

### Post by Fíona on 2012-08-31
I bought a toshiba c850 and was extremely disappointed to discover that it kept dropping wifi. I refused to accept that the problem could not be solved in spite of a lot of the threads I read about the problem. I downloaded the driver from Realtek (even though it seemed to be installed), compiled it (following instructions from the readme file or one of the ubuntu forum threads) and the problem seems to be over and out.
The toshiba has 
*-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter [10EC:8176]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:c6:3c:65:08:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wir

I had tried out a laptop in the shop with a livecd (not the toshiba but also with realtek wireless) and it looked like the wireless worked ok. I discovered that it connected ok but dropped after a periode of time. So you may think it's ok.

Good luck and don't despair

---

### Post by Ddamia on 2012-09-13
Similar problem here on new Lenovo Thinkpad x121e with 12.04. When I first installed 12.04 everything seemed to work perfectly fine for about a week-10 days, and then the wifi problems started. At first it only had difficulty connecting to a network, then networks started not showing up under the network icon, then it started dropping the network connection for no apparent reason. 

I downloaded, compiled and installed the rtl8188ce driver yesterday (as explained here: [http://ubuntuforums.org/showthread.php?t=1944493](http://ubuntuforums.org/showthread.php?t=1944493) ) and now connection is definitely more stable, networks show up under the network icon, but it still doesn't work properly. Occasionally it will drop the connection and then most of the time it's unable to reconnect. Sometimes it manages to reconnect after repeatedly asking for the password, but most times only a reboot will fix things, and even then connecting might be hugely problematic and require several reboots before it works.

Any and all help would be greatly appreciated!

---

### Post by Fíona on 2012-09-13
I also followed the instructions on the post mentioned by Ddamia and also this post,
[http://ubuntuforums.org/showthread.php?t=1930475](http://ubuntuforums.org/showthread.php?t=1930475) 

...with reference to the instruction regarding rtl8192ce.ko

I have had no problems since; I'm using linuxmint 13.

---

### Post by dboonz on 2012-09-13
@Ddamia:

It depends on your wireless network card. If you buy a lenovo, you can choose different options for the wireless network card. I chose the intel 2200 bgn network card, and it works flawlessly. So you could just try to change the network card - if you can still return it to the shop.

---

### Post by Ddamia on 2012-09-13
> **dboonz said:**
> @Ddamia:

It depends on your wireless network card. If you buy a lenovo, you can choose different options for the wireless network card. I chose the intel 2200 bgn network card, and it works flawlessly. So you could just try to change the network card - if you can still return it to the shop.

Um, no... I don't think I can get the same computer with a different network card from the shop I bought it from. All their Lenovos have realtek cards if I remember correctly.

---

### Post by Ddamia on 2012-09-15
Tentative bump! 
Anyone have any suggestions on how to make the wireless connection with rtl8188ce driver more stable?

As I said above, compiling and installing from the rtl site improved stability hugely, but it's still not working 100% reliably.

---

### Post by seshdroid on 2012-11-04
> **Ddamia said:**
> Similar problem here on new Lenovo Thinkpad x121e with 12.04....
I downloaded, compiled and installed the rtl8188ce driver yesterday (as explained here: [http://ubuntuforums.org/showthread.php?t=1944493](http://ubuntuforums.org/showthread.php?t=1944493) ) and now connection is definitely more stable, networks show up under the network icon, but it still doesn't work properly.

Well I don't know how many drivers I have downloaded and installed reading various forums over the last few days and I am still getting horrible WiFi stability on my x120e. However the surprising fact is that it works flawlessly, out of the box, if you install the 32 bit Ubuntu 12.04.

 I'm not a great with hardware and drivers so I have little knowledge about how stuff works behind the scenes. But then why I really need the amd64 Ubuntu 12.04 is to make full use of the 6gb ram I have installed in the system so that I can run winXP on virtual box that would run ArcGIS in it. 

[off-topic] If there is a work around to get ArcGIS on Ubuntu (I already have QGIS), I'd love to know that too [/off-topic]

 Many thanks in advance

---

### Post by koebln on 2012-11-22
I am the owner of an Lenovo x121e (Type 3051-5QG). The build-in rtl8188ce Wifi shows the same problems since I have changed the OS from 32Bit to 64Bit (currently Ubuntu 12.10 64Bit).  

But today I found a hint, that might fix the problem easily. Look at
[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)

Type the following in the command line
 ** gksudo gedit  /etc/nsswitch.conf**
 This will open the nsswitch.conf file in the text editor. Then simply change the following line
 hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
 to the below line and save the file.
 hosts:          files dns
 That is it. Just reset your internet connection or probably restart your system

This change disables Multicast DNS and for me it looks like the Wifi runs stable. I hope you can agree and you don't need Multicast DNS either.

2012-11-23: The WLAN Connection is still unstable if the signal gets weak. So I followed the other hint in the forums. Download the original driver-software from realtek and compile it for your own machine. I found the driver at
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true)
I took the version  0007.0809.2012 (2012-10-23), unpack and compiled it with
make
sudo make install
The wlan reacts different and up to now the connection is stable even with an weak signal.

---

### Post by lilacsunbird on 2013-01-02
> **koebln said:**
> I am the owner of an Lenovo x121e (Type 3051-5QG). The build-in rtl8188ce Wifi shows the same problems since I have changed the OS from 32Bit to 64Bit (currently Ubuntu 12.10 64Bit).  

But today I found a hint, that might fix the problem easily. Look at
[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)

Type the following in the command line
 ** gksudo gedit  /etc/nsswitch.conf**
 This will open the nsswitch.conf file in the text editor. Then simply change the following line
 hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
 to the below line and save the file.
 hosts:          files dns
 That is it. Just reset your internet connection or probably restart your system

This change disables Multicast DNS and for me it looks like the Wifi runs stable. I hope you can agree and you don't need Multicast DNS either.

2012-11-23: The WLAN Connection is still unstable if the signal gets weak. So I followed the other hint in the forums. Download the original driver-software from realtek and compile it for your own machine. I found the driver at
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=278&DownTypeID=3&GetDown=false&Downloads=true)
I took the version  0007.0809.2012 (2012-10-23), unpack and compiled it with
make
sudo make install
The wlan reacts different and up to now the connection is stable even with an weak signal.

Hi,
 Your suggestion on editing  nsswitch.conf, got my wireless working in fresh install 12.10, however the installing drivers from the realtek website will screw it up. I think the drivers do not support the kernel 3.5 yet, which is default in 12.10 ubuntu. But my wireless used to stop working after 5 mins, now it alteast works. Thanks a lot.

so in short, if you have a fresh install of 12.10, editing  nsswitch.conf as mentioned above should do the trick. Do not try to install the drivers from the realtek website

---

### Post by cforput on 2013-01-12
I didn't want to start a new thread so I'm hoping someone following this one can answer my question. I too am having intermittent wifi connection problems and I have the RTL8188CE card which the OP has as well. My question is why are all the drivers for the 8192 and not the 8188 card? If I look at Realtek's site, they have drivers for both cards listed but this post and others seem to use the 8192 drivers.

Realtek has some new drivers for the both the RTL8188CE and the RTL8192CE-VA4 just released on 10th Jan 2013. Which ones do I use?

---

### Post by asg1290 on 2013-01-26
Have you tried the latest upstream drivers?  If not give this a shot

```
sudo apt-get install linux-headers-$(uname -r) build-essential
wget http://www.kernel.org/pub/linux/kernel/projects/backports/2013/01/23/compat-drivers-2013-01-23-1-u.tar.bz2
tar -jxvf compat-drivers-2013-01-23-1-u.tar.bz2 
cd compat-drivers-2013-01-23-1-u/
./scripts/driver-select rtl818x
make clean
make
sudo make install
```

Reboot and see if that helps.

To revert just 
```
sudo make uninstall
```
reboot

---

### Post by bogan on 2013-01-26
Hi!, **asg1290**, & others,

The compat-drivers that your Post describes, are now available from the Ubuntu Software center or from: ```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
# substitute 'precise' for 'quantal' if appropriate
```Without the need to compile a tar,bz file.

That version -22, and an update -23, are included with the latest Proposed Quantal kernal update releases

Edit: The Software Center includes versions 3.5.0-22 & -23 as well as in 32 & 64 bit versions.

With both Realtek & Ralink adapters I have found them a huge improvement

Chao!, bogan.

---

### Post by cforput on 2013-01-27
OK, so I'm not super technical. What are you guys suggesting? Also, I moved back to 11.10 because the wifi seemed to be more stable. In fact, it was odd but I rebuilt my laptop to 11.10 and the driver worked well. Then the Update Manager popped up and I installed over 400 updates. Right after that I went back to the old intermittant problems. That tells me something between 11.10 and the updates broke the wifi. So, I rebuilt again and am not doing any updates. Not the best plan but it beats not being able to use the internet.

OK, back to my original question, what are you suggesting I do? What do I look for and install in the software center (synaptic actually)

---

### Post by bogan on 2013-01-27
Hi!,** cforput,**

Is/was your problem a difficulty in Network connection ? low download speeds ? intermittent dropping of the connection ? persistent Password requesters ? or something else ??

Which Adapter have you got and which driver are you using ??

The 3.6 compat-wireless-modules will work with 12.10 & 12.04, at least they have solved the problems for me, but you need different versions for 10.04 & 11.10.

Compiling the version in **asg1290**'s Post might work, but that is a 'Techie' solution.

Edit: I would not recommend using the Synaptic route as there are too many alternatives - do a search on 'backports' and you will see.

Chao!, **bogan.**

---

### Post by cforput on 2013-01-27
My problem is intermittent drops. When I say intermittent, my laptop is disconnected more than it is connected so basically worthless. I have a toshiba satellite L655-s5150 and a RealTek RTL8188CE wireless card. I'm using the drivers that come off the live CD which are working right now much better. 

I don't know what backports are but I will look at the post and do some research. I'm just really skeptical to try 12.04 or 12.10 becuase if it doesn't work that means I have to move back to 11.10 which calls for wiping my drive and starting from scratch.

---

### Post by asg1290 on 2013-01-28
> **bogan said:**
> Hi!,** cforput,**

Is/was your problem a difficulty in Network connection ? low download speeds ? intermittent dropping of the connection ? persistent Password requesters ? or something else ??

Which Adapter have you got and which driver are you using ??

The 3.6 compat-wireless-modules will work with 12.10 & 12.04, at least they have solved the problems for me, but you need different versions for 10.04 & 11.10.

Compiling the version in **asg1290**'s Post might work, but that is a 'Techie' solution.

Edit: I would not recommend using the Synaptic route as there are too many alternatives - do a search on 'backports' and you will see.

Chao!, **bogan.**

My solution gives you the latest drivers from the next kernel whereas your package only installs the drivers from 3.6.  I personally needed the latest to get my system up but as always YMMV.

Basically if the packaged comapt wireless works for you then you then great.  If it doesn't then compiling from upstream, like my post instructs, is a reasonable next option to try.  Good luck

---

### Post by bogan on 2013-01-29
Hi!, **asg1290**,

Yes, you are partly correct.

In 12.10 the cw-3.6 command actually loads and installs two versions of the backports-modules-cw-3.5. -xx.x source, one '-23.9', in my case, for the latest installed kernal version, and one '.23.29', "for the generic kernal image".

The use of:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```for 12.04 & 12.10, was recommended to me by **Chili55**5, and works reasonably for me, if not perfectly, certainly a great improvement.

**Chili555 **also suggested the same compile source solution as you Posted, with:  '2.6.39-1', for use with 10.04 & 11.10, for which the cw-3.6 does not work; though I have not tried it so far.

Chao!, **bogan**.

---

