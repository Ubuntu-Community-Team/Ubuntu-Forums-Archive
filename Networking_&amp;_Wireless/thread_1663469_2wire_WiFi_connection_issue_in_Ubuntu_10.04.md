---
title: "2wire WiFi connection issue in Ubuntu 10.04"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by jsweet on 2011-01-09
I'm brand new to Ubuntu, and Linux in general, and honestly don't know what I am doing. I installed Ubuntu 10.04 on my external hard drive and am able to boot fine (other than an issue with my monitor falling asleep because my graphics card needs a different driver. I have a work around for this that i'm currently using but I would like to fix it permanently and thus need an internet connection.) 

When trying to connect to the network in my home, I am unable to. I click on the WiFi symbol in the top right corner, and I can see my network. I then click it and a page comes up asking for the key. I put it in but it doesn't sync and usually after a minute or so it pops back up asking for the key again.
What can I do to gain internet access? I'm unable to connect my computer via a hard wire Ethernet cord and need to sort out this WiFi issue.

---

### Post by chili555 on 2011-01-09
Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with WPA ***or*** WPA2; not both.

Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

### Post by jsweet on 2011-01-10
Sorry for the day's delay in response.

I got on and tried to connect to the internet by clicking the internet symbol and selecting my dad's network, "2wire566". When it requested a security code I accessed the drop down menu but could not find a choice for WPA or WPA2. There were choices for WEP 40/128, WEP 128, LEAP, and something else. I then went into System, Preferences, Network Connection and selected Auto2wire566. I clicked edit, security, and choose WPA and WPA2 Personal. There was no singular WPA or WPA2 choice. I put in the key but there was still no internet connection.

Is it possible that I can't connect because my Dad has the network locked out to new machines? I just assumed that by the computer being able to recognize it and me having a pass code, that I would be able to get in.

---

### Post by wjz on 2011-01-10
I would say it is possible if he has mac address filtering for specific machines, If you had cable connectivity you could log into the router and change security settings until you get up and running.

---

### Post by chili555 on 2011-01-10
Generally, the popup shows the configuration of the network. If it can tell, and it usually can, that the network is WEP, it will ask for the WEP key. Are you sure the network is WPA? By default, many 2wire devices are set for 40 (really 64) bit WEP. Do you have a ten digit HEX key, meaning numbers and, possibly, letters from a to f?

A lot of the 2wires I have seen have the ten digit WEP key printed on the bottom, unless you affirmatively change it.

---

### Post by jsweet on 2011-01-10
I have a ten number key code with no letters that I have been using. I believe this is the right code- but I can check the bottom and see if there is anything else in the way of ten digit key codes. 

I also am not sure if its WEP or WPA. When I set up my Windows XP OS it only asked for the key, it did not give me a drop down of security options like Linux did. I'll keep trying and see if there is a different code.

---

### Post by chili555 on 2011-01-10
I believe you will find it is 40-bit WEP. Please try it.

---

### Post by jsweet on 2011-01-11
So I know that I have the correct password to log in but still no connection under WEP 40 or WEP. I originally assumed that it was not a driver error because I can select the wireless network from a drop down list of choices. Is it possible that it is driver related? I can't think of anything else that could solve it and I really don't know where to go from here.

---

### Post by chili555 on 2011-01-11
I think it is quite doubtful it's a driver issue. Let's do some diagnoses. Please open Applications > Accessories > Terminal and run and post:```
iwconfig
```If your wireless interface is wlan0, next run:```
sudo iwlist wlan0 scan
```Post the result of the commands and let's proceed.

---

### Post by jsweet on 2011-01-11
So here are my results

johnsweet@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Channel: 0  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:64 dBm   Sensitivity=0/3  
          RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level:0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

johnsweet@Ubuntu:~$ sudo iwlist wlano scan
[sudo] password for johnsweet: 
wlano     Interface doesn't support scanning.

johnsweet@Ubuntu:~$ 


(Please be patient as I only have one computer and am bouncing between Windows XP and Ubuntu to post new items)

---

### Post by chili555 on 2011-01-11
> sudo iwlist wlano scanIt's wlan0 not wlano.

I can be plenty patient, but I'll run out of time in a while.

---

### Post by jsweet on 2011-01-11
Sorry about that...


johnsweet@Ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:B3:4F:8C: D9
                    ESSID:"2WIRE566"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

          Cell 02 - Address: 00:14:95:20:79: D9
                    ESSID:"2WIRE646"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

johnsweet@Ubuntu:~$

My network is 2wire566

---

### Post by chili555 on 2011-01-11
> johnsweet@Ubuntu:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:1F:B3:4F:8C: D9
ESSID:"2WIRE566"
Protocol:IEEE 802.11g
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:64/100 Signal level:-55 dBm Noise level:-96 dBm
Encryption key: on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0It looks like WEP to me. Here is a WPA scan for comparison:> Cell 01 - Address: 99:24:66:2A:D7:99
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c6091b59e
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : [COLOR="Red"]PSK[/COLOR]
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
What does this tell us?```
sudo cat /var/log/syslog | grep wlan0
```If the file is scant, try syslog.1

Even though the strength is 64/100, it ought to connect, although maybe not at maximum speed.

---

### Post by jsweet on 2011-01-11
So I ran

[CODE]sudo cat /var/log/syslog | grep wlan0

and got this:


ns (scan_capa 0x01).
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'zd1211rw')
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 20:40:34 Ubuntu kernel: [   18.763064] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 11 20:40:34 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE566'
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE566' has security, but secrets are required.
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 20:40:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE566' has security, and secrets exist.  No new secrets needed.
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 20:41:22 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jan 11 20:41:23 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:41:23 Ubuntu kernel: [   67.257908] wlan0: deauthenticating from 00:1f:b3:4f:8c:d9 by local choice (reason=3)
Jan 11 20:41:23 Ubuntu kernel: [   67.270930] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:23 Ubuntu kernel: [   67.274149] wlan0: direct probe responded
Jan 11 20:41:23 Ubuntu kernel: [   67.274152] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:33 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:41:33 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 20:41:34 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:41:34 Ubuntu kernel: [   78.133936] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:34 Ubuntu kernel: [   78.136526] wlan0: direct probe responded
Jan 11 20:41:34 Ubuntu kernel: [   78.136529] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:44 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:41:44 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 20:41:45 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:41:45 Ubuntu kernel: [   88.985993] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:45 Ubuntu kernel: [   88.989179] wlan0: direct probe responded
Jan 11 20:41:45 Ubuntu kernel: [   88.989186] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:55 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:41:55 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 20:41:55 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:41:55 Ubuntu kernel: [   99.846000] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:41:55 Ubuntu kernel: [   99.848431] wlan0: direct probe responded
Jan 11 20:41:55 Ubuntu kernel: [   99.848437] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:42:04 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 11 20:42:05 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:42:05 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 20:42:06 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:42:06 Ubuntu kernel: [  110.709005] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:42:06 Ubuntu kernel: [  110.712315] wlan0: direct probe responded
Jan 11 20:42:06 Ubuntu kernel: [  110.712322] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:42:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:42:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 20:42:17 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 20:42:17 Ubuntu kernel: [  121.570007] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:42:17 Ubuntu kernel: [  121.574772] wlan0: direct probe responded
Jan 11 20:42:17 Ubuntu kernel: [  121.574780] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
Jan 11 20:42:23 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan 11 20:42:23 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 20:42:23 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan 11 20:42:23 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 20:42:31 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Jan 11 20:42:31 Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (2WIRE566)
Jan 11 20:42:31 Ubuntu NetworkManager: <info>  Activation (wlan0) failed.
Jan 11 20:42:31 Ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan 11 20:42:31 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan 11 20:53:15 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 11 20:53:15 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'zd1211rw')
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 20:53:15 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 20:53:16 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 20:53:16 Ubuntu kernel: [   19.059068] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 20:53:16 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 20:53:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 11 20:53:16 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 11 20:53:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 21:01:54 Ubuntu kernel: [   20.757843] wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: 'ZyDAS ZD1211B 802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Jan 11 21:01:54 Ubuntu kernel: [   20.763162] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 11 21:01:54 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 11 21:01:54 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 21:01:54 Ubuntu kernel: [   20.785393] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 21:01:54 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE566'
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE566' has security, but secrets are required.
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 21:02:19 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 21:02:25 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> inactive
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE566' has security, and secrets exist.  No new secrets needed.
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 21:02:45 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jan 11 21:02:50 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:02:55 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:02:55 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:00 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:03:05 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:03:05 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:10 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:03:15 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:03:15 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:20 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:03:25 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:03:25 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:25 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 11 21:03:30 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:03:35 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:03:35 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:40 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:03:45 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:03:45 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:46 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan 11 21:03:46 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 21:03:46 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan 11 21:03:46 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE566' has security, and secrets exist.  No new secrets needed.
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 21:03:53 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:03:58 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:03 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:03 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:08 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:13 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:13 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:18 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:23 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:23 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:28 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:33 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:33 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:34 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 11 21:04:38 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:43 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:43 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:48 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:04:53 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:04:53 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:04:54 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan 11 21:04:54 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 21:04:54 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan 11 21:04:54 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Jan 11 21:05:09 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE566' has security, and secrets exist.  No new secrets needed.
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 11 21:05:24 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:05:29 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:05:34 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:05:34 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:05:39 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:05:44 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:05:44 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:05:49 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:05:54 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:05:54 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:05:59 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:06:04 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 11 21:06:04 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:06:04 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:06:09 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:06:14 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:06:14 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 11 21:06:19 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 11 21:06:24 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Jan 11 21:06:24 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 11 21:06:24 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Jan 11 21:06:24 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 11 21:06:33 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Jan 11 21:06:33 Ubuntu NetworkManager: <info>  Activation (wlan0) failed for access point (2WIRE566)
Jan 11 21:06:33 Ubuntu NetworkManager: <info>  Activation (wlan0) failed.
Jan 11 21:06:33 Ubuntu NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Jan 11 21:06:33 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Jan 11 21:24:06 Ubuntu kernel: [   19.249414] wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: 'ZyDAS ZD1211B 802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Jan 11 21:24:06 Ubuntu kernel: [   19.255160] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 11 21:24:06 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 11 21:24:06 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 21:24:06 Ubuntu kernel: [   19.274994] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 21:24:06 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jan 11 21:44:28 Ubuntu kernel: [   19.436333] wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: 'ZyDAS ZD1211B 802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Jan 11 21:44:28 Ubuntu kernel: [   19.443159] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 11 21:44:28 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 11 21:44:28 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 21:44:28 Ubuntu kernel: [   19.468299] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 21:44:28 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jan 11 22:02:11 Ubuntu kernel: [   19.247897] wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: 'ZyDAS ZD1211B 802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Jan 11 22:02:11 Ubuntu kernel: [   19.251269] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 11 22:02:11 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 11 22:02:11 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 11 22:02:11 Ubuntu kernel: [   19.274295] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 11 22:02:11 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
johnsweet@Ubuntu:~$

