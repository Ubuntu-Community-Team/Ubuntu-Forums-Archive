---
title: "Datron TW3 Wireless Problem"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by ProLogger on 2012-05-19
Hi guys.I have this notebook and I can't solve this problem.I can connect with ethernet but wireless isn't working.What can I do ? I am new user of ubuntu.Help me pls.

My notebook using Intel PRO/Wireless 3945ABG card.

---

### Post by ProLogger on 2012-05-19
Help pls :(

---

### Post by chili555 on 2012-05-19
Let's have a look at:```
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by ProLogger on 2012-05-19
```
enigma@Enigma:~$ dmesg \ grep iwl

Usage:
 dmesg [options]

Options:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string

Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages

enigma@Enigma:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by chili555 on 2012-05-19
> enigma@Enigma:~$ dmesg \ grep iwlIt is *NOT* dmesg [COLOR="Blue"]\[/COLOR] grep iwl; it is dmesg [COLOR="Red"]|[/COLOR] grep iwl. As I said above, the pipe symbol | is on the right side of my US keyboard on the same key with \. It is not the same.

---

### Post by ProLogger on 2012-05-19
> **chili555 said:**
> It is *NOT* dmesg [COLOR="Blue"]\[/COLOR] grep iwl; it is dmesg [COLOR="Red"]|[/COLOR] grep iwl. As I said above, the pipe symbol | is on the right side of my US keyboard on the same key with \. It is not the same.

I wrote dmesg | grep iwl but output is empty.So I tried '/'.

---

### Post by chili555 on 2012-05-19
Let's do some diagnostics:```
lspci -nn | grep 0280
sudo modprobe iwl3945
dmesg | grep iwl
rfkill list all
```> I wrote dmesg | grep iwl but output is empty.So I tried '/'. Then please tell me that the first time.

---

### Post by ProLogger on 2012-05-19
> **chili555 said:**
> Let's do some diagnostics:```
lspci -nn | grep 0280
sudo modprobe iwl3945
dmesg | grep iwl
rfkill list all
```Then please tell me that the first time.


lspci -nn | grep 0280 is empty.

```

lspci -nn | grep 0280


sudo modprobe iwl3945

[sudo] password for enigma: 
enigma@Enigma:~$ dmesg | grep iwl
[  429.985686] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  429.985692] iwl3945: Copyright(c) 2003-2011 Intel Corporation


 rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

And this output is from my other laptop.It isn't connected to internet.

---

### Post by chili555 on 2012-05-19
> And this output is from my other laptop.It isn't connected to internet.Meaning what? The commands you ran were run on the Datron W3, correct?> lspci -nn | grep 0280 is empty.
Then you probably don't have any wireless card at all; certainly not an Intel 3945ABG. Let's dig deeper:```
lspci -nn
lsusb
```

---

### Post by ProLogger on 2012-05-20
> **chili555 said:**
> Meaning what? The commands you ran were run on the Datron W3, correct?Then you probably don't have any wireless card at all; certainly not an Intel 3945ABG. Let's dig deeper:```
lspci -nn
lsusb
```

Yup.Datron TW3.

lspci -nn
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 10)
05:01.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
05:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
05:01.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
05:01.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

```

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18e8:6217 Qcom 

```

---

