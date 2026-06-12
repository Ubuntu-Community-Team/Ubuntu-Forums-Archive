---
title: "3945ABG wirless card not connecting ubuntu 9.10 karmic"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by bukii on 2009-12-01
there are many threads like this but none helped me out. my wireless detects netowrks but it fails to connect (secured/non secured) it even asks for the authentication for secured networks but it fails to connect.
i've tried ndiswrapper, backports, compact wireless,network manager, wicd, wpa association but no luck. network manager keeps prompting me for the wireless routher password and it never connects.. wicd says Could not contact the wireless access point. here are some details..
 lshw :
*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: wmaster0
                version: 02
                serial: 00:19:d2:0b:87:f8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:28 memory:44100000-44100fff
_____
ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:19:d2:0b:87:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
_____
iwconfig: 
wlan0     IEEE 802.11abg  ESSID:"Bukii"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
____
/etc/network/interfaces >>

auto lo
iface lo inet loopback

____
dhclient wlan0:
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:d2:0b:87:f8
Sending on   LPF/wlan0/00:19:d2:0b:87:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
.....
the compat-wireless-2.6.31-rc7 package i have shows an error :
bu@bu-laptop:~/compat-wireless-2.6.31-rc7$ make
make -C /lib/modules/2.6.31-15-generic/build M=/home/bu/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
make[3]: *** No rule to make target `/home/bu/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/bu/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/bu/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/bu/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [modules] Error 2

so i didnt try this one..
i tried static and dynamic ips through wicd, netwok manager and interfaces file but still
anywyas any suggestions? i ve been strugglin through this since the past 5 months..
thanks in advance

---

### Post by bukii on 2009-12-02
anyone? -.-'

---

### Post by chili555 on 2009-12-02
So, where are you now? Is Wicd or Network Manager installed or both? You do have the correct driver, *iwl3945*. May we please see:```
sudo iwlist wlan0 scanning
```What kind of encryption are you using: WEP or WPA or...? If WEP, how many characters is it?

---

### Post by SimonVirgo on 2009-12-02
Hello,

I just happen to have the same problem or at least it looks like it. I have tried wicd, ndiswrapper with different windows drivers, backports, etc. Nothing worked.

I can see the networks but can't connect.

I've got a Packard-Bell EasyNote MX66 with Intel 3945ABG wireless inside. The network I am trying to connect to uses WPA security, the driver is iwl3945 and I currently use wicd.

sudo lshw -C network
--
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:23:15:36
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:fe1ff000-fe1fffff

sudo ifconfig wlan0
--
wlan0     Link encap:Ethernet  HWaddr 00:18:de:23:15:36  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo iwconfig wlan0
--
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist wlan0 scan
--
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:64:D7:35
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Zodiacus Koper"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013e76f4188
                    Extra: Last beacon: 2676ms ago
                    IE: Unknown: 000E5A6F646961637573204B6F706572
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD06001018020100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

cat /var/log/syslog | grep iwl
--
Dec  2 18:59:56 leo kernel: [   14.826128] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Dec  2 18:59:56 leo kernel: [   14.826132] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Dec  2 18:59:56 leo kernel: [   14.826269] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  2 18:59:56 leo kernel: [   14.826288] iwl3945 0000:03:00.0: setting latency timer to 64
Dec  2 18:59:56 leo kernel: [   14.896516] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Dec  2 18:59:56 leo kernel: [   14.896520] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
Dec  2 18:59:56 leo kernel: [   14.896683] iwl3945 0000:03:00.0: irq 28 for MSI/MSI-X
Dec  2 18:59:56 leo kernel: [   15.048900] phy0: Selected rate control algorithm 'iwl-3945-rs'
Dec  2 18:59:57 leo kernel: [   16.194111] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
Dec  2 18:59:57 leo kernel: [   16.282081] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
Dec  2 18:59:57 leo kernel: [   16.404301] Registered led device: iwl-phy0::radio
Dec  2 18:59:57 leo kernel: [   16.404324] Registered led device: iwl-phy0::assoc
Dec  2 18:59:57 leo kernel: [   16.404382] Registered led device: iwl-phy0::RX
Dec  2 18:59:57 leo kernel: [   16.404401] Registered led device: iwl-phy0::TX
Dec  2 19:02:51 leo kernel: [  189.556797] Registered led device: iwl-phy0::radio
Dec  2 19:02:51 leo kernel: [  189.556900] Registered led device: iwl-phy0::assoc
Dec  2 19:02:51 leo kernel: [  189.556934] Registered led device: iwl-phy0::RX
Dec  2 19:02:51 leo kernel: [  189.556965] Registered led device: iwl-phy0::TX

--

I was thinking... Could be the problem laptop-specific? I mean, could be the source of the problem connected to the LED, wireless on/off button or something? The LED indicating if the wireless is on or off is always on. Is there a way of disabling the connection between the wifi on/off button, LED and the wireless network card?

Best regards,
Simon V.

---

### Post by jberkery on 2009-12-02
I just put a fresh 9.10 install on an old laptop with a pcmcia wireless card (not a 3945abg) that has to use windows drivers under ndiswrapper. For me the key to getting it working was to edit 
/etc/modporbe.d/blacklist.conf

Add these three lines after "blacklist bcm43xx"

blacklist b43
blacklist b43legacy
blacklist ssb

---

### Post by bukii on 2009-12-02
am using wicd right now.. encryption is wpa psk (TKIP).. here is the output

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
[sudo] password for bu: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:40:ED:4B:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BVB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c942e318b
                    Extra: Last beacon: 1940ms ago
                    IE: Unknown: 0003425642
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:40:ED:4B:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"BVB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c9555818a
                    Extra: Last beacon: 1836ms ago
                    IE: Unknown: 0003425642
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     No scan results

bu@bu-laptop:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:40:AF:D8:40
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Bukii"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d7b782186
                    Extra: Last beacon: 1772ms ago
                    IE: Unknown: 000542756B6969
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


* my network is "bukii" i dont know why the command output acts randomly it showes different output in everytime 

come to think about what SimonVirgo said i think maybe it has somethin todo with the switch button .. btw in my /var/log/messages file there is a line >> Nov 29 13:49:19 bu-laptop kernel: [13600.500834] iwl3945 0000:05:00.0: Radio Frequency Kill Switch is On: 
ive been tryin to figure out how to turn it off but still my wireless is up 
sometimes i have to repeat the scan till i see the network am intending to hook my wireless with

---

### Post by stefangr1 on 2009-12-02
It appears that your wifi chip is detected and working, but that the network manager doesn't succeed in establishing a connection. What you can try is to manually connect by using wpa_supplicant.

First you install wpasupplicant.

In your /etc/network/interfaces you should have something like this:

auto wlan0
iface wlan0 inet dhcp
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

Thin you should configure a basic wpa_supplicant.conf, something like this:

network={
   ssid="mywireless"
   psk=7b271c9a7c8a6ac07d12403a1f0792d7d92b5957ff8dfd56481ced43ec6a6515
}

---

### Post by SimonVirgo on 2009-12-03
> **jberkery said:**
> I just put a fresh 9.10 install on an old laptop with a pcmcia wireless card (not a 3945abg) that has to use windows drivers under ndiswrapper. For me the key to getting it working was to edit 
/etc/modporbe.d/blacklist.conf

Add these three lines after "blacklist bcm43xx"

blacklist b43
blacklist b43legacy
blacklist ssb

It didn't work.

> **stefangr1 said:**
> It appears that your wifi chip is detected and working, but that the network manager doesn't succeed in establishing a connection. What you can try is to manually connect by using wpa_supplicant.

I disabled security and still can't connect. The same problem - can't get the IP.

It's not a router problem, I can connect normally with other computers.

Any ideas for the switch button?

Simon V.

---

### Post by LookTJ on 2009-12-03
May you post:
```
dmesg | tail
```

---

### Post by SimonVirgo on 2009-12-03
I think I know what's not working. The antenna is receiving but not broadcasting. In the router logs there are no DHCP requests from my computer as there are for the others.

Any ideas?

Simon V.

---

### Post by SimonVirgo on 2009-12-03
> **LookTJ said:**
> May you post:
```
dmesg | tail
```

Here it is...

```
[ 2561.077759] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2561.240942] Registered led device: iwl-phy0::radio
[ 2561.241053] Registered led device: iwl-phy0::assoc
[ 2561.241087] Registered led device: iwl-phy0::RX
[ 2561.241120] Registered led device: iwl-phy0::TX
[ 2561.254035] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2564.160251] wlan0: direct probe to AP 00:1e:e5:64:d7:35 try 1
[ 2564.360055] wlan0: direct probe to AP 00:1e:e5:64:d7:35 try 2
[ 2564.560054] wlan0: direct probe to AP 00:1e:e5:64:d7:35 try 3
[ 2564.760052] wlan0: direct probe to AP 00:1e:e5:64:d7:35 timed out

