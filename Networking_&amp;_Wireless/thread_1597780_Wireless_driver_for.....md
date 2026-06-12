---
title: "Wireless driver for...."
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by elliottj on 2010-10-15
.....06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

I have an Acer Aspire 4551 and would liek to know if anyone out there either:
a) Has the proper driver for my machine (I get about have of the range and performance that I got with Windows 7)

or b) can tell me where to obtain the information on how to make it myself (I've haerd you can port windows drivers to Linux..)

Any and all help appreciated!!!

---

### Post by chili555 on 2010-10-15
I believe it uses the module *ath9k* which should be already in your kernel, assuming you are using a recent version of Ubuntu.

Please post:```
lspci -nn | grep Network
modinfo ath9k
dmesg | grep ath
```Thanks.

---

### Post by elliottj on 2010-10-15
$ lspci -nn | grep Network
06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

$ modinfo ath9k
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F512940B820872C31133E06
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,led-class,ath,cfg80211,ath9k_common
vermagic:       2.6.35-22-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)

$ dmesg | grep ath
[    0.561648] device-mapper: multipath: version 1.1.1 loaded
[    0.561650] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.222452] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.222461] ath9k 0000:06:00.0: setting latency timer to 64
[    4.651453] ath: EEPROM regdomain: 0x65
[    4.651456] ath: EEPROM indicates we should expect a direct regpair map
[    4.651460] ath: Country alpha2 being used: 00
[    4.651461] ath: Regpair used: 0x65
[    4.659667] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    4.660226] Registered led device: ath9k-phy0::radio
[    4.660239] Registered led device: ath9k-phy0::assoc
[    4.660253] Registered led device: ath9k-phy0::tx
[    4.660266] Registered led device: ath9k-phy0::rx

---

### Post by chili555 on 2010-10-15
Looks perfect! It is in your kernel and loads. It is correct for your device:> 06:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [[COLOR="Red"]168c:002a[/COLOR]] (rev 01)
> $ modinfo ath9k
filename: /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless LAN cards.
author: Atheros Communications
srcversion: F512940B820872C31133E06
--- snip ---
alias: pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]002A[/COLOR]sv*sd*bc*sc*i*So what is not working as expected? Can you click the Network Manager icon and see networks? What happens if you select yours and try to connect?

---

### Post by elliottj on 2010-10-15
Well, I have two problems, possibly related. 
1) wireless isnt enabled at startup. it works after i click "enable wireless", but wont start at bootup. not a huge deal, but very annoying.
2) performance compared to windows is half. This goes for range of my wireless router and the d/l speed, and I have confirmed it is my laptop that has changed, not the network itself

---

### Post by chili555 on 2010-10-15
Please reboot and try:```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```If you right-click the Network Manager icon and select 'Edit Connections' and select 'Wireless,' is the box "Connect Automatically' checked? Please see attached.

Any change in speeds? If it improves, we can make it automatic.

---

### Post by elliottj on 2010-10-16
I cant tell if the speed is much better, but  It's not slower at least! :p it still doesnt connect on startup :( thanks though!!!

---

### Post by chili555 on 2010-10-16
Maybe the system log will tell us why it isn't connecting at boot. Let's create an information file I can look at. Please reboot and before you do anything else, open a terminal and do:```
ifconfig > info.txt
iwconfig >> info.txt
lsmod | grep ath >> info.txt
sudo tail -n30 /var/log/syslog >> info.txt
zip info.zip info.txt
```You will find a zip file in your home directory called info.zip. Transfer it on a USB key or otherwise so you can post it here as an attachment to your reply.

---

