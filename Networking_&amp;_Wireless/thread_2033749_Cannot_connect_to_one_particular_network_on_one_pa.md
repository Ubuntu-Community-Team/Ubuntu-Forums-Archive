---
title: "Cannot connect to one particular network on one particular machine using Ubuntu"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by JW_00000 on 2012-07-26
Hello,

I'm experiencing a very strange issue: on **one** laptop I cannot connect to **one particular** network, **only** on Ubuntu. However, I can perfectly connect to other networks on this machine, I can connect without problems to this particular network on that same computer using Windows, and I can connect to this network using another machine with Ubuntu.

To be correct: I **can connect** to the network (i.e. the tray icon shows I am connected with two out of three bars lighted), but any request **times out**. Firefox (and other browsers) show a time-out message, pinging 8.8.8.8 times out, pinging the router (192.167.1.1) times out, pinging myself (192.167.1.103) works though.

Anyone got any suggestions?

Some more information:
[LIST]
[*] I tried setting the DNS server to 8.8.8.8, this didn't solve the issue.
[*] I tried manually setting my IP address etc. in the settings for the network (instead of using DHCP), didn't help.
[*] I tried disabling IPv6, doesn't seem to work.
[*] I removed the network and added it again, checked and double-checked the password, etc.
[*] I rebooted the router, checked its settings, etc.
[*] I've been attempting to connect to the network for more than a week, it has never worked.
[*] Again, **I can connect perfectly fine to the network using Windows on the same machine**.
[*] And, **I can connect to the network using another Ubuntu 12.04 laptop**, and my Android phone too.
[/LIST]

Information about my machine:

Brand/type: Acer Aspire Timeline 3810T

Ubuntu version: 12.04 LTS

```
$ uname -a
Linux my-laptop 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

```

```
$ sudo lspci -v -s 01:00.0
01:00.0 Network controller: Intel Corporation WiFi Link 5100
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at e3500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-22-fb-ff-ff-5d-04-26
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
```

```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:22:fb:5d:04:26  
          inet addr:192.167.1.103  Bcast:192.167.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fe5d:426/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:105876 (105.8 KB)  TX bytes:48996 (48.9 KB)
```

```
$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"[SSID of network I'm trying to connect to]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:86:DE:65   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:372   Missed beacon:0
```

```
$ ping -c 3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

$ ping -c 3 192.167.1.1
PING 192.167.1.1 (192.167.1.1) 56(84) bytes of data.

--- 192.167.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms
```

```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:5d:04:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic-pae firmware=8.83.5.1 build 33692 ip=192.167.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:e3500000-e3501fff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:1e:33:22:5e:33
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:e2500000-e253ffff ioport:1000(size=128)
```

The router is a Cisco Linksys WRT160N.

Any help would be greatly appreciated! :)

---

### Post by wildmanne39 on 2012-07-26
Hi, please do:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

