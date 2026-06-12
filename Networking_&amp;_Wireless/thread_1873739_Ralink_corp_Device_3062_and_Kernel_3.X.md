---
title: "Ralink corp Device 3062 and Kernel 3.X"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by BTorielli on 2011-11-01
I am trying to make my Azio AWD102N work on ubuntu 11.10 and this seems to be impossible so far.

output for lspci | grep Network

08:01.0 Network controller: Ralink corp. Device 3062

Does not show up as a device in Network Manager

This setup is fresh out of the box, currently bridged to a laptop on my wifi to even get online until I get this sorted.

Drivers are not in restricted drivers or anywhere else I have looked.

Any help would be greatly appreciated.

---

### Post by chili555 on 2011-11-02
We need just a bit more information. Please post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by BTorielli on 2011-11-02
bryan@bryan-pc:~$ lspci -nn | grep 0280
08:01.0 Network controller [0280]: Ralink corp. Device [1814:3062]
bryan@bryan-pc:~$ rfkill list all
bryan@bryan-pc:~$

---

### Post by chili555 on 2011-11-02
This is supposed to work with the module rt2800pci. Please try:```
sudo modprobe rt2800pci
dmesg | grep -i rt2
iwconfig
```Thanks.

---

### Post by BTorielli on 2011-11-02
bryan@bryan-pc:~$ dmesg | grep -i rt2
[ 2324.420500] rt2800pci 0000:08:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2324.446258] Registered led device: rt2800pci-phy0::radio
[ 2324.446281] Registered led device: rt2800pci-phy0::assoc
[ 2324.446301] Registered led device: rt2800pci-phy0::quality
[ 2324.511833] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
bryan@bryan-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

Been working with Azio to get this sorted also.. Found a driver through them on some off site that is getting me further along but still not connecting to anything or showing anything.

---

### Post by chili555 on 2011-11-02
> phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware> Found a driver through them on some off siteDo you think that error is a driver problem or, as I do, a firmware problem? Please post:```
md5sum /lib/firmware/rt2860.bin
```

---

### Post by BTorielli on 2011-11-02
They sent me to the following RAlink site for Firmware for the card.
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

This is the md5 sum response.

md5sum /lib/firmware/rt2860.bin

---

### Post by chili555 on 2011-11-02
The response should have been more like this; an actual sum:> chili@LAPTOP40:~$ md5sum /lib/firmware/rt2860.bin
[COLOR="Red"]75a1da3caa0b1c95e81dfba207f834c6 [/COLOR] /lib/firmware/rt2860.binPlease check again. If not, it implies that you lack the firmware altogether. Please check:```
ls /lib/firmware | grep 286
```Let me switch computers and I'll attach a firmware file and instructions.

---

### Post by BTorielli on 2011-11-02
rt2860.bin

sorry had a bad copy earlier didn't notice.

75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin

---

### Post by chili555 on 2011-11-02
Please see posts #72 and 74 here: [http://ubuntuforums.org/showthread.php?t=1740963&page=8&highlight=rt2860.bin](http://ubuntuforums.org/showthread.php?t=1740963&page=8&highlight=rt2860.bin)

---

### Post by BTorielli on 2011-11-02
After doing what you had on 72 and 74 I no longer have a wireless device when doing iwconfig.

Little confused.

---

