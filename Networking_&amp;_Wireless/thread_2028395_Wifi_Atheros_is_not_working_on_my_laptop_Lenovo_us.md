---
title: "Wifi Atheros is not working on my laptop Lenovo using ubuntu 12.04"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by widiru on 2012-07-18
this is description my wifi :




 *-network DISABLED
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wlan0
                version: 01
                serial: 9c:b7:0d:46:a6:fd
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet phy
sical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-26
-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
n
                resources: irq:17 memory:96400000-9640ffff

---

### Post by chili555 on 2012-07-18
> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.This typically means the wireless switch or key combination is set to OFF. Can you switch it? Please post:```
rfkill list all
```Thanks.

---

### Post by wnelson on 2012-07-18
What brand and model?

---

### Post by RPander93 on 2012-07-18
Having the same problems. Just bought a Lenovo G780 with Atheros Wi-Fi card which isn't working. It cannot find networks and entering the SSID manual also doesn't work because it will not connect.

Google'd it but did not find anything real useful.

---

### Post by chili555 on 2012-07-18
> Having the same problems.Need the same information:```
sudo lshw -C network
rfkill list all
```

---

### Post by RPander93 on 2012-07-18
Allright. Will restart live usb and brb.

> ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d3900000-d393ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 08:ed:b9:9b:17:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d3800000-d3803fff
ubuntu@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Just got a pop-up for enabling the Broadcom Wi-Fi driver and enabled it. But that didn't make it work unfortunately

---

### Post by chili555 on 2012-07-18
> enabling the Broadcom Wi-Fi driver > Just bought a Lenovo G780 with Atheros Wi-Fi card Hmmm. Maybe we'll work on the *Broadcom* wireless card. Afterwards, let's fix the Atheros wired ethernet.

Please post:```
lspci -nn | grep 0280
lsmod | grep -e brcm -e b43 -e wl
```

---

### Post by RPander93 on 2012-07-18
Excuse me for my minor mistake there. Was mixing it up indeed.

```
ubuntu@ubuntu:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
ubuntu@ubuntu:~$ lsmod | grep -e brcm -e b43 -e wl
wl                   2568210  0 
lib80211               14381  1 wl
brcmsmac              570859  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac


```

---

### Post by chili555 on 2012-07-18
No problem at all; I've made worse today and probably more of them!

Ahhh, the infamous 14e4:4727! Just my luck. This is a rare duck that seems to have two ways to get it going. There are threads around here that swear one way works and the other doesn't. First, let's remove wl and see what happens. ```
sudo modprobe -r wl
sudo iwlist wlan0 scan
```If it scans, we can get it to connect. We'll need to remove the STA driver.

If not, remove brcmsmac:```
sudo modprobe -r brcmsmac
sudo modprobe -r bcma
```And now reload wl:```
sudo modprobe wl
sudo iwlist eth1 scan
```Now which combination works? We'll amend a file or two and make it persistent.

---

### Post by RPander93 on 2012-07-18
Okay so I tried those commands. After the first two it reported "wlan0 No scan results" so I continued with the next sets of commands. The last one reports "eth1 Interface doesn't support scanning."

Quite unfortunate, this is. Anything else you'd like to know?

---

### Post by chili555 on 2012-07-18
Please unload all:```
sudo modprobe -r wl
sudo modprobe -r bcma
sudo modprobe -r brcmsmac
```Now reload brcmsmac:```
sudo modprobe brcmsmac
```Now let's check the logs and see what's going on or not:```
dmesg | grep -e brcm -e wlan
```

---

### Post by RPander93 on 2012-07-18
```
ubuntu@ubuntu:~$ sudo modprobe -r wl
ubuntu@ubuntu:~$ sudo modprobe -r bcma
ubuntu@ubuntu:~$ sudo modprobe -r brcmsmac
ubuntu@ubuntu:~$ sudo modprobe brcmsmac
ubuntu@ubuntu:~$ dmesg | grep -e brcm -e wlan
[   18.667806] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 10
[   18.667851] brcmsmac 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.667858] brcmsmac 0000:03:00.0: setting latency timer to 64
[   19.043673] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   19.043677] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   19.044775] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   19.045498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.046391] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   83.731621] brcmsmac 0000:03:00.0: PCI INT A disabled
[   94.048593] brcmsmac 0000:03:00.0: bus 3 slot 0 func 0 irq 17
[   94.048638] brcmsmac 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   94.048647] brcmsmac 0000:03:00.0: setting latency timer to 64
[   94.106905] udevd[5010]: renamed network interface wlan0 to wlan1
[   94.161281] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[   94.161289] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   94.162429] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   94.163412] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   94.164704] ADDRCONF(NETDEV_UP): wlan1: link is not ready
ubuntu@ubuntu:~$ 
```

