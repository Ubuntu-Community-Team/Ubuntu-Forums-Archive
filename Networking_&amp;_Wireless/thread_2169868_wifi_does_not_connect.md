---
title: "wifi does not connect"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by jlh68 on 2013-08-23
I am running Ubuntu 12.04.2LTS and have an Atheros AR9485 WiFi card in my netbook.  I set netbook up to dual boot with Win7, but the chain boot does not work, so no booting into Win7.  The system seems to try to connect but never does.  It does find my network, just no connection.  This is a new netbook and so far has never connected to 'WiFi.

---

### Post by varunendra on 2013-08-23
Please show us the output of -
```
lspci -nnk | grep -iA2 net
```

If the "driver in use" happens to be ath9k, try the following without a reboot -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
Does it help connecting?

**PS:**
For win7 boot issue, have you tried [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") yet?

---

### Post by jlh68 on 2013-09-04
```
*************** info trace ***************

***** uname -a *****

Linux Osprey 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0740]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e047]
	Kernel modules: ath9k

***** lsusb *****

Bus 002 Device 002: ID 064e:d251 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****

0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

ath9k_common           14054  0 
ath9k_hw              399752  1 ath9k_common
ath                    24124  2 ath9k_common,ath9k_hw
cfg80211              208382  2 mac80211,ath

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.110
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             216.12.78.10
    DNS:             216.12.78.20



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****

nameserver 127.0.0.1
search ntelos.net

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     1673D73171C827FC143E431
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 

filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9CD150684E747A4C35E7D8F
depends:        ath
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8C339DF4D303827C9304BB0
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   10.823642] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[   11.279750] ath9k: `1' invalid for parameter `enable_diversity'

****************** done ******************

```

```
john@Osprey:~$ grep -R ath9k /etc/modprobe.d/
/etc/modprobe.d/ath9k.conf~:options ath9k nohcrypt=1 blink=1 btcoex_enable_diversity=1
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 enable_diversity=1
john@Osprey:~$ 

```

---

### Post by jlh68 on 2013-09-04
I tried this ```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
``` with no improvement.

I have tried several boot-repair disks (on USB flash dtives)  No luck.  In fact I tried to do a Windows Disk-to-Disk restore and that would not work.  I think the windows parts are toast.   I can boot without a problem into Ubuntu.

---

### Post by varunendra on 2013-09-04
As of now, an incorrect parameter is causing the required "ath9k" driver to fail to load -> **jlh68 said:**
> ```
john@Osprey:~$ grep -R ath9k /etc/modprobe.d/
/etc/modprobe.d/ath9k.conf~:options ath9k nohcrypt=1 blink=1 **[COLOR="#FF0000"]btcoex_enable_diversity=1[/COLOR]**
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1 blink=1 btcoex_enable=1 **[COLOR="#FF0000"]enable_diversity=1[/COLOR]**

```

Let's first correct that. Please overwrite the file with only one parameter -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Then do again -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
In the output, you should see the module ath9k load with the "nohwcrypt=1" parameter this time. Check if it's loaded correctly -
```
lsmod | grep ath
```
You should see ath9k, besides the currently existing lines in the lsmod part.

If you still can't connect to the internet, please download and run an alternate version of wireless_script (delete or rename the current one to avoid confusion)- [http://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script](http://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script) and post back the new result file it creates.

---

### Post by jlh68 on 2013-09-15
**varunendra** I have not had time to try your suggestion.  I was doing some maintenace on my Laptop (replaced the front panel and the LCD cable).  Upon reassembly the fan made noise like a screw was in it or something, and I had to shut it down quickly.  Now it will not boot.  I can not even boot from a flashdrive or cd.  The LCD cable corrected my problem but now the unit is black. I have disassembled it since and checked all the cable connections.

That caused me to try to find out if the HD was screwed up or the laptop.  I removed the HD and installed in in the "WiFi troubled" netbook.   Well, the install of my laptop HD in my netbook worked just great and even the WiFi works.  

That makes me think that your suggestion(s) will sooner or later revive the netbook WiFi as it has now proven NOT to be a HARDWARE problem.  Please bear with me on this.  I will have to swap HD,s and work on it soon.  

Do you think I could copy the WiFi file from the laptop HD and put it on Ubuntu One then down load it to the netbook HD overwriting the bad WiFi file?  If so which ones? This is just a thought since it is obvious that the files on the laptop will work on the netbook.

---

### Post by varunendra on 2013-09-15
> **jlh68 said:**
> 
Do you think I could copy the WiFi file from the laptop HD and put it on Ubuntu One then down load it to the netbook HD overwriting the bad WiFi file?  If so which ones? This is just a thought since it is obvious that the files on the laptop will work on the netbook.

Obviously we need to confirm which driver and which version of it is in use when it is working. That combined with kernel version, possible other variables etc. Most or all of this info should be covered by the report that the wireless_script generates.

Please run it when the wifi is working, and post back the report so we can see the difference between various involved factors. Thanks.

---

### Post by jlh68 on 2013-09-15
```
************** info trace *************** 

***** uname -a ***** 

Linux Nighthawk 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 

***** lsb_release ***** 

Distributor ID:	Ubuntu 
Description:	Ubuntu 12.04.3 LTS 
Release:	12.04 
Codename:	precise 

***** lspci ***** 

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 
	Subsystem: Acer Incorporated [ALI] Device [1025:0740] 
	Kernel driver in use: r8169 
-- 
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01) 
	Subsystem: Foxconn International, Inc. Device [105b:e047] 
	Kernel driver in use: ath9k 