```Simon V.

---

### Post by LookTJ on 2009-12-03
> **SimonVirgo said:**
> I think I know what's not working. The antenna is receiving but not broadcasting. In the router logs there are no DHCP requests from my computer as there are for the others.

Any ideas?

Simon V.
The router broadcasts(hidden or not), it is probably not offering your wireless' MAC an IP. Have you tried static IP?

---

### Post by SimonVirgo on 2009-12-03
> **LookTJ said:**
> The router broadcasts(hidden or not), it is probably not offering your wireless' MAC an IP. Have you tried static IP?

Yes.

I don't know if I was clear enough - the computer's antenna isn't broadcasting, not routers.

Simon V.

---

### Post by LookTJ on 2009-12-03
Well, I really doubt the firmware is the problem here. 

It couldn't hurt to try removing the module and modprobing again.

```
lsmod | grep iwl
``` and find something related to the 3945 driver.

```
sudo rmmod *module*
```
```
sudo modprobe *module*
```

---

### Post by bukii on 2009-12-03
didnt work... heres my outputs:

/etc/wpa_supplicant.conf >>>

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="bukii"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=40c9f1ed4c6ed0ff1e25bc1bc39ecc04a102909a3de9c9135293c0fcb8e52fe6
}

___________________

/etc/network/interfaces>>>>>

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.1.7
netmask 255.255.255.0
wireless-essid bukii
gateway 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
___________
i run the command : 
bu@bu-laptop:~$ sudo wpa_supplicant -B -Dwext -i wlan0 -c/etc/wpa_supplicant.conf
bu@bu-laptop:~$ echo $?
0
but no connection

---

### Post by LookTJ on 2009-12-03
> **SimonVirgo said:**
> Yes.

I don't know if I was clear enough - the computer's antenna isn't broadcasting, not routers.

Simon V.
Odd. By the way, the on/off wireless switch is hardware-wired on the laptop, not software-wired I believe.

---

### Post by bukii on 2009-12-03
bu@bu-laptop:~$ dmesg | tail
[14080.109073] wlan0: direct probe to AP 00:1e:40:af:d8:40 try 2
[14080.204364] wlan0 direct probe responded
[14080.204375] wlan0: authenticate with AP 00:1e:40:af:d8:40
[14080.404088] wlan0: authenticate with AP 00:1e:40:af:d8:40
[14080.604107] wlan0: authenticate with AP 00:1e:40:af:d8:40
[14080.615306] wlan0: authenticated
[14080.615314] wlan0: associate with AP 00:1e:40:af:d8:40
[14080.812054] wlan0: associate with AP 00:1e:40:af:d8:40
[14081.012062] wlan0: associate with AP 00:1e:40:af:d8:40
[14081.212072] wlan0: association with AP 00:1e:40:af:d8:40 timed out
 this after trying to connect with wicd
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Bukii"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

no matter what i did i cant get  Access Point: Not-Associated to associated with the router..
remodroping the module wont help as well neithr ndiswrapper nor backports..

---

### Post by SimonVirgo on 2009-12-03
> **LookTJ said:**
> Well, I really doubt the firmware is the problem here. 

It couldn't hurt to try removing the module and modprobing again.

```
lsmod | grep iwl
``` and find something related to the 3945 driver.

```
sudo rmmod *module*
``````
sudo modprobe *module*
```

Tried several times, doesn't work.

> **LookTJ said:**
> Odd. By the way, the on/off wireless switch is hardware-wired on the laptop, not software-wired I believe.

I am sure about this. In 9.04 the led was going on/off in 9.10 the led is always on. The switch probably has a driver too, doesn't it?

What if the switch is not working as it should? Like turning send on and receive off at the same time and vice versa?

Simon V.

---

### Post by LookTJ on 2009-12-03
> **SimonVirgo said:**
> Tried several times, doesn't work.



I am sure about this. In 9.04 the led was going on/off in 9.10 the led is always on. The switch probably has a driver too, doesn't it?

What if the switch is not working as it should? Like turning send on and receive off at the same time and vice versa?

Simon V.
According to the iwlwifi website, the latest driver was released in late 2009 April, so 9.04 might have been released with an older release?

But you could try the switch vice versa by all means. It just seems strange.

EDIT: Was it working fine in 9.04?

---

### Post by SimonVirgo on 2009-12-03
> **LookTJ said:**
> According to the iwlwifi website, the latest driver was released in late 2009 April, so 9.04 might have been released with an older release?

But you could try the switch vice versa by all means. It just seems strange.

I'll give 9.04 a try..

Simon V.

---

### Post by SimonVirgo on 2009-12-03
I have installed 9.04 and tested. The problem remains the same. However there could be some clues...

cat /var/log/syslog | grep iwl
```
Dec  3 12:39:52 leo kernel: [   10.351529] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Dec  3 12:39:52 leo kernel: [   10.351532] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Dec  3 12:39:52 leo kernel: [   10.351650] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec  3 12:39:52 leo kernel: [   10.351666] iwl3945 0000:03:00.0: setting latency timer to 64
Dec  3 12:39:52 leo kernel: [   10.351719] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Dec  3 12:39:52 leo kernel: [   10.352069] iwl3945 0000:03:00.0: irq 2299 for MSI/MSI-X
Dec  3 12:39:52 leo kernel: [   10.406512] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Dec  3 12:39:52 leo kernel: [   10.407460] phy0: Selected rate control algorithm 'iwl-3945-rs'
Dec  3 12:39:54 leo NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/iwl_wlan_switch 
Dec  3 12:39:54 leo NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945') 
Dec  3 12:39:59 leo kernel: [   20.670211] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-1.ucode
Dec  3 12:39:59 leo kernel: [   20.794777] Registered led device: iwl-phy0:radio
Dec  3 12:39:59 leo kernel: [   20.794858] Registered led device: iwl-phy0:assoc
Dec  3 12:39:59 leo kernel: [   20.794894] Registered led device: iwl-phy0:RX
Dec  3 12:39:59 leo kernel: [   20.794932] Registered led device: iwl-phy0:TX
Dec  3 12:42:56 leo kernel: [  197.918835] iwl3945: Error sending REPLY_SCAN_ABORT_CMD: iwl3945_enqueue_hcmd failed: -5
Dec  3 12:42:56 leo kernel: [  197.932177] iwl3945: MAC is in deep sleep!
Dec  3 12:42:56 leo kernel: [  198.432052] iwl3945: Error sending REPLY_RXON: time out after 500ms.
Dec  3 12:42:56 leo kernel: [  198.432059] iwl3945: Error setting new configuration (-110).
Dec  3 12:42:56 leo kernel: [  198.482178] Registered led device: iwl-phy0:radio
Dec  3 12:42:56 leo kernel: [  198.482253] Registered led device: iwl-phy0:assoc
Dec  3 12:42:56 leo kernel: [  198.482285] Registered led device: iwl-phy0:RX
Dec  3 12:42:56 leo kernel: [  198.482315] Registered led device: iwl-phy0:TX
Dec  3 12:45:30 leo kernel: [  352.319923] iwl3945: Error sending REPLY_SCAN_ABORT_CMD: iwl3945_enqueue_hcmd failed: -5
Dec  3 12:45:30 leo kernel: [  352.336169] iwl3945: MAC is in deep sleep!
Dec  3 12:45:31 leo kernel: [  352.836056] iwl3945: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Dec  3 12:45:33 leo kernel: [  355.472490] iwl3945: No space for Tx
Dec  3 12:45:33 leo kernel: [  355.472499] iwl3945: Error sending REPLY_CARD_STATE_CMD: iwl3945_enqueue_hcmd failed: -28
```

The errors are probably related to switching the wireless on/off.

The LED is working as it should but the switch doesn't seem to work. Wireless is always "on" as I can detect wireless networks.

Simon V.

---

### Post by zaphod777 on 2009-12-03
I had the same problem with this adapter I had to install the backport drivers.

```
sudo apt-get install karmic-backports

