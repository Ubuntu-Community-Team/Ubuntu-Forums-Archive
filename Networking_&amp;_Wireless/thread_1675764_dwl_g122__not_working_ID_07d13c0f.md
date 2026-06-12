---
title: "dwl g122  not working ID 07d1:3c0f"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by baubas101 on 2011-01-26
hi there ;)
trying to use this usbwifi as my pc dont have the integrated wireless. but dlink i see is not ubuntu friend.... so tryied alot of things sugested in this forum but no luck....

maybe someone can check the solution for me :) ?
when i start pc adapter dead . found in one thread chilli suggestion
sudo modprobe rt 2800usb

at last there started to blink a lamp on it.
but no more moves i can find my self...
maybe too much already precompiled and compiled and subextracompiled... so is there a way to delete everything ad start over or any other way to get that d link working.

Thanks for reading :D
one more thing after runing modprobe 2800 gsm network also stoped...

ID 07d1:3c0f
root@kobus:/home/kobus# modinfo rt3070sta | grep 3C0D
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
root@kobus:/home/kobus# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usbpn0    no wireless extensions.

ppp0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=6 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
         
root@kobus:/home/kobus# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

root@kobus:/home/kobus# sudo iwlist wlan1 scan
wlan1     No scan results

root@kobus:/home/kobus# dmesg | grep -e wlan -e rt2 -e rt3
[   27.161284] usbcore: registered new interface driver rndis_wlan
[  370.597721] rt3070sta: Unknown symbol usb_alloc_urb
[  370.598087] rt3070sta: Unknown symbol usb_free_urb
[  370.599135] rt3070sta: Unknown symbol usb_register_driver
[  370.599867] rt3070sta: Unknown symbol usb_put_dev
[  370.600196] rt3070sta: Unknown symbol usb_get_dev
[  370.600702] rt3070sta: Unknown symbol usb_submit_urb
[  370.601936] rt3070sta: Unknown symbol usb_control_msg
[  370.602828] rt3070sta: Unknown symbol usb_deregister
[  370.604098] rt3070sta: Unknown symbol usb_kill_urb
[  370.604369] rt3070sta: Unknown symbol usb_buffer_free
[  370.605505] rt3070sta: Unknown symbol usb_buffer_alloc
[  494.201380] Registered led device: rt2800usb-phy0::radio
[  494.202974] Registered led device: rt2800usb-phy0::assoc
[  494.204878] Registered led device: rt2800usb-phy0::quality
[  494.205255] usbcore: registered new interface driver rt2800usb
[  494.227982] udev: renamed network interface wlan0 to wlan1
[  494.248516] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin
[  494.600055] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  649.228295] ADDRCONF(NETDEV_UP): wlan1: link is not ready

---

### Post by chili555 on 2011-01-26
> ID 07d1:3c0[COLOR="Red"]**f**[/COLOR]
root@kobus:/home/kobus# modinfo rt3070sta | grep 3C0[COLOR="Red"]**D**[/COLOR]
alias: usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*So, which is it? Please post:```
lsusb
modinfo rt3070sta | grep version
uname -r
```Thanks.

PS - Do you need Dr. Chili's harsh talk about running as root? It's dangerous.

---

### Post by baubas101 on 2011-01-26
hi :) ok ok :D mister dr chilli dont need to tell this :) understood dont do this again :D

ok so here is the comands output :

