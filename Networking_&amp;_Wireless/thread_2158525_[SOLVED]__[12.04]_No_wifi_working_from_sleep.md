---
title: "[SOLVED]  [12.04] No wifi working from sleep"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2013-06-29
Hello 
I've an old laptop (Lenovo 3000N200) which was fitted with an Intel 5100 wifi card. It ran trouble free for years.
Lastly, the wifi card began to make huge transmitting errors and caught one packet on 1000.
As I was unable to get my hand on a mini PCI card that fit inside the laptop and runs well, I switched back to the original Intel PRO/Wireless 3945ABG it has when it left the factory.
Transmission problem are settled. Fine. 
Now, as usual, the wifi link start on boot (it is set up in /etc/network/interfaces) and runs fine. But when I get back from sleep, the iwconfig shows : 
```

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Good ESSID OF the Wifi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC of the WIFI router>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0

eth0      no wireless extensions.


```
The ifconfig shows :
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:09:3f:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:19 

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:09:3f:5f  
          inet adr:169.254.4.126  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:19 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:265 erreurs:0 :0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:26713 (26.7 KB) Octets transmis:26713 (26.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:a4:6f:74  
          inet adr:192.168.0.2  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::21b:77ff:fea4:6f74/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:40109 erreurs:0 :0 overruns:0 frame:0
          TX packets:38010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:37598877 (37.5 MB) Octets transmis:8313314 (8.3 MB)

```
but when I try to ping the default router :
```
root@biniou:~# ping 192.168.0.254
PING 192.168.0.254 (192.168.0.254) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=5 Destination Host Unreachable
From 192.168.0.2 icmp_seq=7 Destination Host Unreachable
From 192.168.0.2 icmp_seq=8 Destination Host Unreachable
From 192.168.0.2 icmp_seq=11 Destination Host Unreachable
^C
--- 192.168.0.254 ping statistics ---
14 packets transmitted, 0 received, +7 errors, 100% packet loss, time 13071ms


```
I get this on syslog :
```

Jun 29 12:20:25 biniou dhclient: No DHCPOFFERS received.
Jun 29 12:20:25 biniou dhclient: No working leases in persistent database - sleeping.

``` 
which puzzle me because the ifconfig shows that the card has an IP address set up... 
And the wifi LED on the laptop flashes like hell. 
The only way I've to make it work is to do :
```

sudo ifdown wlan0
sudo ifup wlan0

```
Could you help me find what is wrong and how I can make it work again ? 
Many thanks in advance for your help !

---

### Post by chili555 on 2013-06-29
Please put the laptop to sleep, refill the coffee cup and awake. Before you do anything, please run and post:```
lsmod | grep iwl
```Is the driver iwl3945 loaded? All it dependencies, too?> $ modinfo iwl3945
filename:       /lib/modules/3.8.0-25-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     3E1175EF45527087DD84DA7
<snip>
depends:       [COLOR="#FF0000"] iwlegacy,cfg80211,mac80211[/COLOR]
<snip>
Is Network Manager removed?

---

### Post by georgesgiralt on 2013-06-29
Hello !
Thanks for your answer.
Here is what I get BEFORE sleep :
```

root@biniou:~# lsmod | grep iwl
iwl3945                79087  0 
iwl_legacy             83098  1 iwl3945
mac80211              506862  2 iwl3945,iwl_legacy
cfg80211              205774  3 iwl3945,iwl_legacy,mac80211
root@biniou:~# service network-manager status
network-manager stop/waiting

```
Everything is working !  ;-)  Nice !
And after sleep :
```

root@biniou:~# lsmod | grep iwl
iwl3945                79087  0 
iwl_legacy             83098  1 iwl3945
mac80211              506862  2 iwl3945,iwl_legacy
cfg80211              205774  3 iwl3945,iwl_legacy,mac80211
root@biniou:~# 

```
As per NetworkManager : 
```

root@biniou:~# service network-manager status
network-manager stop/waiting
root@biniou:~# 

```
The dhclient info in syslog may pertain to eth0 as it is "auto" in /etc/network/interfaces.
Thanks for your help !

---

### Post by chili555 on 2013-06-29
Network Manager and /etc/network/interfaces are designed to work and play well together. They often don't, as i suspect here:> root@biniou:~# service network-manager status
network-manager [COLOR="#FF0000"]stop/waiting[/COLOR]
root@biniou:~#I strongly suggest you pick one or the other and abandon the other. If this is a stay at home computer, you can probably safely remove NM, as I have on this very laptop. If you need to connect down at the internet cafe, I'd recommend commenting out all the entries in /etc/network/interfaces except loopback and rely on NM. 

Thoughts?

---

### Post by georgesgiralt on 2013-06-29
Well, 
It has worked like that for years, and NM is disabled and not running. So I wonder why it should play a part here ?
I need Nm when I travel with the computer and have to choose from various network. Once I've set up my mind, and if I have to stay a while on one place, I revert to a static interface definition and not on NM.  
Tomorrow I'll try to comment out all eth0 lines in interfaces and see what I get. 
If nothing changes I'll follow your advice to remove NM and see where I go.

---

### Post by chili555 on 2013-06-29
> Tomorrow I'll try to comment out all eth0 lines in interfaces and see what I get. I would certainly comment out eth0; however, isn't wireless what you are having trouble with? It might be enough to comment out 'auto eth0.' I'd certainly start there first.

---

### Post by georgesgiralt on 2013-06-29
Yess my trouble is with wireless. the commenting out eth0 part was to try to understand why dhclient complains in syslog. In order to ascertain the fact that the dhclient messages are from an unplugged eth0 or a non working wlan0 ....

---

### Post by chili555 on 2013-06-29
> **georgesgiralt said:**
> Yess my trouble is with wireless. the commenting out eth0 part was to try to understand why dhclient complains in syslog. In order to ascertain the fact that the dhclient messages are from an unplugged eth0 or a non working wlan0 ....With auto eth0 declared and no connection, I believe the system will stumble to enable a non-enable-able (if that's a word!) interface. I suggest you comment out 'auto eth0' and see if the behavior improves.

---

### Post by georgesgiralt on 2013-06-30
I have commented out all entries except loopback and wifi interface.
Reboot, then worked a bit. I will put it to sleep and see what goes when I come back from shopping in a couple of hours.

---

### Post by georgesgiralt on 2013-06-30
So, back from sleep. 
No network connection as "usual".... Iwconfig; ifconfig say I'm OK but ping still complain "host unreachable".
No more dhclient messages in syslog. 
Actually no messages pertaining to network in syslog at all.
Puzzled, baffled, disappointed.....

---

### Post by chili555 on 2013-06-30
Here is a technique that sometimes helps: [http://ubuntuforums.org/showthread.php?t=1840116&page=2&p=11694361#post11694361](http://ubuntuforums.org/showthread.php?t=1840116&page=2&p=11694361#post11694361)

Of course, you'll substitute iwl3945.

---

### Post by georgesgiralt on 2013-07-01
So, I've created  /etc/pm/config.d/config with the "suspend" stanza. 
Totally no joy !
This time, no LED lit after awakening the laptop, iwconfig says I'm not associated anymore and ifconfig shows no IP address... 
So I needed the couple ifdwon/ifup to get back on business.
B.......

---

### Post by georgesgiralt on 2013-07-01
Hummm 
Today, I came home this mid day to gather some papers I forgot at home. 
I opened the laptop and was forced to ifdow/ifup the interface to make it work. I closed the laptop shut to go to work. It went into sleep mode. 
Now, after work, I opened the laptop and was surprised to see the Wifi led to blink ! 
And astonished to get my mails downloaded without any intervention !
So I've a problem going back from sleep but I wonder if it is not caused by anything else than the wifi interface/software.... 
I'm more and more puzzled.... 
P.S. : this very same laptop with this very same wifi card has been used a couple of years under Ubuntu (not the same release) without any problem. It came back from sleep without any problem. OK, at that time I used a Netgear 54 Mb/s wifi router instead of the set top box of my ISP (with 300 Mb/s wifi) I have now, but....

---

### Post by chili555 on 2013-07-01
I am more than a little interested in this case because I have a Lenovo laptop with an Intel 3945 wireless card that resumes from sleep perfectly. It does, however, currently run 12.10. Another laptop runs 13.04 but uses an Intel 6200. One runs Network Manager; one does not.

I am still suspicious of Network Manager. I'd like to see what, if anything, the logs say:```
cat /var/log/syslog | grep etwork
```syslog fills up, archives and starts over from time to time, so let's look at the previous log as well:```
cat /var/log/syslog.1 | grep etwork
```The next time you resume from sleep, let's see what the last several lines of the log is, whether wireless returns or not:```
cat /var/log/syslog | tail -n25
```We hope there may be some clue as to what the fault is.

---

### Post by georgesgiralt on 2013-07-01
Hello !
Tomorrow I'll try it without the config.d file just to see how it behave. 
I more and more think that we are chasing the wrong dog here. 
It worked twice this evening and none yesterday... As it's not Microsoft code, should be more consistent... 
See the requested information : 
here we are : cat /var/log/syslog | grep etwork
```
Jul  1 07:18:04 biniou dhclient: receive_packet failed on wlan0: Network is down
Jul  1 12:19:27 biniou kernel: [31820.838472] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  1 12:20:28 biniou dhclient: send_packet: Network is unreachable
Jul  1 12:53:20 biniou dhclient: receive_packet failed on wlan0: Network is down
Jul  1 19:17:24 biniou kernel: [33857.595299] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  1 21:06:30 biniou dhclient: receive_packet failed on wlan0: Network is down
Jul  1 23:13:06 biniou kernel: [40406.997400] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s

```
next : cat /var/log/syslog.1 | grep etwork
```

root@biniou:/etc/pm/config.d# cat /var/log/syslog.1 | grep etwork
Jun 30 17:29:23 biniou dhclient: receive_packet failed on wlan0: Network is down
Jun 30 18:42:47 biniou kernel: [19167.710370] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jun 30 18:55:29 biniou dhclient: receive_packet failed on wlan0: Network is down
Jun 30 20:55:08 biniou kernel: [19933.005180] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jun 30 22:58:45 biniou dhclient: receive_packet failed on wlan0: Network is down
Jul  1 06:03:44 biniou kernel: [27355.088246] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  1 06:04:58 biniou kernel: [27429.653873] init: network-interface (wlan0) pre-start process (9274) killed by TERM signal
Jul  1 06:04:58 biniou dhclient: send_packet: Network is unreachable
root@biniou:/etc/pm/config.d# 

```
and last : cat /var/log/syslog | tail -n100
```
Jul  1 23:13:05 biniou kernel: [40404.428365] usb 5-1: reset low-speed USB device number 2 using uhci_hcd
Jul  1 23:13:05 biniou kernel: [40404.735409] PM: resume of drv: dev:ep_00 complete after 1310.357 msecs
Jul  1 23:13:05 biniou kernel: [40404.735434] PM: resume of drv:usbhid dev:5-1:1.0 complete after 1310.431 msecs
Jul  1 23:13:05 biniou kernel: [40404.735468] PM: resume of drv: dev:ep_81 complete after 1310.439 msecs
Jul  1 23:13:05 biniou kernel: [40404.828144] usb 6-2: reset full-speed USB device number 2 using uhci_hcd
Jul  1 23:13:05 biniou kernel: [40404.974516] btusb 6-2:1.0: no reset_resume for driver btusb?
Jul  1 23:13:05 biniou kernel: [40404.974521] btusb 6-2:1.1: no reset_resume for driver btusb?
Jul  1 23:13:05 biniou kernel: [40405.224340] PM: resume of drv:usb dev:6-2:1.0 complete after 1799.242 msecs
Jul  1 23:13:05 biniou kernel: [40405.224352] PM: resume of drv: dev:ep_00 complete after 1798.992 msecs
Jul  1 23:13:05 biniou kernel: [40405.224358] PM: resume of drv:usb dev:6-2:1.3 complete after 1799.035 msecs
Jul  1 23:13:05 biniou kernel: [40405.224362] PM: resume of drv:usb dev:6-2:1.1 complete after 1799.173 msecs
Jul  1 23:13:05 biniou kernel: [40405.224365] PM: resume of drv:usb dev:6-2:1.2 complete after 1799.110 msecs
Jul  1 23:13:05 biniou kernel: [40405.224370] PM: resume of drv: dev:ep_81 complete after 1799.252 msecs
Jul  1 23:13:05 biniou kernel: [40405.224374] PM: resume of drv: dev:ep_84 complete after 1799.096 msecs
Jul  1 23:13:05 biniou kernel: [40405.224377] PM: resume of drv: dev:ep_82 complete after 1799.234 msecs
Jul  1 23:13:05 biniou kernel: [40405.224380] PM: resume of drv: dev:ep_04 complete after 1799.080 msecs
Jul  1 23:13:05 biniou kernel: [40405.224382] PM: resume of drv: dev:ep_02 complete after 1799.218 msecs
Jul  1 23:13:05 biniou kernel: [40405.224390] PM: resume of drv: dev:ep_03 complete after 1799.160 msecs
Jul  1 23:13:05 biniou kernel: [40405.224394] PM: resume of drv: dev:ep_83 complete after 1799.182 msecs
Jul  1 23:13:05 biniou kernel: [40406.712111] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  1 23:13:05 biniou kernel: [40406.713003] ata1.00: unexpected _GTF length (8)
Jul  1 23:13:05 biniou kernel: [40406.716895] ata1.00: unexpected _GTF length (8)
Jul  1 23:13:05 biniou kernel: [40406.717302] ata1.00: configured for UDMA/133
Jul  1 23:13:05 biniou kernel: [40406.748487] PM: resume of drv:sd dev:0:0:0:0 complete after 3323.818 msecs
Jul  1 23:13:05 biniou kernel: [40406.748502] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 3060.111 msecs
Jul  1 23:13:05 biniou kernel: [40406.748527] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 3323.812 msecs
Jul  1 23:13:05 biniou kernel: [40406.748831] PM: resume of devices complete after 3331.215 msecs
Jul  1 23:13:05 biniou kernel: [40406.749194] PM: resume devices took 3.332 seconds
Jul  1 23:13:05 biniou kernel: [40406.749225] PM: Finishing wakeup.
Jul  1 23:13:05 biniou bluetoothd[507]: HCI dev 0 down
Jul  1 23:13:05 biniou bluetoothd[507]: Adapter /org/bluez/507/hci0 has been disabled
Jul  1 23:13:05 biniou bluetoothd[507]: HCI dev 0 unregistered
Jul  1 23:13:05 biniou bluetoothd[507]: Stopping hci0 event socket
Jul  1 23:13:05 biniou bluetoothd[507]: Unregister path: /org/bluez/507/hci0
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/HFPAG
Jul  1 23:13:05 biniou bluetoothd[507]: HCI dev 0 registered
Jul  1 23:13:05 biniou bluetoothd[507]: Listening for HCI events on hci0
Jul  1 23:13:05 biniou kernel: [40406.749226] Restarting tasks ... done.
Jul  1 23:13:05 biniou bluetoothd[507]: HCI dev 0 up
Jul  1 23:13:05 biniou bluetoothd[507]: input-headset driver probe failed for device 30:17:C8:11:5A:15
Jul  1 23:13:05 biniou bluetoothd[507]: input-headset driver probe failed for device 84:00:D2:F4:66:A7
Jul  1 23:13:05 biniou bluetoothd[507]: Adapter /org/bluez/507/hci0 has been enabled
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/HFPAG
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jul  1 23:13:05 biniou bluetoothd[507]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jul  1 23:13:05 biniou kernel: [40406.884232] video LNXVIDEO:01: Restoring backlight state
Jul  1 23:13:05 biniou acpid: client 1348[0:0] has disconnected
Jul  1 23:13:05 biniou acpid: client connected from 1348[0:0]
Jul  1 23:13:05 biniou acpid: 1 client rule loaded
Jul  1 23:13:06 biniou anacron[13441]: Anacron 2.3 started on 2013-07-01
Jul  1 23:13:06 biniou anacron[13441]: Normal exit (0 jobs run)
Jul  1 23:13:06 biniou kernel: [40406.975102] cfg80211: Calling CRDA to update world regulatory domain
Jul  1 23:13:06 biniou kernel: [40406.993144] cfg80211: World regulatory domain updated:
Jul  1 23:13:06 biniou kernel: [40406.993148] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  1 23:13:06 biniou kernel: [40406.993151] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  1 23:13:06 biniou kernel: [40406.993153] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  1 23:13:06 biniou kernel: [40406.993156] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  1 23:13:06 biniou kernel: [40406.993158] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  1 23:13:06 biniou kernel: [40406.993161] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  1 23:13:06 biniou kernel: [40406.997400] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  1 23:13:06 biniou kernel: [40406.997403] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Jul  1 23:13:06 biniou kernel: [40406.997494] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  1 23:13:06 biniou kernel: [40406.997517] iwl3945 0000:04:00.0: setting latency timer to 64
Jul  1 23:13:06 biniou kernel: [40407.051326] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jul  1 23:13:06 biniou kernel: [40407.051329] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Jul  1 23:13:06 biniou kernel: [40407.051476] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
Jul  1 23:13:06 biniou kernel: [40407.051620] Registered led device: phy0-led
Jul  1 23:13:06 biniou kernel: [40407.051647] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jul  1 23:13:06 biniou kernel: [40407.051751] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Jul  1 23:13:06 biniou wpa_supplicant[12150]: Failed to initiate AP scan.
Jul  1 23:13:06 biniou kernel: [40407.079290] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Jul  1 23:13:06 biniou wpa_supplicant[12150]: CTRL-EVENT-TERMINATING - signal 15 received
Jul  1 23:13:06 biniou kernel: [40407.157665] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  1 23:13:06 biniou wpa_supplicant[13485]: Failed to initiate AP scan.
Jul  1 23:13:06 biniou kernel: [40407.337303] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  1 23:13:06 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  1 23:13:06 biniou anacron[13634]: Anacron 2.3 started on 2013-07-01
Jul  1 23:13:06 biniou anacron[13634]: Normal exit (0 jobs run)
Jul  1 23:13:08 biniou kernel: [40409.020157] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
Jul  1 23:13:08 biniou kernel: [40409.406067] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Jul  1 23:13:09 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  1 23:13:10 biniou wpa_supplicant[13485]: Trying to authenticate with 00:24:d4:66:6b:ac (SSID='FreeboxDeGeorges' freq=2412 MHz)
Jul  1 23:13:10 biniou kernel: [40411.830870] wlan0: authenticate with 00:24:d4:66:6b:ac (try 1)
Jul  1 23:13:10 biniou wpa_supplicant[13485]: Trying to associate with 00:24:d4:66:6b:ac (SSID='FreeboxDeGeorges' freq=2412 MHz)
Jul  1 23:13:10 biniou kernel: [40411.832711] wlan0: authenticated
Jul  1 23:13:10 biniou kernel: [40411.832904] wlan0: associate with 00:24:d4:66:6b:ac (try 1)
Jul  1 23:13:10 biniou kernel: [40411.836951] wlan0: RX AssocResp from 00:24:d4:66:6b:ac (capab=0x411 status=0 aid=1)
Jul  1 23:13:10 biniou kernel: [40411.836960] wlan0: associated
Jul  1 23:13:10 biniou wpa_supplicant[13485]: Associated with 00:24:d4:66:6b:ac
Jul  1 23:13:10 biniou kernel: [40411.841638] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  1 23:13:10 biniou wpa_supplicant[13485]: WPA: Key negotiation completed with 00:24:d4:66:6b:ac [PTK=CCMP GTK=TKIP]
Jul  1 23:13:10 biniou wpa_supplicant[13485]: CTRL-EVENT-CONNECTED - Connection to 00:24:d4:66:6b:ac completed (auth) [id=0 id_str=]
Jul  1 23:13:12 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  1 23:13:12 biniou dhclient: DHCPACK of 192.168.0.2 from 192.168.0.254
Jul  1 23:13:12 biniou dhclient: bound to 192.168.0.2 -- renewal in 19411 seconds.
Jul  1 23:13:22 biniou ntpdate[13804]: step time server 91.189.89.199 offset 1.044173 sec
Jul  1 23:13:22 biniou kernel: [40422.848049] wlan0: no IPv6 routers present
Jul  1 23:17:01 biniou CRON[13859]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
root@biniou:/etc/pm/config.d# 

```

---

### Post by chili555 on 2013-07-02
> I revert to a static interface definition and not on NM. However:> Jul  1 23:13:12 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  1 23:13:12 biniou dhclient: DHCPACK of 192.168.0.2 from 192.168.0.254
Jul  1 23:13:12 biniou dhclient: bound to 192.168.0.2 -- renewal in 19411 seconds.
Jul  1 23:13:22 biniou ntpdate[13804]: step time server 91.189.89.199 offset 1.044173 sec:confused: Is it perhaps only the *static* configuration that won't resume correctly? Does the DHCP resume? 

I am troubled by this and I'm Googling:> dhclient: receive_packet failed on wlan0: Network is downThat may be a natural consequence of sleep.

It all looks pretty solid.

---

### Post by georgesgiralt on 2013-07-02
Hello !
This morning (very early), I booted the laptop without the config file in /etc/pm/config.d. Then  after some time I put it to sleep and a while after, awakened it. No wifi. Zip.
So I put back the /etc/pm/config.d/config file and restarted the whole ....and then put it to sleep.
At noon, I awakened it, got a nice and clean wifi connection. Then I went back to work, with the laptop asleep. 
Now I'm home and the wifi is up and running. It start on awakening of the laptop. 
So your fix seems to work fine. 
The DHCP errors arose when the wifi link is not functional. Or when the wifi led blinks furiously but without any link set (iwconfig and ifconfig says that the link is up and set but.... ).
With the /etc/pm/config.d/config file with the SUSPEND_MODULE stanza everything is like the last syslog I sent. The dhcp client send a request and got it's answer right away. (I fix all the IP addresses in the set top box DHCP server and the MAC filtering security also).
So Maybe I should turn the whole subject as solved ! 
Thanks for your help and advices !

---

### Post by chili555 on 2013-07-02
> So Maybe I should turn the whole subject as solved ! Awesome!

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by georgesgiralt on 2013-07-03
Well don't know if it is totally solved. 
Today, back from work. I open the laptop, the LED does not light. lsmod | grep 3945 shows all the modules are loaded. Ifconfig and iwconfig are a bit strange (iwconfig says it is associated with no access point...)
sudo ifdown wlan0 works but sudo ifup wlan0 fails "wpa_supplicant failed to start". 
And :
```

georges@biniou:~$ ps ax | grep supplicant
 4270 ?        Ss     0:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant

```

So I killed it 
```

georges@biniou:~$ sudo  kill -TERM 4270
georges@biniou:~$ ps ax | grep supplicant
 5801 pts/0    S+     0:00 grep supplicant
georges@biniou:~$ sudo ifup wlan0
ssh stop/waiting
ssh start/running, process 5930
georges@biniou:~$

```
There is still a Gremlin left somewhere ;-)

---

### Post by georgesgiralt on 2013-07-04
Well don't know if it is totally solved. 
Today, back from work. I open the laptop, the LED does not light. lsmod | grep 3945 shows all the modules are loaded. Ifconfig and iwconfig are a bit strange (iwconfig says it is associated with no access point...)
sudo ifdown wlan0 works but sudo ifup wlan0 fails "wpa_supplicant failed to start". 
And :
```

georges@biniou:~$ ps ax | grep supplicant
 4270 ?        Ss     0:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant

```

So I killed it 
```

georges@biniou:~$ sudo  kill -TERM 4270
georges@biniou:~$ ps ax | grep supplicant
 5801 pts/0    S+     0:00 grep supplicant
georges@biniou:~$ sudo ifup wlan0
ssh stop/waiting
ssh start/running, process 5930
georges@biniou:~$

```
There is still a Gremlin left somewhere ;-)

---

### Post by chili555 on 2013-07-05
How is wpa_supplicant invoked? In /etc/network/interfaces? [http://static.mini-itx.com/projects/xbmc-ion/images/xbmc-ion-0071L.jpg](http://static.mini-itx.com/projects/xbmc-ion/images/xbmc-ion-0071L.jpg)

Or the easy way? [http://learn.adafruit.com/system/assets/assets/000/002/929/medium800/occ_2.png?1355172069](http://learn.adafruit.com/system/assets/assets/000/002/929/medium800/occ_2.png?1355172069)  <--even there, I am suspicious of the 'hotplug' declaration.

Do you mind if we have a peek at your redacted /etc/network/interfaces?

---

### Post by georgesgiralt on 2013-07-06
Not at all. Here we are :
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
#carte wifi
#iface wlan0 inet dhcp
#	wpa-ssid troutpool
#	wpa-key-mgmt WPA-PSK
#	wpa-psk	 "susan of troutpool"

auto wlan0
iface wlan0 inet dhcp
        wpa-ssid   FreeboxDeGeorges
        wpa-key-mgmt WPA-PSK
        wpa-psk "My-big-key-very complicated-and hard-to-guess-and difficult-to-type-on-a-smartphone"

#clef

#        wpa-psk "Key for the old Netgear router which is stored nowhere else"

```
The wpa supplicant is not started directly here. 
I can't remember how and why I set up the Wifi this way (only that I wanted/needed to get rid of NetworkManager)
Thanks for your help !

---

### Post by chili555 on 2013-07-06
> only that I wanted/needed to get rid of NetworkManagerOld skool! My main laptop is free of NM also. I hear you.

This may have nothing to do with anything, but my interfaces file lacks the WPA-PSK declaration and, also with an Intel chip, resumes perfectly. Would you humor an old man and try:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
#carte wifi
#iface wlan0 inet dhcp
#	wpa-ssid troutpool
#	wpa-key-mgmt WPA-PSK
#	wpa-psk	 "susan of troutpool"

auto wlan0
iface wlan0 inet dhcp
wpa-ssid   FreeboxDeGeorges
wpa-psk "My-big-key-very complicated-and hard-to-guess-and difficult-to-type-on-a-smartphone"

```Then get the system to re-read and use the change:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```I added the '-v' for verbose so you can see if there are any obvious glitches.

I certainly think these two might be related:> wpa-key-mgmt WPA-PSK

....

sudo ifup wlan0 fails "wpa_supplicant failed to start". ...but let's see.

---

### Post by georgesgiralt on 2013-07-06
Here we are :
```

georges@biniou:~$ sudo view /etc/network/interfaces
[sudo] password for georges: 
georges@biniou:~$ sudo ifdown wlan0 && sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "FreeboxDeGeorges" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases -1 wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 6964
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
georges@biniou:~$ 

```
We will have to wait some time for the sleep/awakening part ... 
'tell you once done !

---

### Post by georgesgiralt on 2013-07-07
Hello !
Nice try ! but ....
First awakening went well. After a couple of seconds, the Wifi LED came on, blinked furious and I was connected. Fine.
Then I put it back to sleep and some hours later, no Wifi. 
In syslog I get :
```

Jul  7 08:01:48 biniou kernel: [28070.799224] cfg80211: Calling CRDA to update world regulatory domain
Jul  7 08:01:48 biniou kernel: [28070.815260] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  7 08:01:48 biniou kernel: [28070.815264] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Jul  7 08:01:48 biniou kernel: [28070.815344] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  7 08:01:48 biniou kernel: [28070.815364] iwl3945 0000:04:00.0: setting latency timer to 64
Jul  7 08:01:48 biniou kernel: [28070.852734] cfg80211: World regulatory domain updated:
Jul  7 08:01:48 biniou kernel: [28070.852737] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  7 08:01:48 biniou kernel: [28070.852740] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 08:01:48 biniou kernel: [28070.852743] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  7 08:01:48 biniou kernel: [28070.852745] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  7 08:01:48 biniou kernel: [28070.852748] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 08:01:48 biniou kernel: [28070.852750] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 08:01:48 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 08:01:48 biniou kernel: [28070.869140] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jul  7 08:01:48 biniou kernel: [28070.869144] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Jul  7 08:01:48 biniou kernel: [28070.869300] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
Jul  7 08:01:48 biniou kernel: [28070.869500] Registered led device: phy0-led
Jul  7 08:01:48 biniou kernel: [28070.869530] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jul  7 08:01:48 biniou kernel: [28070.869655] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Jul  7 08:01:48 biniou kernel: [28070.899954] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Jul  7 08:01:48 biniou kernel: [28070.970741] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  7 08:01:48 biniou wpa_supplicant[11419]: ctrl_iface exists and seems to be in use - cannot override it
Jul  7 08:01:48 biniou wpa_supplicant[11419]: Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Jul  7 08:01:48 biniou wpa_supplicant[11419]: Failed to initialize control interface '/var/run/wpa_supplicant'.#012You may have another wpa_supplicant process already running or the file was#012left by an unclean termination of wpa_supplicant in which case you will need#012to manually remove this file before starting wpa_supplicant again.
Jul  7 08:01:48 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 08:01:48 biniou kernel: [28071.077376] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  7 08:01:48 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  7 08:01:49 biniou anacron[11570]: Anacron 2.3 started on 2013-07-07
Jul  7 08:01:49 biniou anacron[11570]: Normal exit (0 jobs run)
Jul  7 08:01:49 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 08:01:51  wpa_supplicant[10066]: last message repeated 2 times
Jul  7 08:01:51 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  7 08:01:52 biniou wpa_supplicant[10066]: Failed to initiate AP scan.

```
The "Failed to initiate AP scan" is repeated ad libitum.... 
So I was forced to do :
```

georges@biniou:~$ sudo rm /var/run/wpa_supplicant/wlan0
georges@biniou:~$ sudo ifdown wlan0
RTNETLINK answers: No such process
georges@biniou:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "FreeboxDeGeorges" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases -1 wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 11949
run-parts: executing /etc/network/if-up.d/postfix
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
georges@biniou:~$ 

```
Still not found what's wrong here ! 
I wonder why the socket lay back and is not removed ? (or changed on restart) ?
Have a nice Sunday !

---

### Post by georgesgiralt on 2013-07-07
Hello !
Maybe did I got something.
Awakening it, no wifi.
But I've got this :
```

georges@biniou:~$ tail -100 /var/log/syslog
Jul  7 11:16:47 biniou bluetoothd[933]: input-headset driver probe failed for device 30:17:C8:11:5A:15
Jul  7 11:16:47 biniou acpid: client 1413[0:0] has disconnected
Jul  7 11:16:47 biniou acpid: client connected from 1413[0:0]
Jul  7 11:16:47 biniou acpid: 1 client rule loaded
Jul  7 11:16:47 biniou bluetoothd[933]: input-headset driver probe failed for device 84:00:D2:F4:66:A7
Jul  7 11:16:47 biniou bluetoothd[933]: Adapter /org/bluez/933/hci0 has been enabled
Jul  7 11:16:47 biniou bluetoothd[933]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/HFPAG
Jul  7 11:16:47 biniou bluetoothd[933]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jul  7 11:16:47 biniou bluetoothd[933]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jul  7 11:16:48 biniou anacron[12792]: Anacron 2.3 started on 2013-07-07
Jul  7 11:16:48 biniou anacron[12792]: Normal exit (0 jobs run)
Jul  7 11:16:48 biniou kernel: [33320.640871] cfg80211: Calling CRDA to update world regulatory domain
Jul  7 11:16:48 biniou kernel: [33320.652534] cfg80211: World regulatory domain updated:
Jul  7 11:16:48 biniou kernel: [33320.652539] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  7 11:16:48 biniou kernel: [33320.652542] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 11:16:48 biniou kernel: [33320.652544] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  7 11:16:48 biniou kernel: [33320.652547] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  7 11:16:48 biniou kernel: [33320.652550] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 11:16:48 biniou kernel: [33320.652552] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  7 11:16:48 biniou kernel: [33320.662093] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  7 11:16:48 biniou kernel: [33320.662097] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Jul  7 11:16:48 biniou kernel: [33320.662184] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  7 11:16:48 biniou kernel: [33320.662204] iwl3945 0000:04:00.0: setting latency timer to 64
Jul  7 11:16:48 biniou kernel: [33320.715804] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jul  7 11:16:48 biniou kernel: [33320.715809] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Jul  7 11:16:48 biniou kernel: [33320.715960] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
Jul  7 11:16:48 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:48 biniou kernel: [33320.716295] Registered led device: phy0-led
Jul  7 11:16:48 biniou kernel: [33320.716327] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jul  7 11:16:48 biniou kernel: [33320.716508] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Jul  7 11:16:48 biniou kernel: [33320.767556] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Jul  7 11:16:48 biniou kernel: [33320.838666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  7 11:16:48 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:48 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:49 biniou anacron[12954]: Anacron 2.3 started on 2013-07-07
Jul  7 11:16:49 biniou anacron[12954]: Normal exit (0 jobs run)
Jul  7 11:16:49 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:49 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:50 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:50 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:51 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:51 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:52 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:52 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:53 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:53 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:54 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:54 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:55 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:55 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:56 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:56 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:57 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:57 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:58 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:58 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:16:59 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:16:59 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:00 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:00 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:01 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:01 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:02 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:02 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:03 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:03 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:04 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:04 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:05 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:05 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:06 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:06 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:07 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:07 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:08 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:08 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:09 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:09 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:10 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:10 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:11 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:11 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:12 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:12 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:13 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:13 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:14 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:14 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:15 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:15 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:16 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:16 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:17 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:17 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:18 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:18 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:19 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:19 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
Jul  7 11:17:20 biniou wpa_supplicant[11830]: Failed to initiate AP scan.
Jul  7 11:17:20 biniou wpa_supplicant[10066]: Failed to initiate AP scan.
georges@biniou:~$ ps ax | grep wpa
10066 ?        Ss     0:01 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
11830 ?        Ss     0:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
13077 pts/1    S+     0:00 grep wpa
georges@biniou:~$ sudo kill -TERM 10066
[sudo] password for georges: 
georges@biniou:~$ ps ax | grep wpa
11830 ?        Ss     0:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
13083 pts/1    S+     0:00 grep wpa
georges@biniou:~$ sudo kill -TERM 11830
georges@biniou:~$ ll /var/run/wpa_supplicant*
ls: impossible d'accéder à /var/run/wpa_supplicant*: Aucun fichier ou dossier de ce type
georges@biniou:~$ sudo ifdown wlan0
RTNETLINK answers: No such process
georges@biniou:~$ sudo ifup  wlan0
ssh stop/waiting
ssh start/running, process 13270
georges@biniou:~$ 

```
As you can see, I had two wpa_supplicant processes running. 
So maybe the problem lies on the fact that the awakening process sometimes tries to start another connection from scratch but the previous connection processes are restarted (as they where put to sleep and awakened)...
Am I right ? Is this possible ?

---

### Post by chili555 on 2013-07-07
> As you can see, I had two wpa_supplicant processes running.
So maybe the problem lies on the fact that the awakening process sometimes tries to start another connection from scratch but the previous connection processes are restarted (as they where put to sleep and awakened)...
Am I right ? Is this possible ? An entirely credible theory. Have you created your own custom /etc/wpa_supplicant.conf? I don't have or need one.

You might also try adding to your interfaces file:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
#carte wifi
#iface wlan0 inet dhcp
#	wpa-ssid troutpool
#	wpa-key-mgmt WPA-PSK
#	wpa-psk	 "susan of troutpool"

auto wlan0
iface wlan0 inet dhcp
wpa-ssid   FreeboxDeGeorges
wpa-psk "My-big-key-very complicated-and hard-to-guess-and difficult-to-type-on-a-smartphone"
post-down killall -q wpa_supplicant
```A very sticky problem you have here. The moderators never let me get the easy questions!

---

### Post by georgesgiralt on 2013-07-07
No, I don't have any  /etc/wpa_supplicant.conf file. 
I'll try the modifications to the interface file and let you know. It could be in a couple of days (this little b... likes to show off by letting things run fine at first so we think it's fixed ! )

---

### Post by nathanservicesinc on 2013-07-07
I wonder if Linux 12.04 has a --->IPCONFIG  /flush<----command that will allow you to start all over;
or maybe there's a --->IPCONFIG  /release<---command in the sudo command prompt that you can use?  This is a question not really an answer.....???

---

### Post by georgesgiralt on 2013-07-07
No. No ipconfig nor IPCONFIG.

---

### Post by chili555 on 2013-07-07
May we see:```
cat /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
```We want to know if you actually have the file and if it is readable and executable appropriately:```
ls -al /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
```I saw this: [http://forums.gentoo.org/viewtopic-t-824414-start-0.html](http://forums.gentoo.org/viewtopic-t-824414-start-0.html) We may want to try it, just because we seem to be running low on options/mojo/talent right now.

---

### Post by georgesgiralt on 2013-07-08
My pleasure :
```

georges@biniou:~$ cat /usr/lib/pm-utils/sleep.d/60_wpa_supplicant 
#!/bin/sh

# /etc/pm/sleep.d/60_wpa_supplicant
# Action script to notify wpa_supplicant of pm-action events.

PATH=/sbin:/usr/sbin:/bin:/usr/bin

WPACLI=wpa_cli

case "$1" in
	suspend|hibernate)
		$WPACLI suspend
		;;
	resume|thaw)
		$WPACLI resume
		;;
