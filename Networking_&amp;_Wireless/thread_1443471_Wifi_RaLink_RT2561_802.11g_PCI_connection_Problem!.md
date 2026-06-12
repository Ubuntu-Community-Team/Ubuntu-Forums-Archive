---
title: "Wifi RaLink RT2561 802.11g PCI connection Problem! Need Help!"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by radko87 on 2010-03-31
Hi guys.
Before i start i want to say that I'm new to Ubuntu (linux at all).

I have tried countless times to set up Wireless network adapter  "RaLink RT2561/RT61 802.11g PCI" on Ubuntu server 9.10 (don't ask why i need wireless on server) but there is no result.
When I installed it from CD, the driver rt61pci was loaded ... it found my card but i was unable to connect to any network...
So I followed few thread's in the forum and I installed the Windows drivers with ndiswrapper.

here some ifo
lspci | grep Network 
[HTML]
lspci | grep Network
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
[/HTML]i tried to scan for Wireless networks in range with :


[HTML]
sudo iwlist  wlan0 scan

wlan0     Scan completed :
          Cell 01 - Address: 00:23:8E:CE:36:96
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:23:8E:CE:36:97
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:16:0A:14:32:32
                    ESSID:"Velika's Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-13 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

[/HTML]And here comes the funny part

When i try to connect to a network - no matter if i use  ESSID or AP MAC, I'm unable to.

Here is a example
[HTML]
sudo iwconfig wlan0 essid "Velika's Network" key 67657267616e616574726f6c
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
[/HTML]The same happens if i try to connect not with ESSID but with AP MAC

I tried  to input the key not in HEX but in ASCII  with s:myPass , even tried s:"myPass"
(my pass is a single word it's not pass phrase )

If i don't specify the key no error is thrown.

here it the output of  >> sudo dhclient wlan0


[HTML]
Listening on LPF/wlan0/00:1f:1f:1b:62:c5
Sending on   LPF/wlan0/00:1f:1f:1b:62:c5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.

[/HTML]if tried  to

[HTML]
 sudo ifconfig wlan0 down 
makeing settings and then 
  sudo ifconfig wlan0 up

[/HTML]Same result.

I don't know what exactly is happening but a have the feeling that my card can't associate with any AP. 
There is something wrong with the key
[HTML]
 dmesg | grep -e ndis -e wlan
[   19.901585] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   20.584507] ndiswrapper: driver oem4 (Ralink Technology, Inc.,08/02/2006, 1.01.02.0000) loaded
[   20.585205] ndiswrapper 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[   20.600868] ndiswrapper: using IRQ 17
[   20.873179] wlan0: ethernet device 00:1f:1f:1b:62:c5 using serialized NDIS driver: oem4, version: 0x10001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0301.5.conf
[   20.873213] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.889648] usbcore: registered new interface driver ndiswrapper
[   20.889937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.837746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  236.493014] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  345.533636] ndiswrapper (add_wep_key:841): adding encryption key 1 failed (C0010015)
[  364.220271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1634.423086] ndiswrapper (add_wep_key:841): adding encryption key 1 failed (C0010015)
[ 1647.528980] ndiswrapper (add_wep_key:841): adding encryption key 1 failed (C0010015)

[/HTML]

Finaly here is my /etc/metwork/interfaces
[HTML]
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
 iface wlan0 inet dhcp
 wireless_essid "Velika's Network"
 wireless_key s:"gerganaetrol" 
 wireless-mode managed
[/HTML]I've tried with static ... setting the gateway,ip,network,pass but no effect.


ouu I've tried to install the lates RT61 driver but i could't  compile it ... it throwed 2 Errors ... (and i was folowing thread in the forum for "how to")

Sorry for the bad English.

I'll appreciate any help or suggestion.

---

### Post by chili555 on 2010-03-31
Is Network Manager installed and running on your system? NM will not easily give up control to manual configuration. Either remove all the stanzas from /etc/network/interfaces except for lo and let NM do the job, or remove NM entirely.

The biggest problem is that your configuration:> wireless_key s:"gerganaetrol" is appropriate for ASCII WEP. The access point you are trying to connect to is clearly not using WEP, but WPA:> Cell 03 - Address: 00:16:0A:14:32:32
                    ESSID:"Velika's Network"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-13 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : [COLOR="Red"]PSK[/COLOR]Even if you could get NM to hand over control to /etc/network/interfaces, the stanzas are incorrect for WPA.

Sometimes, network ESSIDs with spaces are difficult. If this is your access point, you might have better luck if you renamed it, for example, VelikaNet.

In my experience, NM will see my network, prompt me for the WPA/WPA2 Pre-shared key and connect. What has happened incorrectly in your case?

May I see:```
iwconfig
```Thanks.

---

### Post by radko87 on 2010-03-31
Here it is ... iwconfig


[HTML]
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/HTML]

---

### Post by chili555 on 2010-03-31
> **radko87 said:**
> Here it is ... iwconfig


[HTML]
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/HTML]It looks perfect! Address your WPA issue and I am confident you can connect.

---

### Post by radko87 on 2010-03-31
I'dont know how to deal with the WPA ... How to set the ecryption and the pass ?



[HTML]rado@master:~$ dmesg | grep -e wlan -e b43 -e bcm
[   20.873179] wlan0: ethernet device 00:1f:1f:1b:62:c5 using serialized NDIS driver: oem4, version: 0x10001, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 1814:0301.5.conf
[   20.873213] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   20.889937] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[/HTML]

---

### Post by radko87 on 2010-03-31
Problem Solved .... 
this thread helped a lot

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

The problem was indeed encryption ....

---