***** lsusb ***** 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 002: ID 064e:d251 Suyin Corp. 

***** PCMCIA Card Info ***** 


***** iwconfig ***** 

wlan2     IEEE 802.11bgn  ESSID:"KangarooJump"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 68:7F:74:4D:36:C3   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:1  Invalid misc:48   Missed beacon:0 


***** rfkill ***** 

0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: acer-wireless: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 

***** lsmod ***** 

wl                   3074895  0 
lib80211               14381  1 wl 
ath9k                 132428  0 
mac80211              506862  1 ath9k 
ath9k_common           14053  1 ath9k 
ath9k_hw              411239  2 ath9k,ath9k_common 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw 
cfg80211              205774  4 wl,ath9k,mac80211,ath 

***** nm-tool ***** 

NetworkManager Tool 

State: connected (global) 

- Device: wlan2  [KangarooJump] ------------------------------------------------ 
  Type:              802.11 WiFi 
  Driver:            ath9k 
  State:             connected 
  Default:           yes 
  HW Address:        08:ED:B9:3F:0D:AA 

  Capabilities: 
    Speed:           65 Mb/s 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points (* = current AP) 
    HOME-3E62:       Infra, 00:1D:D3:11:3E:60, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 
    *KangarooJump:   Infra, 68:7F:74:4D:36:C3, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2 
    RGBDGII-guest:   Infra, 68:7F:74:CD:8A:1D, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 
    pcclarke:        Infra, 00:24:B2:C9:E3:D8, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA 
    RGBDGII:         Infra, 68:7F:74:CD:8A:1C, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 

  IPv4 Settings: 
    Address:         192.168.2.107 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.2.1 

    DNS:             192.168.2.1 
    DNS:             216.12.78.10 
    DNS:             216.12.78.20 


- Device: eth2 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        04:7D:7B:9D:F6:3B 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 



***** NetworkManager.state ***** 

[main] 
NetworkingEnabled=true 
WirelessEnabled=true 
WWANEnabled=true 
WimaxEnabled=true 

***** NetworkManager.conf ***** 

[main] 
plugins=ifupdown,keyfile 
dns=dnsmasq 

[ifupdown] 
managed=false 

***** interfaces ***** 

auto lo 
iface lo inet loopback 


***** iwlist ***** 
```

---

### Post by varunendra on 2013-09-15
The output is incomplete. Copy-paste error?

Also, even though it is connected, this seems a bit out of order to me -
> **jlh68 said:**
> ```


***** uname -a ***** 

Linux Nighthawk **[COLOR="#FF0000"]3.2.0-52-generic[/COLOR]** #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux 

***** lsb_release ***** 

Distributor ID:	Ubuntu 
Description:	**[COLOR="#FF0000"]Ubuntu 12.04.3 LTS[/COLOR]** 
Release:	12.04 
Codename:	precise 
```
The point release 12.04.3 comes with kernel version 3.8 as far as I know. So even if it upgraded itself to 12.04.3, I'd expect the kernel would be upgraded to 3.8 too, but you are using an older kernel.

However, this can be the key to be able to connect. The newer version of the ath9k driver in kernel 3.8 seems to be somewhat broken (we are seeing many cases where normal fixes are not working). Since you are using an older kernel, the driver is an older version too, where the current problem didn't exist.

So.. you may choose to stick with kernel version 3.2.. for the time being, or, try kernel version 3.11 on 12.04.3 (not available by default, must be installed from ppa) which seems to work better again.

You can also try just the newer version of ath9k driver backported from kernel 3.11, not the whole kernel. It also seems to work fine, at least in the only case where I saw someone testing it.

Just copying the driver over to the non-working system won't work, since it is only compiled for the kernel it is working upon.

So the bottomline is -
Either stick with kernel version 3.2, or,
Upgrade to kernel 3.11 or at least the backported driver from 3.11

Instructions to compile the backported driver, if you wish to try, are [post=12785322]here[/post] (the last suggestion in the post).

If you need further help, please let me know what option you wish to go with, and post the full output of the script, like the first one you posted (should end with ** done ***)

---

