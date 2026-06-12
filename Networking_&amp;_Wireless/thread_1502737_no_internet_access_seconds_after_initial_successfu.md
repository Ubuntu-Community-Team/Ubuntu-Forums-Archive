---
title: "no internet access seconds after initial successful connection"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by ppperez on 2010-06-05
Hello,

When I boot ubuntu, also each time I disable/enable wireless, I can access internet for around 30 seconds, after that my wireless can´t access my router anymore (ubuntu still declares that the connection is established).

Below is the syslog output, please any help?

Jun  5 16:07:35 bob-laptop dhclient: DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
Jun  5 16:07:35 bob-laptop kernel: [  851.063777] DHCP pkt src port:68, dest port:67!!
Jun  5 16:07:35 bob-laptop dhclient: DHCPACK of 192.168.2.4 from 192.168.2.1
Jun  5 16:07:35 bob-laptop dhclient: bound to 192.168.2.4 -- renewal in 15165693 seconds.
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  5 16:07:35 bob-laptop NetworkManager: <info>    address 192.168.2.4
Jun  5 16:07:35 bob-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Jun  5 16:07:35 bob-laptop NetworkManager: <info>    gateway 192.168.2.1
Jun  5 16:07:35 bob-laptop NetworkManager: <info>    nameserver '192.168.2.1'
Jun  5 16:07:35 bob-laptop NetworkManager: <info>    domain name 'Belkin'
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  5 16:07:35 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jun  5 16:07:35 bob-laptop avahi-daemon[933]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.4.
Jun  5 16:07:35 bob-laptop avahi-daemon[933]: New relevant interface wlan0.IPv4 for mDNS.
Jun  5 16:07:35 bob-laptop avahi-daemon[933]: Registering new address record for 192.168.2.4 on wlan0.IPv4.
Jun  5 16:07:36 bob-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jun  5 16:07:36 bob-laptop NetworkManager: <info>  Policy set 'Auto Mywireless' (wlan0) as default for routing and DNS.
Jun  5 16:07:36 bob-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jun  5 16:07:36 bob-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  5 16:07:37 bob-laptop ntpdate[2156]: adjust time server 91.189.94.4 offset -0.003626 sec
Jun  5 16:07:43 bob-laptop kernel: [  859.709644] wlan0: no IPv6 routers present

<HERE is where it seems I lose the connection to Internet>

Jun  5 16:07:56 bob-laptop kernel: [  872.113394] ----------->rtl8192se_check_hw_scan()
Jun  5 16:07:56 bob-laptop kernel: [  872.113398] FW Scan long time without stop, stop hw scan
Jun  5 16:07:56 bob-laptop kernel: [  872.114400] <-----------rtl8192se_check_hw_scan()
Jun  5 16:08:36 bob-laptop kernel: [  912.055495] ----------->rtl8192se_check_hw_scan()
Jun  5 16:08:36 bob-laptop kernel: [  912.055499] FW Scan long time without stop, stop hw scan
Jun  5 16:08:36 bob-laptop kernel: [  912.056499] <-----------rtl8192se_check_hw_scan()

---

### Post by pterion on 2011-06-19
Anything new on this?

---

### Post by nbound on 2011-06-19
post result of **lshw -c network**

---

### Post by pterion on 2011-06-19
In my case, I see similar errors in the log, e.g.

```
Jun 5 16:07:35 bob-laptop kernel: [ 851.063777] DHCP pkt src port:68, dest port:67!!
```

when I cannot reconnect to the wireless network after coming back from standby. I must reboot to be able to connect.

I guess, I should collect the data by lshw -c network while having the problem, right?

---

### Post by nbound on 2011-06-19
At any time

---

### Post by pterion on 2011-06-19
```
$ sudo lshw -c network
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 10
       serial: 1c:4b:d6:6f:22:56
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.0.110 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:19 ioport:d800(size=256) memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c0
       serial: 48:5b:39:11:f0:6e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

