---
title: "[newbie] ThinkPad/ath5k &lt;-&gt; WRT54GL: solid on winxp-sp3, problems on xubuntu-9.04"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by tlroche on 2009-07-25
summary: Linux desktop newbie wants to know: how to configure my ThinkPad Z61t with ath5k_pci to work with my Linksys WRT54GL? When I boot winxp I use ThinkVantage Access Connections with

wireless security type=WPA-PSK
access point authentication=WPA2-PSK
data encryption=TKIP

and my wireless connections start quickly and are uninterrupted. When I boot xubuntu-9.04, my connections drop frequently. (Details in [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) format @ end of post.)

details:

My ThinkPad Z61t (one of the last pre-Lenovo models) came with winxp (currently SP3) to which I recently added xubuntu-9.04 via wubi. Both OS are patched up-to-date. Its winxp comes with all the ThinkVantage software, which I'm unable to find for linux. At home I have a Linksys WRT54GL (yes, the linux version) connected to a cablemodem. Both CAT5 and wireless connections from the Z61t go through the WRT54GL.

On winxp @ home, using ThinkVantage Access Connections, I connect via CAT5 immediately and connect via wireless pretty quickly. For the profile I use @ home, TVAC is configured like

wireless security type=WPA-PSK
access point authentication=WPA2-PSK
data encryption=TKIP

(et al) and the WRT54GL is configured

wireless network mode=mixed
wireless channel=6 (2.437 GHz)
WPA algorithms=TKIP+AES

(et al). On xubuntu @ home my CAT5 experience is identical: immediate connection, continuous connection while the Z61t is in use.

However my wireless experience is much less pleasant, despite using the same hardware in the same physical location relative to the router as I do in winxp. Sometimes the wireless connects automatically after login, sometimes not. Even when it connects automatically, it will make several cycles of disconnection and reconnection before stabilizing.

I'm new to linux on the desktop (though I've shelled into servers for quite a while) and to ubuntu (most of my experience has been with RHLs), so I'd appreciate advice regarding how to debug this, and how to configure my Z61t. (FWIW I'm pretty convinced the hardware is not the problem, since it works fine on xp.)

 1) Machine Brand and Model: IBM ThinkPad Z61t 9442-UN6

 2) Wireless Brand, Model and Wireless Chipset:

tlroche@tlrZ61t:~$ lspci | fgrep -ie 'net'
> 02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752M Gigabit Ethernet PCI Express (rev 02)
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

 3) Interface:

tlroche@tlrZ61t:~$ iwconfig 2>&1 | fgrep -ve 'no wireless extensions'
> wlan0     IEEE 802.11abg  ESSID:"tocwireless.net"  

Note that it's picking up a nearby, weak, open public carrier

>           Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated

note frequency matches the wireless channel=6 previously set on router
(above)

>           Tx-Power=20 dBm
>           Retry min limit:7   RTS thr:off   Fragment thr=2352 B
>           Power Management:off
>           Link Quality:0  Signal level:0  Noise level:0
>           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
>           Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 4) Modules:

tlroche@tlrZ61t:~$ lsmod | fgrep -ie 'ath'
> ath5k                 107008  0
> mac80211              217464  1 ath5k
> led_class              12036  2 ath5k,thinkpad_acpi
> cfg80211               38288  2 ath5k,mac80211

 5) Kernel boot messages

tlroche@tlrZ61t:~$ dmesg | fgrep -ie 'ath5k' | wc -l
> 755

Most of these are like

> ath5k phy0: gain calibration timeout (2437MHz)
> ath5k phy0: can't reset hardware (-11)

and

> ath5k phy0: noise floor calibration timeout (2437MHz)

 6) Network configuration

tlroche@tlrZ61t:~$ sudo lshw -C network
> [sudo] password for tlroche:
>   *-network
>        description: Ethernet interface
>        product: NetXtreme BCM5752M Gigabit Ethernet PCI Express
>        vendor: Broadcom Corporation
>        physical id: 0
>        bus info: pci@0000:02:00.0
>        logical name: eth0
>        version: 02
>        serial: 00:16:36:53:4d:0d
>        size: 100MB/s
>        capacity: 1GB/s
>        width: 64 bits
>        clock: 33MHz
>        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
>        configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5752m-v3.22 ip=192.168.1.103 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
>   *-network
>        description: Wireless interface
>        product: AR5212 802.11abg NIC
>        vendor: Atheros Communications Inc.
>        physical id: 0
>        bus info: pci@0000:03:00.0
>        logical name: wmaster0
>        version: 01
>        serial: 00:16:cf:00:01:0c
>        width: 64 bits
>        clock: 33MHz
>        capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
>        configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11abg
>   *-network DISABLED
>        description: Ethernet interface
>        physical id: 1
>        logical name: pan0
>        serial: 7a:cf:7e:1f:42:bb
>        capabilities: ethernet physical
>        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

 7) Scan for networks:

tlroche@tlrZ61t:~$ iwlist wlan0 scan
> wlan0     Scan completed :
>           Cell 01 - Address: 00:13:1A:CA:35:50
>                     ESSID:"tocwireless.net"
>                     Mode:Master
>                     Channel:6
>                     Frequency:2.437 GHz (Channel 6)
>                     Quality=12/100  Signal level:-87 dBm  Noise level=-95 dBm
>                     Encryption key:off
>                     IE: Unknown: 000F746F63776972656C6573732E6E6574
>                     IE: Unknown: 010882848B0C12961824
>                     IE: Unknown: 030106
>                     IE: Unknown: 2A0102
>                     IE: Unknown: 32043048606C
>                     IE: Unknown: 851E00004C000F00FF03210063632D7075622D63697361703133300002000025
>                     IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
>                     IE: Unknown: DD1600409604000307A4000023A400004243000062320000
>                     IE: Unknown: DD050040960302
>                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
>                               11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
>                               48 Mb/s; 54 Mb/s
>                     Extra:tsf=000001c12f7f7946
>                     Extra: Last beacon: 272ms ago

When I force an attempt to connect to my router (via the Network icon
@ upper right of my xubuntu panel), I get

tlroche@tlrZ61t:~$ iwlist wlan0 scan
> wlan0     Scan completed :
>           Cell 01 - Address: 

omitted, correct

>                     ESSID:

omitted, correct

>                     Mode:Master
>                     Channel:6
>                     Frequency:2.437 GHz (Channel 6)
>                     Quality=96/100  Signal level:-34 dBm  Noise level=-96 dBm
>                     Encryption key:on
>                     IE: Unknown: 000E4361736144654C61734761746173
>                     IE: Unknown: 010882848B962430486C
>                     IE: Unknown: 030106
>                     IE: Unknown: 2A0100
>                     IE: Unknown: 2F0100
>                     IE: IEEE 802.11i/WPA2 Version 1
>                         Group Cipher : TKIP
>                         Pairwise Ciphers (2) : CCMP TKIP
>                         Authentication Suites (1) : PSK
>                     IE: Unknown: 32040C121860
>                     IE: Unknown: DD06001018020004
>                     IE: WPA Version 1
>                         Group Cipher : TKIP
>                         Pairwise Ciphers (2) : CCMP TKIP
>                         Authentication Suites (1) : PSK
>                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
>                               24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
>                               12 Mb/s; 48 Mb/s
>                     Extra:tsf=000000059dfb7187
>                     Extra: Last beacon: 68ms ago

 8) Ubuntu Version:

tlroche@tlrZ61t:~$ lsb_release -d
> Description:	Ubuntu 9.04

 9) Kernel/architecture (including 32 vs. 64 bit):

tlroche@tlrZ61t:~$ uname -mr
> 2.6.28-13-generic i686

10) Restarting the network:

tlroche@tlrZ61t:~$ sudo /etc/init.d/networking restart
>  * Reconfiguring network interfaces...
> Ignoring unknown interface eth0=eth0.
> Ignoring unknown interface wlan0=wlan0.       [ OK ]

Your assistance is appreciated, Tom Roche <Tom_Roche@pobox.com>

---

### Post by tlroche on 2009-07-27
> **tlroche said:**
> summary: Linux desktop newbie wants to know: how to configure my ThinkPad Z61t with ath5k_pci to work with my Linksys WRT54GL?

OK, don't everybody respond all at once :-)

I still don't know how to change my configuration, but it now appears that

[LIST]
[*]the default network management tool for xubuntu-9.04 is '[network-manager-gnome]("http://packages.ubuntu.com/jaunty/network-manager-gnome")'
[*]installing '[wicd]("http://packages.ubuntu.com/jaunty/wicd")' uninstalls network-manager-*
[*]I haven't had any wireless connection problems since installing wicd
[*]wicd can be run from the tray, just like network-manager, so it's a pretty straightforward replacement
[/LIST]

---

### Post by pbateman on 2009-07-28
Thanks for this post. I have a Thinkpad z60t and my wireless card is doing the same thing. It works great on Windows but under Ubuntu it is a mess. First off it does not automatically connect, when I manually connect to it, it takes at least 2-5 minutes to connect but it only lasts about 10 minutes or so before it disconnects and re-connects itself again (taking again at least 2-5 minutes or more to do so).
You mentions the above fix worked for you? I'll try this once I get home.....hopefully works out for me too.
Thanks again

---

### Post by pbateman on 2009-07-29
I tried installing wicd but I can't even add my wireless network to it (it doesn't broadcast so i have to add it manually) . When i try to add  it by going to  'add hidden network', it only lets me type the name then click OK. Once I do that it hangs for a while but when it comes back the network is still not listed. Back to square one for me...

---

### Post by pbateman on 2009-07-29
I reinstalled network management, somehow after the reinstall it seemed to be behaving better ( I noticed there were like 3 instances of my connection created, so i deleted all but one). I could only test it again for a while before leaving to work.  I will keep trying once Im back home and see if things really improved or it was just a fluke

---