esac

exit 0
georges@biniou:~$ ls -al /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
-rwxr-xr-x 1 root root 267 oct.   7  2012 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
georges@biniou:~$ 


```
Did I tell you that I tried a lot of different Wifi Dongles on that laptop ? And that I reset /etc/udev/rules.d/70-persistent-net.rules to regain wlan0 for this Intel wifi card ?

---

### Post by georgesgiralt on 2013-07-08
No joy today...
Get caught on first awakening... 
No Wifi :
```

root@biniou:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
eth0      no wireless extensions.

root@biniou:~# ifdown wlan0
RTNETLINK answers: No such process
root@biniou:~# ifup wlan0
ssh stop/waiting
ssh start/running, process 4175
root@biniou:~# tail -100 /var/log/syslog
Jul  8 18:56:17 biniou kernel: [ 2106.196316] PM: resume of drv: dev:ep_81 complete after 1870.789 msecs
Jul  8 18:56:17 biniou kernel: [ 2106.196325] PM: resume of drv: dev:ep_04 complete after 1870.657 msecs
Jul  8 18:56:17 biniou kernel: [ 2107.608085] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul  8 18:56:17 biniou kernel: [ 2107.608969] ata1.00: unexpected _GTF length (8)
Jul  8 18:56:17 biniou kernel: [ 2107.614536] ata1.00: unexpected _GTF length (8)
Jul  8 18:56:17 biniou kernel: [ 2107.614955] ata1.00: configured for UDMA/133
Jul  8 18:56:17 biniou kernel: [ 2107.646106] PM: resume of drv:sd dev:0:0:0:0 complete after 3320.867 msecs
Jul  8 18:56:17 biniou kernel: [ 2107.646122] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 3059.730 msecs
Jul  8 18:56:17 biniou kernel: [ 2107.646146] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 3320.861 msecs
Jul  8 18:56:17 biniou kernel: [ 2107.646452] PM: resume of devices complete after 3328.801 msecs
Jul  8 18:56:17 biniou kernel: [ 2107.646802] PM: resume devices took 3.328 seconds
Jul  8 18:56:17 biniou kernel: [ 2107.646834] PM: Finishing wakeup.
Jul  8 18:56:17 biniou kernel: [ 2107.646836] Restarting tasks ... done.
Jul  8 18:56:17 biniou bluetoothd[554]: HCI dev 0 down
Jul  8 18:56:17 biniou bluetoothd[554]: Adapter /org/bluez/554/hci0 has been disabled
Jul  8 18:56:17 biniou bluetoothd[554]: HCI dev 0 unregistered
Jul  8 18:56:17 biniou bluetoothd[554]: Stopping hci0 event socket
Jul  8 18:56:17 biniou bluetoothd[554]: Unregister path: /org/bluez/554/hci0
Jul  8 18:56:17 biniou bluetoothd[554]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jul  8 18:56:17 biniou bluetoothd[554]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jul  8 18:56:17 biniou bluetoothd[554]: Endpoint unregistered: sender=:1.40 path=/MediaEndpoint/HFPAG
Jul  8 18:56:17 biniou bluetoothd[554]: HCI dev 0 registered
Jul  8 18:56:17 biniou bluetoothd[554]: Listening for HCI events on hci0
Jul  8 18:56:17 biniou bluetoothd[554]: HCI dev 0 up
Jul  8 18:56:18 biniou bluetoothd[554]: input-headset driver probe failed for device 30:17:C8:11:5A:15
Jul  8 18:56:18 biniou bluetoothd[554]: input-headset driver probe failed for device 84:00:D2:F4:66:A7
Jul  8 18:56:18 biniou bluetoothd[554]: Adapter /org/bluez/554/hci0 has been enabled
Jul  8 18:56:18 biniou bluetoothd[554]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/HFPAG
Jul  8 18:56:18 biniou bluetoothd[554]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSource
Jul  8 18:56:18 biniou bluetoothd[554]: Endpoint registered: sender=:1.40 path=/MediaEndpoint/A2DPSink
Jul  8 18:56:18 biniou kernel: [ 2107.740297] video LNXVIDEO:01: Restoring backlight state
Jul  8 18:56:18 biniou acpid: client 1326[0:0] has disconnected
Jul  8 18:56:18 biniou acpid: client connected from 1326[0:0]
Jul  8 18:56:18 biniou acpid: 1 client rule loaded
Jul  8 18:56:18 biniou anacron[3475]: Anacron 2.3 started on 2013-07-08
Jul  8 18:56:18 biniou anacron[3475]: Will run job `cron.daily' in 5 min.
Jul  8 18:56:18 biniou anacron[3475]: Jobs will be executed sequentially
Jul  8 18:56:18 biniou kernel: [ 2107.820969] cfg80211: Calling CRDA to update world regulatory domain
Jul  8 18:56:18 biniou kernel: [ 2107.832896] cfg80211: World regulatory domain updated:
Jul  8 18:56:18 biniou kernel: [ 2107.832900] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul  8 18:56:18 biniou kernel: [ 2107.832903] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  8 18:56:18 biniou kernel: [ 2107.832906] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  8 18:56:18 biniou kernel: [ 2107.832908] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul  8 18:56:18 biniou kernel: [ 2107.832911] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  8 18:56:18 biniou kernel: [ 2107.832913] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul  8 18:56:18 biniou kernel: [ 2107.835432] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Jul  8 18:56:18 biniou kernel: [ 2107.835435] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Jul  8 18:56:18 biniou kernel: [ 2107.835510] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  8 18:56:18 biniou kernel: [ 2107.835530] iwl3945 0000:04:00.0: setting latency timer to 64
Jul  8 18:56:18 biniou wpa_supplicant[979]: Failed to initiate AP scan.
Jul  8 18:56:18 biniou kernel: [ 2107.889182] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Jul  8 18:56:18 biniou kernel: [ 2107.889185] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Jul  8 18:56:18 biniou kernel: [ 2107.889334] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
Jul  8 18:56:18 biniou kernel: [ 2107.889530] Registered led device: phy0-led
Jul  8 18:56:18 biniou kernel: [ 2107.889559] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jul  8 18:56:18 biniou kernel: [ 2107.889669] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
Jul  8 18:56:18 biniou kernel: [ 2107.895277] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Jul  8 18:56:18 biniou wpa_supplicant[979]: CTRL-EVENT-TERMINATING - signal 15 received
Jul  8 18:56:18 biniou kernel: [ 2107.968233] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 18:56:23 biniou kernel: [ 2113.119868] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 18:56:23 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul  8 18:56:26 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jul  8 18:56:32 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jul  8 18:56:47 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jul  8 18:56:58 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Jul  8 18:57:08 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jul  8 18:57:44  dhclient: last message repeated 2 times
Jul  8 18:57:44 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jul  8 18:57:51 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jul  8 18:57:53 biniou kernel: [ 2203.544460] init: network-interface (wlan0) pre-start process (3493) killed by TERM signal
Jul  8 18:57:53 biniou dhclient: DHCPRELEASE on wlan0 to 192.168.0.254 port 67
Jul  8 18:57:53 biniou dhclient: send_packet: Network is unreachable
Jul  8 18:57:53 biniou dhclient: send_packet: please consult README file regarding broadcast address.
Jul  8 18:57:55 biniou wpa_supplicant[3525]: CTRL-EVENT-TERMINATING - signal 15 received
Jul  8 18:58:02 biniou kernel: [ 2212.201579] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul  8 18:58:03 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul  8 18:58:04 biniou kernel: [ 2213.896394] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
Jul  8 18:58:04 biniou kernel: [ 2214.121412] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
Jul  8 18:58:04 biniou kernel: [ 2214.380253] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
Jul  8 18:58:06 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jul  8 18:58:07 biniou wpa_supplicant[4056]: Trying to authenticate with 00:24:d4:66:6b:ac (SSID='FreeboxDeGeorges' freq=2412 MHz)
Jul  8 18:58:07 biniou kernel: [ 2216.822763] wlan0: authenticate with 00:24:d4:66:6b:ac (try 1)
Jul  8 18:58:07 biniou wpa_supplicant[4056]: Trying to associate with 00:24:d4:66:6b:ac (SSID='FreeboxDeGeorges' freq=2412 MHz)
Jul  8 18:58:07 biniou kernel: [ 2216.824613] wlan0: authenticated
Jul  8 18:58:07 biniou kernel: [ 2216.824794] wlan0: associate with 00:24:d4:66:6b:ac (try 1)
Jul  8 18:58:07 biniou kernel: [ 2216.828626] wlan0: RX AssocResp from 00:24:d4:66:6b:ac (capab=0x411 status=0 aid=1)
Jul  8 18:58:07 biniou kernel: [ 2216.828634] wlan0: associated
Jul  8 18:58:07 biniou kernel: [ 2216.831423] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul  8 18:58:07 biniou wpa_supplicant[4056]: Associated with 00:24:d4:66:6b:ac
Jul  8 18:58:07 biniou wpa_supplicant[4056]: WPA: Key negotiation completed with 00:24:d4:66:6b:ac [PTK=CCMP GTK=TKIP]
Jul  8 18:58:07 biniou wpa_supplicant[4056]: CTRL-EVENT-CONNECTED - Connection to 00:24:d4:66:6b:ac completed (auth) [id=0 id_str=]
Jul  8 18:58:09 biniou dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jul  8 18:58:09 biniou dhclient: DHCPREQUEST of 192.168.0.2 on wlan0 to 255.255.255.255 port 67
Jul  8 18:58:09 biniou dhclient: DHCPOFFER of 192.168.0.2 from 192.168.0.254
Jul  8 18:58:09 biniou dhclient: DHCPACK of 192.168.0.2 from 192.168.0.254
Jul  8 18:58:10 biniou dhclient: bound to 192.168.0.2 -- renewal in 21039 seconds.
Jul  8 18:58:17 biniou kernel: [ 2227.136078] wlan0: no IPv6 routers present
Jul  8 18:58:18 biniou ntpdate[4170]: step time server 91.189.89.199 offset -0.708272 sec
Jul  8 19:01:17 biniou anacron[3475]: Job `cron.daily' started
Jul  8 19:01:17 biniou anacron[4246]: Updated timestamp for job `cron.daily' to 2013-07-08
root@biniou:~#

```