---

### Post by chili555 on 2011-01-11
The plot thickens...please let us see:```
lsmod | grep -e ndis -e zd12
ndiswrapper -l
```I have a hunch.

---

### Post by jsweet on 2011-01-11
This is what I got:

johnsweet@Ubuntu:~$ lsmod | grep -e ndis -e zd12
ndiswrapper           184677  0 
johnsweet@Ubuntu:~$ 
johnsweet@Ubuntu:~$ lsmod | grep -e ndis -e zd12 ndiswrapper -l
grep: ndiswrapper: No such file or directory
johnsweet@Ubuntu:~$

---

### Post by chili555 on 2011-01-12
> johnsweet@Ubuntu:~$ lsmod | grep -e ndis -e zd12 ndiswrapper -l
grep: ndiswrapper: No such file or directorySorry; that was intended to be two separate commands. Please let us see:```
ndiswrapper -l
```That's a lower-case L as in 'list.'

---

### Post by jsweet on 2011-01-13
johnsweet@Ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
zd1211bu : driver installed
	device (0ACE:1215) present (alternate driver: zd1211rw)
johnsweet@Ubuntu:~$

---

### Post by chili555 on 2011-01-13
> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.We can fix this easily. Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```The next one is a bit more complex:> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.There is already a file in your system blacklist.conf and now the ndiswrapper installation process has added a separate new blacklist file. We don't need two, one of which will soon be ignored. Please do:```
cat /etc/modprobe.d/blacklist
```What I hope is in there is *blacklist zd1211rw*. Write it down carefully and proofread. Next do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add the entry you wrote down. Proofread carefully, save and close gedit. Now lets get rid of the extra file:```
sudo rm /etc/modprobe.d/blacklist
```

Why did you decide to use ndiswrapper instead of the native driver?

---

### Post by jsweet on 2011-01-13
Code:
cat /etc/modprobe.d/blacklist

When I ran this code I got:
johnsweet@Ubuntu:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xxnblacklist b43nblacklist b43legacynblaclist ssb
blacklist bcm43xxnblacklist b43nblacklist b43legacynblacklist ssb
johnsweet@Ubuntu:~$ 


What is it that I am adding/saving?
Also should I put a number sign in front of it like all of the other entries?

---

### Post by chili555 on 2011-01-13
Do you have an internal Broadcom card? If not, these entries, as wrongly formed as they are, are not needed.

---

### Post by jsweet on 2011-01-13
No it is an external 2wire receiver
"2wire 802.11g USB Wireless Adapter"
"US-G-AT-02"

---

### Post by chili555 on 2011-01-13
> wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: [COLOR="Red"]'ZyDAS ZD1211B 802.11 b+g Wireless LAN'[/COLOR], 0ACE:1215.F.confOne of us is not understanding. Your 2wire device hooks to the computer by USB?? When the internet comes in to your house, what does it connect to? Where does wireless come in to the picture?

I thought the internet arrived and was wired into the 2wire which has wireless capability and, clear across the house, your computer had a wireless dongle that has a Zydas chipset. No??

Please help me understand.

---

### Post by jsweet on 2011-01-13
The wireless comes into the house. It goes through our 2wire gateway which manages our wireless (which broadcasts around the house)and Ethernet ports. I then have an adapter/receiver (the information I presented earlier) which picks up the signal and transfers it to my computer by a USB line. It is an older desktop and has no wireless card built in (that i know of).

---

### Post by chili555 on 2011-01-13
Then you do not need the b43xx blacklist items. Please do:```
sudo rm /etc/modprobe.d/blacklist
sudo gedit /etc/modprobe.d/blacklist.conf
```Make sure this line exists in the file on its own line:```
blacklist zd1211rw
```Proofread carefully, save and close gedit. Reboot and tell us if your wireless is now able to connect.

---

### Post by jsweet on 2011-01-13
I put both codes in the terminal separately, and both completed without a problem. Still no internet connection unfortunately. I copied my gedit file...


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

# blacklist zd1211rw


that last part is what I put in

---

### Post by chili555 on 2011-01-13
> [COLOR="Red"]#[/COLOR] blacklist zd1211rwThat little pound sign means, 'these are merely comments to make the file more understandable. Don't act on it.' Having text preceded by # is referred to as being 'commented out.' ```
#These are comments only
```Please remove the pound sign.

---

### Post by jsweet on 2011-01-13
Changed it to:

...
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist zd1211rw


Rebooted the computer, still no internet connection :(

---

### Post by chili555 on 2011-01-14
When you boot, does the Network Manager pop up a notifier saying that networks are available? Do you see your specific network as one that's available? When you click on it, does it ask for your 40/128-bit hex WEP password? When you enter your ten numbers, does it fail to connect with any messages?

Have you added your network by editing connections by right-clicking the NM icon? Is it set for 40/128-bit hex WEP?

---

### Post by chili555 on 2011-01-14
Duplicate, sorry.

---

### Post by chili555 on 2011-01-14
Duplicate, sorry.

---

### Post by wjz on 2011-01-14
You must have a huge house mate.

---

### Post by wjz on 2011-01-14
How big is your house? lol

---

### Post by jsweet on 2011-01-14
Yes, it pops up in the right hand corner that networks are available. Yes, I see my network as available, along with one other network. When I click on my network, it then asks me for the 40/128 bit password. The little internet symbol then cycles up and down for maybe 30 seconds or so and then it comes up &#8220;failed to connect&#8221; asking for my password again.
I don&#8217;t think that I have edited my connections but, I&#8217;m going to switch over right after typing this too double check that all is in order (ie: set up for a WEP connection).

EDIT:
I double checked and it is set for WEP 40/128 bit
Is it possible that the driver I need is mis configured/damaged/or nonexistent?
      Maybe there is a code I can run in the terminal to check this?

---

### Post by chili555 on 2011-01-15
Non-existent? No. If the system creates a wireless interface, wlan0 in your case, looks for and finds networks and tries to connect, then you have a functioning driver. Is it functioning correctly? Perhaps not. This command should tell you if the driver and hardware are present:```
ndiswrapper -l
```The question remains: why did you pick ndiswrapper instead of the native driver *zd1211rw*, which we blacklisted? We might get some insight if you try to connect and then run:```
sudo cat /var/log/syslog | grep wlan
```The file is likely to be quite lengthy, so try to find the twenty or so lines that show the attempt to connect and subsequent failure and post them. If the log has recently filled up, been stored and started over, you might get very little; try syslog.1 instead.

---

### Post by jsweet on 2011-01-15
I did not choose to use ndiswrapper versus the native driver. A friend helped me to set up my computer and must have used that.

Here are the lines that I think you need (I can give you the whole file if you need it):


Jan 13 17:27:06 Ubuntu kernel: [   19.193263] wlan0: ethernet device 00:1a:6b:cb:ef:f2 using NDIS driver: zd1211bu, version: 0x6130000, NDIS version: 0x501, vendor: 'ZyDAS ZD1211B 802.11 b+g Wireless LAN', 0ACE:1215.F.conf
Jan 13 17:27:06 Ubuntu kernel: [   19.199526] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Jan 13 17:27:06 Ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0)
Jan 13 17:27:06 Ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-3/1-3:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): now managed
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): bringing up device.
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): preparing device.
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 13 17:27:06 Ubuntu kernel: [   19.224337] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 13 17:27:06 Ubuntu NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto 2WIRE566'
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto 2WIRE566' has security, but secrets are required.
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Jan 13 17:27:11 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> inactive
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto 2WIRE566' has security, and secrets exist.  No new secrets needed.
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 13 17:27:16 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jan 13 17:27:21 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 13 17:27:26 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 13 17:27:26 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 13 17:27:31 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 13 17:27:36 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 13 17:27:36 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 13 17:27:41 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 13 17:27:46 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 13 17:27:46 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 13 17:27:51 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 13 17:27:56 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jan 13 17:27:56 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jan 13 17:27:56 Ubuntu NetworkManager: <info>  wlan0: link timed out.
Jan 13 17:28:01 Ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating

---

### Post by chili555 on 2011-01-15
Let's see if we have better luck with the native driver. Please detach the ethernet cable and do:```
sudo ifconfig wlan0 down
sudo rmmod ndiswrapper
sudo modprobe zd1211rw
sudo ifconfig wlan0 up
```Any better luck connecting? If so, we can make this permanent.

---

### Post by jsweet on 2011-01-16
I ran the following code:
sudo ifconfig wlan0 down
sudo rmmod ndiswrapper
sudo modprobe zd1211rw
sudo ifconfig wlan0 up

I still was unable to connect to the internet by this way.

I also ran a small test of my own. I booted from my live disk and attempted to connect to the internet in that interface. Same results as if I booted from the hard drive. I clicked on the internet symbol, selected my network (from the two available), it asked for my WEP 40/128 bit key which I promptly entered, and no connection. I don't know if this will aid in the diagnosis but I thought it might be a valuable thing to try.

---

### Post by chili555 on 2011-01-17
> I don't know if this will aid in the diagnosis but I thought it might be a valuable thing to try.It is very valuable. It shows that neither the native driver nor ndiswrapper will connect; they have the same symptom.

I have extensively googled zd1211rw and it seems to be relatively trouble-free. 

Please assure that the ethernet cable is detached as you are trying to connect. Network Manager is designed to switch to wired ethernet when it's available, effectively disallowing wireless. 
Please boot into the live CD and let's try to eliminate Network Manager as the culprit. These things I am asking you to do in the live CD environment will, in no way, affect your harddrive installation.

While booted into the live CD, do:```
sudo apt-get remove --purge network-manage*
```The wildcard * will remove everything with network-manage in it's name. Now do:```
sudo iwconfig wlan0 essid 2WIRE566
sudo iwconfig wlan0 key 0123456789
```Substitute your ten-digit WEP key here.```
sudo dhclient wlan0
```Does it connect? Are there any interesting messages here?```
dmesg | grep wlan
```

---

### Post by jsweet on 2011-01-17
I do not have an ethernet cable hooked in to my computer. It's a desktop and is too far away from my router (which is downstairs on the other side of the house).
I'll go run that code on the live disk now.

---

### Post by jsweet on 2011-01-17
No internet connection still but I have the results from the code I ran:


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get remove --purge network-manage*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting network-manager-pptp-gnome for regex 'network-manage*'
Note, selecting network-manager-pptp for regex 'network-manage*'
Note, selecting network-manager for regex 'network-manage*'
Note, selecting network-manager-gnome for regex 'network-manage*'
Note, selecting network-manager-vpnc-kde for regex 'network-manage*'
Note, selecting network-manager-openvpn-kde for regex 'network-manage*'
Note, selecting network-manager-pptp-kde for regex 'network-manage*'
Note, selecting network-manager-dev for regex 'network-manage*'
Note, selecting network-manager-kde for regex 'network-manage*'
The following packages will be REMOVED:
  network-manager* network-manager-gnome* network-manager-pptp*
  network-manager-pptp-gnome*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 8,405kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 128778 files and directories currently installed.)
Removing network-manager-gnome ...
Purging configuration files for network-manager-gnome ...
Removing network-manager ...
network-manager stop/waiting
Purging configuration files for network-manager ...
dpkg: warning: while removing network-manager, directory '/var/lib/NetworkManager' not empty so not removed.
Removing network-manager-pptp-gnome ...
Purging configuration files for network-manager-pptp-gnome ...
Removing network-manager-pptp ...
Purging configuration files for network-manager-pptp ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
ubuntu@ubuntu:~$ sudo iwconfig wlan0 essid 2wire566
ubuntu@ubuntu:~$ sudo iwconfig wlan0 key 7737667951
ubuntu@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1a:6b:cb:ef:f2
Sending on   LPF/wlan0/00:1a:6b:cb:ef:f2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ dmesg | grep wlan
[   58.099671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  370.471169] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Hope this helps or points us in the right direction.

---

### Post by chili555 on 2011-01-17
> ubuntu@ubuntu:~$ sudo iwconfig wlan0 essid [COLOR="Red"]2wire566[/COLOR]
ubuntu@ubuntu:~$ sudo iwconfig wlan0 key 7737667951
ubuntu@ubuntu:~$ sudo dhclient wlan0According to your scan in post #12, it's actually 2WIRE566:> johnsweet@Ubuntu:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:1F:B3:4F:8C: D9
ESSID:"2WIRE566"
Protocol:IEEE 802.11g
Mode:ManagedCase counts; please try again.

---

### Post by jsweet on 2011-01-17
Re-ran the code:

ubuntu@ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1a:6b:cb:ef:f2
Sending on   LPF/wlan0/00:1a:6b:cb:ef:f2
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.65 from 192.168.1.254
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.254
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.65 -- renewal in 33444 seconds
ubuntu@ubuntu:~$ dmesg | grep wlan
[   90.141717] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  412.932138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  412.945654] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
[  412.948671] wlan0: direct probe responded
[  412.948677] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
[  412.975655] wlan0: direct probe to AP 00:1f:b3:4f:8c:d9 (try 1)
[  412.978171] wlan0: direct probe responded
[  412.978177] wlan0: authenticate with AP 00:1f:b3:4f:8c:d9 (try 1)
[  412.983799] wlan0: authenticated
[  412.983843] wlan0: associate with AP 00:1f:b3:4f:8c:d9 (try 1)
[  412.985668] wlan0: RX AssocResp from 00:1f:b3:4f:8c:d9 (capab=0x431 status=0 aid=1)
[  412.985675] wlan0: associated
[  412.986820] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  423.944024] wlan0: no IPv6 routers present


I only attached th part that I thought was important. I have the rest of the text saved and can attach it in another post if you need it. It's just the same from before though.

---

### Post by chili555 on 2011-01-17
> It's just the same from before though.What??> bound to 192.168.1.65 -- renewal in 33444 secondsYou are connected. So the driver and Network Manager were not working well together, it appears. Are you ready to repair your permanent harddrive installation?

---

### Post by jsweet on 2011-01-17
I can work on it tonight or any other night past 8:30... For now I have to be away from the computer. Ill log back in and check for updates by 8:30

In Addition:
I am also off today (Tuesday) because of snow so I can work on it today.

---

### Post by chili555 on 2011-01-19
If you right-click the Network Manager icon and select Edit Connections, is you network listed as 2wire566 or 2WIRE566? That may be what allowed us to connect.

---

