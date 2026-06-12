---
title: "xubuntu 10.04 wireless network disconnected"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by zking74 on 2011-05-21
I am totally noob..this is my first ever encounter with linux. I have successfully installed xubuntu on my 2nd partition of hard disk through unetbootin. everything works fine except wireless network. my ethernet works good, i am tethering through my android mobile no problem....just wireless says disconnected where as it is enabled. As far I know its sould scan all the available wireless AP near me and it should appear below wireless networks, and from there I should be able to select the AP which I want to connct...am I right??

here are some commands log

laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe000000-fe00ffff

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

usb0      no wireless extensions.

pan0      no wireless extensions.

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

usb0      no wireless extensions.

pan0      no wireless extensions.

Please help I like to b a linux champ....in near future...if u need any other command to be posted here pls let men kno...I know only this much of linux..

my netbook is MSI wind U135DX

---

### Post by zking74 on 2011-05-22
bump +4

---

### Post by Toz on 2011-05-22
Seems that this card is problematic. Here are some links of interest:

[http://ubuntuforums.org/showthread.php?t=1600498](http://ubuntuforums.org/showthread.php?t=1600498) (post #7)
[http://ubuntuforums.org/showthread.php?t=1314747](http://ubuntuforums.org/showthread.php?t=1314747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651778](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651778)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666853](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666853)

A few of those articles reference this PPA:

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)
(Click the "Read about installing" link for instructions)

---