So the "post-down killall -q wpa_supplicant" stanza will goto the bin, I think.....

---

### Post by georgesgiralt on 2013-07-10
Hello !
This is becoming a nightmare ! 
Now, the laptop does not activate the wifi on awakening. 
Before, I was lucky one every other try. No more....

---

### Post by chili555 on 2013-07-10
Is there any clue here?```
sudo ifdown wlan0 && sudo ifup -v wlan0
```Does the wireless restart on resume if you do:```
sudo service networking restart
```Once you get it started, what does this tell us?```
ps aux | grep wpa
```The script I linked above is inappropriate for Ubuntu 13.04, unfortunately, although we may experimentally find a similar solution. I am still suspicious of the lurking Network Mangler.

How about this:```
ls /etc/init.d | grep wpa
```

---

### Post by georgesgiralt on 2013-07-12
So,
I am unable to reproduce the problem. It works flawlessly since I posted a couple of days ago. I'm thinking more and more on a race condition at awakening. 
I'll keep you posted.

---

### Post by georgesgiralt on 2013-07-12
So,
I am unable to reproduce the problem. It works flawlessly since I posted a couple of days ago. I'm thinking more and more on a race condition at awakening. 
I'll keep you posted. 
In the mean time :
```

georges@biniou:~$ ls /etc/init.d | grep wpa
georges@biniou:~$ ps aux | grep wpa
root      5667  0.0  0.0  31784  1568 ?        Ss   15:10   0:00 /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
georges   6612  0.0  0.0   9424   904 pts/0    S+   16:40   0:00 grep wpa
georges@biniou:~$

```

---

### Post by chili555 on 2013-07-13
I will be very interested to see if you can get the wireless working again upon resume by simply restarting networking. Maybe we can come up with a script; maybe we can develop a vaccine, build up our immunity...  Oops, sorry, wrong movie.

---

### Post by georgesgiralt on 2013-07-15
Hello !
Yesterday was a holiday. In France. 
The laptop made me desperate because the network was not working on awakening. Seems one Union talked to the card and daemons and they decided to stop working. 
So I tried to "sudo service networking restart" and it does nothing useful. I was forced to "sudo ifdown wlan0", kill the remaining (not always) wpa supplicant process and "sudo ifup wlan0" to get the network up. The wifi led in the front of the laptop is consistent with the actual state of the wifi..... 
I've bought a blanket and a heap of moist wood. Once I've found my match box, I'll try to speak with smoke clouds to my network to see if it is more efficient ;-)

---

