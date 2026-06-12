---
title: "Intel 3945ABG not working"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by CbrPad on 2010-10-16
I've just installed Maverick and my wireless card doesn't seem to work properly.  Any suggestions ?

lspci | grep 3945 gives this...

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Iwconfig gives this...

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
right
iwlist wlan0 scan gives this...

wlan0     Failed to read scan data : Network is down

I've tried removing and modprobing iwl3945 but no luck.

---

### Post by chili555 on 2010-10-16
Let's do some diagnostics. Please post:```
rfkill list
dmesg | grep iwl
```Thanks.

---

### Post by CbrPad on 2010-10-16
Hi, thanks for the help !

rfkill list  gives...

1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


The next part gives this...


[   14.645944] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.645948] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   14.646044] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.646060] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.686445] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.686448] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.686603] iwl3945 0000:05:00.0: irq 45 for MSI/MSI-X
[   14.703213] phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 4038.072958] iwl3945 0000:05:00.0: PCI INT A disabled
[ 4042.523223] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network [   14.645944] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.645948] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   14.646044] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.646060] iwl3945 0000:05:00.0: setting latency timer to 64
[   14.686445] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.686448] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.686603] iwl3945 0000:05:00.0: irq 45 for MSI/MSI-X
[   14.703213] phy0: Selected rate control algorithm 'iwl-3945-rs'

---

### Post by chili555 on 2010-10-16
> 3: phy1: Wireless LAN
Soft blocked: yes
Hard blocked: yesThat suggests the wireless switch on the front of your laptop is switched to 'Off.' Please try switching it on.

---

### Post by CbrPad on 2010-10-16
Lol, I've done that several dozen times.  Switching it on and off just gives a red light, no blue.  It works fine in Mint and Windows.

---

### Post by chili555 on 2010-10-16
Please let us see:```
rfkill list all
```Both with and without the wireless switch switched. Also:```
lsmod | grep wmi
```If hp-wmi is listed, try:```
sudo rmmod -f hp-wmi
rfkill list all
```If removing the hp-wmi module works, we can blacklist it.

---

### Post by Vincent_Lin on 2010-10-20
Dear all,

My Intel wireless 3945abg chip on Sony VAIO is not working on 10.10 either.  Current states is like this:

1. Networkmanager would not see the card, thus no selection of wlreless routers even they are really available.  Actually, initially Networkmanager would not show at all, unless I specific kill it in terminal to force a restart, and NetworkManager would show.

2. When I typed 
```
iwlist wlan0 scanning
```
in terminal would return those available wireless routers.

3. When I typed 
```
sudo iwconfig wlan0 mode managed channel 1 essid "MyRouterEssid" key "MyRouterKey"
``` 
would complain 
Invalid argument "MyRouterKey"

I have tried download firmware for 3945, and tried the trick talked about this forum such as 
```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```
that did not work.

I am totally lost now - this card is powered on, active, can scan routers, but could not associate, and NetworkManager could not see it.

Thank in advance for any solutions.

---

### Post by chili555 on 2010-10-20
> key "MyRouterKey"Is the key hex or ascii? How many characters? May we see the scan details for your network, like this:```
Cell 01 - Address: 99:24:56:88:D7:77
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"mylilrouter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
```

---

### Post by Vincent_Lin on 2010-10-20
Thanks for the prompt reply.

1. The key is ascii, but only 5 characters.

The result of the scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:0B:6C:BB:F8:B3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"JennisonBCP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005106a0977
                    Extra: Last beacon: 4470ms ago
                    IE: Unknown: 000B4A656E6E69736F6E424350
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:03:52:93:0D:D0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"kodiak-wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000366293652e0
                    Extra: Last beacon: 4320ms ago
                    IE: Unknown: 000F6B6F6469616B2D776972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 03 - Address: 00:03:52:93:0D:D1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Kodiak-PUB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000036629365e79
                    Extra: Last beacon: 4310ms ago
                    IE: Unknown: 000A4B6F6469616B2D505542
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 04 - Address: 00:03:52:93:45:20
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"kodiak-wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011bbe1f6181
                    Extra: Last beacon: 11050ms ago
                    IE: Unknown: 000F6B6F6469616B2D776972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600
          Cell 05 - Address: 00:1E:52:79:3C:FF
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"NKTT WiFi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be20810180
                    Extra: Last beacon: 4460ms ago
                    IE: Unknown: 00114E4B54542057694669204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605001B00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301690120
          Cell 06 - Address: 00:03:52:93:45:21
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Kodiak-PUB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011bbe84f786
                    Extra: Last beacon: 4390ms ago
                    IE: Unknown: 000A4B6F6469616B2D505542
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600

```

I was trying to access the first one "JENNISONBCP".

Thanks again,

Vincent

---

### Post by Vincent_Lin on 2010-10-20
Also the result of iwconfig
```
vincent@vaio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```

Thanks.

Vincent

---

### Post by chili555 on 2010-10-20
It is very difficult and sometimes impossible to use manual methods to connect if Network Manager is running. Also, according to *man iwconfig*, ascii keys should be preceded with **s:**```
key/enc[ryption]
              Used  to  manipulate  encryption or scrambling keys and security mode.
To set the current encryption key, just enter  the  key  in  hex digits  as  XXXX-XXXX-XXXX-XXXX or XXXXXXXX.
To set a key other than the current key, prepend  or  append  [index]  to  the  key itself (this won't change which is the active key). 
[COLOR="Red"]You can also  enter the key as  an  ASCII  string  by  using  the  s:  prefix.[/COLOR]
```Is Network Manager not working as expected?

---

### Post by Vincent_Lin on 2010-10-20
chili555,

Thanks for the help.

At first, I issue
```
sudo /etc/init.d/network-manager stop
```
to stop network-Manager.  I ps-ed to check that it is not running.

I put the s: infront of the actual key, and the command
```
sudo iwconfig wlan0 mode managed channel 1 essid "myrouter" key s:"mykey"
```
does not return an error.

Then, the follwoing 
```
iwconfig
```
gives that wlan0 has an essid assigned, but Access Point is still Not-assocaited.

Still no networking.

Any more ideas?



Thanks again.

Vincent

---