Does it connect know? if not post the output of:
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
```
Thanks

---

### Post by TheFu on 2012-07-26
If you can't ping the router (assuming this is a home network), then you aren't really connected at all. You have left over connection data in your 'ifconfig'.

I like to check the routes myself - 'route print' to see if the default route somehow was confused between wired and wireless connections. Having multiple network interfaces active at the same time can cause the disconnected interface to have priority over the connected interface.  The lower "metric" value gets priority.

'ifconfig -a' might help too.

---

### Post by olinart on 2012-07-27
I have had the same problem for some time, and have been trying to debug it. I have had consistent problems over weveral months connecting to some wireless networks with my VOSTRO 130, while it connects successfully to others. The problem began when I upgraded to ubuntu 12.04 - connections were fine with 9.04. I can make it fail on a WPA network with only TKIP encryption, but it works when the same network is set to TKIP/AES. It also fails on a network using WEP protocol. My friend's Dell running 12.04 but with a different network card works on the WEP network. So this is likely a driver or configuration issue.
This seems different from the problems reported in other posts where a connection is made but then lost hours later, or after a suspend.

The failure is the same whether I use NetworkManager or WICD.
How do I submit this as a bug?

Error messages in failure mode (TKIP) and success mode (TKIP/AES
)
```
dmesg with TKIP:
[38764.650996] wlan0: authenticate with 00:26:88:e6:db:34 (try 1)
[38764.653084] wlan0: authenticated
[38764.682511] wlan0: associate with 00:26:88:e6:db:34 (try 1)
[38764.686507] wlan0: RX AssocResp from 00:26:88:e6:db:34 (capab=0x411 status=12 aid=0)
[38764.686520] wlan0: 00:26:88:e6:db:34 denied association (code=12)
[38764.756105] wlan0: deauthenticating from 00:26:88:e6:db:34 by local choice (reason=3)
syslog with TKIP:
Jul 26 20:20:23 olin-mob NetworkManager[994]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 26 20:20:24 olin-mob wpa_supplicant[31648]: Trying to authenticate with 00:26:88:e6:db:34 (SSID='Blacknight' freq=2462 MHz)
Jul 26 20:20:24 olin-mob NetworkManager[994]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 26 20:20:24 olin-mob kernel: [42565.755129] wlan0: authenticate with 00:26:88:e6:db:34 (try 1)
Jul 26 20:20:24 olin-mob wpa_supplicant[31648]: Trying to associate with 00:26:88:e6:db:34 (SSID='Blacknight' freq=2462 MHz)
Jul 26 20:20:24 olin-mob kernel: [42565.757202] wlan0: authenticated
Jul 26 20:20:24 olin-mob NetworkManager[994]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 26 20:20:24 olin-mob kernel: [42565.786755] wlan0: associate with 00:26:88:e6:db:34 (try 1)
Jul 26 20:20:24 olin-mob kernel: [42565.790771] wlan0: RX AssocResp from 00:26:88:e6:db:34 (capab=0x411 status=12 aid=0)
Jul 26 20:20:24 olin-mob kernel: [42565.790778] wlan0: 00:26:88:e6:db:34 denied association (code=12)
Jul 26 20:20:24 olin-mob wpa_supplicant[31648]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jul 26 20:20:24 olin-mob kernel: [42565.863997] wlan0: deauthenticating from 00:26:88:e6:db:34 by local choice (reason=3)
Jul 26 20:20:24 olin-mob NetworkManager[994]: <info> (wlan0): supplicant interface state: associating -> disconnected
```
/var/lib/NetworkManager.state (with TKIP):
[main]
```
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```
lib/NetworkManager/NetworkManager.state (END)
dmesg with tkip/AES:
```
[42915.853474] wlan0: authenticate with 00:26:88:e6:db:34 (try 1)
[42916.050274] wlan0: authenticate with 00:26:88:e6:db:34 (try 2)
[42916.250070] wlan0: authenticate with 00:26:88:e6:db:34 (try 3)
[42916.449827] wlan0: authentication with 00:26:88:e6:db:34 timed out
[42922.525419] wlan0: authenticate with 00:26:88:e6:db:34 (try 1)
[42922.527509] wlan0: authenticated
[42922.556851] wlan0: associate with 00:26:88:e6:db:34 (try 1)
[42922.561013] wlan0: RX AssocResp from 00:26:88:e6:db:34 (capab=0x411 status=0 aid=1)
[42922.561024] wlan0: associated
[42922.568028] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
syslog with TKIP/AES:
Jul 26 20:26:26 olin-mob NetworkManager[994]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jul 26 20:26:26 olin-mob NetworkManager[994]: <info> Activation (wlan0) successful, device activated.
Jul 26 20:26:26 olin-mob NetworkManager[994]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 20:26:26 olin-mob dbus[935]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:26:26 olin-mob dbus[935]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:26:32 olin-mob kernel: [42933.752944] wlan0: no IPv6 routers present
Jul 26 20:26:36 olin-mob ntpdate[1652]: adjust time server 91.189.94.4 offset 0.004493 sec
Jul 26 20:26:43 olin-mob NetworkManager[994]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 26 20:26:43 olin-mob NetworkManager[994]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 26 20:26:43 olin-mob NetworkManager[994]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 26 20:26:43 olin-mob NetworkManager[994]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout)
``` 
System information:
```
uname -a
Linux olin-mob 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux
lspci -vvnn
12:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

