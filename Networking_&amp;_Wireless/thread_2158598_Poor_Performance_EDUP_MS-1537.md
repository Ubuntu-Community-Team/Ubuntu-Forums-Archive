---
title: "Poor Performance EDUP MS-1537"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by neutronforrest on 2013-06-29
Dear Forum,

I purchased a cheap EDUP ms1537 usb wifi adapter with antenna.  I installed Ubuntu 12.10 and then plugged in the usb wifi adapter.  It did recognize the my wifi and I entered my password.  It connected to the internet right out of the box.  

That was to good to be true.  The wifi drops after only a few minutes.  I have been trying to understand how to install the driver.  I would appreciate the help.  I have downloaded the driver from edup and have been unable to install.  

Please help...
CJ

---

### Post by chili555 on 2013-06-29
Let's start by identifying your device. Please open a terminal Ctrl+Alt+t and run and post for us:```
lsusb
iwconfig
ping -c3 www.google.com
```Thank you!

---

### Post by neutronforrest on 2013-06-30
Thank you for the help.  I hope to learn from this also.  Here is the info,


lsusb

```

LAN Adapter
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```




iwconfig

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ForrestHomeWireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:E5:4A:76   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



ping -c3 [www.google.com](www.google.com)



```

PING www.google.com (74.125.26.99) 56(84) bytes of data.
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=1 ttl=39 time=56.4 ms
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=2 ttl=39 time=53.2 ms
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=3 ttl=39 time=53.5 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 53.217/54.420/56.452/1.469 ms

```

If it is not to much trouble could you explain a little about each command.
CJ

---

### Post by chili555 on 2013-06-30
You said:>  I installed Ubuntu 12.10 and then plugged in the usb wifi adapter.In order to identify the exact device and then deduce the driver, I asked for a listing of the USB devices: lsusb:> [COLOR="#FF0000"]???[/COLOR] LAN Adapter
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hubIt appears to me that your copy and paste missed the USB wireless so please try again.> wlan0     IEEE 802.11bgn  ESSID:"ForrestHomeWireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F2:E5:4A:76   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0I hoped to see if you are connected (Yes); if you are reasonably close to the router; usually a significant factor in wireless performance (Link Quality=70/70; Yes) and look at problems with lost packets, etc. (None). So far, so good.> PING [www.google.com](www.google.com) (74.125.26.99) 56(84) bytes of data.
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=1 ttl=39 time=56.4 ms
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=2 ttl=39 time=53.2 ms
64 bytes from vh-in-f99.1e100.net (74.125.26.99): icmp_req=3 ttl=39 time=53.5 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 53.217/54.420/56.452/1.469 msPing times are an indication of how long a packet takes to get to your ISP, through the DNS nameserver to the destination and an acknowledgement packet all the way back. [http://en.wikipedia.org/wiki/Ping_%28networking_utility%29](http://en.wikipedia.org/wiki/Ping_%28networking_utility%29)

In your case, the times a a little slow but not terrible. For comparison, mine averages about 45 ms and I consider my connection pretty good. Maybe we can see if the DNS nameserver is a factor by bypassing it and pinging by number:```
ping -c3 74.125.26.99
```Any better?

Until we find out about your device and driver, we're a bit stuck.

---

### Post by neutronforrest on 2013-06-30
Yes...I missed it.

Here is it again,

```

Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

So this is a realtek usb wifi-adapter.  Does this also give the chipset?
For some reason I am unable to get the wifi to work on this computer now.  So I am unable to do,


ping -c3 74.125.26.99


I am glad you are explaining this.  What should we do next?
CJ

---

### Post by neutronforrest on 2013-06-30
An interesting observation is if I unplug the USB wifi-adpater and plug back in I get a connection.

```

:~$ ping -c3 74.125.26.99
PING 74.125.26.99 (74.125.26.99) 56(84) bytes of data.
64 bytes from 74.125.26.99: icmp_req=1 ttl=39 time=54.9 ms
64 bytes from 74.125.26.99: icmp_req=2 ttl=39 time=56.7 ms
64 bytes from 74.125.26.99: icmp_req=3 ttl=39 time=54.3 ms

--- 74.125.26.99 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 54.346/55.339/56.742/1.038 ms

```

However, like last time the connection only last a few minutes and does not reconnect.

---

