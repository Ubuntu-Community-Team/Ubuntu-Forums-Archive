---
title: "Just installed my first Ubunto. Everything is great, but no wi-fi. Please help"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by alex_oakland on 2011-10-11
I installed 11.0.4 last night on a Dell Latitude D610. The wi-fi worked fine while it was running Vista (about the only thing that worked fine)

Ubuntu is up and running, but for wireless networks, It says device not ready (firmware missing)

I've been reading before I came here, and this is what I got from the terminal so far.

for nm-tool I get:

Device: wlan)
Type: 802.11 WiFi
Driver: b43
State: unavailable
Default: no
HW Address: 00:14:A%:43:DO:95

fir sudo lshw -c network
description: NEtwork controller
product: BCM4318 [AirForce 54g] 802.11a/b/g PCI Transceiver
vendor: Broadcom Corp
physical ID: 3
bus infor; pci@0000:03:03.0
version: 02
clock: 33Mhz
capabilities: bus master
configuration: driver=b43-pci-bridge latency=64
resources: irq:17 memory:dfce000-dfcffff
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:43:d0:95
capabilities: eitherbet physical wireless
configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic fi
rmware=N/a link=no multicast+yes wireless+IEEE 802.11bg

I tired sudo lsmod and that did not fix the problem.

I tried sudo iwconfig and got:
lo no wireless extensions
eth- no wireless extensions
wlan0 IEEE 802.aabg ESSID:off/any
Mode:Manages Acess Point: Not-Associated Tx-power=0 dBm
Retry Long limit: 7 RTS thr:0ff Fragment thr:off
Encryption key:off
Power managent: off

sudo iwlist scan:
Interface doesn't support scanning: Network is down


lastly, ndiswrapper-l
The program ndiswrapper is currently not installed. You can instal it by typing... which resulted in "Unable to locate package ndiswrapper-common

That's all I got.

I typed that in by hand, typos are mine.

Any help would be greatly appreciated.

---

### Post by carl4926 on 2011-10-11
[http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2FDebian](http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2FDebian)

---

### Post by DanRichNC on 2011-10-11
Give this a try.


sudo mkdir -p /etc/Wireless/RT2860STA/
sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
sudo service network-manager restart

---

### Post by alex_oakland on 2011-10-11
Typed "
sudo apt-get install firmware-b43-installer

what I saw:

unable to locate package firmware-b43-installer

---

### Post by wildmanne39 on 2011-10-11
Hi, it should be as simple as:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Then unplug your wired connection and restart your computer.

If that does not work please post the result of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by alex_oakland on 2011-10-11
> **wildmanne39 said:**
> Hi, it should be as simple as:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Then unplug your wired connection and restart your computer.

If that does not work please post the result of these commands here:
```
cat /etc/lsb-release; uname -a
``````
nm-tool
``````
lspci -nnk | grep -iA2 net
``````
rfkill list all
``````
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you


Here is what finally worked.

Originally, the [SIZE=5][FONT=Trebuchet MS]sudo apt-get install b43-fwcutter firmware-b43-installer resulted in a "not found" error.[/FONT][/SIZE]

but then I used the 
[SIZE=5][FONT=Trebuchet MS]
sudo service network-manager restart

[/FONT][/SIZE][SIZE=5][FONT=Trebuchet MS]DanRichNC posted[/FONT][/SIZE][SIZE=5][FONT=Trebuchet MS], and then

sudo apt-get install b43-fwcutter firmware-b43-installer

Is there a place to mark this as resolved?

Thanks everyone!
[/FONT][/SIZE]

---

### Post by wildmanne39 on 2011-10-11
Hi, your welcome! I am glad it is working.

---