sudo lshw -C network
[sudo] password for olin: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: ec:55:f9:42:85:eb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-27-generic-pae firmware=N/A ip=192.168.1.72 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe400000-fe40ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 06
       serial: 78:2b:cb:dc:51:47
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.73 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
```

The documentation  WifiDocs/Device/Atheros/AR9285 says:
For 10.04 install linux-backports-modules-wireless-lucid-generic

For 10.10 install linux-backports-modules-wireless-maverick-generic
I have installed both Additional Drivers (jockey-kde) and (jockey gtk)
 Is there yet a driver approved for 12.04?

---

### Post by JW_00000 on 2012-07-27
@wildmanne39, your solution fixed the issue. Thank you so much!

Afterwards, I re-enabled the default power management (I removed /etc/pm/power.d/wireless again), and it still works, so apparently using wireless N-mode was the problem!

---

### Post by wildmanne39 on 2012-07-27
Hi JW_00000, good to know if you have any other issues it is usually best to have power management turn off, I am glad it is working. Enjoy!!!

---

### Post by wildmanne39 on 2012-07-27
Hi olinart, 

1. You have a different device and it is considered rude to post in someone elses thread when they are still trying to get help so you should have started a new thread.

2. If you look at my first post I gave directions for posting information using code tags to make your post look clean and use less space these things are only mentioned to help teach.

3. Ubuntu works best with wpa2 only not wep or mixed so it is best to use just wpa2 if you have that option.

4. Try:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

Does that help?

5. Bug report has already been filed for quite awhile.
Thanks

---

### Post by olinart on 2012-07-29
Hi, Wildemanne39. Unfortunately the changes you suggested tor reconfigure the ath9k driver do not solve my problem.  I do use the WPA/AES on my home router, where I have control, but it doesn't work in my workplace, which is WEP, did work at the labs I recently visited in Japan, and I'll find out about CERN soon.  So if this doesn't get fixed, it will be a showstopper for me, and I'll have to go back to Fedora.
I wasn't trying to be rude by joining the other discussion. It seemed to me that JW's symptoms were similar and that my information could help diagnose his problem. This forum is rather fragmented, so I think that the better way is to search for related postings so we can help each other. Just starting your own thread leaves this work to others. One of the big problems in debugging this stuff is the "failure to reproduce", so expanding the platforms of the failure is important.
Thanks for the information that the bug report is in. The attention that it gets will presumably depend on whether it can be easily reproduced and how widespread it is.
I'll try to remember to use code tags in the future.

---

### Post by wildmanne39 on 2012-07-29
Hi, > This forum is rather fragmented, so I think that the better way is to search for related postings so we can help each other. Just starting your own thread leaves this work to others. 
it is great to search but make sure you have the same device and it is still best to start your own thread and not to post in one that is still being worked on because it gets confusing for the people trying to help and a lot of times if you get several people in a thread with problems the people that can help may just skip that thread because of the confusion that will be created trying to help a lot of people at once.
Thanks

---

### Post by olinart on 2012-08-10
Dear Wildmanne39,
As a very active moderator of this forum I would ask you whether my problem seems unique. I an afraid, since the bug report is longstanding, that it might be irreproducible because it's some subtle configuration or corruption problem. Otherwise others would be complaining about connecting to some networks and not others.

My 12.04 system is 32 bits and was obtained by upgrading my 10.04 LTS system. Is it likely that loading a clean 64bit OS would have any effect? Or perhaps there are drivers I could remove and reload? I'd be grateful for some advice on how to proceed.

---

### Post by wildmanne39 on 2012-08-10
Hi, your issue is not unique, many people have this issue, besides just wep encryption there are some routers that do not do well with linux.

Since you are only having problems with one location and you are not having any other issues then I doubt that reinstalling ubuntu will help.

You could find an updated driver and try it but this has been going on for a long time so again I do not think that will help but you could try ndiwrapper it is best to ask for help installing it here:
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
Thanks

---

### Post by MichaelMale on 2012-08-10
Hi,

I'm not sure if I should be making a new thread or not, but I've been having this problem too. I tried the steps but it seems to have made the problem worse. I'm using a Netgear N600 Wi-fi adapter, with ndiswrapper maintaining the drivers. This issue has been reported in a 24-page thread on my ISP's help forums, with a usual company response of, "We are trying to fix this, thank you for your patience." This was two years ago and most peoples' PCs now work perfectly. I'm currently using a dLAN in a house with wires that are about 80 years old, so it's not working very well. Can anyone help me with this?

---

### Post by wildmanne39 on 2012-08-10
Hi MichaelMale, you already have two threads going so stay with them please and yes it is better to start your own and not jump into someone else's.
Thanks

---

### Post by olinart on 2012-10-06
I'm happy to report that my wireless worked without problems at numerous hotels and airports in Europe and at large labs in Japan and Switzerland, so it's not so common as I first surmised when it failed on the first two locations that I tried - home and work - where fortunately wired connections are easily available.  Mislead agan by small statistics!

---

