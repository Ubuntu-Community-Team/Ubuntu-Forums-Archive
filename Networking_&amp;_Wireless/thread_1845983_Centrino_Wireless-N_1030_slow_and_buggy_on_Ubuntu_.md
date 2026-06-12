---
title: "Centrino Wireless-N 1030 slow and buggy on Ubuntu 11.4 64 bits"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by zoquero on 2011-09-18
Hi!
  

  I’ve got a** Dell XPS 17 (L702X)** shipped with a “*Intel Centrino Wireless-N 1030*”, it supports BGN. I installed Ubuntu Desktop 11.4 64 bits with latest updates but wifi is not working fine. **It works really slowly**, below the 10% of it’s capabilities (tested booting on the OEM Windoze it still has). I use just WEP, no WPA. *ifconfig* tells that there are no errors in the interface. Sometimes, just sometimes, once rebooted it works fine, but if you reboot again then it goes slow again.
  

  Each 10 minutes (aprox) you get lines like this in “*dmesg*”, looks like a re-link :
  [FONT=Courier New][SIZE=1][ 3614.922677] cfg80211: All devices are disconnected, going to restore regulatory settings[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.922692] cfg80211: Restoring regulatory settings[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.922704] cfg80211: Calling CRDA to update world regulatory domain[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929453] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929464] cfg80211: World regulatory domain updated:[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929469] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929476] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929482] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929488] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929493] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3614.929499] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.656438] wlan0: authenticate with 00:24:d1:29:b5:c3 (try 1)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.854144] wlan0: authenticate with 00:24:d1:29:b5:c3 (try 2)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.856736] wlan0: authenticated[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.857085] wlan0: associate with 00:24:d1:29:b5:c3 (try 1)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.859432] wlan0: RX AssocResp from 00:24:d1:29:b5:c3 (capab=0x411 status=0 aid=2)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1][ 3615.859441] wlan0: associated[/SIZE][/FONT]
  

  I tried to disable the “*wireless N*” mode, this way, with same results :
  [FONT=Courier New][SIZE=2]# sudo vi /etc/modprobe.d/iwlagn.conf[/SIZE][/FONT]
  [FONT=Courier New][SIZE=2]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT]
  

  I can’t find this device as explicitly supported on [COLOR=#000099]_[https]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[://]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[help]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[.]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[ubuntu]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[.]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[com]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[/]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[community]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[/]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")[HardwareSupportComponentsWirelessNetworkCardsIntel]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")_[/COLOR]
  

  Can you help me, please? Maybe some idea about what to do? or some extra info to give you?
  Best regards,
  

 



  Some data:
  

  $ lspci
  ...
  [FONT=Courier New][SIZE=1]00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)[/SIZE][/FONT]
  

  $ lspci -nn
  …
  [FONT=Courier New][SIZE=1]03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [8086:008a] (rev 34)[/SIZE][/FONT]
  

  

  $ uname -mr
  [FONT=Courier New][SIZE=1]2.6.38-11-generic x86_64[/SIZE][/FONT]
  

  

  $ ifconfig wlan0
  [FONT=Courier New][SIZE=1]wlan0     Link encap:Ethernet  direcciónHW ac:72:89:73:d6:3d  [/SIZE][/FONT] 
        [FONT=Courier New][SIZE=1]    Direc. inet:192.168.0.13  Difus.:192.168.0.255  Másc:255.255.255.0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    Dirección inet6: fe80::ae72:89ff:fe73:d63d/64 Alcance:Enlace[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    Paquetes RX:61996 errores:0 perdidos:0 overruns:0 frame:0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    Paquetes TX:46802 errores:0 perdidos:0 overruns:0 carrier:0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    colisiones:0 long.colaTX:1000[/SIZE][/FONT]
        [FONT=Courier New][SIZE=1]    Bytes RX:85832997 (85.8 MB)  TX bytes:5593452 (5.5 MB)[/SIZE][/FONT]
  

  $ iwconfig wlan0
  [FONT=Courier New][SIZE=2]wlan0     IEEE 802.11bg  ESSID:"MY_ESSID"  [/SIZE][/FONT] 
        [FONT=Courier New][SIZE=2]    Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:D1:29:B5:C3   [/SIZE][/FONT] 
        [FONT=Courier New][SIZE=2]    Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   [/SIZE][/FONT] 
        [FONT=Courier New][SIZE=2]    Retry  long limit:7   RTS thr:off   Fragment thr:off[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    Power Management:off[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    Link Quality=30/70  Signal level=-80 dBm  [/SIZE][/FONT] 
        [FONT=Courier New][SIZE=2]    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/SIZE][/FONT]
        [FONT=Courier New][SIZE=2]    Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/SIZE][/FONT]
  (as you can see I have already disabled the Wireless-N)
  

  $ lsmod
  …
  [FONT=Courier New][SIZE=1]iwlagn                333716  0[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]iwlcore               167502  1 iwlagn[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]mac80211              294370  2 iwlagn,iwlcore[/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]cfg80211              178528  3 iwlagn,iwlcore,mac80211[/SIZE][/FONT]
 

(to disable Wireless-N , for testing)

  $ cat /etc/modprobe.d/iwlagn.conf
  [FONT=Courier New][SIZE=1]options iwlagn 11n_disable50=1 11n_disable=1[/SIZE][/FONT]
  

  $ sudo lshw -C network
  [FONT=Courier New][SIZE=1]PCI (sysfs)  [/SIZE][/FONT] 
    [FONT=Courier New][SIZE=1]*-network               [/SIZE][/FONT] 
     [FONT=Courier New][SIZE=1]    description: Wireless interface[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    product: Centrino Wireless-N 1030[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    vendor: Intel Corporation[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    physical id: 0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    bus info: pci@0000:03:00.0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    logical name: wlan0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    version: 34[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    serial: ac:72:89:73:d6:3d[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    width: 64 bits[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    clock: 33MHz[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=17.168.5.2 build 35905 ip=192.168.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    resources: irq:51 memory:f3b00000-f3b01fff[/SIZE][/FONT]
    [FONT=Courier New][SIZE=1]*-network[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    description: Ethernet interface[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    product: RTL8111/8168B PCI Express Gigabit Ethernet controller[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    vendor: Realtek Semiconductor Co., Ltd.[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    physical id: 0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    bus info: pci@0000:0a:00.0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    logical name: eth0[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    version: 06[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    serial: 14:fe:b5:c6:55:da[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    size: 100Mbit/s[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    capacity: 1Gbit/s[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    width: 64 bits[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    clock: 33MHz[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.14 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s[/SIZE][/FONT]
     [FONT=Courier New][SIZE=1]    resources: irq:41 ioport:2000(size=256) memory:f3004000-f3004fff memory:f3000000-f3003fff[/SIZE][/FONT]
  

    Thanks a lot!


 / Angel Galindo Muñoz

---

### Post by zoquero on 2011-09-20
[COLOR=#000000][FONT=Arial]Hi![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I’ve solved it. Nothing was wrong. When the system detects that the laptop is on [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**battery mode**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] (AC is not plugged in) it sets the *wlan* interface in “[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*power off*[/FONT][/COLOR][COLOR=#000000][FONT=Arial]” mode.

It can be easily tested. To know the running power mode just have to do :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]$ iwconfig wlan0 | grep "Power Management"[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]          Power Management:off[/FONT][/COLOR][COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If it’s set to “*on*” then there become my performance problems.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]To change it on runtime you just have to do :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]$ sudo iwconfig wlan0 power off[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If you, like me, want to set it always off then you can for example modify the script [/FONT][/COLOR][COLOR=#000000][FONT=Arial]**/usr/lib/pm-utils/power.d/wireless**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] . I simply set this on line 39 (it's *iwlagn*) :[/FONT][/COLOR][COLOR=#000000][FONT=Arial]****[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]iwconfig_batt="power off"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
  There should be some more elegant way to do it ... but it works. There’s more info in these two links about power management, but by now I’ve got enough:[/FONT][/COLOR]
[[COLOR=#000099][FONT=Arial]_https://help.ubuntu.com/community/PowerManagement/ReducedPower_[/FONT][/COLOR]]("https://help.ubuntu.com/community/PowerManagement/ReducedPower")[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[[COLOR=#000099][FONT=Arial]_https://wiki.ubuntu.com/PowerManagement_[/FONT][/COLOR]]("https://wiki.ubuntu.com/PowerManagement")[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Best regards![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/ Angel[/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-09-20
Hi, glad you got it working, and thank you for posting your results for other people to use when they need it.

---

### Post by zoquero on 2011-09-29
Hi,
some one asked me for a **beginer guide to disable the power management of the wireless NIC**.

First of all: this problem will probably affect to lots of wireless cards, overall on laptops and probably on all GNU/Linux distributions . But probably there will be lots of problems on wireless cards on Linux laptops that nothing have to do with this. So, this may not be the solution to your problem.

1) open a **terminal** to run subsequent commands (in unity, do Ctrl+Alt+t or look for "*terminal*" in the menu)
2) ```
sudo iwconfig wlan0 power off
```3) Run ```
iwconfig
``` and take a loot at its output. There will appear a list of network interfaces. Look for the lines regarding your wireless card, most probably "*wlan0*", like this:

```
wlan0     IEEE 802.11bgn  ESSID:"YOUR_ESSID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:22:33:44:55   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```Verify if "***Power Management***" appears "***off***", if not then maybe did something wrong or on the wrong interface. Well, you could have used this command before the 2nd step to verify if it was "***on***" before. It if were "***on***" before then your problem will not be solved this way.

4) Verify if now your network works as expected. If so, then you solved the problem, like me. Now you must set this configuration for future system boots, this way:
5) ```
sudo gedit /usr/lib/pm-utils/power.d/wireless
```now substitute each "***power off***" by "***power on***" (a straight way, you could improve it, obviously). Save it. On other GNU/Linux distributions the power management transition scripts could be in other location.


Can't wait to see if the final release of Ubuntu 11.10 running on my XPS
Best regards,
/ Angel

---

### Post by Vega on 2011-11-08
Just a quick question with this card (centrino 1030)

Since power management is off and I have a 25mbps connection and my bit rate is only 11mbps(sometimes I get 1 or 5mbps), what else can be done that's preventing this card from going to full output?

---

### Post by wildmanne39 on 2011-11-09
Hi, that bit rate is always constantly changing it has a lot to do with signal strength, so you can get closer to your router, but it is not a good way to determine your internet speed.
Thank you

---

### Post by vinkic on 2012-03-30
Great info, help me, linux mint 12 lisa, dell inspirion n411z. My problem was that after hibernation wireless can't connect to any wireless network. I try to reinstall network manager and to install wicd. But only after this fix my wireless working.

---