```

then reboot

---

### Post by bukii on 2009-12-03
> **SimonVirgo said:**
> I have installed 9.04 and tested. The problem remains the same. 

The errors are probably related to switching the wireless on/off.

The LED is working as it should but the switch doesn't seem to work. Wireless is always "on" as I can detect wireless networks.

Simon V.

i had this problem since 9.04 .. in my case the wireless turns off when i switch it off (the switch is labled in bluetooth category though not wireless in device manager)

---

### Post by LookTJ on 2009-12-03
Do you both have the same revision of card? 

```
lspci | grep 3945
```

See if zaphod's solution work. :)

---

### Post by zaphod777 on 2009-12-03
> **LookTJ said:**
> Do you both have the same revision of card? 

```
lspci | grep 3945
```

See if zaphod's solution work. :)

Actually it looks like I have the 4965 my mistake.

---

### Post by VirusCollector on 2009-12-03
Hello, I have the 3945 and will be paying attention. Fairly new to all of this, but I have run the commands mentioned so far and gotten results very similar to what has come up so far.

Tailing produces: "[  260.161803] ADDRCONF(NETDEV_UP): wlan0: link is not ready"

While using Gnome's network-manager, I would click on my network and immediately get the "Network Disconnected" popup as if it hadn't done anything. Tried unloading and reloading the iwl3945 driver and nothing happened.

I found another thread that referenced installing wicd and did so. My main problem is that I can't seem to put it back in my panel, but other than that it's worked so far. A tail also produces normal-looking lines. The reason why I'm so surprised by this is because I'd seem people on the same thread complaining that it didn't work.
** **

---

### Post by bukii on 2009-12-03
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
___
i tried backports already

---

### Post by LookTJ on 2009-12-03
[http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)

Check this out:
[quote=web]
** Using kernels 2.6.24 and up **

 These kernels have the iwlwifi driver included and the released drivers (available from this site under [download page]("http://intellinuxwireless.org/?n=downloads")) do ** not ** work with these kernels. If you want to run the latest (or very close to 		it) development code with your kernel then you should use the [compat-wireless project]("http://linuxwireless.org/en/users/Download") that retrieves the latest driver development code from the [ upstream repository]("http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git"). We do push our changes to this repository very frequently.[/quote]

---

### Post by SimonVirgo on 2009-12-04
Back to 9.10.

> **LookTJ said:**
> [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)

Check this out:

I think it's just saying that these drivers are already included in kernel...

Now, I've checked syslog a bit more. There is a line that might indicate the solution...

 EDIT: Nevermind these lines, my mistake.. :)

cat /var/log/syslog | grep wlan0
```

