---
title: "Intel 3945ABG wireless disabled"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by hg206 on 2009-05-01
[SIZE=2]I have been using my Dell laptop with Ubuntu 8.04 for several months now.  No problems until 2 days ago when the wifi stopped working.   

It's not a problem with the router, as I'm posting this with my other laptop running Windows XP, and the wireless connection works fine.

I think the problem is with the wireless being [/SIZE][FONT=Verdana][SIZE=2]"disabled by HW RF Kill switch[/SIZE][/FONT][SIZE=2]", but I don't know how to solve this problem.  Please help![/SIZE]
[SIZE=2]
Here's more info:

[/SIZE]    [FONT=Verdana][SIZE=2]**1 ) Machine Brand and Model (PC/Laptop)**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]Dell Inspiron 1525 Laptop[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**2 ) Wireless Brand, Model and Wireless Chipset:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ lspci | grep -i 'wireless' [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**3 ) check interface:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ iwconfig [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]lo        no wireless extensions. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]eth0      no wireless extensions. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]wmaster0  no wireless extensions. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]wlan0     IEEE 802.11abg  ESSID:""  [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Tx-Power=0 dBm   [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Link Quality:0  Signal level:0  Noise level:0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]ppp0      no wireless extensions. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**4 ) Check for modules:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ lsmod | grep 'iwl' [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]iwl3945                96244  0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]lbm_iwl_mac80211      242292  1 iwl3945 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]rfkill                  8596  2 iwl3945 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]led_class               6020  1 iwl3945 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]lbm_iwl_cfg80211       33248  2 iwl3945,lbm_iwl_mac80211 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**5 ) Kernel boot messages**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ dmesg | grep 'iwl' [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   23.921723] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   23.921727] iwl3945: Copyright(c) 2003-2008 Intel Corporation [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   25.932766] iwl3945: Detected Intel Wireless WiFi Link 3945ABG [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   26.019336] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   26.020495] phy0: Selected rate control algorithm 'iwl-3945-rs' [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][   33.729904] iwl3945: Radio disabled by HW RF Kill switch [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**6 ) Network configuration**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ sudo lshw -C network [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][sudo] password for heng: [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]  *-network               [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       description: Ethernet interface [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       product: 88E8040 PCI-E Fast Ethernet Controller [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       vendor: Marvell Technology Group Ltd. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       physical id: 0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       bus info: pci@0000:09:00.0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       logical name: eth0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       version: 12 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       serial: 00:21:9b:cc:e5:39 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       capacity: 100MB/s [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       width: 64 bits [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       clock: 33MHz [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]  *-network DISABLED [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       description: Wireless interface [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       product: PRO/Wireless 3945ABG Network Connection [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       vendor: Intel Corporation [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       physical id: 0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       bus info: pci@0000:0b:00.0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       logical name: wmaster0 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       version: 02 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       serial: 00:1f:3c:86:db:6c [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       width: 32 bits [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       clock: 33MHz [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**7 ) Network configuration:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ iwlist scan [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]lo        Interface doesn't support scanning. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]eth0      Interface doesn't support scanning. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]wmaster0  Interface doesn't support scanning. [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]wlan0     No scan results [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**8 ) Ubuntu Version:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ lsb_release -d [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]Description:      Ubuntu 8.04.2 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**9 ) Kernel/architecture:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ uname -mr [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]2.6.24-23-generic i686 [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]**10 ) Restarting the network:**[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]heng@dell-desktop:~$ sudo /etc/init.d/networking restart [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] * Reconfiguring network interfaces...                                   [ OK ] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]
  [FONT=Verdana][SIZE=2] [/SIZE][/FONT]

---

### Post by chili555 on 2009-05-01
> iwl3945: Radio disabled by HW RF Kill switch Somewhere on your laptop, there is a switch or key combination that enables or disables the wireless radio. It has become nudged over to 'off.'

Switch it back on and you should be all set!

---

### Post by hg206 on 2009-05-01
Found the switch - didn't even know it was there!  Feel like an idiot!

Re-connected to wifi now, finally!  Thanks so much for your help!

---

### Post by speedwell68 on 2009-05-07
> **chili555 said:**
> Somewhere on your laptop, there is a switch or key combination that enables or disables the wireless radio. It has become nudged over to 'off.'

Switch it back on and you should be all set!

> **hg206 said:**
> Found the switch - didn't even know it was there!  Feel like an idiot!

Re-connected to wifi now, finally!  Thanks so much for your help!

My friend has recently had a very nasty virus attack in Vista and wanted me to install Linux instead.  So I installed Jaunty, his wireless didn't work.  I have spent all morning trying all sorts fancy ways of getting this card to work and then I read this thread, found the switch and  all was well.  So thanks for that, the simplest fix is usually the best one.:D

---

