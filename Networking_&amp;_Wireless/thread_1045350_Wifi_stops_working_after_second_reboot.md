---
title: "Wifi stops working after second reboot"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Rem3 on 2009-01-20
Hi everyone,

first the short version: I install Ubuntu, run all the updates, restart, instsall ndisgtk, install appropriate windows drivers, reboot, wifi works, reboot again, wifi does not work anymore and nothing helps :(

now the long version:

I've read almost every thread on the Internet about wifi and ndiswrapper. I followed the sticky thread about troubleshooting wifi at this forum. But nothing helped.

Here is my problem and description of what I do:

I have Acer Aspire One which comes with Linpus Lite preinstalled. I remove that one and install Ubuntu 8.04.1 following this manual: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

When the Ubuntu is installed I install all the updates that Update Manager offers. After that I reboot.

Next I install ndisgtk using Add/Remove in Application menu. Then I go to System > Administration > Windows Wireless Drivers and install these drivers:
[http://download2.dvd-driver.cz/atheros/drivers/ar5008/xp32-6.0.3.85.zip](http://download2.dvd-driver.cz/atheros/drivers/ar5008/xp32-6.0.3.85.zip)

Then I reboot and hey! :) Wifi works! It shows all networks around me, I can connect to few of them. Heaven on Earth.

Then I reboot again. And even when I prayed heavily during the reboot the $#@#%^ wifi does not work any more and I can't get it working.

I am stuck with this for more then a week now. Trying different approaches (have reinstalled ubuntu like zillion times), googling a lot. But nothing.

Please help. SOS. . . . / - - - / . . .

Thank you,

Rem3

PS:
lshw -C Network
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,06/05/2007,6.0.3.85 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you need more info please let me know. I will check this thread regullary.

---

### Post by pbc3 on 2009-01-20
I've been experimenting with 8.10 and have similar issues. I've found that removing the network-manager and network-manager-gnome almost fixes my issue. My wifi is usb external and I have to remove it during reboot or I hang when the bluetooth module is loading. If I replace it once the desktop appears, my wifi loads and connects perfectly. You do have to setup your interfaces and resolv.conf files manually. Hope this helps you as well.

---

