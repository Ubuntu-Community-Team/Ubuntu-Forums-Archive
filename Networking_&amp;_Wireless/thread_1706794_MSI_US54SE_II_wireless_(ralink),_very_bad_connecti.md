---
title: "MSI US54SE II wireless (ralink), very bad connection"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by rowland on 2011-03-14
Hello everyone. Since i installed this wifi in my house, and using it on Windows 7, i havent had too many problems with it. But now that i want to use Linux, i started to notice that its very laggy, or my connection works wavy: now it works, now it doesnt.
I have been searching for info about all this, and i have discovered that i need a proper driver. 
([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported))    [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
there found the company that has got the proper drivers made for linux: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
There i downloaded: RT2501USB(RT73:RT2571W/RT2573/RT2671)
The problem with that was that after extracting it, a folder with the same name appears, but inside it there are other 2 folders. Both of them have 1 readme each. I've tried to "understand" what to do, or wich one do i have to install, without success.

I would apreciate very much if anyone could download it, read the readme of both folders, and explaining me what to do, step by step, with all the commands, and if possible, the meaning of the operations.
 (and i need to install both folders content?)

Any help is appreciated.
THANK YOU VERY MUCH

Details if needed:
Ubuntu 9.10, Karmic Coala 2.6.31-22-generic
MSI US54SE II (2)

LSUSB: 
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c529 Logitech, Inc. 
Bus 002 Device 002: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

IFCONFIG (i think the other ones aren't needed):

wlan0     Link encap:Ethernet  HWaddr 00:1d:0f:b3:28:2c  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:feb3:282c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:434145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50050275 (50.0 MB)  TX bytes:355244240 (355.2 MB)

IWCONFIG:
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"Kukamonga"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:E4:3E:E2   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

For easier communication or more info, you can e-mail me: [email]sosroli@gmail.com[/email]

Thank you again.

---