### Post by chili555 on 2013-06-30
> ID 0bda:8178 Realtek Semiconductor Corp.[COLOR="#FF0000"] RTL8192CU[/COLOR] 802.11n WLAN Adapter>  Does this also give the chipset?Yes. We know the driver is rtl8192cu. You can verify that by listing all the loaded modules and filtering for "rtl':```
lsmod | grep rtl
```We can also look at the module details and see your device:```
modinfo rtl8192cu
```> alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]8178[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*Now, let's see if the system logs hold any clue as to the source of the disconnect:```
cat /var/log/syslog | grep -e rtl -e 80211
```

---

### Post by neutronforrest on 2013-06-30
Here is the log file,

```

Jun 30 11:22:07 rockforrest kernel: [    3.873142] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 11:22:07 rockforrest kernel: [    3.892600] rtl8192cu: Chip version 0x11
Jun 30 11:22:07 rockforrest kernel: [    4.095823] rtl8192cu: MAC address: e8:4e:06:0e:36:59
Jun 30 11:22:07 rockforrest kernel: [    4.095837] rtl8192cu: Board Type 0
Jun 30 11:22:07 rockforrest kernel: [    4.096062] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Jun 30 11:22:07 rockforrest kernel: [    4.096069] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096073] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096076] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096079] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096081] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096084] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096087] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096090] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096092] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096095] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096098] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096101] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096103] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096106] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096109] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096112] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096114] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096117] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096120] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096123] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096125] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:07 rockforrest kernel: [    4.096128] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:22:07 rockforrest kernel: [    4.096131] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:22:07 rockforrest kernel: [    4.096133] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:22:07 rockforrest kernel: [    4.096136] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:22:07 rockforrest kernel: [    4.096156] cfg80211: Pending regulatory request, waiting for it to be processed...
Jun 30 11:22:07 rockforrest kernel: [    4.096209] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
Jun 30 11:22:07 rockforrest kernel: [    4.099936] usbcore: registered new interface driver rtl8192cu
Jun 30 11:22:08 rockforrest kernel: [    4.872563] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 11:22:08 rockforrest NetworkManager[730]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jun 30 11:22:08 rockforrest kernel: [    5.108926] ieee80211 phy0: >Selected rate control algorithm 'rtl_rc'
Jun 30 11:22:08 rockforrest kernel: [    5.110823] rtlwifi: wireless switch is on
Jun 30 11:22:08 rockforrest kernel: [    5.151959] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 11:22:08 rockforrest kernel: [    5.151970] cfg80211: World regulatory domain updated:
Jun 30 11:22:08 rockforrest kernel: [    5.151972] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 11:22:08 rockforrest kernel: [    5.151976] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.151980] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.151983] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.151986] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.151988] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.152011] cfg80211: Calling CRDA for country: US
Jun 30 11:22:08 rockforrest NetworkManager[730]: <info> (wlan0): using nl80211 for WiFi device control
Jun 30 11:22:08 rockforrest NetworkManager[730]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 3)
Jun 30 11:22:08 rockforrest kernel: [    5.215696] rtl8192cu: MAC auto ON okay!
Jun 30 11:22:08 rockforrest kernel: [    5.254291] rtl8192cu: Tx queue select: 0x05
Jun 30 11:22:08 rockforrest kernel: [    5.259612] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259621] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259625] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259628] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259631] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259634] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259637] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259640] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259656] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259659] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259662] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259664] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259667] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259670] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259673] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259676] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259678] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259681] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259684] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259689] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:22:08 rockforrest kernel: [    5.259692] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259694] cfg80211: Disabling freq 2467 MHz
Jun 30 11:22:08 rockforrest kernel: [    5.259696] cfg80211: Disabling freq 2472 MHz
Jun 30 11:22:08 rockforrest kernel: [    5.259698] cfg80211: Disabling freq 2484 MHz
Jun 30 11:22:08 rockforrest kernel: [    5.259703] cfg80211: Regulatory domain changed to country: US
Jun 30 11:22:08 rockforrest kernel: [    5.259705] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 11:22:08 rockforrest kernel: [    5.259708] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259711] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259714] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259717] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259720] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:08 rockforrest kernel: [    5.259723] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jun 30 11:22:56 rockforrest kernel: [   53.382726] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 11:22:56 rockforrest kernel: [   53.382739] cfg80211: Restoring regulatory settings
Jun 30 11:22:56 rockforrest kernel: [   53.382748] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 11:22:56 rockforrest kernel: [   53.391134] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 11:22:56 rockforrest kernel: [   53.391144] cfg80211: World regulatory domain updated:
Jun 30 11:22:56 rockforrest kernel: [   53.391146] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 11:22:56 rockforrest kernel: [   53.391150] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:56 rockforrest kernel: [   53.391153] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:56 rockforrest kernel: [   53.391157] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:56 rockforrest kernel: [   53.391160] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:22:56 rockforrest kernel: [   53.391163] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:31:53 rockforrest kernel: [  590.084365] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x130049
Jun 30 11:31:53 rockforrest kernel: [  590.084387] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x10018
Jun 30 11:31:53 rockforrest kernel: [  590.084402] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1
Jun 30 11:31:53 rockforrest kernel: [  590.084420] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
Jun 30 11:31:53 rockforrest NetworkManager[730]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/ieee80211/phy0/rfkill0 disappeared
Jun 30 11:31:58 rockforrest kernel: [  595.081369] rtl8192cu: Chip version 0x11
Jun 30 11:31:59 rockforrest kernel: [  595.159113] rtl8192cu: MAC address: e8:4e:06:0e:36:59
Jun 30 11:31:59 rockforrest kernel: [  595.159132] rtl8192cu: Board Type 0
Jun 30 11:31:59 rockforrest kernel: [  595.159348] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Jun 30 11:31:59 rockforrest kernel: [  595.159360] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159374] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159386] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159393] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159398] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159404] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159409] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159415] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159420] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159426] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159431] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159437] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159442] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159453] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159460] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159465] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159471] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159476] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 11:31:59 rockforrest kernel: [  595.159482] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 11:31:59 rockforrest kernel: [  595.159487] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:31:59 rockforrest kernel: [  595.159492] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:31:59 rockforrest kernel: [  595.159497] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 11:31:59 rockforrest kernel: [  595.159589] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
Jun 30 11:31:59 rockforrest kernel: [  595.171650] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 11:31:59 rockforrest kernel: [  595.171885] ieee80211 phy1: >Selected rate control algorithm 'rtl_rc'
Jun 30 11:31:59 rockforrest kernel: [  595.172719] rtlwifi: wireless switch is on
Jun 30 11:31:59 rockforrest NetworkManager[730]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy1/rfkill1) (driver (unknown))
Jun 30 11:31:59 rockforrest NetworkManager[730]: <info> (wlan0): using nl80211 for WiFi device control
Jun 30 11:31:59 rockforrest NetworkManager[730]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 4)
Jun 30 11:31:59 rockforrest kernel: [  595.212211] rtl8192cu: MAC auto ON okay!
Jun 30 11:31:59 rockforrest kernel: [  595.247474] rtl8192cu: Tx queue select: 0x05
Jun 30 11:43:18 rockforrest kernel: [ 1274.857059] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 11:43:18 rockforrest kernel: [ 1274.857079] cfg80211: Restoring regulatory settings
Jun 30 11:43:18 rockforrest kernel: [ 1274.857090] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 11:43:18 rockforrest kernel: [ 1274.869983] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 11:43:18 rockforrest kernel: [ 1274.869994] cfg80211: World regulatory domain updated:
Jun 30 11:43:18 rockforrest kernel: [ 1274.869997] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 11:43:18 rockforrest kernel: [ 1274.870000] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:43:18 rockforrest kernel: [ 1274.870004] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:43:18 rockforrest kernel: [ 1274.870007] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:43:18 rockforrest kernel: [ 1274.870010] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 11:43:18 rockforrest kernel: [ 1274.870013] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:53:18 rockforrest kernel: [ 5474.851934] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 12:53:18 rockforrest kernel: [ 5474.851953] cfg80211: Restoring regulatory settings
Jun 30 12:53:18 rockforrest kernel: [ 5474.851966] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 12:53:18 rockforrest kernel: [ 5474.864570] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 12:53:18 rockforrest kernel: [ 5474.864580] cfg80211: World regulatory domain updated:
Jun 30 12:53:18 rockforrest kernel: [ 5474.864583] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 12:53:18 rockforrest kernel: [ 5474.864587] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:53:18 rockforrest kernel: [ 5474.864590] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:53:18 rockforrest kernel: [ 5474.864593] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:53:18 rockforrest kernel: [ 5474.864596] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 12:53:18 rockforrest kernel: [ 5474.864599] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:01:18 rockforrest kernel: [ 5954.855276] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 13:01:18 rockforrest kernel: [ 5954.855294] cfg80211: Restoring regulatory settings
Jun 30 13:01:18 rockforrest kernel: [ 5954.855306] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 13:01:18 rockforrest kernel: [ 5954.865714] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 13:01:18 rockforrest kernel: [ 5954.865724] cfg80211: World regulatory domain updated:
Jun 30 13:01:18 rockforrest kernel: [ 5954.865726] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 13:01:18 rockforrest kernel: [ 5954.865730] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:01:18 rockforrest kernel: [ 5954.865734] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:01:18 rockforrest kernel: [ 5954.865737] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:01:18 rockforrest kernel: [ 5954.865740] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:01:18 rockforrest kernel: [ 5954.865743] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:08:37 rockforrest kernel: [ 6393.650818] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 13:08:37 rockforrest kernel: [ 6393.650836] cfg80211: Restoring regulatory settings
Jun 30 13:08:37 rockforrest kernel: [ 6393.650848] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 13:08:37 rockforrest kernel: [ 6393.663112] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 13:08:37 rockforrest kernel: [ 6393.663126] cfg80211: World regulatory domain updated:
Jun 30 13:08:37 rockforrest kernel: [ 6393.663131] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 13:08:37 rockforrest kernel: [ 6393.663139] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:08:37 rockforrest kernel: [ 6393.663145] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:08:37 rockforrest kernel: [ 6393.663152] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:08:37 rockforrest kernel: [ 6393.663158] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 13:08:37 rockforrest kernel: [ 6393.663164] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:26 rockforrest kernel: [    4.154310] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 16:45:26 rockforrest kernel: [    4.276015] rtl8192cu: Chip version 0x11
Jun 30 16:45:27 rockforrest kernel: [    4.693593] rtl8192cu: MAC address: e8:4e:06:0e:36:59
Jun 30 16:45:27 rockforrest kernel: [    4.693606] rtl8192cu: Board Type 0
Jun 30 16:45:27 rockforrest kernel: [    4.693834] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Jun 30 16:45:27 rockforrest kernel: [    4.693843] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693847] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693850] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693853] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693856] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693859] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693861] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693865] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693867] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693870] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693873] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693875] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693878] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693881] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693883] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693886] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693889] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693894] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693897] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693899] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    4.693902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.693905] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:45:27 rockforrest kernel: [    4.693908] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:45:27 rockforrest kernel: [    4.693910] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:45:27 rockforrest kernel: [    4.693925] cfg80211: Pending regulatory request, waiting for it to be processed...
Jun 30 16:45:27 rockforrest kernel: [    4.693971] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
Jun 30 16:45:27 rockforrest kernel: [    4.694232] usbcore: registered new interface driver rtl8192cu
Jun 30 16:45:27 rockforrest kernel: [    4.833342] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 16:45:27 rockforrest kernel: [    4.934549] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 16:45:27 rockforrest kernel: [    4.934560] cfg80211: World regulatory domain updated:
Jun 30 16:45:27 rockforrest kernel: [    4.934562] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 16:45:27 rockforrest kernel: [    4.934566] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.934570] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.934573] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.934576] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.934579] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    4.934612] cfg80211: Calling CRDA for country: US
Jun 30 16:45:27 rockforrest kernel: [    5.001836] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001845] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001848] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001852] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001855] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001858] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001861] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001864] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001866] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001869] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001872] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001875] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001877] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001880] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001883] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001886] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001888] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001891] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001894] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001897] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001899] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:45:27 rockforrest kernel: [    5.001902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001904] cfg80211: Disabling freq 2467 MHz
Jun 30 16:45:27 rockforrest kernel: [    5.001906] cfg80211: Disabling freq 2472 MHz
Jun 30 16:45:27 rockforrest kernel: [    5.001908] cfg80211: Disabling freq 2484 MHz
Jun 30 16:45:27 rockforrest kernel: [    5.001914] cfg80211: Regulatory domain changed to country: US
Jun 30 16:45:27 rockforrest kernel: [    5.001916] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 16:45:27 rockforrest kernel: [    5.001919] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001922] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001925] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001927] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001930] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:45:27 rockforrest kernel: [    5.001933] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jun 30 16:45:27 rockforrest NetworkManager[763]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy0/rfkill0) (driver (unknown))
Jun 30 16:45:27 rockforrest kernel: [    5.040224] ieee80211 phy0: >Selected rate control algorithm 'rtl_rc'
Jun 30 16:45:27 rockforrest kernel: [    5.048572] rtlwifi: wireless switch is on
Jun 30 16:45:27 rockforrest NetworkManager[763]: <info> (wlan0): using nl80211 for WiFi device control
Jun 30 16:45:27 rockforrest NetworkManager[763]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 3)
Jun 30 16:45:27 rockforrest kernel: [    5.143575] rtl8192cu: MAC auto ON okay!
Jun 30 16:45:27 rockforrest kernel: [    5.179328] rtl8192cu: Tx queue select: 0x05
Jun 30 16:46:14 rockforrest kernel: [   52.296787] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 30 16:46:14 rockforrest kernel: [   52.296801] cfg80211: Restoring regulatory settings
Jun 30 16:46:14 rockforrest kernel: [   52.296810] cfg80211: Calling CRDA to update world regulatory domain
Jun 30 16:46:14 rockforrest kernel: [   52.305442] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 16:46:14 rockforrest kernel: [   52.305453] cfg80211: World regulatory domain updated:
Jun 30 16:46:14 rockforrest kernel: [   52.305455] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 30 16:46:14 rockforrest kernel: [   52.305459] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:46:14 rockforrest kernel: [   52.305462] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:46:14 rockforrest kernel: [   52.305466] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:46:14 rockforrest kernel: [   52.305469] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:46:14 rockforrest kernel: [   52.305472] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 30 16:47:18 rockforrest kernel: [  116.101073] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3903f2a
Jun 30 16:47:18 rockforrest kernel: [  116.101099] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
Jun 30 16:47:18 rockforrest kernel: [  116.101114] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f3f
Jun 30 16:47:18 rockforrest kernel: [  116.101132] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x3f3f3f27
Jun 30 16:47:18 rockforrest NetworkManager[763]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy0/rfkill0 disappeared
Jun 30 16:47:20 rockforrest kernel: [  118.003266] rtl8192cu: Chip version 0x11
Jun 30 16:47:20 rockforrest kernel: [  118.081517] rtl8192cu: MAC address: e8:4e:06:0e:36:59
Jun 30 16:47:20 rockforrest kernel: [  118.081535] rtl8192cu: Board Type 0
Jun 30 16:47:20 rockforrest kernel: [  118.081751] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Jun 30 16:47:20 rockforrest kernel: [  118.081763] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081771] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081777] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081783] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081789] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081800] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081811] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081822] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081829] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081834] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081840] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081845] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081851] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081856] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081862] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081867] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081873] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081878] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:47:20 rockforrest kernel: [  118.081884] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:47:20 rockforrest kernel: [  118.081889] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:47:20 rockforrest kernel: [  118.081894] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:47:20 rockforrest kernel: [  118.081899] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:47:20 rockforrest kernel: [  118.081991] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
Jun 30 16:47:20 rockforrest kernel: [  118.093428] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 16:47:20 rockforrest kernel: [  118.093749] ieee80211 phy1: >Selected rate control algorithm 'rtl_rc'
Jun 30 16:47:20 rockforrest kernel: [  118.095253] rtlwifi: wireless switch is on
Jun 30 16:47:20 rockforrest NetworkManager[763]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy1/rfkill1) (driver (unknown))
Jun 30 16:47:20 rockforrest NetworkManager[763]: <info> (wlan0): using nl80211 for WiFi device control
Jun 30 16:47:20 rockforrest NetworkManager[763]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 4)
Jun 30 16:47:20 rockforrest kernel: [  118.136925] rtl8192cu: MAC auto ON okay!
Jun 30 16:47:20 rockforrest kernel: [  118.170049] rtl8192cu: Tx queue select: 0x05
Jun 30 16:48:53 rockforrest NetworkManager[763]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy1/rfkill1 disappeared
Jun 30 16:48:59 rockforrest kernel: [  216.395194] rtl8192cu: Chip version 0x11
Jun 30 16:48:59 rockforrest kernel: [  216.471938] rtl8192cu: MAC address: e8:4e:06:0e:36:59
Jun 30 16:48:59 rockforrest kernel: [  216.471957] rtl8192cu: Board Type 0
Jun 30 16:48:59 rockforrest kernel: [  216.472175] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Jun 30 16:48:59 rockforrest kernel: [  216.472187] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472195] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472200] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472207] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472212] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472219] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472224] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472230] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472235] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472241] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472246] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472252] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472257] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472264] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472269] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472275] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472279] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472286] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472291] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472297] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472301] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 30 16:48:59 rockforrest kernel: [  216.472304] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Jun 30 16:48:59 rockforrest kernel: [  216.472307] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:48:59 rockforrest kernel: [  216.472309] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:48:59 rockforrest kernel: [  216.472312] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Jun 30 16:48:59 rockforrest kernel: [  216.472371] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
Jun 30 16:48:59 rockforrest kernel: [  216.486454] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun 30 16:48:59 rockforrest kernel: [  216.486637] ieee80211 phy2: >Selected rate control algorithm 'rtl_rc'
Jun 30 16:48:59 rockforrest kernel: [  216.488029] rtlwifi: wireless switch is on
Jun 30 16:48:59 rockforrest NetworkManager[763]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/ieee80211/phy2/rfkill2) (driver (unknown))
Jun 30 16:48:59 rockforrest NetworkManager[763]: <info> (wlan0): using nl80211 for WiFi device control
Jun 30 16:48:59 rockforrest NetworkManager[763]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 5)
Jun 30 16:48:59 rockforrest kernel: [  216.517596] rtl8192cu: MAC auto ON okay!
Jun 30 16:48:59 rockforrest kernel: [  216.552310] rtl8192cu: Tx queue select: 0x05

