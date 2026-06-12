---
title: "Atheros AR9285/Ubuntu 11.04/Lenovo B575 (Wireless Disabled?)"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by mdunphy on 2011-08-31
**/* SOLVED */**

Hi guys, I recently bought a new laptop (Lenovo B575) for school/work and went to put Ubuntu on it.  I run it on my desktop which has a wired connection and I've never had any problems.  However I seem to be having a bit of trouble getting the wireless to work at all.  Even with "Enable Wireless" checked off in Network Manager and my wifi switch turned on, it is still telling me that my wireless is disabled.  From what I've gathered from troubleshooting this, my card (Atheros AR9285) has worked on previous versions of Ubuntu, but doesn't seem to play nice with Natty Narwhal for some reason.  I have checked the wireless troubleshooting guide as well as scoured the internet to find a solution but have found nothing that has worked.  I will post all recommended information as mentioned in [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681).

1. Make and Model: Lenovo B575

2. lspci -nn | grep 'Atheros' output:

> mark@ubuntu:~$ lspci -nn | grep 'Atheros'
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

3. ifconfig and iwconfig output:

> mark@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:de:f1:6d:e7:5c  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe6d:e75c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4687716 (4.6 MB)  TX bytes:514442 (514.4 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
4.lsmod | grep "ath9k" output:

> mark@ubuntu:~$ lsmod | grep "ath9k"
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath

5. Will post dmesg on request if necessary.

6. sudo lshw -C network output (excluding eth0 which works fine):

 >  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:12:8c:79
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:e0100000-e010ffff

7. iwlist scan output:

> mark@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

8. lsb_release -d output:

> mark@ubuntu:~$ lsb_release -d
Description:	Ubuntu 11.04

9. uname -mr output:

> mark@ubuntu:~$ uname -mr
2.6.38-11-generic x86_64

10. sudo /etc/init.d/networking restart output:

> mark@ubuntu:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                      [ OK ] 
mark@ubuntu:~$ 


I appreciate any help I can get with this issue.  If any more information is needed to help, please ask.  Thank you!

---

### Post by wildmanne39 on 2011-08-31
Hi, Is your network set to WPA and WPA2 mixed mode? That is often troublesome. If you can, try WPA2 only. You might also try:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if you run this command and it works then we will need to make it persistent.

Do not restart your computer this is a one time only method for testing purposes.
Thank you

---

### Post by mdunphy on 2011-08-31
> **wildmanne39 said:**
> Hi, Is your network set to WPA and WPA2 mixed mode? That is often troublesome. If you can, try WPA2 only. You might also try:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
if you run this command and it works then we will need to make it persistent.

Do not restart your computer this is a one time only method for testing purposes.
Thank you

My apologies, I should have been a bit more clear as to my actual problem.  I am unable to even see any wireless networks as it is grayed out in the Network Manager on the top right of my screen.  There is also a grayed out message that says "wireless is disabled" despite "Enable wireless" being checked off in the same drop down menu.  Also, my network is WPA2-Personal, not mixed mode for future reference.

After trying those commands, I am still unable to detect any networks as it seems wireless is still disabled.  Thank you for the response.  I should also mention that my wireless works without any issues in Windows 7 Home Premium 64-bit.

---

### Post by wildmanne39 on 2011-08-31
Hi, I suspect you need the firmware, run these commands and post the results.
```
dmesg | grep wlan0
```
```
dmesg | egrep 'ath|firm'
```
```
rfkill list all
```
Thank you

---

### Post by mdunphy on 2011-08-31
> **wildmanne39 said:**
> Hi, I suspect you need the firmware, run these commands and post the results.
```
dmesg | grep wlan0
```
```
dmesg | egrep 'ath|firm'
```
```
rfkill list all
```
Thank you

dmesg | grep wlan0 output:
```
mark@ubuntu:~$ dmesg | grep wlan0
[   16.735323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6838.007998] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

dmesg | egrep 'ath|firm' output:
```
mark@ubuntu:~$ dmesg | egrep 'ath|firm'
[    1.407146] device-mapper: multipath: version 1.2.0 loaded
[    1.407157] device-mapper: multipath round-robin: version 1.0.0 loaded
[   15.917031] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.917053] ath9k 0000:03:00.0: setting latency timer to 64
[   15.968536] ath: EEPROM regdomain: 0x65
[   15.968544] ath: EEPROM indicates we should expect a direct regpair map
[   15.968551] ath: Country alpha2 being used: 00
[   15.968554] ath: Regpair used: 0x65
[   16.021020] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.022126] Registered led device: ath9k-phy0::radio
[   16.022169] Registered led device: ath9k-phy0::assoc
[   16.022210] Registered led device: ath9k-phy0::tx
[   16.022244] Registered led device: ath9k-phy0::rx
[ 6799.341183] ath9k 0000:03:00.0: PCI INT A disabled
[ 6799.341254] ath9k: Driver unloaded
[ 6818.920975] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6818.920997] ath9k 0000:03:00.0: setting latency timer to 64
[ 6818.973227] ath: EEPROM regdomain: 0x65
[ 6818.973231] ath: EEPROM indicates we should expect a direct regpair map
[ 6818.973238] ath: Country alpha2 being used: 00
[ 6818.973241] ath: Regpair used: 0x65
[ 6818.977063] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[ 6818.978536] Registered led device: ath9k-phy1::radio
[ 6818.978580] Registered led device: ath9k-phy1::assoc
[ 6818.978619] Registered led device: ath9k-phy1::tx
[ 6818.978665] Registered led device: ath9k-phy1::rx

```

rfkill list all output:
```
mark@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Thanks

---

### Post by wildmanne39 on 2011-08-31
Hi, disconnect your wired connection then run this command and give it a minute to work then see if you can connect.

But do not restart your computer this is a one time only command and if it works we will need to make it persistent.
```
rmmod -f acer-wmi
``` 
Thank you

---

### Post by mdunphy on 2011-08-31
> **wildmanne39 said:**
> Hi, disconnect your wired connection then run this command and give it a minute to work then see if you can connect.

But do not restart your computer this is a one time only command and if it works we will need to make it persistent.
```
rmmod -f acer-wmi
``` 
Thank you

That seems like it's almost done the trick.  I'm now able to see available wireless networks.  However, I'm unable to connect to my WPA2 secured network.  I was able to connect to my neighbor's unsecured network though.  Might need to change some of my router settings around?  Thanks again for your help, we're almost there!

---

### Post by mdunphy on 2011-08-31
Nevermind, apparently my router was set for TKIP and AES.  Changed it to just AES and can now connect without issue.  Just need to know how to go about making this fix permanent now.  Thanks!

---

### Post by wildmanne39 on 2011-08-31
Hi do what I suggested in post 2 for the wpa2 issue and do this to make it persistent.
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
Add one line:
```
options ath9k nohwcrypt=1
```
Proofread, save and close gedit and you should be all set.
Thank you

---

### Post by wildmanne39 on 2011-08-31
Hi, sorry wrong directions just a minute.

---

### Post by wildmanne39 on 2011-08-31
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

```
Thank you

---

### Post by mdunphy on 2011-08-31
Just did it, restarted, and it is now working fine.  Thanks a lot for your help!

---

### Post by wildmanne39 on 2011-08-31
Hi, your welcome! I am glad I could help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by mdunphy on 2011-09-01
Scratch that.  I don't think we're finished quite yet... After a restart I am now unable to connect to any wireless connections be it secured or unsecured.  Now when I try to connect to a network it tries and tries and eventually gives up and disconnects.  

iwconfig output while attempting to connect to WPA2 AES network:

```
mark@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"teamRAMROD"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 68:7F:74:FC:44:9A   
          Bit Rate=65 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:102   Missed beacon:0

```

ifconfig right after that:

```
mark@ubuntu:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr d0:df:9a:12:8c:79  
          inet6 addr: fe80::d2df:9aff:fe12:8c79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1776 (1.7 KB)  TX bytes:15785 (15.7 KB)