### Post by chili555 on 2012-05-20
Well, a new device heard from! Or, in this case, an old device. It is new to me and I thought I'd seen everything!> ID [COLOR="Red"]18e8:6217 [/COLOR]QcomThis device is claimed by the module* w35und*.> $ modinfo w35und 
filename:       /lib/modules/3.2.0-24-generic-pae/kernel/drivers/staging/winbond/w35und.ko
version:        0.1
license:        GPL
description:    IS89C35 802.11bg WLAN USB Driver
srcversion:     BC243CFBB8E68ECAC001C05
alias:          usb:v1131p2035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6233d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6230d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]18E8[/COLOR]p[COLOR="Red"]6217[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6206d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0416p0035d*dc*dsc*dp*ic*isc*ip*
depends:        mac80211
staging:        Y
intree:         Y
vermagic:       3.2.0-24-generic-pae SMP mod_unload modversions 686Let's load it and see what happens. Please run and post:```
rfkill list all
sudo modprobe w35und
dmesg | grep w35
iwconfig
```I love a mystery!

As you no doubt see, you haven't an Intel 3945ABG.

---

### Post by ProLogger on 2012-05-20
> **chili555 said:**
> Well, a new device heard from! Or, in this case, an old device. It is new to me and I thought I'd seen everything!This device is claimed by the module* w35und*.Let's load it and see what happens. Please run and post:```
rfkill list all
sudo modprobe w35und
dmesg | grep w35
iwconfig
```I love a mystery!

As you no doubt see, you haven't an Intel 3945ABG.

```

enigma@Enigma:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
enigma@Enigma:~$ sudo modprobe w35und
[sudo] password for enigma: 
enigma@Enigma:~$ dmesg | grep w35
[   14.752802] w35und: module is from the staging directory, the quality is unknown, you have been warned.
[   15.184176] usbcore: registered new interface driver w35und
enigma@Enigma:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

---

### Post by chili555 on 2012-05-20
> wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offWell, there you have a wireless interface and it's not blocked by the hardware switch. Can you click the Network Manager icon, see your network and connect? What does this tell us?```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```I doubt this old-timer is going to do WPA or WPA2. You may need to set the router on WEP.

---

### Post by ProLogger on 2012-05-20
> **chili555 said:**
> Well, there you have a wireless interface and it's not blocked by the hardware switch. Can you click the Network Manager icon, see your network and connect? What does this tell us?```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```I doubt this old-timer is going to do WPA or WPA2. You may need to set the router on WEP.

I can click Network Manager icon but I can't see my wireless connection at Wireless tab.I am using WPA2 on my modem.Try to WEP ?

```

enigma@Enigma:~$ sudo iwlist wlan0 scan
[sudo] password for enigma: 
wlan0     No scan results

enigma@Enigma:~$ sudo iwlist wlan0 auth
[sudo] password for enigma: 
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP

```

---

### Post by chili555 on 2012-05-20
> I am using WPA2 on my modem.Try to WEP ?Not yet; it looks like the card does WPA2:> wlan0     Authentication capabilities :
        [COLOR="Red"]WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP[/COLOR]Let's try to figure out why it isn't scanning and connecting:```
dmesg | grep -e w35 -e wlan -e 80211
```

---

### Post by ProLogger on 2012-05-20
> **chili555 said:**
> Not yet; it looks like the card does WPA2:Let's try to figure out why it isn't scanning and connecting:```
dmesg | grep -e w35 -e wlan -e 80211
```


```

enigma@Enigma:~$ dmesg | grep -e w35 -e wlan -e 80211
[   14.295362] cfg80211: Calling CRDA to update world regulatory domain
[   14.591903] w35und: module is from the staging directory, the quality is unknown, you have been warned.
[   14.974641] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.974647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   15.054747] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.057195] usbcore: registered new interface driver w35und
[   16.078714] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   16.078721] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.078724] cfg80211: World regulatory domain updated:
[   16.078726] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.078730] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.078734] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.078738] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.078741] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.078745] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.188844] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.190643] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  496.288087] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  496.288092] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.288240] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[  497.817671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  497.820458] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by chili555 on 2012-05-20
It all looks pretty normal. In fact,the timestamps in 14-16.xx range occurred during bootup, so it's trying to start. Have you made any additions or changes to Network Manager? Usually, no human settings are required. I notice your card says it's an 802.11b device.> wlan0     IEEE [COLOR="Red"]802.11b[/COLOR]  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:offIs your modem set to transmit B, G and N speeds? G only? N only? I suspect that, in order for this device to see and connect, the modem must broadcast in, at least, B. Any clues here?```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by ProLogger on 2012-05-20
> **chili555 said:**
> It all looks pretty normal. In fact,the timestamps in 14-16.xx range occurred during bootup, so it's trying to start. Have you made any additions or changes to Network Manager? Usually, no human settings are required. I notice your card says it's an 802.11b device.Is your modem set to transmit B, G and N speeds? G only? N only? I suspect that, in order for this device to see and connect, the modem must broadcast in, at least, B. Any clues here?```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```


I am using Airties RT-206 modem at home.I established Ubuntu and I can't connect with wireless.

```

enigma@Enigma:~$ sudo cat /var/log/syslog | grep -e wlan -etwork | tail -n20
[sudo] password for enigma: 
May 20 19:33:53 Enigma NetworkManager[582]: <info> waking up and re-enabling...
May 20 19:33:53 Enigma NetworkManager[582]: <info> WWAN now enabled by management service
May 20 19:33:53 Enigma NetworkManager[582]: <info> (eth0): now managed
May 20 19:33:53 Enigma NetworkManager[582]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 20 19:33:53 Enigma NetworkManager[582]: <info> (eth0): bringing up device.
May 20 19:33:53 Enigma NetworkManager[582]: <info> (eth0): preparing device.
May 20 19:33:53 Enigma NetworkManager[582]: <info> (eth0): deactivating device (reason 'managed') [2]
May 20 19:33:53 Enigma NetworkManager[582]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 19:33:53 Enigma NetworkManager[582]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): now managed
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): bringing up device.
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): preparing device.
May 20 19:33:53 Enigma kernel: [  497.817671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): deactivating device (reason 'managed') [2]
May 20 19:33:53 Enigma kernel: [  497.820458] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): supplicant interface state: starting -> ready
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 20 19:33:53 Enigma NetworkManager[582]: <info> (wlan0): supplicant interface state: ready -> inactive
May 20 19:33:53 Enigma NetworkManager[582]: <warn> Trying to remove a non-existant call id.

```

---

### Post by chili555 on 2012-05-20
Let's see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Thanks.

---