### Post by chili555 on 2011-11-02
Let's see:```
dmesg | grep rt2
ls /lib/firmware | grep 286
md5sum /lib/firmware/rt2860.bin
```Thanks.

---

### Post by BTorielli on 2011-11-02
bryan@bryan-pc:~$ dmesg | grep rt2
bryan@bryan-pc:~$ ls /lib/firmware | grep 286
rt2860.bin
rt2860.old.
bryan@bryan-pc:~$ md5sum /lib/firmware/rt2860.bin
66332d7636ee78db31b056aa0e44b097  /lib/firmware/rt2860.bin

---

### Post by chili555 on 2011-11-03
It looks good so far except that rt2800pci didn't load automatically. Let's load it and see if it helps or if there are any errors or warnings. Please show us:```
sudo modprobe rt2800pci
dmesg | grep -i rt2
```Thanks.

---

### Post by BTorielli on 2011-11-03
bryan@bryan-pc:~$ sudo modprobe rt2800pci
bryan@bryan-pc:~$ dmesg | grep -i rt2
[38973.152284] rt2800pci 0000:08:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[38973.177505] Registered led device: rt2800pci-phy0::radio
[38973.177526] Registered led device: rt2800pci-phy0::assoc
[38973.177546] Registered led device: rt2800pci-phy0::quality


So now it shows as a wireless device in Network Manager also, but does not find any networks. Also if I manually add mine it does not connect or do anything.

But progress is exciting.

---

### Post by chili555 on 2011-11-03
What about:```
dmesg | grep wlan
iwconfig
sudo iwlist wlan0 scan
```If there are errors or warnings, the exact wording may be informative, so please post them.

---

### Post by BTorielli on 2011-11-03
```
bryan@bryan-pc:~$ dmesg | grep wlan
[38973.317721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
bryan@bryan-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bryan@bryan-pc:~$ sudo iwlist wlan0 scan
[sudo] password for bryan: 
wlan0     No scan results

```

---

### Post by chili555 on 2011-11-03
Let's try to find out why wlan0 is "not ready" and doesn't scan. Please post:```
sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Thanks.

---

### Post by BTorielli on 2011-11-03
```
bryan@bryan-pc:~$ sudo cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
[sudo] password for bryan: 
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> dhclient started with pid 4525
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Nov  3 12:09:03 bryan-pc NetworkManager[931]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info> (eth0): DHCPv4 state changed preinit -> bound
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info>   address 192.168.1.12
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info>   prefix 24 (255.255.255.0)
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info>   gateway 192.168.1.1
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info>   nameserver '192.168.1.1'
Nov  3 12:09:14 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov  3 12:09:15 bryan-pc NetworkManager[931]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov  3 12:09:15 bryan-pc NetworkManager[931]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Nov  3 12:09:15 bryan-pc NetworkManager[931]: <info> Activation (eth0) successful, device activated.
Nov  3 12:09:15 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  3 12:09:15 bryan-pc NetworkManager[931]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.

```

---

### Post by chili555 on 2011-11-03
Oooops! We have a complete picture of the connection of the wired ethernet, but we need the wireless. Please detach the ethernet cable and run and post:```
sudo cat /var/log/syslog | grep wlan | tail -n20
```

---

### Post by BTorielli on 2011-11-03
```
bryan@bryan-pc:~$ sudo cat /var/log/syslog | grep wlan | tail -n20
Nov  3 09:53:11 bryan-pc NetworkManager[931]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:01.0/net/wlan0, iface: wlan0)
Nov  3 09:53:11 bryan-pc NetworkManager[931]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:01.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 6)
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): now managed
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): bringing up device.
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): preparing device.
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov  3 09:53:11 bryan-pc kernel: [38973.317721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): supplicant interface state: starting -> ready
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): supplicant interface state: ready -> inactive

```

---

### Post by chili555 on 2011-11-03
> device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]May I see:```
cat /etc/NetworkManager/NetworkManager.conf 
cat /etc/network/interfaces
```Thanks.

---

### Post by BTorielli on 2011-11-03
```
bryan@bryan-pc:~$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
bryan@bryan-pc:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

bryan@bryan-pc:~$ 

```

---

### Post by chili555 on 2011-11-03
> bryan@bryan-pc:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopbackPerfect!> bryan@bryan-pc:~$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=falseNot so much. Please do:```
sudo gedit /etc/NetworkManager/NetworkManager.conf 
```Change managed=false to managed=true. Proofread, save and close gedit. Reboot. Now try again:```
sudo cat /var/log/syslog | grep wlan | tail -n20
```

---

### Post by BTorielli on 2011-11-03
```
bryan@bryan-pc:~$ sudo cat /var/log/syslog | grep wlan | tail -n20
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): preparing device.
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov  3 09:53:11 bryan-pc kernel: [38973.317721] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): supplicant interface state: starting -> ready
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov  3 09:53:11 bryan-pc NetworkManager[931]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov  3 17:15:06 bryan-pc NetworkManager[899]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:01.0/net/wlan0, iface: wlan0)
Nov  3 17:15:06 bryan-pc NetworkManager[899]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:08:01.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 4)
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): now managed
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): bringing up device.
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): preparing device.
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov  3 17:15:06 bryan-pc kernel: [  119.397275] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): supplicant interface state: starting -> ready
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov  3 17:15:06 bryan-pc NetworkManager[899]: <info> (wlan0): supplicant interface state: ready -> inactive

```

---

### Post by BTorielli on 2011-11-05
Any idea's or am I SOL at this point?

---

### Post by chili555 on 2011-11-06
> **BTorielli said:**
> Any idea's or am I SOL at this point?I'm sorry, I have no more ideas except to add to an existing or file a new bug report: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by BTorielli on 2011-11-06
Hey, it's all good.

I really appreciate all the help. Something will pop up eventually that will solve it I am sure.

Thanks again

---

### Post by laurens@pz.nl on 2011-12-13
Have u seen this [http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482](http://forum.ubuntuusers.de/topic/doppelseitiges-problem-wlan-kabel/#post-2739482) Its kinds in German but think u will get the:

sudo apt-get install linux-headers-$(uname -r) build-essential 
wget [http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz)
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 

to make ur card working

---

### Post by BTorielli on 2011-12-19
Yup, that did the trick.

Can now connect to Wireless networks with or without encryption also.

Thanks a ton

---

### Post by ctijacob on 2012-02-22
This link is now down, can anyone send me the tar or direct me to a current link, please?

---