### Post by chili555 on 2010-10-20
You must tell it how to connect. Either:```
sudo dhclient wlan0
```Or:```
sudo ifconfig wlan0 192.168.1.101 up
```In the latter case, you will be responsible to write /*etc/resolv.conf*.

---

### Post by Vincent_Lin on 2010-10-20
Thanks chili555,

I sent the code as you described:
```
sudo dhclient wlan0
```

Then what it came back on the terminal is like this:

It went through port 67 Interval 3 3 8 19 16 12, then it spit out
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I double checked with "iwlist wlan0 scnning" and this 3945 still sess all those routers out there, and "iwconfig" still says Access point: Not associated.

Any other ideas?

Thanks again,

Vincent

---

### Post by chili555 on 2010-10-20
And does ps still show Network Manager is gone? > Cell 01 - Address: 00:0B:6C:BB:F8:B3
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=[COLOR="Red"]31/70[/COLOR]  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"JennisonBCP"
Is the router close enough to get a reliable connection?

Again, is Network Manager not performing as expected?

---

### Post by Vincent_Lin on 2010-10-20
Hi chili555,

1. The networkmanager is not running.  ps confirms that.
2. The router is not close, but close enough for my other laptops to receive signals.
3. Network manager, when running, does not show available routers at all.  It looks as if wireless connection/hardware is diabled.  It looks sort of like wired connection when the wire is unplugged.

Thanks for helping me out.  I know it is puzzling enough.  

I read somewhere else in this forum that people actually brought 3945 back to work using some wireless driver in backport.  I am wondering if there is such thing for 10.10 yet, and what that set of debs would work, if it works.

Thanks.

Vincent

---

### Post by chili555 on 2010-10-20
It is indeed mystifying. My 3945ABG works perfectly. I am answering all these posts with it.> some wireless driver in backport. I am wondering if there is such thing for 10.10 yet, and what that set of debs would work, if it works.Not that I know of.

Is your wired ethernet connected all this time? Is the behavior the same if you reboot without the ethernet cable attached?

What does syslog have to say?```
sudo cat /var/log/syslog | grep -e iwl -e wlan
```

---

### Post by Vincent_Lin on 2010-10-20
chili555,

I did not have my wired ethernet connected all the time.  My office networking setup goes to Internet via a proxy, which I hate a lot - because I have to change the proxy setting all the time - system wide proxy, and synaptic/apt-get uses their own proxy setting, then again firefox can either use system-wide proxy setting or its own.  

But I do have a company issued USB760 boradband card with Verizon, which works flawlessly since 9.04. But I have it on and off during this session working with you.

Here is the syslog iwl related:
> Oct 20 15:28:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:28:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 15:28:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 15:28:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 15:28:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 15:28:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 15:29:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 15:33:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:33:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 15:33:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 15:33:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 15:33:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 15:33:46 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 15:33:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 15:41:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:41:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 15:41:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 15:41:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 15:41:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 15:42:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 15:42:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 15:42:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 15:50:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:50:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 15:50:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 15:50:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 15:50:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 15:50:46 vaio kernel: [ 2589.851093] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:50:46 vaio kernel: [ 2589.853281] wlan0: authenticated
Oct 20 15:50:46 vaio kernel: [ 2589.853995] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:50:46 vaio kernel: [ 2589.857561] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=4)
Oct 20 15:50:46 vaio kernel: [ 2589.857566] wlan0: associated
Oct 20 15:50:46 vaio kernel: [ 2589.860140] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 15:50:46 vaio kernel: [ 2589.900194] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:50:48 vaio avahi-daemon[1089]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::218:deff:fe77:86b9.
Oct 20 15:50:48 vaio avahi-daemon[1089]: New relevant interface wlan0.IPv6 for mDNS.
Oct 20 15:50:48 vaio avahi-daemon[1089]: Registering new address record for fe80::218:deff:fe77:86b9 on wlan0.*.
Oct 20 15:50:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 15:50:57 vaio kernel: [ 2600.542572] wlan0: no IPv6 routers present
Oct 20 15:53:30 vaio kernel: [ 2753.993032] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:53:30 vaio kernel: [ 2753.995205] wlan0: authenticated
Oct 20 15:53:30 vaio kernel: [ 2753.995260] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:53:30 vaio kernel: [ 2753.998474] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=4)
Oct 20 15:53:30 vaio kernel: [ 2753.998480] wlan0: associated
Oct 20 15:53:30 vaio kernel: [ 2754.030128] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:53:54 vaio kernel: [ 2778.129018] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:53:54 vaio kernel: [ 2778.131818] wlan0: authenticated
Oct 20 15:53:54 vaio kernel: [ 2778.131876] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:53:54 vaio kernel: [ 2778.135438] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=4)
Oct 20 15:53:54 vaio kernel: [ 2778.135444] wlan0: associated
Oct 20 15:53:55 vaio kernel: [ 2778.170184] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:53:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:53:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 15:54:02 vaio kernel: [ 2785.360249] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:54:02 vaio kernel: [ 2785.362425] wlan0: authenticated
Oct 20 15:54:02 vaio kernel: [ 2785.362480] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:54:02 vaio kernel: [ 2785.365697] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=4)
Oct 20 15:54:02 vaio kernel: [ 2785.365704] wlan0: associated
Oct 20 15:54:02 vaio kernel: [ 2785.390181] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:54:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 15:54:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 15:54:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 15:54:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 15:55:16 vaio NetworkManager[2904]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 15:55:16 vaio NetworkManager[2904]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 15:55:16 vaio NetworkManager[2904]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 15:55:16 vaio NetworkManager[2904]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 15:55:16 vaio NetworkManager[2904]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 15:55:16 vaio NetworkManager[2904]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 15:55:16 vaio NetworkManager[2904]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 15:55:16 vaio NetworkManager[2904]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 15:55:39 vaio kernel: [ 2882.624519] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:55:39 vaio kernel: [ 2882.626688] wlan0: authenticated
Oct 20 15:55:39 vaio kernel: [ 2882.631381] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:55:39 vaio kernel: [ 2882.634944] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 15:55:39 vaio kernel: [ 2882.634949] wlan0: associated
Oct 20 15:55:39 vaio kernel: [ 2882.660130] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:56:28 vaio NetworkManager[2946]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 15:56:28 vaio NetworkManager[2946]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 15:56:28 vaio NetworkManager[2946]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 15:56:28 vaio NetworkManager[2946]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 15:56:28 vaio NetworkManager[2946]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 15:56:28 vaio NetworkManager[2946]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 15:56:28 vaio NetworkManager[2946]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 15:56:28 vaio NetworkManager[2946]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 15:56:47 vaio NetworkManager[2953]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 15:56:47 vaio NetworkManager[2953]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 15:56:47 vaio NetworkManager[2953]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 15:56:47 vaio NetworkManager[2953]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 15:56:47 vaio NetworkManager[2953]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 15:56:47 vaio NetworkManager[2953]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 15:56:47 vaio NetworkManager[2953]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 15:56:47 vaio NetworkManager[2953]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 15:56:55 vaio kernel: [ 2958.322295] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:56:55 vaio kernel: [ 2958.324470] wlan0: authenticated
Oct 20 15:56:55 vaio kernel: [ 2958.324528] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:56:55 vaio kernel: [ 2958.327822] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 15:56:55 vaio kernel: [ 2958.327828] wlan0: associated
Oct 20 15:56:55 vaio kernel: [ 2958.352620] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:58:13 vaio kernel: [ 3036.202982] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:58:13 vaio kernel: [ 3036.205156] wlan0: authenticated
Oct 20 15:58:13 vaio kernel: [ 3036.205212] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 15:58:13 vaio kernel: [ 3036.208426] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 15:58:13 vaio kernel: [ 3036.208432] wlan0: associated
Oct 20 15:58:13 vaio kernel: [ 3036.232657] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 15:58:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:58:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 15:58:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 15:58:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 15:59:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 15:59:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 15:59:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 16:03:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:03:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 16:03:38 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 16:03:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 16:04:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 16:04:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 16:09:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:09:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 16:09:28 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 16:09:38 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 16:09:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 16:10:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 16:10:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 16:15:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:15:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 16:16:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 16:16:13 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 16:16:34 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 16:16:41 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 16:16:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 20 16:23:24 vaio kernel: [ 4516.830101] iwl3945 0000:06:00.0: power state changed by ACPI to D3
Oct 20 16:23:24 vaio kernel: [ 4518.851817] iwl3945 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Oct 20 16:23:24 vaio kernel: [ 4518.851884] iwl3945 0000:06:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xde100000)
Oct 20 16:23:24 vaio kernel: [ 4518.851897] iwl3945 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 20 16:23:24 vaio kernel: [ 4518.851916] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
Oct 20 16:23:24 vaio kernel: [ 4518.858503] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:23:24 vaio kernel: [ 4518.858682] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:23:24 vaio kernel: [ 4518.859432] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:23:24 vaio kernel: [ 4518.859870] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:45:50 vaio kernel: [   15.107226] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Oct 20 16:45:50 vaio kernel: [   15.107230] iwl3945: Copyright(c) 2003-2010 Intel Corporation
Oct 20 16:45:50 vaio kernel: [   15.107309] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:45:50 vaio kernel: [   15.107323] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 16:45:50 vaio kernel: [   15.107342] iwl3945 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 20 16:45:50 vaio kernel: [   15.107356] iwl3945 0000:06:00.0: setting latency timer to 64
Oct 20 16:45:50 vaio kernel: [   15.216000] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Oct 20 16:45:50 vaio kernel: [   15.216004] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
Oct 20 16:45:50 vaio kernel: [   15.216160] iwl3945 0000:06:00.0: irq 46 for MSI/MSI-X
Oct 20 16:45:50 vaio kernel: [   15.229560] phy0: Selected rate control algorithm 'iwl-3945-rs'
Oct 20 16:45:50 vaio kernel: [   15.705853] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
Oct 20 16:45:50 vaio kernel: [   15.912004] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 16:45:50 vaio NetworkManager[1069]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 16:45:50 vaio NetworkManager[1069]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 16:45:50 vaio NetworkManager[1069]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 16:45:50 vaio NetworkManager[1069]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 16:45:50 vaio NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 16:45:51 vaio NetworkManager[1069]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 16:45:51 vaio NetworkManager[1069]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 16:45:51 vaio NetworkManager[1069]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 16:45:51 vaio NetworkManager[1069]: <info> (wlan0): supplicant manager state:  down -> idle
Oct 20 16:45:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 16:46:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 16:46:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 16:46:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 16:46:48 vaio avahi-autoipd(wlan0)[1956]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 16:46:48 vaio avahi-autoipd(wlan0)[1956]: Successfully called chroot().
Oct 20 16:46:48 vaio avahi-autoipd(wlan0)[1956]: Successfully dropped root privileges.
Oct 20 16:46:48 vaio avahi-autoipd(wlan0)[1956]: Starting with address 169.254.9.239
Oct 20 16:46:53 vaio avahi-autoipd(wlan0)[1956]: Callout BIND, address 169.254.9.239 on interface wlan0
Oct 20 16:46:53 vaio avahi-daemon[1072]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 16:46:53 vaio avahi-daemon[1072]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 16:46:53 vaio avahi-daemon[1072]: Registering new address record for 169.254.9.239 on wlan0.IPv4.
Oct 20 16:46:57 vaio avahi-autoipd(wlan0)[1956]: Successfully claimed IP address 169.254.9.239
Oct 20 16:47:58 vaio NetworkManager[2034]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 16:47:58 vaio NetworkManager[2034]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 16:47:58 vaio NetworkManager[2034]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 16:47:58 vaio NetworkManager[2034]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 16:47:58 vaio NetworkManager[2034]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 16:47:58 vaio NetworkManager[2034]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 16:47:58 vaio NetworkManager[2034]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 16:47:58 vaio NetworkManager[2034]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 16:48:15 vaio kernel: [  164.504390] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 16:48:15 vaio kernel: [  164.507044] wlan0: authenticated
Oct 20 16:48:15 vaio kernel: [  164.507714] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 16:48:15 vaio kernel: [  164.510933] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=1)
Oct 20 16:48:15 vaio kernel: [  164.510939] wlan0: associated
Oct 20 16:48:15 vaio kernel: [  164.513816] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 16:48:15 vaio kernel: [  164.540133] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 16:48:17 vaio avahi-daemon[1072]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::218:deff:fe77:86b9.
Oct 20 16:48:17 vaio avahi-daemon[1072]: New relevant interface wlan0.IPv6 for mDNS.
Oct 20 16:48:17 vaio avahi-daemon[1072]: Registering new address record for fe80::218:deff:fe77:86b9 on wlan0.*.
Oct 20 16:48:26 vaio kernel: [  175.340037] wlan0: no IPv6 routers present
Oct 20 16:51:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:51:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:51:28 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 16:51:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 16:51:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 16:51:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 16:52:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 16:52:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 16:57:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:57:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:57:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 16:57:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 16:57:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:01:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:01:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:01:13 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:01:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 17:01:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 17:01:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:01:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 17:02:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 17:05:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:05:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:05:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 17:05:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 17:05:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:06:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 17:06:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 17:06:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 17:06:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:09:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:09:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:09:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 17:09:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 17:10:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 17:10:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:14:14 vaio kernel: [   15.140716] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Oct 20 17:14:14 vaio kernel: [   15.140720] iwl3945: Copyright(c) 2003-2010 Intel Corporation
Oct 20 17:14:14 vaio kernel: [   15.140795] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 17:14:14 vaio kernel: [   15.140809] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 17:14:14 vaio kernel: [   15.140828] iwl3945 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
Oct 20 17:14:14 vaio kernel: [   15.140842] iwl3945 0000:06:00.0: setting latency timer to 64
Oct 20 17:14:14 vaio kernel: [   15.205760] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Oct 20 17:14:14 vaio kernel: [   15.205764] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
Oct 20 17:14:14 vaio kernel: [   15.205917] iwl3945 0000:06:00.0: irq 47 for MSI/MSI-X
Oct 20 17:14:14 vaio kernel: [   15.236791] phy0: Selected rate control algorithm 'iwl-3945-rs'
Oct 20 17:14:14 vaio kernel: [   15.443589] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
Oct 20 17:14:14 vaio kernel: [   15.855485] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 17:14:14 vaio NetworkManager[1059]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 17:14:14 vaio NetworkManager[1059]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 17:14:14 vaio NetworkManager[1059]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 17:14:14 vaio NetworkManager[1059]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 17:14:14 vaio NetworkManager[1059]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 17:14:14 vaio NetworkManager[1059]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 17:14:14 vaio NetworkManager[1059]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 17:14:14 vaio NetworkManager[1059]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 17:14:14 vaio NetworkManager[1059]: <info> (wlan0): supplicant manager state:  down -> idle
Oct 20 17:14:16 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 17:14:16 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 17:14:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:14:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 17:14:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 17:14:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 17:14:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 17:15:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 17:15:16 vaio avahi-autoipd(wlan0)[1890]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 17:15:16 vaio avahi-autoipd(wlan0)[1890]: Successfully called chroot().
Oct 20 17:15:16 vaio avahi-autoipd(wlan0)[1890]: Successfully dropped root privileges.
Oct 20 17:15:16 vaio avahi-autoipd(wlan0)[1890]: Starting with address 169.254.9.239
Oct 20 17:15:21 vaio avahi-autoipd(wlan0)[1890]: Callout BIND, address 169.254.9.239 on interface wlan0
Oct 20 17:15:21 vaio avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 17:15:21 vaio avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 17:15:21 vaio avahi-daemon[1062]: Registering new address record for 169.254.9.239 on wlan0.IPv4.
Oct 20 17:15:25 vaio avahi-autoipd(wlan0)[1890]: Successfully claimed IP address 169.254.9.239
Oct 20 17:15:48 vaio NetworkManager[1985]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 17:15:48 vaio NetworkManager[1985]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 17:15:48 vaio NetworkManager[1985]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 17:15:48 vaio NetworkManager[1985]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 17:15:48 vaio NetworkManager[1985]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 17:15:48 vaio NetworkManager[1985]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 17:15:48 vaio NetworkManager[1985]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 3)
Oct 20 17:15:48 vaio NetworkManager[1985]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 17:19:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:19:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:19:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 17:19:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 17:19:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 17:26:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:26:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:27:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:27:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 17:27:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 17:27:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 17:27:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:31:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:31:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 17:31:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 17:31:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:32:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 17:32:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 17:36:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:36:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:36:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 17:36:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 17:36:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 17:36:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 17:37:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 17:43:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:43:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:43:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:43:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 17:43:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 17:43:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 17:44:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 17:47:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:47:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 17:47:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 17:47:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 17:47:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 17:47:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 17:47:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 17:51:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:51:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:51:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 17:51:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 17:51:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 17:52:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 17:57:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 17:57:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 17:57:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 17:57:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 17:57:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 17:57:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 18:02:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:02:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 18:02:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 18:02:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:02:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 18:03:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:03:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 20 18:06:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:06:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 18:06:34 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 18:06:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 18:06:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:07:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 18:07:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:11:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:11:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 18:12:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 18:12:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:12:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 18:12:38 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 18:16:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:16:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:16:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 18:16:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:16:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 18:17:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 18:19:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:20:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:20:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 18:20:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 18:20:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 18:20:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 18:25:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:25:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 18:25:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:25:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:25:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 18:26:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 18:30:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:30:46 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 18:30:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 18:31:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:31:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 18:31:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 18:35:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:35:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 18:35:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 18:35:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 18:35:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:36:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 18:40:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:40:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 18:40:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:40:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:40:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 18:41:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 18:41:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 18:46:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:46:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:46:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 18:47:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:47:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:47:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 18:47:34 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 18:47:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 18:52:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:52:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:52:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 18:52:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 18:52:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 18:52:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 18:53:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:53:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:55:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 18:56:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 18:56:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 18:56:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 18:56:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 18:56:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:00:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:00:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 19:00:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 19:00:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 19:00:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 19:01:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 19:06:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:06:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 19:06:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 19:06:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 19:06:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 19:07:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:07:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 19:12:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:12:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 19:13:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 19:13:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 19:13:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 19:13:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 19:18:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:18:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 19:18:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 19:18:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 19:18:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 19:19:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:23:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:23:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:23:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 19:24:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 19:24:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:24:34 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:31:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:31:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:31:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 19:31:38 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 19:31:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:32:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:32:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 19:36:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:36:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 19:37:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 19:37:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:37:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 19:37:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 19:37:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 19:43:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:43:47 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 19:43:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 19:44:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 19:44:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 19:44:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 19:51:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:51:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 19:51:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:51:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:51:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:51:47 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 19:52:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 19:59:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 19:59:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 19:59:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 19:59:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 19:59:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 19:59:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 19:59:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 20:05:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:05:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 20:05:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 20:05:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:05:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 20:06:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:06:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:06:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:11:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:11:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:11:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:11:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:11:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:12:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 20 20:16:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:16:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 20:16:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 20:16:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:16:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:17:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:17:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:18:08 vaio kernel: [11050.810315] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:18:08 vaio kernel: [11050.812569] wlan0: authenticated
Oct 20 20:18:08 vaio kernel: [11050.814067] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:18:08 vaio kernel: [11050.817446] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 20:18:08 vaio kernel: [11050.817452] wlan0: associated
Oct 20 20:18:08 vaio kernel: [11050.820369] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 20:18:08 vaio kernel: [11050.850140] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 20:18:09 vaio avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::218:deff:fe77:86b9.
Oct 20 20:18:09 vaio avahi-daemon[1062]: New relevant interface wlan0.IPv6 for mDNS.
Oct 20 20:18:09 vaio avahi-daemon[1062]: Registering new address record for fe80::218:deff:fe77:86b9 on wlan0.*.
Oct 20 20:18:18 vaio kernel: [11061.040049] wlan0: no IPv6 routers present
Oct 20 20:20:11 vaio kernel: [11173.838539] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:20:11 vaio kernel: [11173.840681] wlan0: authenticated
Oct 20 20:20:11 vaio kernel: [11173.840741] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:20:11 vaio kernel: [11173.844108] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 20:20:11 vaio kernel: [11173.844115] wlan0: associated
Oct 20 20:20:11 vaio kernel: [11173.880188] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 20:21:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:21:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:21:46 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:22:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:22:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 20:25:34 vaio kernel: [11496.829741] wlan0: authenticate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:25:34 vaio kernel: [11496.831880] wlan0: authenticated
Oct 20 20:25:34 vaio kernel: [11496.831934] wlan0: associate with 00:0b:6c:bb:f8:b3 (try 1)
Oct 20 20:25:34 vaio kernel: [11496.835571] wlan0: RX AssocResp from 00:0b:6c:bb:f8:b3 (capab=0x411 status=0 aid=2)
Oct 20 20:25:34 vaio kernel: [11496.835578] wlan0: associated
Oct 20 20:25:34 vaio kernel: [11496.860160] wlan0: deauthenticating from 00:0b:6c:bb:f8:b3 by local choice (reason=3)
Oct 20 20:28:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:28:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:28:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:28:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:28:47 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 20:28:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 20:29:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 20:35:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:35:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:35:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 20:35:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 20:36:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 20:36:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 20:36:37 vaio avahi-autoipd(wlan0)[1890]: Got SIGTERM, quitting.
Oct 20 20:36:37 vaio avahi-autoipd(wlan0)[1890]: Callout STOP, address 169.254.9.239 on interface wlan0
Oct 20 20:36:37 vaio avahi-daemon[1062]: Withdrawing address record for 169.254.9.239 on wlan0.
Oct 20 20:36:37 vaio avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:36:37 vaio avahi-daemon[1062]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 20:36:37 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:36:37 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:36:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:36:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 20:36:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:36:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:37:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 20:37:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 20:37:38 vaio avahi-autoipd(wlan0)[2971]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 20:37:38 vaio avahi-autoipd(wlan0)[2971]: Successfully called chroot().
Oct 20 20:37:38 vaio avahi-autoipd(wlan0)[2971]: Successfully dropped root privileges.
Oct 20 20:37:38 vaio avahi-autoipd(wlan0)[2971]: Starting with address 169.254.9.239
Oct 20 20:37:43 vaio avahi-autoipd(wlan0)[2971]: Callout BIND, address 169.254.9.239 on interface wlan0
Oct 20 20:37:43 vaio avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:37:43 vaio avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 20:37:43 vaio avahi-daemon[1062]: Registering new address record for 169.254.9.239 on wlan0.IPv4.
Oct 20 20:37:47 vaio avahi-autoipd(wlan0)[2971]: Successfully claimed IP address 169.254.9.239
Oct 20 20:38:03 vaio avahi-daemon[1062]: Interface wlan0.IPv6 no longer relevant for mDNS.
Oct 20 20:38:03 vaio avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::218:deff:fe77:86b9.
Oct 20 20:38:03 vaio avahi-daemon[1062]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 20:38:03 vaio avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:38:03 vaio dhclient: receive_packet failed on wlan0: Network is down
Oct 20 20:38:03 vaio dhclient: receive_packet failed on wlan0: Network is down
Oct 20 20:38:03 vaio avahi-autoipd(wlan0)[2971]: if_indextoname() failed: No such device or address
Oct 20 20:38:03 vaio avahi-autoipd(wlan0)[2971]: Callout STOP, address 169.254.9.239 on interface (null)
Oct 20 20:38:03 vaio avahi-autoipd(wlan0)[2972]: if_indextoname() failed: No such device or address
Oct 20 20:38:03 vaio avahi-daemon[1062]: Withdrawing address record for fe80::218:deff:fe77:86b9 on wlan0.
Oct 20 20:38:03 vaio avahi-daemon[1062]: Withdrawing address record for 169.254.9.239 on wlan0.
Oct 20 20:38:03 vaio avahi-daemon[1062]: Withdrawing workstation service for wlan0.
Oct 20 20:38:03 vaio kernel: [12245.602974] iwl3945 0000:06:00.0: PCI INT A disabled
Oct 20 20:38:03 vaio dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1927
Oct 20 20:38:37 vaio kernel: [12279.512363] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Oct 20 20:38:37 vaio kernel: [12279.512367] iwl3945: Copyright(c) 2003-2010 Intel Corporation
Oct 20 20:38:37 vaio kernel: [12279.512459] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 20:38:37 vaio kernel: [12279.512473] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 20:38:37 vaio kernel: [12279.512493] iwl3945 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
Oct 20 20:38:37 vaio kernel: [12279.512529] iwl3945 0000:06:00.0: setting latency timer to 64
Oct 20 20:38:37 vaio kernel: [12279.553798] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Oct 20 20:38:37 vaio kernel: [12279.553802] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
Oct 20 20:38:37 vaio kernel: [12279.553952] iwl3945 0000:06:00.0: irq 47 for MSI/MSI-X
Oct 20 20:38:37 vaio kernel: [12279.554523] phy1: Selected rate control algorithm 'iwl-3945-rs'
Oct 20 20:38:37 vaio kernel: [12279.558710] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
Oct 20 20:38:37 vaio kernel: [12279.581434] WARNING: at /build/buildd/linux-2.6.35/drivers/net/wireless/iwlwifi/iwl-core.c:2044 iwl_mac_add_interface+0x127/0x150 [iwlcore]()
Oct 20 20:38:37 vaio kernel: [12279.581440] Modules linked in: iwl3945 ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt option usb_wwan usbserial parport_pc ppdev tpm_infineon rfcomm binfmt_misc sco bnep l2cap nvidia(P) snd_hda_codec_idt arc4 pcmcia snd_hda_intel joydev snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwlcore snd_timer snd_seq_device tpm_tis mac80211 sony_laptop tpm tifm_7xx1 tpm_bios lp btusb tifm_core yenta_socket pcmcia_rsrc snd parport bluetooth pcmcia_core psmouse led_class soundcore serio_raw intel_agp cfg80211 snd_page_alloc usb_storage firewire_ohci firewire_core crc_itu_t sky2 [last unloaded: iwl3945]
Oct 20 20:38:37 vaio kernel: [12279.581515]  [<ffffffffa0bb39f7>] iwl_mac_add_interface+0x127/0x150 [iwlcore]
Oct 20 20:38:37 vaio kernel: [12279.692141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 20:38:38 vaio kernel: [12280.841856] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 20:38:38 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:38:38 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:38:38 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:38:41 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:38:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:38:50 vaio kernel: [12293.090078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:38:58 vaio kernel: [12300.440072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:39:05 vaio kernel: [12307.792615] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:12 vaio kernel: [12315.140073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 20:39:20 vaio kernel: [12322.490069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 20:39:32 vaio kernel: [12334.740067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:39 vaio avahi-autoipd(wlan0)[3053]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 20:39:39 vaio avahi-autoipd(wlan0)[3053]: Successfully called chroot().
Oct 20 20:39:39 vaio avahi-autoipd(wlan0)[3053]: Successfully dropped root privileges.
Oct 20 20:39:39 vaio avahi-autoipd(wlan0)[3053]: Starting with address 169.254.9.239
Oct 20 20:39:39 vaio kernel: [12342.090072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:39 vaio avahi-autoipd(wlan0)[3053]: Got SIGTERM, quitting.
Oct 20 20:39:39 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:39:39 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:39:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:39:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 20:39:46 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:39:47 vaio kernel: [12349.442575] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:39:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 20:39:54 vaio kernel: [12356.790078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:01 vaio kernel: [12364.140065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:06 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:40:06 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:40:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:40:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:40:09 vaio kernel: [12371.510070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:40:16 vaio kernel: [12378.870070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:40:23 vaio kernel: [12386.250063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:31 vaio kernel: [12393.600075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:38 vaio kernel: [12400.950083] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Oct 20 20:40:45 vaio kernel: [12408.310062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:53 vaio kernel: [12415.660071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:40:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 20:41:00 vaio kernel: [12423.020069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:07 vaio avahi-autoipd(wlan0)[3103]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 20:41:07 vaio avahi-autoipd(wlan0)[3103]: Successfully called chroot().
Oct 20 20:41:07 vaio avahi-autoipd(wlan0)[3103]: Successfully dropped root privileges.
Oct 20 20:41:07 vaio avahi-autoipd(wlan0)[3103]: Starting with address 169.254.9.239
Oct 20 20:41:08 vaio kernel: [12430.380070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:11 vaio avahi-autoipd(wlan0)[3103]: Callout BIND, address 169.254.9.239 on interface wlan0
Oct 20 20:41:11 vaio avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:41:11 vaio avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 20:41:11 vaio avahi-daemon[1062]: Registering new address record for 169.254.9.239 on wlan0.IPv4.
Oct 20 20:41:15 vaio kernel: [12437.740076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:15 vaio avahi-autoipd(wlan0)[3103]: Successfully claimed IP address 169.254.9.239
Oct 20 20:41:22 vaio kernel: [12445.090078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:30 vaio kernel: [12452.440062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:37 vaio kernel: [12459.790065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:44 vaio kernel: [12467.140065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:52 vaio kernel: [12474.490067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:41:59 vaio kernel: [12481.840058] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:06 vaio kernel: [12489.190077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:14 vaio kernel: [12496.540075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:21 vaio kernel: [12503.890062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:28 vaio kernel: [12511.240071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:36 vaio kernel: [12518.590068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:43 vaio kernel: [12525.940074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:50 vaio kernel: [12533.290066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:42:58 vaio kernel: [12540.650071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:05 vaio kernel: [12548.020067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:13 vaio kernel: [12555.390064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:20 vaio kernel: [12562.740071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:27 vaio kernel: [12570.090078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:35 vaio kernel: [12577.440068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:42 vaio kernel: [12584.792599] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:49 vaio kernel: [12592.140064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:43:57 vaio kernel: [12599.490066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:04 vaio kernel: [12606.850070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:11 vaio kernel: [12614.200070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:13 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:44:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:44:19 vaio kernel: [12621.570076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:44:26 vaio kernel: [12628.930063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:44:33 vaio kernel: [12636.280129] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:41 vaio kernel: [12643.640076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:44:48 vaio kernel: [12650.990064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:55 vaio kernel: [12658.340067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:44:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:45:03 vaio kernel: [12665.690085] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:45:10 vaio kernel: [12673.050072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:18 vaio kernel: [12680.400074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:25 vaio kernel: [12687.750076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:32 vaio kernel: [12695.100079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:40 vaio kernel: [12702.450073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:41 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:45:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:45:47 vaio kernel: [12709.800072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:45:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:45:54 vaio kernel: [12717.150088] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:02 vaio kernel: [12724.500076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:46:09 vaio kernel: [12731.850074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:46:16 vaio kernel: [12739.200072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:24 vaio kernel: [12746.550075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:46:31 vaio kernel: [12753.900070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:38 vaio kernel: [12761.250070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:46:46 vaio kernel: [12768.600066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:46:53 vaio kernel: [12775.950077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:00 vaio kernel: [12783.300072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:08 vaio kernel: [12790.650075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:15 vaio kernel: [12798.000064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:23 vaio kernel: [12805.350074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:30 vaio kernel: [12812.700082] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:37 vaio kernel: [12820.050078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:45 vaio kernel: [12827.400076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:52 vaio kernel: [12834.750069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:47:59 vaio kernel: [12842.112568] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:07 vaio kernel: [12849.470071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:14 vaio kernel: [12856.820065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:21 vaio kernel: [12864.170066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:29 vaio kernel: [12871.520064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:36 vaio kernel: [12878.870075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:43 vaio kernel: [12886.220066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:51 vaio kernel: [12893.570074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:48:58 vaio kernel: [12900.920074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:05 vaio kernel: [12908.270076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:13 vaio kernel: [12915.620073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:20 vaio kernel: [12922.970073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:27 vaio kernel: [12930.320071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:35 vaio kernel: [12937.670063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:42 vaio kernel: [12945.030073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:50 vaio kernel: [12952.380067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:49:57 vaio kernel: [12959.730066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:04 vaio kernel: [12967.080080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:12 vaio kernel: [12974.430073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:19 vaio kernel: [12981.780060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:26 vaio kernel: [12989.130066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:34 vaio kernel: [12996.480076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:41 vaio kernel: [13003.840071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:48 vaio kernel: [13011.190074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:50:56 vaio kernel: [13018.540066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:03 vaio kernel: [13025.890071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:10 vaio kernel: [13033.240061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:18 vaio kernel: [13040.590071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:25 vaio kernel: [13047.940074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:32 vaio kernel: [13055.290059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:40 vaio kernel: [13062.640070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:47 vaio kernel: [13069.990072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:51:54 vaio kernel: [13077.340066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:02 vaio kernel: [13084.690076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:09 vaio kernel: [13092.040079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:52:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:52:17 vaio kernel: [13099.400073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:21 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:52:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:52:24 vaio kernel: [13106.760069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 20:52:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 20:52:31 vaio kernel: [13114.110062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 20:52:39 vaio kernel: [13121.460070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:41 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:52:46 vaio kernel: [13128.810063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:53 vaio kernel: [13136.160070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:52:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 20:52:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 20:53:01 vaio kernel: [13143.510066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:53:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 20:53:08 vaio kernel: [13150.860065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:15 vaio kernel: [13158.210073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:53:17 vaio avahi-autoipd(wlan0)[3103]: Got SIGTERM, quitting.
Oct 20 20:53:17 vaio avahi-autoipd(wlan0)[3103]: Callout STOP, address 169.254.9.239 on interface wlan0
Oct 20 20:53:17 vaio avahi-daemon[1062]: Withdrawing address record for 169.254.9.239 on wlan0.
Oct 20 20:53:17 vaio avahi-daemon[1062]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:53:17 vaio avahi-daemon[1062]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 20:53:17 vaio dhclient: Listening on LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:53:17 vaio dhclient: Sending on   LPF/wlan0/00:18:de:77:86:b9
Oct 20 20:53:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:53:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:53:23 vaio kernel: [13165.560088] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 20:53:30 vaio kernel: [13172.910067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:53:37 vaio kernel: [13180.260074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:45 vaio kernel: [13187.640074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:48 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 20:53:52 vaio kernel: [13194.990074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:53:59 vaio kernel: [13202.340075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 20:54:07 vaio kernel: [13209.690084] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:14 vaio kernel: [13217.040079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:18 vaio avahi-autoipd(wlan0)[3181]: Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 108).
Oct 20 20:54:18 vaio avahi-autoipd(wlan0)[3181]: Successfully called chroot().
Oct 20 20:54:18 vaio avahi-autoipd(wlan0)[3181]: Successfully dropped root privileges.
Oct 20 20:54:18 vaio avahi-autoipd(wlan0)[3181]: Starting with address 169.254.9.239
Oct 20 20:54:22 vaio kernel: [13224.390062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:22 vaio avahi-autoipd(wlan0)[3181]: Callout BIND, address 169.254.9.239 on interface wlan0
Oct 20 20:54:22 vaio avahi-daemon[1062]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.239.
Oct 20 20:54:22 vaio avahi-daemon[1062]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 20:54:22 vaio avahi-daemon[1062]: Registering new address record for 169.254.9.239 on wlan0.IPv4.
Oct 20 20:54:26 vaio avahi-autoipd(wlan0)[3181]: Successfully claimed IP address 169.254.9.239
Oct 20 20:54:29 vaio kernel: [13231.740071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:36 vaio kernel: [13239.100074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:44 vaio kernel: [13246.450063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:51 vaio kernel: [13253.800072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:54:58 vaio kernel: [13261.150070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:06 vaio kernel: [13268.500065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:13 vaio kernel: [13275.850072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:20 vaio kernel: [13283.200072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:28 vaio kernel: [13290.550071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:35 vaio kernel: [13297.900065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:42 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:55:42 vaio kernel: [13305.250074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:55:50 vaio kernel: [13312.600072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:55:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Oct 20 20:55:57 vaio kernel: [13319.950074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:04 vaio kernel: [13327.300066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 20:56:12 vaio kernel: [13334.650070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:19 vaio kernel: [13342.000058] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 20:56:27 vaio kernel: [13349.350074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 20:56:34 vaio kernel: [13356.710064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:41 vaio kernel: [13364.060083] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:49 vaio kernel: [13371.410073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:56:56 vaio kernel: [13378.760073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:03 vaio kernel: [13386.120154] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:11 vaio kernel: [13393.470077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:18 vaio kernel: [13400.820073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:25 vaio kernel: [13408.170071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:33 vaio kernel: [13415.520064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:40 vaio kernel: [13422.880066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:47 vaio kernel: [13430.230069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:57:55 vaio kernel: [13437.580060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:02 vaio kernel: [13444.930068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 20:58:09 vaio kernel: [13452.290060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 20:58:17 vaio kernel: [13459.640066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:58:24 vaio kernel: [13466.990068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:31 vaio kernel: [13474.340077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 20:58:39 vaio kernel: [13481.692570] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:46 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 20:58:46 vaio kernel: [13489.040139] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:58:54 vaio kernel: [13496.390075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 20:59:01 vaio kernel: [13503.740070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:08 vaio kernel: [13511.100085] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:16 vaio kernel: [13518.450072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:23 vaio kernel: [13525.800073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:30 vaio kernel: [13533.150074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:38 vaio kernel: [13540.500068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:45 vaio kernel: [13547.850074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 20:59:52 vaio kernel: [13555.200064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:00 vaio kernel: [13562.550075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:07 vaio kernel: [13569.900066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:14 vaio kernel: [13577.270065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:22 vaio kernel: [13584.630074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:29 vaio kernel: [13591.980077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:36 vaio kernel: [13599.330065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:44 vaio kernel: [13606.680062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:51 vaio kernel: [13614.030073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:00:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:00:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 21:00:59 vaio kernel: [13621.380066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:01:06 vaio kernel: [13628.730060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:01:13 vaio kernel: [13636.080071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:21 vaio kernel: [13643.450070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:01:28 vaio kernel: [13650.800065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:01:35 vaio kernel: [13658.150078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 21:01:43 vaio kernel: [13665.500074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:50 vaio kernel: [13672.850076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:01:57 vaio kernel: [13680.200071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:05 vaio kernel: [13687.550074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:12 vaio kernel: [13694.900069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:19 vaio kernel: [13702.250065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:27 vaio kernel: [13709.600074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:34 vaio kernel: [13716.960073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:41 vaio kernel: [13724.310059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:49 vaio kernel: [13731.670074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:02:56 vaio kernel: [13739.040081] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:04 vaio kernel: [13746.400073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:11 vaio kernel: [13753.750071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:18 vaio kernel: [13761.100077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:26 vaio kernel: [13768.450073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:03:30 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:03:33 vaio kernel: [13775.800074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:37 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:03:40 vaio kernel: [13783.150083] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:48 vaio kernel: [13790.500073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:03:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
Oct 20 21:03:55 vaio kernel: [13797.850061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:02 vaio kernel: [13805.200071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 21:04:10 vaio kernel: [13812.550077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:17 vaio kernel: [13819.900063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:24 vaio kernel: [13827.250075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 21:04:32 vaio kernel: [13834.600071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:39 vaio kernel: [13841.950067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:46 vaio kernel: [13849.300067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:04:54 vaio kernel: [13856.650072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:01 vaio kernel: [13864.010070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:09 vaio kernel: [13871.360073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:16 vaio kernel: [13878.720086] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:23 vaio kernel: [13886.080069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:31 vaio kernel: [13893.430063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:38 vaio kernel: [13900.780075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:45 vaio kernel: [13908.140071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:05:53 vaio kernel: [13915.490063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:00 vaio kernel: [13922.840072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:07 vaio kernel: [13930.210076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:15 vaio kernel: [13937.560066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:22 vaio kernel: [13944.910070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:29 vaio kernel: [13952.260074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:37 vaio kernel: [13959.610078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:44 vaio kernel: [13966.967115] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:51 vaio kernel: [13974.320072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:06:59 vaio kernel: [13981.680072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:06 vaio kernel: [13989.030075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:14 vaio kernel: [13996.380074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:21 vaio kernel: [14003.730077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:28 vaio kernel: [14011.080072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:36 vaio kernel: [14018.430066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:43 vaio kernel: [14025.780072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:50 vaio kernel: [14033.150069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:07:58 vaio kernel: [14040.510064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:05 vaio kernel: [14047.870079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:12 vaio kernel: [14055.220071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:08:20 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:08:20 vaio kernel: [14062.570061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 21:08:27 vaio kernel: [14069.920072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:08:34 vaio kernel: [14077.290077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:42 vaio kernel: [14084.640061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:08:49 vaio kernel: [14091.990072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:08:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:08:56 vaio kernel: [14099.340075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:04 vaio kernel: [14106.700073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:09:11 vaio kernel: [14114.060089] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 20 21:09:19 vaio kernel: [14121.410074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:26 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:09:26 vaio kernel: [14128.770070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:09:33 vaio kernel: [14136.120066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 21:09:41 vaio kernel: [14143.470075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:09:48 vaio kernel: [14150.830073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:55 vaio kernel: [14158.180059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:09:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:10:03 vaio kernel: [14165.530075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:10:10 vaio kernel: [14172.880061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:17 vaio kernel: [14180.240071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:10:25 vaio kernel: [14187.590074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:32 vaio kernel: [14194.940070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:39 vaio kernel: [14202.300067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:47 vaio kernel: [14209.650071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:10:54 vaio kernel: [14217.000071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:02 vaio kernel: [14224.350073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:09 vaio kernel: [14231.700066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:16 vaio kernel: [14239.050075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:24 vaio kernel: [14246.400073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:31 vaio kernel: [14253.750067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:38 vaio kernel: [14261.100077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:46 vaio kernel: [14268.450069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:11:53 vaio kernel: [14275.800074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:00 vaio kernel: [14283.150078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:08 vaio kernel: [14290.500074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:15 vaio kernel: [14297.850069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:22 vaio kernel: [14305.200066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:30 vaio kernel: [14312.550072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:37 vaio kernel: [14319.900067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:44 vaio kernel: [14327.260066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:52 vaio kernel: [14334.610073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:12:59 vaio kernel: [14341.960066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:13:06 vaio kernel: [14349.320066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:13:14 vaio kernel: [14356.670072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:13:21 vaio kernel: [14364.020069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:29 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:13:29 vaio kernel: [14371.380070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:36 vaio kernel: [14378.730073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:13:43 vaio kernel: [14386.080081] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:13:51 vaio kernel: [14393.430073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:13:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:13:58 vaio kernel: [14400.780076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 21:14:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 21:14:05 vaio kernel: [14408.130070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:14:13 vaio kernel: [14415.480059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:14:20 vaio kernel: [14422.830063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:27 vaio kernel: [14430.180072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:14:35 vaio kernel: [14437.530074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:42 vaio kernel: [14444.880060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:14:49 vaio kernel: [14452.230067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:14:56 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 21:14:57 vaio kernel: [14459.580072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:04 vaio kernel: [14466.930073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:11 vaio kernel: [14474.280141] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:19 vaio kernel: [14481.630075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:26 vaio kernel: [14488.990070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:33 vaio kernel: [14496.340069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:41 vaio kernel: [14503.690067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:48 vaio kernel: [14511.040079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:15:56 vaio kernel: [14518.390061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:03 vaio kernel: [14525.750074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:10 vaio kernel: [14533.100058] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:18 vaio kernel: [14540.450064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:25 vaio kernel: [14547.800071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:32 vaio kernel: [14555.150076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:40 vaio kernel: [14562.500064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:47 vaio kernel: [14569.850072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:16:54 vaio kernel: [14577.210074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:02 vaio kernel: [14584.560074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:09 vaio kernel: [14591.910067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:17:16 vaio kernel: [14599.260074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:17:24 vaio kernel: [14606.610072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:17:31 vaio kernel: [14613.960063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:38 vaio kernel: [14621.310073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:17:46 vaio kernel: [14628.660069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:17:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:17:53 vaio kernel: [14636.010065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:01 vaio kernel: [14643.360069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:18:08 vaio kernel: [14650.710067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:15 vaio kernel: [14658.060086] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:23 vaio kernel: [14665.410069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:30 vaio kernel: [14672.760075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:37 vaio kernel: [14680.110079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:45 vaio kernel: [14687.460076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:52 vaio kernel: [14694.810075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:18:59 vaio kernel: [14702.160073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:07 vaio kernel: [14709.510067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:14 vaio kernel: [14716.860077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:21 vaio kernel: [14724.210074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:29 vaio kernel: [14731.560059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:36 vaio kernel: [14738.920077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:43 vaio kernel: [14746.270075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:51 vaio kernel: [14753.620067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:19:58 vaio kernel: [14760.970067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:05 vaio kernel: [14768.320073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:13 vaio kernel: [14775.680066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:20 vaio kernel: [14783.030070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:28 vaio kernel: [14790.380072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:35 vaio kernel: [14797.730074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:42 vaio kernel: [14805.090081] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:50 vaio kernel: [14812.440074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:20:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:20:52 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:20:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:20:55 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 21:20:57 vaio kernel: [14819.790074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:00 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:21:01 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:21:04 vaio kernel: [14827.140066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:21:12 vaio kernel: [14834.490073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:21:19 vaio kernel: [14841.840076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:25 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:21:26 vaio kernel: [14849.190065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:21:34 vaio kernel: [14856.540075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:35 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:21:41 vaio kernel: [14863.890072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:21:48 vaio kernel: [14871.240063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:21:49 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 21:21:56 vaio kernel: [14878.590080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:03 vaio kernel: [14885.940073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:10 vaio kernel: [14893.290068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:18 vaio kernel: [14900.650078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:25 vaio kernel: [14908.030072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:33 vaio kernel: [14915.380072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:40 vaio kernel: [14922.750071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:47 vaio kernel: [14930.110064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:22:55 vaio kernel: [14937.460067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:02 vaio kernel: [14944.810067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:09 vaio kernel: [14952.170071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:17 vaio kernel: [14959.530067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:24 vaio kernel: [14966.880064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:31 vaio kernel: [14974.240072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:39 vaio kernel: [14981.590070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:46 vaio kernel: [14988.950076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:23:53 vaio kernel: [14996.300066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:01 vaio kernel: [15003.650074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:08 vaio kernel: [15011.000072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:16 vaio kernel: [15018.350068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:23 vaio kernel: [15025.700074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:30 vaio kernel: [15033.050067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:38 vaio kernel: [15040.400070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:45 vaio kernel: [15047.760064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:24:52 vaio kernel: [15055.110071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:00 vaio kernel: [15062.460067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:07 vaio kernel: [15069.810060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:25:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:25:14 vaio kernel: [15077.180071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:19 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 21:25:22 vaio kernel: [15084.530072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:29 vaio kernel: [15091.890062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:36 vaio kernel: [15099.240071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:40 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:25:44 vaio kernel: [15106.590078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:51 vaio kernel: [15113.940073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:25:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:25:58 vaio kernel: [15121.290067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:26:06 vaio kernel: [15128.640076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:08 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:26:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Oct 20 21:26:13 vaio kernel: [15135.990073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:16 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Oct 20 21:26:20 vaio kernel: [15143.340071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:28 vaio kernel: [15150.690074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:26:35 vaio kernel: [15158.040083] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:43 vaio kernel: [15165.390062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:26:50 vaio kernel: [15172.750079] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:26:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 21:26:57 vaio kernel: [15180.100080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:05 vaio kernel: [15187.450067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:12 vaio kernel: [15194.800069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:19 vaio kernel: [15202.150080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:27 vaio kernel: [15209.500063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:34 vaio kernel: [15216.850069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:41 vaio kernel: [15224.200072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:49 vaio kernel: [15231.550074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:27:56 vaio kernel: [15238.900068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:03 vaio kernel: [15246.260071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:11 vaio kernel: [15253.610074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:18 vaio kernel: [15260.960063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:25 vaio kernel: [15268.310073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:33 vaio kernel: [15275.670070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:40 vaio kernel: [15283.030065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:48 vaio kernel: [15290.380064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:28:55 vaio kernel: [15297.730070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:02 vaio kernel: [15305.090078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:10 vaio kernel: [15312.440072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:17 vaio kernel: [15319.790076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:24 vaio kernel: [15327.140064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:32 vaio kernel: [15334.500064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:39 vaio kernel: [15341.850068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:46 vaio kernel: [15349.200060] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:29:54 vaio kernel: [15356.550063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:01 vaio kernel: [15363.900066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:08 vaio kernel: [15371.250073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:30:16 vaio kernel: [15378.600064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:18 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 21:30:23 vaio kernel: [15385.960072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:30:30 vaio kernel: [15393.320073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:36 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:30:38 vaio kernel: [15400.680068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:45 vaio kernel: [15408.030067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:30:50 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:30:53 vaio kernel: [15415.380115] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:00 vaio kernel: [15422.730074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:31:07 vaio kernel: [15430.080070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:31:14 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 21:31:15 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:31:15 vaio kernel: [15437.430074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:22 vaio kernel: [15444.780077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:23 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:31:29 vaio kernel: [15452.140064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:31:37 vaio kernel: [15459.490074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:31:44 vaio kernel: [15466.840071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:51 vaio kernel: [15474.190074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:31:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 21:31:59 vaio kernel: [15481.540073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:06 vaio kernel: [15488.890070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:07 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 21:32:13 vaio kernel: [15496.240072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:21 vaio kernel: [15503.590070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:28 vaio kernel: [15510.950075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:35 vaio kernel: [15518.300073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:43 vaio kernel: [15525.650064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:50 vaio kernel: [15533.000066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:32:58 vaio kernel: [15540.350074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:05 vaio kernel: [15547.700066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:12 vaio kernel: [15555.050077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:20 vaio kernel: [15562.410068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:27 vaio kernel: [15569.770064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:34 vaio kernel: [15577.120080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:42 vaio kernel: [15584.470072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:49 vaio kernel: [15591.820078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:33:56 vaio kernel: [15599.170073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:04 vaio kernel: [15606.520073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:11 vaio kernel: [15613.870075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:18 vaio kernel: [15621.220062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:26 vaio kernel: [15628.570076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:33 vaio kernel: [15635.930069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:40 vaio kernel: [15643.280247] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:48 vaio kernel: [15650.630072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:34:55 vaio kernel: [15657.990068] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:02 vaio kernel: [15665.340063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:03 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:35:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Oct 20 21:35:10 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:35:10 vaio kernel: [15672.690065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:12 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:35:13 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 21:35:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:35:17 vaio kernel: [15680.040082] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:22 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:35:25 vaio kernel: [15687.400074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:28 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
Oct 20 21:35:32 vaio kernel: [15694.760073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:33 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:35:39 vaio kernel: [15702.120080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:41 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:35:45 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:35:47 vaio kernel: [15709.470077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:53 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:35:54 vaio kernel: [15716.820066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:35:59 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:36:01 vaio kernel: [15724.170075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 21:36:09 vaio kernel: [15731.530072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:16 vaio kernel: [15738.880066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:23 vaio kernel: [15746.230076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:31 vaio kernel: [15753.580077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:38 vaio kernel: [15760.940072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:45 vaio kernel: [15768.290077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:36:53 vaio kernel: [15775.650066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:00 vaio kernel: [15783.000066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:08 vaio kernel: [15790.350063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:15 vaio kernel: [15797.700072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:22 vaio kernel: [15805.050074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:30 vaio kernel: [15812.400066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:37 vaio kernel: [15819.750073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:44 vaio kernel: [15827.110078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:52 vaio kernel: [15834.460062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:37:59 vaio kernel: [15841.810075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:06 vaio kernel: [15849.160072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:14 vaio kernel: [15856.510075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:21 vaio kernel: [15863.870072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:28 vaio kernel: [15871.230069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:36 vaio kernel: [15878.580074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:43 vaio kernel: [15885.930062] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:50 vaio kernel: [15893.280081] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:38:58 vaio kernel: [15900.630083] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:05 vaio kernel: [15908.000099] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:06 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:39:09 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 21:39:13 vaio kernel: [15915.360072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:17 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 21:39:20 vaio kernel: [15922.710075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:39:27 vaio kernel: [15930.070078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:35 vaio kernel: [15937.430074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:39 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Oct 20 21:39:42 vaio kernel: [15944.780073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:49 vaio kernel: [15952.140080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:39:57 vaio kernel: [15959.490065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:39:58 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:40:04 vaio kernel: [15966.840074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:05 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
Oct 20 21:40:11 vaio kernel: [15974.190075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:19 vaio kernel: [15981.550063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:26 vaio kernel: [15988.900067] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:33 vaio kernel: [15996.260070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:41 vaio kernel: [16003.610077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:48 vaio kernel: [16010.960071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:40:55 vaio kernel: [16018.310066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:03 vaio kernel: [16025.670072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:10 vaio kernel: [16033.050069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:18 vaio kernel: [16040.410069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:25 vaio kernel: [16047.760069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:32 vaio kernel: [16055.120065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:40 vaio kernel: [16062.470072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:47 vaio kernel: [16069.820071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:41:54 vaio kernel: [16077.170064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:02 vaio kernel: [16084.520071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:09 vaio kernel: [16091.870070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:16 vaio kernel: [16099.230072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:24 vaio kernel: [16106.580073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:31 vaio kernel: [16113.950070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:38 vaio kernel: [16121.300255] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:46 vaio kernel: [16128.650064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:42:53 vaio kernel: [16136.000074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:01 vaio kernel: [16143.350071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:08 vaio kernel: [16150.700071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:15 vaio kernel: [16158.050077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:23 vaio kernel: [16165.400072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:24 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:43:27 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 21:43:30 vaio kernel: [16172.760074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:32 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:43:37 vaio kernel: [16180.110078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:43 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
Oct 20 21:43:45 vaio kernel: [16187.470072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:52 vaio kernel: [16194.820073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:43:54 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 21:43:57 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 20 21:43:59 vaio kernel: [16202.180061] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:02 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 21:44:04 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:44:07 vaio kernel: [16209.530071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:11 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Oct 20 21:44:13 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Oct 20 21:44:14 vaio kernel: [16216.880077] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:21 vaio kernel: [16224.240120] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:29 vaio kernel: [16231.590066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:31 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Oct 20 21:44:36 vaio kernel: [16238.940071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:43 vaio kernel: [16246.290072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:44 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 21:44:51 vaio dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Oct 20 21:44:51 vaio kernel: [16253.640072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:44:58 vaio kernel: [16260.990073] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:45:06 vaio kernel: [16268.350064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:45:13 vaio kernel: [16275.700078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:45:20 vaio kernel: [16283.060078] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:45:28 vaio kernel: [16290.410076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:45:35 vaio kernel: [16297.760059] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:54:34 vaio kernel: [16303.432628] iwl3945 0000:06:00.0: power state changed by ACPI to D3
Oct 20 21:54:34 vaio kernel: [16305.451822] iwl3945 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Oct 20 21:54:34 vaio kernel: [16305.451889] iwl3945 0000:06:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xde100000)
Oct 20 21:54:34 vaio kernel: [16305.451902] iwl3945 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Oct 20 21:54:34 vaio kernel: [16305.451921] iwl3945 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100406)
Oct 20 21:54:34 vaio kernel: [16305.469692] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 21:54:34 vaio kernel: [16305.469780] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 21:54:34 vaio kernel: [16305.470084] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 21:54:34 vaio kernel: [16305.470358] iwl3945 0000:06:00.0: power state changed by ACPI to D0
Oct 20 21:55:11 vaio kernel: [16344.360070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:19 vaio kernel: [16351.720096] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:26 vaio kernel: [16359.070071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:33 vaio kernel: [16366.420071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:41 vaio kernel: [16373.800070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:48 vaio kernel: [16381.150072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:55:55 vaio kernel: [16388.505483] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:03 vaio kernel: [16395.860069] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:10 vaio kernel: [16403.210063] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:17 vaio kernel: [16410.560064] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:25 vaio kernel: [16417.910072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:32 vaio kernel: [16425.260072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:39 vaio kernel: [16432.610081] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:47 vaio kernel: [16439.960074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:56:54 vaio kernel: [16447.310066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:01 vaio kernel: [16454.660065] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:09 vaio kernel: [16462.010071] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:16 vaio kernel: [16469.370070] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:24 vaio kernel: [16476.720074] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:31 vaio kernel: [16484.070072] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:38 vaio kernel: [16491.420075] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:41 vaio NetworkManager[4211]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
Oct 20 21:57:41 vaio NetworkManager[4211]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Oct 20 21:57:41 vaio NetworkManager[4211]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
Oct 20 21:57:41 vaio NetworkManager[4211]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
Oct 20 21:57:41 vaio NetworkManager[4211]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:06:00.0/net/wlan0, iface: wlan0)
Oct 20 21:57:41 vaio NetworkManager[4211]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 21:57:41 vaio NetworkManager[4211]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 5)
Oct 20 21:57:41 vaio NetworkManager[4211]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 21:57:43 vaio kernel: [16496.250080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:50 vaio kernel: [16503.610076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:58 vaio kernel: [16510.960066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0] 

That's a lot of errors spitted out iwl3945 related.

Thanks,

Vincent
ps - I am leaving for home, and I will not bring this computer home with me, so I will check this thread out tomorrow.  Thanks.

---

### Post by chili555 on 2010-10-21
Look at the last several lines:> Oct 20 21:57:41 vaio [COLOR="Red"]NetworkManager[/COLOR][4211]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 20 21:57:41 vaio [COLOR="Red"]NetworkManager[/COLOR][4211]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwl3945' ifindex: 5)
Oct 20 21:57:41 vaio [COLOR="Red"]NetworkManager[/COLOR][4211]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 20 21:57:43 vaio kernel: [16496.250080] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:50 vaio kernel: [16503.610076] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0]
Oct 20 21:57:58 vaio kernel: [16510.960066] iwl3945 0000:06:00.0: Failed to get channel info for channel 165 [0] As I said, it's difficult.

Instead, let's troubleshoot why NM is not doing its job. First, please do:```
sudo gedit /etc/network/interfaces
```If it contains anything other than this:```
auto lo
iface lo inet loopback
```Then please comment it out with the pound sign, thus:```
auto lo
iface lo inet loopback

#extra stuff
#needless stuff
```The # sign tells the system, 'these are just comments, don't read or act upon them.'

Next, let's do:```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Find the part that says managed = true (or false) and change it to the other. 

Reboot and see if NM has gotten back to work. Post back and let me know.

---

### Post by Vincent_Lin on 2010-10-21
chili555,

Good news.  After the clean-up of those two files you mentioned, network-manager starts to work, and 3945 is connecting to router.

Thanks a bunch!!!

I would summarize what I have done:

0.This is for 10.10, on Sony VAIO with Intel 3945 wireless chip
1. install firmwre.
2. Set iwl3945 module loading option to no-scan
3. clean up /etc/network/interface
4. Clean up /etc/NetworkManager/nm-system-settings.conf

Then it works.

I asked my office IT guy to disable security setting from wireless fouter for a brief moment then 3945 connects and associates with it right away.  Now, WEP keys (64 bit open and too short) would not work, but that is another story.  That IT guy was brought up in MS world, and is not too happy/familiar about what I am doing with linux. Ha!!  Eventually, I had to convince him to adopt 128bit WEP and it works again.

Anyway, at least hardware and system side setup is complete and working now.

Thanks a lot, AGAIN!!

Cheers,

Vincent

---

### Post by chili555 on 2010-10-21
Woo hoo! Glad it's working. Have fun and win over that IT guy!

---

### Post by gentuser on 2010-11-13
Hi all, probably i have found the problem. Maybe It is a bug of Kernel 2.6.35.

When i load Ubuntu 10.10 with kernel 2.6.32 all works fine
and 
rfkill list

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

If i load kernel 2.6.35 "rfkill list" returns this:
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Now it gives 4 devices instead of 2 and doing this:
rfkill unblock 0
rfkill unblock 3

Wireless works again. This problem comes every time i switch off in hardware the wi-fi (with a button). With ubuntu 10.04 or with 10.10 loading 2.6.32 kernel it works fine.
I think that there is mismatch somewhere in kernel configuration, cause it seems that it finds four devices instead of two.
Bye !!

---

### Post by chili555 on 2010-11-13
I wonder if the problem is really the module *hp-wmi.* Is the behavior improved if you do:```
sudo rmmod -f hp-wmi
```If this works, we can amend one file to make it permanent.

---

