---
title: "Can connect via wireless to DSL modem, but no internet."
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by nihiliad on 2011-10-03
I can connect via wireless to my ZyXel PK5000z DSL modem, provided by Qwest/CenturyLink, but cannot access the internet. Qwest's modem config app shows that my laptop is connected to the modem. A traceroute from the laptop shows that the connection goes nowhere beyond the modem.

My laptop is a Lenovo T420s with an Intel Centrino Centrino Advanced-N + WiMAX 6250 (rev 5e) wireless card, running 11.04 Natty.

Any ideas for troubleshooting this?

---

### Post by wildmanne39 on 2011-10-04
Hi, please post the results of these commands:
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep iwl
```
```
dmesg | egrep 'iwl|firm|wlan0'
```
Thank you

---