I'm going to sleep now :p thanks for the help in advance!

---

### Post by chili555 on 2012-07-18
> udevd[5010]: renamed network interface wlan0 to wlan1See you tomorrow. Please post:```
sudo iwlist wlan1 scan
```

---

### Post by RPander93 on 2012-07-19
Well, then I get "wlan1 No scan results". So no improvement yet :(

---

### Post by chili555 on 2012-07-19
Let's try wl and the brute force method:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and run and post:```
sudo iwlist eth1 scan
dmesg | grep -e eth -e wl
```Thanks.

---

### Post by RPander93 on 2012-07-19
RThat als doesnt do the trick. As output I get two msgs about it detecting nvidia optimus. Thats all

---

### Post by chili555 on 2012-07-19
Please try:```
sudo modprobe wl
dmesg | grep wl
```We wonder why wl doesn't load and start.

---

### Post by RPander93 on 2012-07-19
SHWell that one is obvious. First commmand fails with module not found

---

### Post by chili555 on 2012-07-19
> SHWell that one is obvious.Obvious? How so? Wasn't wl loaded previously?> ubuntu@ubuntu:~$ lsmod | grep -e brcm -e b43 -e wl
[COLOR="Red"]wl [/COLOR]                  2568210  0 
lib80211               14381  1[COLOR="Red"] wl[/COLOR]
brcmsmac              570859  0 
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmacWhat is obvious??

---

### Post by kurru on 2012-07-19
Hello, having the same issue. Previously, I had an ASUS A9RP which had the ethernet working perfectly but had very bad wifi driver, so just rarely could use when being close to the router.

Unfortunately, I do not have a solution for this issue now, but I am very interested in the final result. Thanks for the help so far.

---

### Post by kurru on 2012-07-19
I got the following for code:
```

ubuntu@ubuntu:~$ dmesg | grep -e brcm -e wlan
[ 1835.950146] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 17
[ 1835.950191] brcmsmac 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1835.950200] brcmsmac 0000:02:00.0: setting latency timer to 64
[ 1836.059056] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement)
[ 1836.059064] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[ 1836.060209] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1836.060459] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1836.060621] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1838.639539] wlan0: authenticate with e0:cb:4e:ed:2d:c4 (try 1)
[ 1838.641297] wlan0: authenticated
[ 1838.646067] wlan0: associate with e0:cb:4e:ed:2d:c4 (try 1)
[ 1838.648824] wlan0: RX AssocResp from e0:cb:4e:ed:2d:c4 (capab=0x411 status=0 aid=1)
[ 1838.648832] wlan0: associated
[ 1838.649476] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1838.649481] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1838.649487] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[ 1838.649797] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1838.685165] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 1849.252160] wlan0: no IPv6 routers present
```


Please, advise.

---

### Post by RPander93 on 2012-07-19
> **chili555 said:**
> Obvious? How so? Wasn't wl loaded previously?What is obvious??

Obvious as in: it isn't loading because it is not present. Side-note: these last outputs are after I installed from the live usb. Previous ones before you had recommended me to blacklist certain modules were whilst using it from the live usb. I installed Ubuntu on the hard-disk because otherwise blacklisting modules wouldn't stick. So while using it from live usb the "wl" is present, and after installing it isn't anymore.

---

### Post by chili555 on 2012-07-19
I see. It's obvious after you explain what you're doing. I feel like I'm fumbling around in the dark. Are we sticking with the installed to harddrive method now?

---

### Post by RPander93 on 2012-07-20
Yes, that would be the most obvious. I'll do a fresh install to make sure.

---

