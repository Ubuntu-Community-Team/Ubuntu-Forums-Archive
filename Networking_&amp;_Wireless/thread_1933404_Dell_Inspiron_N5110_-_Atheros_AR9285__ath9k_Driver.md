---
title: "Dell Inspiron N5110 - Atheros AR9285 / ath9k Driver won't work"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by Samael1983 on 2012-02-29
Hi folks,

I know that this Atheros AR9285/ath9k issue has been posted before, but I'm literally out of ideas. I have trawled the forums trying to get a fix but to date have found nothing to help. So as per this recommendation [(http://ubuntuforums.org/showpost.php?p=11260941&postcount=35]("http://ubuntuforums.org/showpost.php?p=11260941&postcount=35")) I'm starting this new thread. I know there are more people out there with this problem so hopefully this can help them.

So my Dell is x86_64 and the kernel version is 3.0.0.16-generic. I have already tried the backports solution and loaded up 3.0.0.12 but still had no joy when I installed it through "apt-get -y install" and restarted.

Anyway, clicking on the Gnome Network Manager (with the arrows one pointing up, the other down) shows no wireless networks, offers a VPN connection etc. The Wireless switch (alt+F2) is enabled, and I have checked "Enable Wireless".

The problem could simply be that I have tried all the listed fixes in a different order or something.I tried blacklisting acer-wmi and acer_wmi as well which didn't help either. Running rfkill tells me that "Dell Wifi" and wlan0 are blocked both by hardware and software. I'm really running out of ideas and am hoping that this thread will help to concatenate all the threads out there with different fixes and issues involving this Driver/Chipset.

Many thanks for any help/further assistance anyone can give me with this issue.

I'm not in a position just now to post up dmesg/lspci readouts just yet, but I'll do so as soon as I can if these are required.

Incidentally I'm booting Lubuntu 11.10 (Oneiric Ocelot) from a 16GB Live USB - I can't see how this could be a reason for the problem though...

Thanks in advance!

---

### Post by jayflariston on 2012-02-29
hey Ubuntu-Freaks ;-),

I can agree with Samael. I have a  problem with the AR9285 as well and being a Linux newbie is not really helping the situation either :-(. The grey-displayed message in the Network Manager: "wireless is disabled by hardware switch". Just can't get it to work even after reading several threads and trying out things. My netbook has no hard keys to turn on the wireless, only FN+F8 as it used to be under Windows, but this option doesn't work.

Here my system information regarding to [http://ubuntuforums.org/showthread.php?t=6183681:](http://ubuntuforums.org/showthread.php?t=6183681:)

**1 ) Machine Brand and Model (PC/Laptop)**:
     
Toshiba Netbook NB305/N442BL

**2 ) Wireless Brand, Model and Wireless Chipset:**
 	[B]       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:4d:af:d6:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
[/B][B]

3 ) check interface:[/B]


 	lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

**4 ) Check for modules:**
(I assume ath9k is the wireless module?)

Module                  Size  Used by
ath9k                      117425  0 mac80211              436455  1 ath9k
mac80211              436455  1 ath9k
mac80211              436455  1 ath9k
ath                           19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211                178679  3 ath9k,mac80211,ath
[B]
5 ) Kernel boot messages[/B]
(if there are some missing, let me know)

[   23.959772] init: hybrid-gfx main process (887) terminated with status 127
[   23.971580] r8169 0000:09:00.0: eth0: link up
[   23.972352] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.552760] ppdev: user-space parallel port driver
[   25.506975] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.784025] eth0: no IPv6 routers present
[ 1932.929257] ath9k 0000:07:00.0: PCI INT A disabled
[ 1932.929336] ath9k: Driver unloaded
[ 1950.270708] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1950.270749] ath9k 0000:07:00.0: setting latency timer to 64
[ 1950.321585] ath: EEPROM regdomain: 0x65
[ 1950.321591] ath: EEPROM indicates we should expect a direct regpair map
[ 1950.321600] ath: Country alpha2 being used: 00
[ 1950.321604] ath: Regpair used: 0x65



  **6 ) Network configuration**
 	Code:
 	$ sudo lshw -C network 
**7 ) Scan for networks:**
 	*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:4d:af:d6:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff

 
**8 ) Ubuntu Version: **
 	Description:    Ubuntu precise (development branch)


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
 	3.2.0-17-generic i686



**10 ) Restarting the network:**
 	 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

What I've found it with rfkill list all:

1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


If there is anything else I can assist you with, please let me know. Hopefully we can get it up and running. Thank you very much in advance.

Best regards

---

### Post by Samael1983 on 2012-02-29
Yeah it's a pain. When I can post up dmesg etc. I will and hopefully someone can help.

---

### Post by kurt18947 on 2012-02-29
> [B]
10 ) Restarting the network:[/B]
      * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

What I've found it with rfkill list all:

1: phy1: Wireless LAN
    Soft blocked: no
    _**Hard blocked: yes**_


I'm pretty sure that's your problem.  Are there any hardware switches?  Are you dual booting with Windows?  There have been cases where people have disabled a WiFi adapter in Windows then booted into Ubuntu and could not get the wiFi adapter to come to life.  They booted into windows, enabled the adapter, logged out of windows, logged into Ubuntu and the adapter was live.

---

### Post by Samael1983 on 2012-02-29
No that's not my issue. Windows is on the main HD, Lubuntu is running from an LVM encrypted 16GB USB (I don't think that could cause the problem?). It's definitely a software issue because it works fine with Linux Mint 12 (which is based on 11.10 Oneiric and uses the 3.0.0.16 kernel AFAIK) running the same way. I am considering trying Peppermint OS (apparently a hybrid of Linux Mint and Lubuntu) and seeing if it works on that. How I'd find what Linux Mint/Peppermint(?) has that I don't is beyond me though.

---

### Post by Samael1983 on 2012-02-29
OK - so a bit more mucking around and I managed to fix the issue. Here's how:

Make sure you're connected on a wired connection.
1. Open up a terminal

# sudo -s
# Enter root password:
# sudo modprobe -r acer-wmi < It seems this driver interferes with ath9k
# sudo modprobe -r acer_wmi
# echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
# apt-get -y purge network-manager && apt-get -y install wicd  < Seems a bug in network-manager causes the problem too, so replace  it with wicd
# Reboot and you're up and running!

---

### Post by dg91 on 2012-12-28
what lines I need to change in your tutorial to make it work on my toshiba nb305-n310?? :D

we have same wireless card but diferent netbook ;P so I suppose those lines with "acer" are just for acer netbook?

---