```

---

### Post by wildmanne39 on 2011-09-01
Hi, please run these commands:
```
dmesg | egrep 'ath|firm'
```
```
rfkill list all
```
```
lsmod | grep ath
```
```
dmesg | grep wlan0
```
```
nm-tool
```
```
sudo iwlist scan
```
Thank you

---

### Post by mdunphy on 2011-09-01
dmesg | egrep 'ath|firm' output:
```
mark@ubuntu:~$ dmesg | egrep 'ath|firm'
[    1.412794] device-mapper: multipath: version 1.2.0 loaded
[    1.412804] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.108427] ath9k 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.108447] ath9k 0000:03:00.0: setting latency timer to 64
[   16.199412] ath: EEPROM regdomain: 0x65
[   16.199419] ath: EEPROM indicates we should expect a direct regpair map
[   16.199426] ath: Country alpha2 being used: 00
[   16.199429] ath: Regpair used: 0x65
[   16.276023] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.278084] Registered led device: ath9k-phy0::radio
[   16.278211] Registered led device: ath9k-phy0::assoc
[   16.278326] Registered led device: ath9k-phy0::tx
[   16.278448] Registered led device: ath9k-phy0::rx
```

rfkill list all output:
```
mark@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

lsmod | grep ath output:

```
mark@ubuntu:~$ lsmod | grep ath
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath
```

dmesg | grep wlan0 output:

```
mark@ubuntu:~$ dmesg | grep wlan0
[   16.863598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.656996] wlan0: authenticate with 68:7f:74:fc:44:9a (try 1)
[   35.659262] wlan0: authenticated
[   35.679370] wlan0: associate with 68:7f:74:fc:44:9a (try 1)
[   35.696125] wlan0: RX AssocResp from 68:7f:74:fc:44:9a (capab=0x431 status=0 aid=3)
[   35.696135] wlan0: associated
[   35.705415] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.360260] wlan0: no IPv6 routers present
[   81.215943] wlan0: deauthenticating from 68:7f:74:fc:44:9a by local choice (reason=3)
```

nm-tool output: 
```
mark@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:6D:E7:5C

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.87.64.150
    DNS:             68.87.75.198


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        D0:DF:9A:12:8C:79

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NJEBRWNET01:     Infra, 00:1E:2A:4E:B1:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    denyeau:         Infra, C4:3D:C7:AA:82:D4, Freq 2412 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    linksys:         Infra, 00:14:BF:8B:29:0F, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    teamRAMROD:      Infra, 68:7F:74:FC:44:9A, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA2
    linksys:         Infra, 00:18:F8:DD:3F:15, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    mcfresh45:       Infra, 0C:D5:02:50:24:E4, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    CenterPTwrls:    Infra, E0:91:F5:64:D7:AA, Freq 2432 MHz, Rate 54 Mb/s, Strength 44 WPA2
```

sudo iwlist scan output:
```
mark@ubuntu:~$ sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E0:91:F5:64:D7:AA
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"CenterPTwrls"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024e39da183
                    Extra: Last beacon: 1020ms ago
                    IE: Unknown: 000C43656E746572505477726C73
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16050D1600000000000000000000000000000000000000
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B00010310470010BB2EDDC211B43B2CEE5A5D2E0BFD7D911021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34050D1600000000000000000000000000000000000000
          Cell 02 - Address: 68:7F:74:FC:44:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"teamRAMROD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000051c0d8b37
                    Extra: Last beacon: 530ms ago
                    IE: Unknown: 000A7465616D52414D524F44
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B0001031047001000000000000000011000687F74FC449A102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B4241343435301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:14:BF:8B:29:0F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024e429af93
                    Extra: Last beacon: 580ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020014
```

Thank you

---

### Post by mdunphy on 2011-09-01
After resetting my modem and router it is working fine now.  I didn't think to do that last night since I wasn't able to connect to other networks either but after I booted into Windows this morning and still couldn't connect a light bulb lit up.  All seems to be in order now.  Thanks again for all your help!  I will mark this thread as solved.

---

### Post by wildmanne39 on 2011-09-01
Hi, I am glad it is working, Enjoy.

---

### Post by brucehohl on 2011-09-04
Thanks to all who contributed above. I also just installed 11.04 onto a Lenovo B575 and experienced the same problem of wireless not working.

I now run the following script (from info above) after I logon to get wireless working:

wireless.sh contents:
#!/bin/bash
sudo ifconfig wlan0 down
sudo rmmod -f acer-wmi
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

I think it may also be necessary for the kernel to be updated to at least 2.6.38-11-generic.  The current LiveCD has 2.6.38-8-generic.

I probably won't add this to my config files. Hopefully a later update solve this without any additional action by the user.

---

### Post by wildmanne39 on 2011-09-04
Hi, your welcome! I am glad I could help.

---

### Post by nilrezei on 2011-09-10
Hi guys. Hope you can help with my very similar problem. 

I have about same configuration as above, however I'm not using a router, but an Internet Connection Sharing ad-hoc mode between 2 computers. 

The host is running Windows XP and the client is the Acer laptop with the Atheros wifi.

I can see a list of wireless networks, I'm trying to connect to my home network but it is trying to connect for a few minutes, then it gives up. 

I've tried all the things you mentioned here with no success.

Much appreciated any useful tip.

---

### Post by wildmanne39 on 2011-09-10
Hi, welcome to the forum! I do not know much about internet sharing, I do know that AD-Hoc is problematic for connection issues in ubuntu a lot of times.

I researched for quite awhile before posting I found that with your driver is it is the same one as the OP can be set up as an Access point.
Here is a link for it.
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

---

### Post by nilrezei on 2011-09-11
> **wildmanne39 said:**
> Hi, welcome to the forum! I do not know much about internet sharing, I do not that AD-Hoc is problematic for connection issues in ubuntu a lot of times.

I researched for quite awhile before posting I found that with your driver is it is the same one as the OP can be set up as an Access point.
Here is a link for it.
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

Thank you for your prompt answer. 

It is simpler, actually, no access point is needed. There are 2 computers.  The host computer is a desktop with Windows XP on it. 

A wireless ad-hoc network has already been created there and tested with another vista laptop and another desktop linux, the last 2 both as clients. They connect to the wireless network created on the Windos XP host. So the network is operational and the ICS works fine. 

The linux desktop is having some problems connecting sometimes, but after a few disabling and re-enabling wireless it connects. Manual IPv4 settings only though, automatic seems to try to connect for ever...

However, I just installed Lubuntu 11.04 on a laptop with Atheros wifi and it tries to connect but it gives up after a while. It should connect same as the others. I tried manual settings, same as in the previous desktop linux but nothing. It connects (or just shows connected status, just like that), but no ICS...

So, to summarize: The network created on the host (Windows XP) PC is operational and ICS works with both other Windows and Linux clients. No access points needed, simple ad-hoc mode, just like:

[http://windows.microsoft.com/en-US/windows-xp/help/networking/wireless-network-no-router](http://windows.microsoft.com/en-US/windows-xp/help/networking/wireless-network-no-router)

....
Thanks again.

---

### Post by wildmanne39 on 2011-09-11
Hi, post the results of these commands here please it may be an issue with your wireless driver.
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
lsmod | grep ath
```
```
dmesg | grep ath
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by nilrezei on 2011-09-11
> **wildmanne39 said:**
> Hi, post the results of these commands here please it may be an issue with your wireless driver.
```
sudo lshw -C network
[sudo] password for mese: 

  *-network               

       description: Ethernet interface

       product: NetXtreme BCM5764M Gigabit Ethernet PCIe

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 10

       serial: 00:1f:16:c0:2d:c3

       capacity: 1Gbit/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=5764m-v3.34 latency=0 link=no multicast=yes port=twisted pair

       resources: irq:45 memory:f4500000-f450ffff

  *-network

       description: Wireless interface

       product: AR928X Wireless Network Adapter (PCI-Express)

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:03:00.0

       logical name: wlan0

       version: 01

       serial: 00:17:c4:a3:cd:5c

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn

       resources: irq:17 memory:f4600000-f460ffff

mese@mesezene:~$ 
``````
nm-tool
mese@mesezene:~$ nm-tool



NetworkManager Tool



State: disconnected



- Device: eth0 -----------------------------------------------------------------

  Type:              Wired

  Driver:            tg3

  State:             unavailable

  Default:           no

  HW Address:        00:1F:16:C0:2D:C3



  Capabilities:

    Carrier Detect:  yes



  Wired Properties

    Carrier:         off





- Device: wlan0 ----------------------------------------------------------------

  Type:              802.11 WiFi

  Driver:            ath9k

  State:             disconnected

  Default:           no

  HW Address:        00:17:C4:A3:CD:5C



  Capabilities:



  Wireless Properties

    WEP Encryption:  yes

    WPA Encryption:  yes

    WPA2 Encryption: yes



  Wireless Access Points 

    Pulse:           Infra, 00:1B:FC:3A:DE:2D, Freq 2412 MHz, Rate 54 Mb/s, Strength 35

    default:         Infra, E0:CB:4E:E4:DE:2A, Freq 2447 MHz, Rate 54 Mb/s, Strength 58

    Esmeralda:         Ad-Hoc, D6:72:82:AB:34:04, Freq 2412 MHz, Rate 11 Mb/s, Strength 87 WEP

    obsfere:      Infra, 00:21:27:D6:EB:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2

    AtlasTelecom:    Infra, 00:90:4B:CA:18:45, Freq 2472 MHz, Rate 54 Mb/s, Strength 51 WPA Enterprise





mese@mesezene:~$ 

``````
lspci -nn | grep -e 0280 -e 0200
mese@mesezene:~$ lspci -nn | grep -e 0280 -e 0200

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)

03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

mese@mesezene:~$ 

``````
lsusb
mese@mesezene:~$ lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mese@mesezene:~$ 

``````
iwconfig
mese@mesezene:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bgn  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:on

          

mese@mesezene:~$ 

``````
rfkill list all
mese@mesezene:~$ rfkill list all

0: acer-wireless: Wireless LAN

    Soft blocked: no

    Hard blocked: no

1: acer-threeg: Wireless WAN

    Soft blocked: no

    Hard blocked: no

2: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

mese@mesezene:~$ 

``````
sudo iwlist scan
mese@mesezene:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wlan0     Scan completed :

          Cell 01 - Address: D6:72:82:AB:34:04

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=60/70  Signal level=-50 dBm  

                    Encryption key:on

                    ESSID:"Esmeralda"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

                    Mode:Ad-Hoc

                    Extra:tsf=00000000657f9eca

                    Extra: Last beacon: 844ms ago

                    IE: Unknown: 000750756D706B696E

                    IE: Unknown: 010482848B96

                    IE: Unknown: 030101

                    IE: Unknown: 06020000

          Cell 02 - Address: E0:CB:4E:E4:DE:2A

                    Channel:8

                    Frequency:2.447 GHz (Channel 8)

                    Quality=40/70  Signal level=-70 dBm  

                    Encryption key:off

                    ESSID:"default"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s

                              18 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=0000002d3f83b16a

                    Extra: Last beacon: 392ms ago

                    IE: Unknown: 000764656661756C74

                    IE: Unknown: 010882848B961224486C

                    IE: Unknown: 030108

                    IE: Unknown: 2A0104

                    IE: Unknown: 32040C183060

                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

                    IE: Unknown: 0B05000057127A

                    IE: Unknown: DD07000C4307000000

                    IE: Unknown: 0706494520010D10

          Cell 03 - Address: 00:90:4B:CA:18:45

                    Channel:13

                    Frequency:2.472 GHz (Channel 13)

                    Quality=36/70  Signal level=-74 dBm  

                    Encryption key:on

                    ESSID:"AtlasTelecom"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s

                              9 Mb/s; 12 Mb/s; 18 Mb/s

                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s

                    Mode:Master

                    Extra:tsf=00000005ddc8df65

                    Extra: Last beacon: 52ms ago

                    IE: Unknown: 000C41746C617354656C65636F6D

                    IE: Unknown: 010882848B968C129824

                    IE: Unknown: 03010D

                    IE: Unknown: 0706415420010D14

                    IE: Unknown: 2A0100

                    IE: Unknown: 3204B048606C

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (1) : TKIP

                        Authentication Suites (1) : 802.1x

                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

          Cell 04 - Address: 00:1B:FC:3A:DE:2D

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=26/70  Signal level=-84 dBm  

                    Encryption key:off

                    ESSID:"Pulse"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=0000002504a9018e

                    Extra: Last beacon: 904ms ago

                    IE: Unknown: 00054F63746176

                    IE: Unknown: 010882848B962430486C

                    IE: Unknown: 030101

                    IE: Unknown: 2A0104

                    IE: Unknown: 2F0104

                    IE: Unknown: 32040C121860

                    IE: Unknown: DD090010180201F0000000

``````
lsmod | grep ath
mese@mesezene:~$ lsmod | grep ath

ath9k                 103633  0 

mac80211              257001  1 ath9k

ath9k_common           13611  1 ath9k

ath9k_hw              300328  2 ath9k,ath9k_common

ath                    19141  2 ath9k,ath9k_hw

cfg80211              156212  3 ath9k,mac80211,ath

mese@mesezene:~$ 

``````
dmesg | grep ath
mese@mesezene:~$ dmesg | grep ath

[    0.584088] device-mapper: multipath: version 1.2.0 loaded

[    0.584092] device-mapper: multipath round-robin: version 1.0.0 loaded

[   15.332081] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[   15.332093] ath9k 0000:03:00.0: setting latency timer to 64

[   15.772198] ath: EEPROM regdomain: 0x65

[   15.772201] ath: EEPROM indicates we should expect a direct regpair map

[   15.772204] ath: Country alpha2 being used: 00

[   15.772206] ath: Regpair used: 0x65

[   15.800332] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'

[   15.801575] Registered led device: ath9k-phy0::radio

[   15.801649] Registered led device: ath9k-phy0::assoc

[   15.801716] Registered led device: ath9k-phy0::tx

[   15.801786] Registered led device: ath9k-phy0::rx

[  332.748343] ath: Failed to stop TX DMA in 100 msec after killing last frame

[  332.748392] ath: Failed to stop TX DMA!

[  433.728254] ath: Failed to stop TX DMA in 100 msec after killing last frame

[  433.728301] ath: Failed to stop TX DMA!

mese@mesezene:~$ 

```by clicking on new reply and click # and paste the information between the brackets.
Thank you

There. Sorry if I'm not the good with forum quoting. At first, the editor didn't want to let me paste it all at once, said I can't load too many "images"???...

Hope that helps.

---

### Post by nilrezei on 2011-09-11
Seems to be common bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171)

*sigh*...

Thing of note: After connecting the desktop linux client to the desktop Windows XP host and getting ICS between those2, the linux laptop client is able to connect and ICS as well!
But disconnect the linux desktop and the linux laptop fails too. Should this even be happening?? What's the connection?

IPv4 settings on Manual assigned ip-s, gateway etc. If on Automatic, it will always fail to connect...

...

So tired, wasted an entire day trying to fix this and it seems it's a common bug............

---

### Post by wildmanne39 on 2011-09-11
Hi, first we need to do two things:
Please set your encryption to wpa2 only no wep or mixed mode.

Then run these commands to see if it helps if so we will need to do one more step to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
run the commands one at a time and do not restart your computer.
Thank you

---

### Post by nilrezei on 2011-09-11
> **wildmanne39 said:**
> Hi, first we need to do two things:
Please set your encryption to wpa2 only no wep or mixed mode.