kobus@kobus:~$ lsusb
Bus 003 Device 002: ID 0421:0042 Nokia Mobile Phones E51 (PC Suite mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c0f D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kobus@kobus:~$ modinfo rt3070sta | grep version
version:        2.5.0.1
srcversion:     C152700F8E2BF68CCDA1F57
vermagic:       2.6.32-27-generic SMP mod_unload modversions 586 
kobus@kobus:~$ uname -r
2.6.32-27-generic

---

### Post by chili555 on 2011-01-26
Let's see:```
lsmod | grep -e rt2 -e rt3
```We're almost there!

---

### Post by baubas101 on 2011-01-26
here it is :) 

kobus@kobus:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             461811  0

---

### Post by chili555 on 2011-01-26
> **baubas101 said:**
> here it is :) 

kobus@kobus:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             461811  0What?? I have no idea how or why rt2870sta loaded. I don't believe it's correct for your device. Let's unload it and load rt3070sta and see if the wireless comes to life. If so, we can make some adjustments.```
sudo rmmod -f rt2870sta
sudo modprobe rt3070sta
iwconfig
```Any improvement?

---

### Post by baubas101 on 2011-01-27
ye me neither. . 
so this we have now 
kobus@kobus:~$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.32-27-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg i think theese parts is interesting,,,
................
[   23.410862] udev: starting version 151
[   23.431896] rt3070sta: module license 'unspecified' taints kernel.
[   23.431901] Disabling lock debugging due to kernel taint
[   23.432139] rt3070sta: Unknown symbol usb_alloc_urb
[   23.432256] rt3070sta: Unknown symbol usb_free_urb
[   23.432655] rt3070sta: Unknown symbol usb_register_driver
[   23.432925] rt3070sta: Unknown symbol usb_put_dev
[   23.433018] rt3070sta: Unknown symbol usb_get_dev
[   23.433201] rt3070sta: Unknown symbol usb_submit_urb
[   23.433668] rt3070sta: Unknown symbol usb_control_msg
[   23.434005] rt3070sta: Unknown symbol usb_deregister
[   23.434651] rt3070sta: Unknown symbol usb_kill_urb
[   23.434740] rt3070sta: Unknown symbol usb_buffer_free
[   23.435175] rt3070sta: Unknown symbol usb_buffer_alloc
[   23.438442] Adding 2626588k swap on /dev/sda5.  Priority:-1 extents:1 across:2626588k 
[   23.577995] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   23.586160] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.955656] rtusb init --->
[   23.955713] usbcore: registered new interface driver rt2870
[   23.965038] Linux agpgart interface v0.103
----------------.......................
and

[   25.408666] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.490756] apm: BIOS not found.
[   25.764879] lp0: using parport0 (interrupt-driven).
[   28.821253] lib80211: common routines for IEEE802.11 drivers
[   28.821259] lib80211_crypt: registered algorithm 'NULL'
[   82.896031] usb 3-4: new full speed USB device using ohci_hcd and address 2
[   83.109202] usb 3-4: configuration #1 chosen from 1 choice
[   83.184267] cdc_acm 3-4:1.10: ttyACM0: USB ACM device
[   83.193237] cdc_acm 3-4:1.12: ttyACM1: USB ACM device
[   83.193283] NET: Registered protocol family 35
[   83.197700] usbcore: registered new interface driver cdc_acm
[   83.197704] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   83.201544] usbcore: registered new interface driver cdc_phonet
[   83.204427] usbcore: registered new interface driver cdc_ether
[   83.212164] usbcore: registered new interface driver rndis_host
[   83.248491] cfg80211: Calling CRDA to update world regulatory domain
[   83.262697] usbcore: registered new interface driver rndis_wlan
[   83.285146] cfg80211: World regulatory domain updated:
[   83.285150]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   83.285154]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.285157]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.285160]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   83.285163]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   83.285165]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.102599] PPP BSD Compression module registered
[  106.113345] PPP Deflate Compression module registered
[  249.945977] usb 3-4: USB disconnect, address 2
[  250.035164] usb 3-4: acm_ctrl_irq - usb_submit_urb failed with result -19
[  256.300053] usb 2-3: new full speed USB device using ohci_hcd and address 2
[  256.513327] usb 2-3: configuration #1 chosen from 1 choice
[  256.535749] cdc_acm 2-3:1.10: ttyACM0: USB ACM device
[  256.565770] cdc_acm 2-3:1.12: ttyACM1: USB ACM device
[  263.912065] usb 1-8: new high speed USB device using ehci_hcd and address 4
[  264.061431] usb 1-8: configuration #1 chosen from 1 choice
[  290.783110] usbcore: deregistering interface driver rt2870
[  290.784280] <--- rtusb exit
[  300.999060] rt3070sta: Unknown symbol usb_alloc_urb
[  300.999406] rt3070sta: Unknown symbol usb_free_urb
[  301.000484] rt3070sta: Unknown symbol usb_register_driver
[  301.001208] rt3070sta: Unknown symbol usb_put_dev
[  301.001500] rt3070sta: Unknown symbol usb_get_dev
[  301.002005] rt3070sta: Unknown symbol usb_submit_urb
[  301.003221] rt3070sta: Unknown symbol usb_control_msg
[  301.004131] rt3070sta: Unknown symbol usb_deregister
[  301.005358] rt3070sta: Unknown symbol usb_kill_urb
[  301.005627] rt3070sta: Unknown symbol usb_buffer_free
[  301.006764] rt3070sta: Unknown symbol usb_buffer_alloc

so as i understand there is smth wrong with 3070.ko but how to check it ? or maybe its easier to recompile driver? also then what i need to do to make clean somehow....
the prehistory was i was making the driver from new win driver from dlink, and then find in forum that i need to use old driver. so when trying to recompile to old driver sudo make and make install shows errors...  
stucked here :( 
but anyway ubuntu rocks :D :D just little dlink problem :(

---

### Post by chili555 on 2011-01-27
> there is smth wrong with 3070.ko but how to check it ? or maybe its easier to recompile driver? Yes on both counts. Any time you encounter errors, stop and proceed no farther. It will not lead to a happy ending. 

I still don't understand where rt2870sta is getting loaded. Please check in /etc/modules. If it or ndiswrapper is listed, please remove them. I think, since you are using an older kernel, we may need an older version of the driver. Let's uninstall the old one first. Open a terminal and navigate to the folder where you compiled the driver; for example:```
cd Downloads/2010_3070_DPOetc.whatever
sudo make uninstall
```Now download and compile the older version here using the methods you followed previously. Be sure to set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' in os/linux/config.mk. Then:```
cd Downloads
tar xvf 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO.bz2
cd 2010_0831_RT3070_Linux_STA_v2.4.0.1_DPO
sudo su
make
make install
modprobe rt3370sta
exit
```These are somewhat abbreviated instructions. Since you have compiled before, I assume you know the process fairly well. However, if you get stuck and, especially if you get any error, stop and post back.

---

### Post by baubas101 on 2011-01-27
ok made this new install and now its blinking and no wifi list ! :) at least it start to blink :D :D  i hope this gona be ok soon, but probably missed something ? 

hm etc/wireless the folder is rt2870sta ...

so now i have this :

kobus@kobus:~$ lsusb
Bus 001 Device 003: ID 07d1:3c0f D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
kobus@kobus:~$ modinfo rt3070sta | grep version
ERROR: modinfo: could not find module rt3070sta
kobus@kobus:~$ modinfo rt3370sta | grep version
version:        2.4.0.1
srcversion:     C2F4A8A320EB97457698447
vermagic:       2.6.32-27-generic SMP mod_unload modversions 586 
kobus@kobus:~$ modprobe rt3370sta
kobus@kobus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usbpn0    no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

kobus@kobus:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:76:70:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2912 (2.9 KB)  TX bytes:2912 (2.9 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.148.154.49  P-t-P:10.6.6.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2967 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2353549 (2.3 MB)  TX bytes:383764 (383.7 KB)

ra0       Link encap:Ethernet  HWaddr f0:7d:68:f5:a8:2c  
          inet6 addr: fe80::f27d:68ff:fef5:a82c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2220002 (2.2 MB)  TX bytes:14168 (14.1 KB)

---

### Post by chili555 on 2011-01-27
> ppp0 Link encap:Point-to-Point Protocol
inet addr:188.148.154.49 P-t-P:10.6.6.6 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1500 Metric:1Is your modem connected? I don't think Network Manager is going to start using wireless if there is already another internet connection. What does this tell us?```
dmesg | grep -i rt2
dmesg | grep rt3
sudo iwlist ra0 scan
```

---

### Post by baubas101 on 2011-01-27
then i forgot to put to etc/modules that drivers rt3070sta and so on. but after i put them in there wifi stop to blink, and after i removed them i'm again and restarted again in blinking stage, but there was one connection for short time.... and now it gone... 
but do i feel luck here :) mr dr Chilli what u see here :D ?

---

### Post by chili555 on 2011-01-27
The module rt3070sta is the one that you, hopefully, uninstalled. The module rt3**3**70sta is the one you just built. Forget about rt3070sta. Can you please give me the results fro my post #10?

---

### Post by baubas101 on 2011-01-27
was waiting waiting and missed your one post :D ok here it is 

kobus@kobus:~$ dmesg | grep -i rt2
[  357.521278] rt28xx_get_wireless_stats --->
[  357.521286] <--- rt28xx_get_wireless_stats
[  456.616821] rt28xx_get_wireless_stats --->
[  456.616831] <--- rt28xx_get_wireless_stats
kobus@kobus:~$ dmesg | grep rt3

kobus@kobus:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:02:61:35:DC:A6
                    Protocol:802.11b/g
                    ESSID:"Tafjord-storgt28-118"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/100  Signal level:-79 dBm  Noise level:-86 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 34:21:09:00:F6:C4
                    Protocol:802.11b/g/n
                    ESSID:"AirLink89300"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/100  Signal level:-71 dBm  Noise level:-78 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A88034210900F6C4103C000101
          Cell 03 - Address: 00:0B:6B:7C:E7:FC
                    Protocol:802.11b/g
                    ESSID:"D35Broadband"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/100  Signal level:-65 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 04 - Address: 00:23:F8:82:8F:36
                    Protocol:802.11b/g
                    ESSID:"privat0002tre"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality=26/100  Signal level:-79 dBm  Noise level:-74 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:26:5A:30:38:0C
                    Protocol:802.11b/g/n
                    ESSID:"Claire4ever"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/100  Signal level:-65 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 06 - Address: 00:90:D0:EC:B7:63
                    Protocol:802.11b/g
                    ESSID:"privat70B81E"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 07 - Address: 00:27:19:D2:79:7A
                    Protocol:802.11b/g/n
                    ESSID:"xxx"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/100  Signal level:-75 dBm  Noise level:-70 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 08 - Address: 00:02:61:04:F1:E6
                    Protocol:802.11b/g
                    ESSID:"bombaysapphire"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/100  Signal level:-83 dBm  Noise level:-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 64:16:F0:79:31:67
                    Protocol:802.11b/g
                    ESSID:"NetCom-3167"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/100  Signal level:-65 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 10 - Address: 00:02:CF:61:ED:C0
                    Protocol:802.11b/g
                    ESSID:"privat0354lyn"
                    Mode:Managed
                    Frequency:2.472 GHz (Channel 13)
                    Quality=57/100  Signal level:-67 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s

---

### Post by chili555 on 2011-01-27
Looks outstanding! How about the modem?

---

### Post by baubas101 on 2011-01-27
im using now gsm modem nokia for internet.. very expencive :( 

and as i understood from last command there is already some possible connections, but i cant see them in network manager . so sorry but how to connect :confused:

---

### Post by chili555 on 2011-01-27
Network Manager is designed to connect to the internet the easiest or best way possible and then go to sleep. It is not designed to connect the modem AND the wireless AND the ethernet. As long as the modem is connected and has an IP address, Network Manager is going to make it difficult and probably impossible to connect the wireless.

Detach the cable to the modem, wait a few moments for Network Manager to notice the change of state (tea, anyone?) and click the Network Manager icon. Do you see your network listed under wireless? Can you click it and connect?

---

### Post by baubas101 on 2011-01-27
yes now it works :) !! :guitar:   Thank you so much !!! now i have internet :) ! many thanks !!!! 

the eror was that for this Dlink 3c0f. i needed the specific old driver, not the one that d link gives :) and after recompiling driver then disconecting all the available connections and it finaly works ! 
many thanks for mr dr chili555 :) !

---

### Post by chili555 on 2011-01-27
Woo hoo! I am very glad it's working. You have helped the searchers too. To some extent, older kernel needs older driver; newer kernel needs newer driver. The searchers will be grateful that you went through the process to help them! Enjoy!

---