```

---

### Post by chili555 on 2013-07-01
> [  116.101073] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! This reminded me of another case I worked on where the answer was to update the driver. I'd like to try one step first. I notice there is a lot of activity setting and re-setting the world regulatory domain and it never comes up with a code. Let's try to set one and see if it helps, hurts or does nothing:```
sudo iw reg set US
```If your country is not US, substitute the two-character code from here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Does it help? If not, please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Reboot and tell us if there is any improvement.

---

### Post by neutronforrest on 2013-07-01
Dear Chili555,

I really appreciate your help but nothing works.  I have tried 12.10 and 13.04 with no difference.  I have also tried your suggestions and it never improved.  I have been unable to install the driver.  I keep getting an error when I try to compile the driver.  I think I am going to return this item.  

Do you have a suggestion for a USB WiFi adapter for Ubuntu 12.10.  I plan to make this a desktop with WiFi in another room of the house with no hard line.  The specs are,

AS Rock mobo with the AMD e-350.

I welcome your suggestions...Chad

---

### Post by kurt18947 on 2013-07-02
If you're buying a new device, I have a couple suggestions.  I'm just using wireless for web surfing so ultimate speed isn't important to me -- my broadband connection is only so fast so N150 speed is fine for me.  I have two devices that 'just work'.  Trendnet TEW-649UB uses a Realtek RTL-8192SU chipset.  This one 'feels' a little faster.  The second adapter that 'just works' is a Netgear WNA1100 using an Atheros chipset.

A potential fly-in-the-ointment is manufacturers sometimes change the chipset in a model without changing the model#.  For example,  this seems to have happened with Dlink DWA-131 some time ago.  The original used the RealTek 8192SU chipset and worked great in linux.  Current production uses a different RealTek chipset and doesn't work well if at all.  The only way to tell the difference is to look at the label on the device. It may say something like ver.2 or ver.B or similar.   Of course you have to buy and open the device to read the label.  Grrrr..........

---

### Post by chili555 on 2013-07-02
Have you tried turning off N speeds in the router to see if it helps?

---

### Post by neutronforrest on 2013-07-06
Dear Forum,

Thank you Chili555, I tried turning off the N signal and still just keeps dropping.  I returned the item and now searching for a new adapter.  I am hoping someone can suggest a wireless adapter that works with Ubuntu and my MOBO,

My motherboard is,
[SIZE=3][FONT=arial]
[/FONT][/SIZE]**[SIZE=3][FONT=arial]ASRock E350M1 AMD E-350 APU (1.6GHz, Dual-Core) AMD A50M Hudson M1 Mini ITX Motherboard/CPU Combo[/FONT][/SIZE]**


Is there a way to know if this motherboard works with certain wifi-adapters.  My goal is N-300 adapter since I want to make this for streaming movies and such.
Thanks...Chad

---