Then run these commands to see if it helps if so we will need to do one more step to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```run the commands one at a time and do not restart your computer.
Thank you

Sorry for my little confusion now, but do you mean to set WPA2 in the Linux client or in the Windows host? Cause if it's in the Windows host, we'd better forget this, I intend to travel a bit and people where I'm going may have different sorts of encryption.

---

### Post by wildmanne39 on 2011-09-11
Hi, you can try those commands with out changing the encryption settings but I do not know if it will work, also wpa2 is a lot more secure.
Thank you

---

### Post by nilrezei on 2011-09-11
> **wildmanne39 said:**
> Hi, you can try those commands with out changing the encryption settings but I do not know if it will work, also wpa2 is a lot more secure.
Thank you

I ran those commands, without changing my Windows host encryption, because that is the point. To be able to connect wirelessly no matter the encryption used, as long as I use the proper password, of course.

Same thing...

I would like to know though: is it solvable, is it with the driver? I really want to know what's the cause of it.

---

### Post by wildmanne39 on 2011-09-11
Hi, as I said I am not an expert with AD-HOC but that driver works with wpa2 better then any other and I imagine that is the problem, so I do not have any other recommendations.

With many drivers and cards they work best with wpa2.
Thank you

---

### Post by nilrezei on 2011-09-11
> **wildmanne39 said:**
> Hi, as I said I am not an expert with AD-HOC but that driver works with wpa2 better then any other and I imagine that is the problem, so I do not have any other recommendations.

With many drivers and cards they work best with wpa2.
Thank you

I appreciate your help, but I have decided I can wait a while. Maybe someday, in the not so distant future, things will be more simple with Linux, not so many bugs...

Good luck, friend. Thanks again.

---

### Post by wildmanne39 on 2011-09-11
Hi, your welcome! you could try to install wicd in synaptic then uninstall network manager, that might work my understanding is that driver plays nicer with wicd but make sure you install wicd first or you will not have a connection to install wicd after network manager is removed.
Thank you

---

### Post by 118118 on 2011-09-17
hi - not sure if these commands were the right ones, i'm trying to connect wirelessly to the internet but no access points are shown. but here's their output

sudo lshw - C network

> *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: f4:ec:38:d0:40:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbff0000-fbffffffnm-tool

> NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:25:22:C9:3E:1C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        F4:EC:38:D0:40:CF

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


lspci -nn | grep -e 0280 -e 0200

> 03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)lsub

> Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubiwconfig

> Bus 002 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 002: ID 04d9:1603 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 001 Device 003: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
luke@luke-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
rfkill list all

> 1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
sudo iwlist scan

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
lsmod | grep ath

> No command 'ath' found, did you mean:
 Command 'tth' from package 'tth' (multiverse)
 Command 'ash' from package 'ash' (universe)
 Command 'atd' from package 'at' (main)
 Command 'atc' from package 'bsdgames' (universe)
 Command 'atp' from package 'atp' (universe)
 Command 'at' from package 'at' (main)
 Command 'atq' from package 'at' (main)
ath: command not foundgmseg | grep ath

> [    0.804486] device-mapper: multipath: version 1.2.0 loaded
[    0.804490] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.220888] ath9k 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[    7.220896] ath9k 0000:03:00.0: setting latency timer to 64
[    7.270246] ath: EEPROM regdomain: 0x809c
[    7.270247] ath: EEPROM indicates we should expect a country code
[    7.270249] ath: doing EEPROM country->regdmn map search
[    7.270250] ath: country maps to regdmn code: 0x52
[    7.270251] ath: Country alpha2 being used: CN
[    7.270253] ath: Regpair used: 0x52
[    7.619412] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    7.619924] Registered led device: ath9k-phy0::radio
[    7.619939] Registered led device: ath9k-phy0::assoc
[    7.619953] Registered led device: ath9k-phy0::tx
[    7.619966] Registered led device: ath9k-phy0::rx
[  622.680413] ath9k 0000:03:00.0: PCI INT A disabled
[  622.680443] ath9k: Driver unloaded
[  659.784789] ath9k 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[  659.784800] ath9k 0000:03:00.0: setting latency timer to 64
[  659.833943] ath: EEPROM regdomain: 0x809c
[  659.833944] ath: EEPROM indicates we should expect a country code
[  659.833946] ath: doing EEPROM country->regdmn map search
[  659.833947] ath: country maps to regdmn code: 0x52
[  659.833949] ath: Country alpha2 being used: CN
[  659.833950] ath: Regpair used: 0x52
[  659.835514] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[  659.836279] Registered led device: ath9k-phy1::radio
[  659.836299] Registered led device: ath9k-phy1::assoc
[  659.836318] Registered led device: ath9k-phy1::tx
[  659.836339] Registered led device: ath9k-phy1::rx
it's my parents' router or whatever so i would prefer to not mess with it. i only have a wireless card on this computer... thanks a lot for any help :)

---

### Post by pdc on 2011-09-17
you are often better starting a new thread;

rather than jumping in on someone else's thread..

try this

[http://ubuntuforums.org/showthread.php?t=1840637](http://ubuntuforums.org/showthread.php?t=1840637)

---

### Post by wildmanne39 on 2011-09-17
Hi, please copy and paste these commands into the terminal then post the results here:
```
dmesg | egrep 'ath|firm'
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by 118118 on 2011-09-17
```
[    0.802332] device-mapper: multipath: version 1.2.0 loaded
[    0.802334] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.760802] ath9k 0000:03:00.0: PCI INT A -> Link[LNEB] -> GSI 18 (level, low) -> IRQ 18
[    6.760810] ath9k 0000:03:00.0: setting latency timer to 64
[    6.810438] ath: EEPROM regdomain: 0x809c
[    6.810440] ath: EEPROM indicates we should expect a country code
[    6.810442] ath: doing EEPROM country->regdmn map search
[    6.810443] ath: country maps to regdmn code: 0x52
[    6.810445] ath: Country alpha2 being used: CN
[    6.810446] ath: Regpair used: 0x52
[    7.081827] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    7.082322] Registered led device: ath9k-phy0::radio
[    7.082337] Registered led device: ath9k-phy0::assoc
[    7.082353] Registered led device: ath9k-phy0::tx
[    7.082366] Registered led device: ath9k-phy0::rx
```



```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
binfmt_misc            13213  1 
snd_hda_codec_via      56765  1 
arc4                   12473  2 
ath9k                 103633  0 
snd_hda_intel          24140  2 
mac80211              257001  1 ath9k
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
snd_hwdep              13274  1 snd_hda_codec
ath                    19141  2 ath9k,ath9k_hw
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nouveau               621970  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  3 ath9k,mac80211,ath
soundcore              12600  1 snd
psmouse                73312  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
serio_raw              12990  0 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
k10temp                12951  0 
lp                     13349  0 
ppdev                  12849  0 
parport_pc             32111  1 
parport                36746  3 lp,ppdev,parport_pc
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sata_nv                23176  2 
pata_amd               13762  0 
forcedeth              58190  0 
```

---