Dec  4 12:10:33 leo NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0)
Dec  4 12:10:33 leo NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'iwl3945')
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): now managed
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): bringing up device.
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): preparing device.
Dec  4 12:10:34 leo kernel: [   24.827158] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Dec  4 12:10:34 leo NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready

```The first two lines are probably about the killswitch (=the switch to turn on/off wireless). In 9.04 there was a line about not knowing the ifupdown device, probably the killswitch.

Now, I'm wondering where to configure "ifupdown" (probably the killswitch)? Any ideas?

Simon V.

---

### Post by LookTJ on 2009-12-04
> **SimonVirgo said:**
> Back to 9.10.



I think it's just saying that these drivers are already included in kernel...

Now, I'm wondering where to configure "ifupdown" (probably the killswitch)? Any ideas?

Simon V.I think it's saying that the drivers which are current do not work with the current kernel(at least in Ubuntu's case). You could try the development drivers.

---

### Post by SimonVirgo on 2009-12-04
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1990](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1990)

This bug looks familiar...

Simon V.

---

### Post by LookTJ on 2009-12-04
> **SimonVirgo said:**
> [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1990](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1990)

This bug looks familiar...

Simon V.
Familiar indeed! 

I hope that we can find a fix or workaround of some sort.

As you can probably tell, I don't have the same model of you, I have the 2200BG. :) But I try to help whenever possible in my ability.

What version of the firmware does Ubuntu 9.10 have?

```
modinfo *module* | grep ver
```

---

### Post by SimonVirgo on 2009-12-05
> **LookTJ said:**
> What version of the firmware does Ubuntu 9.10 have?
iwlwifi-3945-2.ucode

Simon V.

---

### Post by juanmafont on 2009-12-16
> **SimonVirgo said:**
> iwlwifi-3945-2.ucode

Simon V.

Hello, Simon, from Spain ¡¡¡

 I have the same problem, and a similar machine, a Packard Bell easynote sw45-003.

lspci ->
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

 And looking for an solution, but no luck ¡¡¡ :(

 This card don't go with ubuntu 9.10

---

### Post by juanmafont on 2009-12-16
YESSS ¡¡¡¡¡ SOLVED ¡¡¡¡  :)

  I have only activate an option into bios.  Into wireless section set "TURN ON CARD when system boot"
 
  Now ubuntu manage the card without problems.. jejeje This post has been write using  3945ABG card  oh yeeeah ¡¡¡

  bye....

---

### Post by jeppo67 on 2011-01-12
finally...after 2 months and hundred of post read, my solution for the same problem (the same hardware, the same outputs af commands) is to add to blacklist the "asus-laptop" module :D

see this thread for reference [http://ubuntuforums.org/showthread.php?t=1039796&highlight=packard+bell+easynote+3945abg](http://ubuntuforums.org/showthread.php?t=1039796&highlight=packard+bell+easynote+3945abg)

PS
juanmafont solution was not applicable to my harware because my BIOS does not have any wireless section.

---

