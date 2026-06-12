---
title: "Intermittent wireless, RaLink, 10.10 64bit"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by TerminalTenant on 2011-04-01
Hello 

I have been experiencing intermittent/dropped wireless internet connection for some time since upgrading to Maverick across multiple kernel upgrades. It seems to be completely random. I'll be surfing the web and suddenly I am disconnected. I can be on for hours or a few minutes before this occurs and then it usually happens several times in a row. Network manager is normally able to reconnect but sometimes it will prompt me to reconnect. I believe the problem lies with Network manager and I've tried Wicd but that won't connect to wireless at all. I am dual booting Windows 7, which remains connected when using wireless. Any help would be greatly appreciated.[INDENT] Laptop: HpG72
OS: Maverick 10.10 64bit               
Kernel Image: Kernel Linux 2.6.35-28-generic
Network Manager Version: 0.8.1+git.20100809t190028.290dc70-0ubuntu3

[/INDENT]> lspci -vv

03:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 1453
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c2400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt2800pci, rt2860sta


---

### Post by TBABill on 2011-04-01
Looks like you have two drivers conflicting from the looks of your lspci output. An easy check would be to just ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following lines to the end of the list: ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```
 
And then ```
gksudo gedit /etc/modules
``` and make sure the only entry that starts with the letters rt is ```
rt2860sta
``` then save and restart.
 
If you want to verify if this will work before committing all these changes, just ```
sudo modprobe -r rt2800pci rt2860sta
``` and then ```
sudo modprobe rt2860sta
``` and see if it works a bit better. This just removes the module rt2800pci from the mix.

---

### Post by TerminalTenant on 2011-04-04
Hi

Thank you and sorry for not responding sooner. I hadn't thought of blacklisting the driver before. However when I went to edit the blacklist.conf as you suggested, the rt2800pci was already blacklisted. Even after using the modprobe commands and restarting, the supposedly blacklisted driver still shows up as in use. Any ideas?

---

### Post by jepong on 2011-04-04
i think i have the same issue with my AR9285... my workaround is installing linux-backports-modules-wireless-maverick-generic.

---

### Post by TerminalTenant on 2011-04-04
Yeah, I have seen other threads mentioning installing the backports and I already have them installed. It does not seem to stop the dropped connection. I'd be interested to know if there was other means of either blacklisting or removing the rt2800pci module like TBABill suggested so I could test whether or not that solved the problem.

output from the modprobe commands

> username@HPG72:~$ sudo modprobe -r rt2800pci rt2860sta
FATAL: Module rt2860sta is in use.
username@HPG72:~$ sudo modprobe rt2860sta
username@HPG72:~$ lspci -vv

03:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
    Subsystem: Hewlett-Packard Company Device 1453
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at c2400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt2800pci, rt2860sta

---

### Post by TBABill on 2011-04-04
> Kernel modules: rt2800pci, rt2860sta
 
This states you have two conflicting drivers. If the rt2800pci is already blacklisted then I wonder if it's listed in /etc/modules? If it is, just precede it with # and restart to test if that works to ignore it. If it does and wireless is reestablished, just remove it completely from /etc/modules.

---

### Post by TerminalTenant on 2011-04-04
Neither the rt2860sta or the rt2800pci modules was listed in my /etc/modules so I added them and commented out the rt2800pci. 

This is what my current /etc/modules looks like.

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt2860sta
#rt2800pcilspci still shows both kernel modules loaded after restart.

Here's the daemon.log at the time I am experiencing disconnects

> Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr  4 11:57:28 HPG72 dhclient: Listening on LPF/wlan0/e0:2a:82:19:68:02
Apr  4 11:57:28 HPG72 dhclient: Sending on   LPF/wlan0/e0:2a:82:19:68:02
Apr  4 11:57:28 HPG72 dhclient: Sending on   Socket/fallback
Apr  4 11:57:28 HPG72 dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Apr  4 11:57:28 HPG72 dhclient: DHCPACK of 192.168.1.104 from 192.168.1.1
Apr  4 11:57:28 HPG72 dhclient: bound to 192.168.1.104 -- renewal in 32956 seconds.
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   address 192.168.1.104
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   prefix 24 (255.255.255.0)
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   gateway 192.168.1.1
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   hostname 'HPG72'
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   nameserver '204.17.139.2'
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info>   nameserver '209.112.128.2'
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  4 11:57:28 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Apr  4 11:57:28 HPG72 avahi-daemon[1082]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.104.
Apr  4 11:57:28 HPG72 avahi-daemon[1082]: New relevant interface wlan0.IPv4 for mDNS.
Apr  4 11:57:28 HPG72 avahi-daemon[1082]: Registering new address record for 192.168.1.104 on wlan0.IPv4.
Apr  4 11:57:29 HPG72 NetworkManager[1084]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Apr  4 11:57:29 HPG72 NetworkManager[1084]: <info> Policy set 'Auto ROUTERNAME' (wlan0) as default for IPv4 routing and DNS.
Apr  4 11:57:29 HPG72 NetworkManager[1084]: <info> Activation (wlan0) successful, device activated.
Apr  4 11:57:29 HPG72 NetworkManager[1084]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  4 11:57:30 HPG72 ntpdate[2312]: adjust time server 91.189.94.4 offset 0.011730 sec
Apr  4 11:57:52 HPG72 wpa_supplicant[1208]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  4 11:57:52 HPG72 wpa_supplicant[1208]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  4 11:57:52 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  4 11:57:53 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  4 11:57:58 HPG72 wpa_supplicant[1208]: Trying to associate with 00:1c:10:8a:95:42 (SSID='ROUTERNAME' freq=2462 MHz)
Apr  4 11:57:58 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  4 11:57:58 HPG72 wpa_supplicant[1208]: Associated with 00:1c:10:8a:95:42
Apr  4 11:57:58 HPG72 wpa_supplicant[1208]: CTRL-EVENT-CONNECTED - Connection to 00:1c:10:8a:95:42 completed (reauth) [id=0 id_str=]
Apr  4 11:57:58 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  4 11:57:58 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr  4 11:58:21 HPG72 wpa_supplicant[1208]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  4 11:58:21 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Apr  4 11:58:21 HPG72 wpa_supplicant[1208]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  4 11:58:21 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Apr  4 11:58:26 HPG72 wpa_supplicant[1208]: Trying to associate with 00:1c:10:8a:95:42 (SSID='ROUTERNAME' freq=2462 MHz)
Apr  4 11:58:26 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  scanning -> associating
Apr  4 11:58:32 HPG72 NetworkManager[1084]: <info> (wlan0): roamed from BSSID 00:1C:10:8A:95:42 (ROUTERNAME) to (none) ((none))
Apr  4 11:58:33 HPG72 wpa_supplicant[1208]: Associated with 00:1c:10:8a:95:42
Apr  4 11:58:33 HPG72 wpa_supplicant[1208]: CTRL-EVENT-CONNECTED - Connection to 00:1c:10:8a:95:42 completed (reauth) [id=0 id_str=]
Apr  4 11:58:33 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  associating -> associated
Apr  4 11:58:33 HPG72 NetworkManager[1084]: <info> (wlan0): supplicant connection state:  associated -> completed
Apr  4 11:58:38 HPG72 NetworkManager[1084]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:1C:10:8A:95:42 (ROUTERNAME)




---

### Post by TerminalTenant on 2011-04-17
Hi

I could still use some help with this. The output of lsmod shows that only the rt2860sta modules is loaded upon boot so apparently even the lspci lists it, it is not in use. Blacklisting it must have worked. Is there some other logs I could post to help diagnose this problem. I will continue to search other threads. Help would be greatly appreciated.

---

### Post by TerminalTenant on 2011-04-22
Hey

I've worked at it some more and I found a solution. I installed the upstream modules found in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/689960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/689960) 

Haven't had a single dropped connection in days. I might have had the previous modules installed or configured improperly. Anyways, marking this thread as solved.

---