### Post by wildmanne39 on 2011-09-17
Hi run these commands one at a time and see if it helps. Disconnect your wired connection first.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```
Thank you

---

### Post by 118118 on 2011-09-18
i reinstalled ubuntu last night and this morning Internet worked fine.
the exact same thing as with my new netbook.


thanks for the help anyway.

---

### Post by 118118 on 2011-09-18
but the new connection is ridiculously slow and keeps disconnecting.

and after resetting connection is not an option again.
i tried the code you typed out but no luck.

---

### Post by wildmanne39 on 2011-09-18
Hi, after you ran my code did you restart your computer? it was not suppose to be restarted after you ran the command, if it worked we need to make it permanent.

I believe I said that in my previous posted but might not have it was getting late here when I posted it last night.

Run the code again and do not restart, then tell me if there is an improvement.
Thank you

---

### Post by ArnabDas on 2011-10-13
Can nybody plz help
i hve a sony vaio y series laptop (Vpcya15fg)
i hve a atheros wireless card in it
but it is not workingi cannot enable wireless in it
i am a beginner i need a stepwise protocol to solve it
plz help
Atheros card ar9285

---

### Post by ArnabDas on 2011-10-13
Can nybody plz help
i hve a sony vaio y series laptop (Vpcya15fg)
i hve a atheros wireless card in it
but it is not workingi cannot enable wireless in it
i am a beginner i need a stepwise protocol to solve it
plz help
Atheros card ar9285

---

### Post by wildmanne39 on 2011-10-13
Hi, welcome to the forum! Please copy and paste the commands in post 24 one at a time into the terminal by hitting ctrl+alt+t then paste the results here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ArnabDas on 2011-10-14
**sudo lshw -C network**
[sudo] password for arnab: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:f0:51:1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:93400000-9340ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 54:42:49:a1:70:d6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pairsudo lshw -C network
[sudo] password for arnab: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:dd:08:f0:51:1a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:93400000-9340ffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 54:42:49:a1:70:d6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:92400000-9243ffff ioport:1000(size=128)

       resources: irq:43 memory:92400000-9243ffff ioport:1000(size=128)
arnab@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        78:DD:08:F0:51:1A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        54:42:49:A1:70:D6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: ttyUSB0  [MTS MBlaze connection] -------------------------------------
  Type:              Mobile Broadband (CDMA)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         180.215.222.123
    Prefix:          32 (255.255.255.255)
    Gateway:         10.228.10.132

    DNS:             10.228.1.113
    DNS:             10.228.1.114


**arnab@ubuntu:~$ lspci -nn | grep -e 0280 -e 0200**
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
**arnab@ubuntu:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b211 Chicony Electronics Co., Ltd 
Bus 001 Device 007: ID 0489:e00f Foxconn / Hon Hai Foxconn T77H114 BCM2070 [Single-Chip Bluetooth 2.1 + EDR Adapter]
Bus 002 Device 003: ID 0bda:0186 Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 19d2:fff1 ONDA Communication S.p.A. 
arnab@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.
**arnab@ubuntu:~$ rfkill list all**
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
[B]
arnab@ubuntu:~$ sudo iwlist scan[/B]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ppp0      Interface doesn't support scanning.

**arnab@ubuntu:~$ lsmod | grep ath**
ath9k                 127538  0 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
**arnab@ubuntu:~$ dmesg | grep ath**
[   11.803601] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.803619] ath9k 0000:02:00.0: setting latency timer to 64
[   11.857842] ath: EEPROM regdomain: 0x65
[   11.857848] ath: EEPROM indicates we should expect a direct regpair map
[   11.857854] ath: Country alpha2 being used: 00
[   11.857857] ath: Regpair used: 0x65
[   11.898188] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.899267] Registered led device: ath9k-phy0




Im using Ubuntu 11.10

---

### Post by wildmanne39 on 2011-10-14
Hi, try this please and if it works we will need to make it permanent.

Also any connection you have to the internet you will have to disconnect from before you run the commands.
```
sudo rmmod -f acer-wmi
```
```
sudo modprobe ath9k
```
Thank you

---

### Post by ArnabDas on 2011-10-15
not working!!

rmmod -f acer-wmi
ERROR:- removing 'acer_wmi':operation not permitted


NOTe: i Hve installed NDISwrapper...and hve installed the wireless driver for windows
plz tell if i hve to remove it??

---

### Post by wildmanne39 on 2011-10-15
Hi, first all commands I give please copy and paste it will be a lot easier on you.

You can remove ndiswrapper with this command.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Please run the commands one line at a time.

Then
```
sudo rmmod -f acer-wmi
```
```
sudo modprobe ath9k
```
Thank you

---

### Post by ArnabDas on 2011-10-15
okk Trying

---

### Post by ArnabDas on 2011-10-15
Its working   :-D
Thnx a lot


One last question is this change permanent??
 if not
Plz tell how to make it permanent



u R AWESOME

---

### Post by wildmanne39 on 2011-10-15
Hi, your welcome! 
Enjoy

---

### Post by wildmanne39 on 2011-10-15
Hi, I am getting tired I forgot we need to make that one permanent.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by ArnabDas on 2011-10-15
thnx a lot again

---

### Post by ArnabDas on 2011-10-15
thats it....wifi probs are over??/
i m throwing win7 out of the window

---

### Post by wildmanne39 on 2011-10-15
Hi, I have done away with my windows too.
Ehjoy

---

### Post by ArnabDas on 2011-10-15
> **wildmanne39 said:**
> Hi, I have done away with my windows too.
Ehjoy
  will contact u again if faced with more issues 
:)

---

### Post by wildmanne39 on 2011-10-15
Hi, this thread is just for networking issues, if it is a different issue post in another part of the forum, I help out in other sections too, but there are a lot of people to help on here that might know more about a particular issue then I do.

---

### Post by teejay17 on 2011-10-27
Hi all, I was thinking about getting the Lenovo B575-500, but after reading this thread I'm mighty hesitant. Has anyone tried it with Ubuntu 11.10 yet? Also, in the past, when I had a machine where wireless didn't work out of the box, I used [WICD]("http://wicd.sourceforge.net/") which worked great; just wondering if anyone's tried that. 
If it is a real complication, I'm also considering a laptop with a Pentium P6200 chip with onboard Intel graphics...

---

### Post by wildmanne39 on 2011-10-27
Hi, I do not recommend getting a computer with the ar9285 it does not seem to work as well as other atheros cards, but the newer the hardware the more likely that linux is not going to have drivers for it yet.
Thank you

---

### Post by teejay17 on 2011-10-28
> **teejay17 said:**
> Hi all, I was thinking about getting the Lenovo B575-500, but after reading this thread I'm mighty hesitant. Has anyone tried it with Ubuntu 11.10 yet? Also, in the past, when I had a machine where wireless didn't work out of the box, I used [WICD]("http://wicd.sourceforge.net/") which worked great; just wondering if anyone's tried that. 
If it is a real complication, I'm also considering a laptop with a Pentium P6200 chip with onboard Intel graphics...
Well just for fun I went out and bought this little machine. It was on sale for $299, and worst case scenario was I could always return it if things didn't work. Long story short, WICD works amazing. Had wireless up and running within two minutes — I'm typing on wireless now!
WICD is, well, wicked (pun totally intended!)

---

### Post by matt_mccarron on 2011-12-13
Hi Wildmanne!  using 11.10 with a lenovo b575

Here's the info requested on the "how to" page...  your help is greatly appreciated!

Lenovo Laptop B575

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b272 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 005 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 

eth0      Link encap:Ethernet  HWaddr f0:de:f1:6f:85:e8  
          inet addr:192.168.2.15  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe6f:85e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4046247 (4.0 MB)  TX bytes:607412 (607.4 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4456 (4.4 KB)  TX bytes:4456 (4.4 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
fglrx                2642629  94 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
joydev                 17393  0 
mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              172392  2 rt2x00lib,mac80211
rts5139               279514  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13575  0 
acer_wmi               23302  0 
lp                     17455  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
sp5100_tco             13495  0 
i2c_piix4              13093  0 
snd_timer              28932  2 snd_pcm,snd_seq
psmouse                73673  0 
eeprom_93cx6           12653  1 rt2800pci
serio_raw              12990  0 
sparse_keymap          13658  2 ideapad_laptop,acer_wmi
video                  18908  0 
k10temp                12990  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 acer_wmi
parport                40930  3 parport_pc,ppdev,lp
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

[    1.284163] udevd[82]: starting version 173
[    1.312144] usb 2-3: new high speed USB device number 2 using ehci_hcd
[    1.436119] Refined TSC clocksource calibration: 1596.599 MHz.
[    1.436132] Switching to clocksource tsc
[    1.458439] ahci 0000:00:11.0: version 3.0
[    1.458483] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.459153] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.459162] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio ccc sxs 
[    1.463476] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.463585] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.463647] r8169 0000:02:00.0: setting latency timer to 64
[    1.463730] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.464608] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xf803e000, f0:de:f1:6f:85:e8, XID 0c200000 IRQ 42
[    1.466303] scsi0 : ahci
[    1.467552] scsi1 : ahci
[    1.471595] scsi2 : ahci
[    1.472348] ata1: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b100 irq 19
[    1.472355] ata2: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b180 irq 19
[    1.472361] ata3: SATA max UDMA/133 abar m1024@0xe024b000 port 0xe024b200 irq 19
[    1.576358] usb 2-5: new high speed USB device number 3 using ehci_hcd
[    1.792415] ata3: SATA link down (SStatus 0 SControl 300)
[    1.844329] usb 5-1: new full speed USB device number 2 using ohci_hcd
[    1.964363] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.964405] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.966497] ata1.00: ATA-8: WDC WD3200BPVT-24ZEST0, 02.01A02, max UDMA/133
[    1.966511] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.966597] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633F, LE02, max UDMA/33
[    1.968106] ata1.00: configured for UDMA/133
[    1.968773] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BPVT-2 02.0 PQ: 0 ANSI: 5
[    1.969098] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.969342] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.969348] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.970125] sd 0:0:0:0: [sda] Write Protect is off
[    1.970135] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.970500] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.971639] ata2.00: configured for UDMA/33
[    1.979701] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  LE02 PQ: 0 ANSI: 5
[    1.989357] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.989366] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.989603] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.989720] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.033659]  sda: sda1 sda2 < sda5 >
[    2.034424] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.434283] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.850493] udevd[317]: starting version 173
[    5.283091] Adding 3773436k swap on /dev/sda5.  Priority:-1 extents:1 across:3773436k 
[    7.080638] wmi: Mapper loaded
[    7.370879] acpi device:3d: registered as cooling_device2
[    7.371239] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[    7.371346] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    7.545016] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    7.569299] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    7.569418] SP5100 TCO timer: mmio address 0xb80830 already in use
[    7.600973] Linux video capture interface: v2.00
[    7.613137] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b272)
[    7.615817] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0/input/input6
[    7.616788] usbcore: registered new interface driver uvcvideo
[    7.616792] USB Video Class driver (v1.1.0)
[    7.689605] lp: driver loaded but no devices found
[    7.773585] acer_wmi: Acer Laptop ACPI-WMI Extras
[    7.779156] input: Ideapad extra buttons as /devices/platform/ideapad/input/input7
[    8.325496] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    8.327738] Initializing rts5139 USB card reader driver...
[    8.335577] scsi3 : SCSI emulation for RTS5139 USB card reader
[    8.336681] scsi 3:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    8.336741] scsi: killing requests for dead queue
[    8.337365] usbcore: registered new interface driver rts5139
[    8.337370] Realtek rts5139 USB card reader support registered.
[    8.352280] scsi: killing requests for dead queue
[    8.358963] cfg80211: Calling CRDA to update world regulatory domain
[    8.368208] scsi: killing requests for dead queue
[    8.376312] scsi: killing requests for dead queue
[    8.388278] scsi: killing requests for dead queue
[    8.404288] scsi: killing requests for dead queue
[    8.407500] type=1400 audit(1323808227.667:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=617 comm="apparmor_parser"
[    8.407538] type=1400 audit(1323808227.667:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=491 comm="apparmor_parser"
[    8.408272] type=1400 audit(1323808227.671:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=491 comm="apparmor_parser"
[    8.408305] type=1400 audit(1323808227.671:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=617 comm="apparmor_parser"
[    8.408762] type=1400 audit(1323808227.671:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=491 comm="apparmor_parser"
[    8.408804] type=1400 audit(1323808227.671:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=617 comm="apparmor_parser"
[    8.416237] scsi: killing requests for dead queue
[    8.434009] scsi: killing requests for dead queue
[    8.446343] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[    8.448620] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    8.453770] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    8.510150] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    8.602232] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.602242] Disabling lock debugging due to kernel taint
[    8.800861] [fglrx] Maximum main memory to use for locked dma buffers: 2746 MBytes.
[    8.800945] [fglrx]   vendor: 1002 device: 9802 count: 1
[    8.801754] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[    8.801782] pci 0000:00:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    8.801791] pci 0000:00:01.0: setting latency timer to 64
[    8.802555] [fglrx] Kernel PAT support is enabled
[    8.802598] [fglrx] module loaded - fglrx 8.90.5 [Oct 12 2011] with 1 minors
[    9.178166] rt2800pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.178184] rt2800pci 0000:03:00.0: setting latency timer to 64
[    9.181334] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    9.181340] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181344] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    9.181349] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181353] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    9.181358] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181362] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    9.181367] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181371] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    9.181375] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181379] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    9.181384] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181388] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    9.181393] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181397] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    9.181402] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181405] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    9.181410] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181414] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    9.181419] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181423] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    9.181428] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181432] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    9.181436] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181440] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    9.181445] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.181449] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    9.181454] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[    9.215114] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    9.216149] Registered led device: rt2800pci-phy0::radio
[    9.216181] Registered led device: rt2800pci-phy0::assoc
[    9.216217] Registered led device: rt2800pci-phy0::quality
[    9.466360] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.466442] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[    9.466481] HDA Intel 0000:00:01.1: setting latency timer to 64
[    9.754357] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[    9.754768] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[    9.755334] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.515377] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.515386] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515391] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.515396] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515400] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.515405] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515409] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.515414] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515417] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.515422] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515426] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.515431] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515435] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.515439] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515443] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.515448] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515452] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.515456] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515460] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.515465] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515469] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.515473] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515477] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.515482] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515486] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.515491] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515495] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.515499] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.515505] cfg80211: World regulatory domain updated:
[   10.515508] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.515513] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.515518] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.515523] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.515527] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.515532] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.186307] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.617743] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   11.617750] vesafb: scrolling: redraw
[   11.617756] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   11.618547] vesafb: framebuffer at 0xd0000000, mapped to 0xf9600000, using 3072k, total 3072k
[   11.618854] Console: switching to colour frame buffer device 128x48
[   11.618900] fb0: VESA VGA frame buffer device
[   14.499560] ppdev: user-space parallel port driver
[   14.839817] type=1400 audit(1323808234.099:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[   14.840649] type=1400 audit(1323808234.103:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   14.841148] type=1400 audit(1323808234.103:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[   15.172794] type=1400 audit(1323808234.435:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=957 comm="apparmor_parser"
[   15.385963] type=1400 audit(1323808234.647:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[   15.386772] type=1400 audit(1323808234.647:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
[   16.143781] r8169 0000:02:00.0: eth0: link down
[   16.143797] r8169 0000:02:00.0: eth0: link down
[   16.144495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.594357] type=1400 audit(1323808235.855:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=956 comm="apparmor_parser"
[   16.595562] type=1400 audit(1323808235.855:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=956 comm="apparmor_parser"
[   16.868729] type=1400 audit(1323808236.131:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=963 comm="apparmor_parser"
[   16.869463] type=1400 audit(1323808236.131:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=963 comm="apparmor_parser"
[   17.780896] r8169 0000:02:00.0: eth0: link up
[   17.781227] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   26.673072] audit_printk_skb: 3 callbacks suppressed
[   26.673079] type=1400 audit(1323808245.935:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=959 comm="apparmor_parser"
[   26.675833] type=1400 audit(1323808245.935:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=959 comm="apparmor_parser"
[   26.677896] type=1400 audit(1323808245.939:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=959 comm="apparmor_parser"
[   27.198532] init: failsafe main process (889) killed by TERM signal
[   27.351908] init: apport pre-start process (1062) terminated with status 1
[   27.357168] init: apport post-stop process (1089) terminated with status 1
[   28.208187] eth0: no IPv6 routers present
[   30.650723] Bluetooth: Core ver 2.16
[   30.650785] NET: Registered protocol family 31
[   30.650788] Bluetooth: HCI device and connection manager initialized
[   30.650793] Bluetooth: HCI socket layer initialized
[   30.650797] Bluetooth: L2CAP socket layer initialized
[   30.652301] Bluetooth: SCO socket layer initialized
[   30.704083] Bluetooth: RFCOMM TTY layer initialized
[   30.704093] Bluetooth: RFCOMM socket layer initialized
[   30.704096] Bluetooth: RFCOMM ver 1.11
[   30.709060] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.709066] Bluetooth: BNEP filters: protocol multicast
[   30.730921] [fglrx] ATIF platform detected with notification ID: 0x81
[   32.145704] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   32.203711] fglrx_pci 0000:00:01.0: irq 44 for MSI/MSI-X
[   32.205048] [fglrx] Firegl kernel thread PID: 1214
[   32.205357] [fglrx] Firegl kernel thread PID: 1215
[   32.205666] [fglrx] Firegl kernel thread PID: 1216
[   32.205910] [fglrx] IRQ 44 Enabled
[   32.485037] [fglrx] Gart USWC size:904 M.
[   32.485044] [fglrx] Gart cacheable size:357 M.
[   32.485055] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   32.485059] [fglrx] Reserved FB block: Unshared offset:fd2b000, size:2d5000 
[   32.485064] [fglrx] Reserved FB block: Unshared offset:17ff4000, size:c000 
[   43.361892] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10322.638118] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10326.300486] PM: Syncing filesystems ... done.
[10326.303314] PM: Preparing system for mem sleep
[10326.303345] Freezing user space processes ... (elapsed 0.01 seconds) done.
[10326.316338] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[10326.332346] PM: Entering mem sleep
[10326.332461] Suspending console(s) (use no_console_suspend to debug)
[10326.333175] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[10326.412460] rt2800pci 0000:03:00.0: PCI INT A disabled
[10326.412512] ohci_hcd 0000:00:14.5: PCI INT C disabled
[10326.412630] ohci_hcd 0000:00:13.0: PCI INT A disabled
[10326.412651] ehci_hcd 0000:00:12.2: PCI INT B disabled
[10326.412664] ohci_hcd 0000:00:12.0: PCI INT A disabled
[10326.412835] [fglrx] IRQ 44 Disabled
[10326.412876] [fglrx] Preparing suspend fglrx in kernel.
[10326.428157] ehci_hcd 0000:00:13.2: PCI INT B disabled
[10326.517361] HDA Intel 0000:00:14.2: PCI INT A disabled
[10326.517457] HDA Intel 0000:00:01.1: PCI INT B disabled
[10326.517493] ACPI handle has no context!
[10326.519261] sd 0:0:0:0: [sda] Stopping disk
[10326.532024] PM: suspend of drv:HDA Intel dev:0000:00:01.1 complete after 119.321 msecs
[10326.532106] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 119.580 msecs
[10326.694301] [fglrx] Suspending fglrx in kernel completed.
[10326.694304] [fglrx] Power down the ASIC .
[10326.694432] PM: suspend of drv:fglrx_pci dev:0000:00:01.0 complete after 281.659 msecs
[10327.111435] PM: suspend of drv:sd dev:0:0:0:0 complete after 778.267 msecs
[10327.111466] PM: suspend of drv:scsi dev:target0:0:0 complete after 778.014 msecs
[10327.111485] PM: suspend of drv:scsi dev:host0 complete after 776.854 msecs
[10327.111742] ahci 0000:00:11.0: PCI INT A disabled
[10327.111752] PM: suspend of drv:ahci dev:0000:00:11.0 complete after 699.082 msecs
[10327.111774] PM: suspend of drv: dev:pci0000:00 complete after 683.633 msecs
[10327.111788] PM: suspend of devices complete after 778.982 msecs
[10327.111792] PM: suspend devices took 0.776 seconds
[10327.112143] r8169 0000:02:00.0: PME# enabled
[10327.112160] pcieport 0000:00:15.0: wake-up capability enabled by ACPI
[10327.160199] PM: late suspend of devices complete after 48.400 msecs
[10327.160243] ACPI: Preparing to enter system sleep state S3
[10327.220887] PM: Saving platform NVS memory
[10327.223407] Disabling non-boot CPUs ...
[10327.223882] Broke affinity for irq 17
[10327.224954] CPU 1 is now offline
[10327.225336] ACPI: Low-level resume complete
[10327.225336] PM: Restoring platform NVS memory
[10327.225336] Enabling non-boot CPUs ...
[10327.225336] Booting Node 0 Processor 1 APIC 0x1
[10327.225336] smpboot cpu 1: start_ip = 99000
[10327.224913] Initializing CPU#1
[10327.336819] CPU1 is up
[10327.337752] ACPI: Waking up from system sleep state S3
[10327.340026] Switched to NOHz mode on CPU #1
[10327.469914] power_supply BAT0: parent PNP0C0A:00 should not be sleeping
[10327.469948] HDA Intel 0000:00:01.1: restoring config space at offset 0xf (was 0x2ff, writing 0x205)
[10327.469966] HDA Intel 0000:00:01.1: restoring config space at offset 0x4 (was 0x0, writing 0xe0244000)
[10327.469973] HDA Intel 0000:00:01.1: restoring config space at offset 0x3 (was 0x800000, writing 0x80000( i had to erase an emoticon with shades on as the rules of posting only  allow 8 images and for some reason they are appearing all over the  place...)
[10327.470027] HDA Intel 0000:00:01.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
[10327.484070] ehci_hcd 0000:00:12.2: BAR 0: set to [mem 0xe024b500-0xe024b5ff] (PCI address [0xe024b500-0xe024b5ff])
[10327.484108] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[10327.500065] ehci_hcd 0000:00:13.2: BAR 0: set to [mem 0xe024b400-0xe024b4ff] (PCI address [0xe024b400-0xe024b4ff])
[10327.500104] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[10327.500148] piix4_smbus 0000:00:14.0: restoring config space at offset 0x1 (was 0x2200403, writing 0x2200400)
[10327.500168] HDA Intel 0000:00:14.2: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[10327.500192] HDA Intel 0000:00:14.2: restoring config space at offset 0x3 (was 0x0, writing 0x4008)
[10327.500334] pcieport 0000:00:15.0: restoring config space at offset 0x3 (was 0x810000, writing 0x81000( i had to erase an emoticon with shades on as the rules of posting only  allow 8 images and for some reason they are appearing all over the  place...)
[10327.500416] pcieport 0000:00:15.2: restoring config space at offset 0x3 (was 0x810000, writing 0x81000( i had to erase an emoticon with shades on as the rules of posting only  allow 8 images and for some reason they are appearing all over the  place...)
[10327.500678] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[10327.500698] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xe000000c)
[10327.500708] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000400c)
[10327.500719] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x1001)
[10327.500727] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x( i had to erase an emoticon with shades on as the rules of posting only  allow 8 images and for some reason they are appearing all over the  place...)
[10327.500737] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[10327.500825] rt2800pci 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[10327.500853] rt2800pci 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xe0100000)
[10327.500861] rt2800pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x ( i had to erase an emoticon with shades on as the rules of posting only allow 8 images and for some reason they are appearing all over the place...)
[10327.500871] rt2800pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[10327.501047] PM: early resume of devices complete after 31.239 msecs
[10327.501207] fglrx_pci 0000:00:01.0: setting latency timer to 64
[10327.501272] HDA Intel 0000:00:01.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[10327.501281] HDA Intel 0000:00:01.1: setting latency timer to 64
[10327.501335] HDA Intel 0000:00:01.1: irq 43 for MSI/MSI-X
[10327.501426] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[10327.501502] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.503715] [fglrx] Power up the ASIC
[10327.503723] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[10327.503879] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.503889] [fglrx] Preparing resume fglrx in kernel.
[10327.503916] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[10327.503956] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[10327.503998] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[10327.504104] pcieport 0000:00:15.0: wake-up capability disabled by ACPI
[10327.504113] r8169 0000:02:00.0: PME# disabled
[10327.504468] rt2800pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[10327.563054] [fglrx] Resuming fglrx in kernel completed.
[10327.563170] [fglrx] IRQ 44 Enabled
[10327.564326] sd 0:0:0:0: [sda] Starting disk
[10327.641183] PM: resume of drv:r8169 dev:0000:02:00.0 complete after 137.081 msecs
[10327.692396] PM: resume of drv:hub dev:2-0:1.0 complete after 129.141 msecs
[10327.692409] PM: resume of drv: dev:ep_00 complete after 129.097 msecs
[10327.692441] PM: resume of drv: dev:ep_81 complete after 129.178 msecs
[10327.828299] usb 5-1: reset full speed USB device number 2 using ohci_hcd
[10327.872359] ata3: SATA link down (SStatus 0 SControl 300)
[10327.991572] PM: resume of drv: dev:ep_00 complete after 418.474 msecs
[10327.991590] PM: resume of drv:usb dev:5-1:1.0 complete after 418.607 msecs
[10327.991713] PM: resume of drv: dev:ep_02 complete after 418.650 msecs
[10327.991731] PM: resume of drv: dev:ep_81 complete after 418.712 msecs
[10328.048205] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[10328.067751] ata2.00: configured for UDMA/33
[10328.096322] usb 2-5: reset high speed USB device number 3 using ehci_hcd
[10328.238110] PM: resume of drv: dev:ep_00 complete after 673.815 msecs
[10328.238130] PM: resume of drv:rts5139 dev:2-5:1.0 complete after 673.986 msecs
[10328.238166] PM: resume of drv: dev:ep_83 complete after 673.908 msecs
[10328.238176] PM: resume of drv: dev:ep_82 complete after 673.963 msecs
[10328.238184] PM: resume of drv: dev:ep_01 complete after 674.006 msecs
[10328.238193] PM: resume of drv:scsi dev:host3 complete after 665.068 msecs
[10328.238207] PM: resume of drv:scsi_host dev:host3 complete after 665.047 msecs
[10328.238215] PM: resume of drv:scsi dev:target3:0:0 complete after 665.020 msecs
[10328.238232] PM: resume of drv:sd dev:3:0:0:0 complete after 665.000 msecs
[10328.238243] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 664.977 msecs
[10328.340328] usb 2-3: reset high speed USB device number 2 using ehci_hcd
[10328.484384] PM: resume of drv: dev:ep_00 complete after 920.313 msecs
[10328.484403] PM: resume of drv:uvcvideo dev:2-3:1.1 complete after 920.416 msecs
[10328.484412] PM: resume of drv:uvcvideo dev:2-3:1.0 complete after 920.533 msecs
[10328.484535] PM: resume of drv: dev:ep_81 complete after 920.609 msecs
[10330.004342] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[10330.037158] ata1.00: configured for UDMA/133
[10330.064169] PM: resume of drv:sd dev:0:0:0:0 complete after 2499.839 msecs
[10330.064288] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2422.970 msecs
[10330.069012] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2496.118 msecs
[10330.069258] PM: resume of devices complete after 2568.130 msecs
[10330.069413] PM: resume devices took 2.568 seconds
[10330.069459] PM: Finishing wakeup.
[10330.069462] Restarting tasks ... done.
[10330.070600] video LNXVIDEO:01: Restoring backlight state
[10332.779796] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[10332.979952] r8169 0000:02:00.0: eth0: link down
[10332.979976] r8169 0000:02:00.0: eth0: link down
[10332.980744] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10334.625939] r8169 0000:02:00.0: eth0: link up
[10334.626668] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[10345.472264] eth0: no IPv6 routers present
[10395.581162] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[10398.821278] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10404.925346] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10406.729286] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10408.158645] r8169 0000:02:00.0: eth0: link down
[10418.889924] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10435.263930] r8169 0000:02:00.0: eth0: link down
[10435.264366] ADDRCONF(NETDEV_UP): eth0: link is not ready
[10444.357271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10458.895876] r8169 0000:02:00.0: eth0: link up
[10458.896554] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[10469.008262] eth0: no IPv6 routers present
[10599.509635] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:6f:85:e8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.2.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:1000(size=256) memory:e0004000-e0004fff memory:e0000000-e0003fff
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: cc:af:78:40:61:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-14-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:e0100000-e010ffff

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

ubuntu version:  ubuntu 11.10

uname -mr
3.0.0-14-generic i686

sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

### Post by matt_mccarron on 2011-12-14
oops... 

problem:  wireless enabled will not check... wireless doesn't work
not sure if atheros or what have you...

thanks

---

### Post by teejay17 on 2011-12-14
> **matt_mccarron said:**
> oops... 

problem:  wireless enabled will not check... wireless doesn't work
not sure if atheros or what have you...

thanks

Go to the software centre and install WICD. It will get things working.

---

### Post by wildmanne39 on 2011-12-16
Hi, please post the results of the following commands here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by snovik on 2011-12-17
Looks like there is a serious expert here who could help me. I have speed problem when connected via wifi but everything is fine when connected via phone

sudo lshw -C network
```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: e4:d5:3d:4e:69:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-14-generic firmware=N/A ip=10.0.0.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0500000-f050ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 5c:9a:d8:5a:f7:0c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:5000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff
```


nm-tool
```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [PBS-1DF6F1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        E4:D5:3D:4E:69:3E

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FRITZ!Box Fon WLAN 7170 Annex A: Infra, 00:1C:4A:07:2B:CF, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    fvztgmbh:        Infra, 00:23:69:19:6C:9A, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    PBS-669EF5:      Infra, 38:22:9D:66:9E:FA, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA
    UPC010229:       Infra, 00:24:D1:71:F1:14, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    PBS-4B8D71:      Infra, 30:39:F2:4B:8D:76, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    wohe:            Infra, 00:01:E3:E1:C6:90, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    HEHome:          Infra, 00:26:44:12:A1:F9, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    PBS-4B8D71:      Infra, 30:39:F2:4B:8D:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    LecxusHome:      Infra, 00:21:E9:B7:EF:BB, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    ACN:             Infra, 00:1A:70:5D:A2:B1, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    kasperl:         Infra, 00:1E:69:62:F0:E7, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Lenet:           Infra, 00:0F:B5:1B:80:A8, Freq 2462 MHz, Rate 11 Mb/s, Strength 75 WEP
    UPC014438:       Infra, 00:24:D1:77:7C:38, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC019073:       Infra, 00:24:D1:72:E5:57, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    UPC0047526:      Infra, 00:26:24:3E:BF:DC, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *PBS-1DF6F1:     Infra, 30:39:F2:1D:F6:F6, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA
    UPC006330:       Infra, 00:18:9B:72:83:E3, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    UPC021785:       Infra, 00:24:D1:72:5A:68, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138

    DNS:             10.0.0.138


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        5C:9A:D8:5A:F7:0C

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```


lspci -nn | grep -e 0280 -e 0200
```

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

```


lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05c8:030e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 1690:0741 Askey Computer Corp. [hex] 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical

```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"PBS-1DF6F1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:39:F2:1D:F6:F6   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:864  Invalid misc:273   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```


rfkill list all
```

1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```


sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 30:39:F2:1D:F6:F6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"PBS-1DF6F1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000030ae289b3
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000A5042532D314446364631
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD720050F204104A00011010440001021041000100103B000103104700102D2B0EC546F09B706A4494DCB2E3599610210007506972656C6C69102300064469736375731024000630303030303110420004303030311054000800060050F204000110110009506972656C6C694150100800020080
                    IE: Unknown: DD090010180204F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080400000000000000000000000000000000000000
          Cell 02 - Address: 00:0F:B5:1B:80:A8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Lenet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000088d42c8185
                    Extra: Last beacon: 248ms ago
                    IE: Unknown: 00054C656E6574
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 0406000200000000
          Cell 03 - Address: 00:24:D1:77:7C:38
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC014438"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003f772b00b
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 0009555043303134343338
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:18:9B:72:83:E3
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC006330"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b51de63da
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0009555043303036333330
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:1E:69:62:F0:E7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"kasperl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028c668d006
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 00076B61737065726C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 00:24:D1:72:E5:57
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"UPC019073"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ee2d5000b
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 0009555043303139303733
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:26:44:12:A1:F9
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HEHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003af66d67
                    Extra: Last beacon: 812ms ago
                    IE: Unknown: 00064845486F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F0
          Cell 08 - Address: 30:39:F2:4B:8D:76
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"PBS-4B8D71"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e5a66dfaa4
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 000A5042532D344238443731
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD720050F204104A00011010440001021041000100103B000103104700104663159CCD4105282F27ADB574D3D11B10210007506972656C6C69102300064469736375731024000630303030303110420004303030311054000800060050F204000110110009506972656C6C694150100800020080
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
          Cell 09 - Address: 00:24:D1:71:F1:14
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UPC010229"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002ab6ab00c
                    Extra: Last beacon: 920ms ago
                    IE: Unknown: 0009555043303130323239
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: 00:26:24:3E:BF:DC
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC0047526"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000086573e7ffd
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 000A55504330303437353236
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 38:22:9D:86:15:EA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000e0687646
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 000B0000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

```


lsmod | grep ath
```

ath9k                 127538  0 
mac80211              462092  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312914  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  4 rndis_wlan,ath9k,mac80211,ath

```


dmesg | grep ath
```

[   19.142195] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.142206] ath9k 0000:03:00.0: setting latency timer to 64
[   19.192710] ath: EEPROM regdomain: 0x6a
[   19.192712] ath: EEPROM indicates we should expect a direct regpair map
[   19.192716] ath: Country alpha2 being used: 00
[   19.192717] ath: Regpair used: 0x6a
[   19.296778] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   19.297374] Registered led device: ath9k-phy0
[   23.920915] type=1400 audit(1324127476.044:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=977 comm="apparmor_parser"
[   23.921291] type=1400 audit(1324127476.044:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=977 comm="apparmor_parser"

```

---

### Post by wildmanne39 on 2011-12-17
Hi, here is a link please try what is in post 6.
[http://ubuntuforums.org/showthread.php?p=11453973#post11453973](http://ubuntuforums.org/showthread.php?p=11453973#post11453973)
Thank you

---

### Post by snovik on 2011-12-17
yes I found it. thank you

---

### Post by Freeman47 on 2012-01-23
> **wildmanne39 said:**
> Hi, disconnect your wired connection then run this command and give it a minute to work then see if you can connect.

But do not restart your computer this is a one time only command and if it works we will need to make it persistent.
```
rmmod -f acer-wmi
```Thank you


Thank you so much, Wildmanne39, I had the same problem, even the same card (Atheros AR9285) and I was looking for hours for a solution. 
In fact I spent a couple of hours reading this solution. And after all, it was only necessary to enter the code[SIZE=2] [SIZE=1]rmmod -f acer-wmi to solve my problem. Thanks from Mexico. [/SIZE][/SIZE]I'm a student of chemistry and that's why I'm not very good at computing. Excuse my bad english... LOL

---

### Post by wildmanne39 on 2012-02-03
Hi, your welcome!

---

### Post by zbanghy0ne on 2012-02-11
Hello guys. I'm having the same problem on the same Wireless chip.

Please help me.

When I try to switch the wireless on, it automatically goes off again.



Edit: SOLVED

How to:

Run this in terminal:  rfkill list

If you get Hard lock yes, then make sure your wifi is enabled from your keyboard (the special wifi button)
If you get Soft lock yes, run 

sudo gksu gedit /etc/modprobe.d/blacklist.conf

and at the end of it add blacklist acer_wmi

---

### Post by jonessoda219 on 2013-03-15
Hi,
I have a Lenovo ideapad s10-3 running ubuntu 12.10. This is my first ubuntu laptop and it is running atheros 9285. I cannot use wireless networks as the option to choose is greyed out. Please show the commands I have to post so you can help me. Also it says under RFKILL that phy0 is hardblocked and softblocked.  Please help as I have looked through about every other resource I could find. Thank you.

---

### Post by wildmanne39 on 2013-03-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

