---
title: "slow wifi connection on ubuntu 13.04 with rtl8723ae realtek wireless driver"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by rchod on 2013-08-07
[B]so i installed ubuntu four days ago on my toshiba SATELLITE-C855-2CF and everything is going well, but i noticed that my wifi connection is slow and when i did a speed test online i found that i have only 0.9 Mbps and when i did the speed test on windows i have 4Mbps so can someone tell me how can i fix this problem ? if don't find any solution for this problem i'll have to go back to windows and leave ubuntu.

here is some info:[/B]

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"SAGEM_C40B"  
      Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:17:EB:3E:C4:0C   
      Bit Rate=18 Mb/s   Tx-Power=20 dBm   
      Retry  long limit:7   RTS thr=2347 B   Fragment thr: off
      Power Management: off
      Link Quality=34/70  Signal level=-76 dBm  
      Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
      Tx excessive retries:0  Invalid misc:6967   Missed beacon:0

$ lsmod | grep rtl
rtl8723ae              86459  0 
rtlwifi                79673  1 rtl8723ae
mac80211              606457  1 rtlwifi
cfg80211              510937  2 mac80211,rtlwifi


$ lspci | grep RTL
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

$ sudo lshw -class network
  *-network               
   description: Wireless interface
   product: RTL8723AE PCIe Wireless Network Adapter
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:02:00.0
   logical name: wlan0
   version: 00
   serial: 2c:d0:5a:3e:ee:bb
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
   configuration: broadcast=yes driver=rtl8723ae driverversion=3.8.0-27-generic firmware=N/A ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
   resources: irq:17 ioport:3000(size=256) memory:c2400000-c2403fff
 *-network
   description: Ethernet interface
   product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:03:00.0
   logical name: eth0
   version: 05
   serial: 70:54:d2:d6:d0:2b
   size: 10Mbit/s
   capacity: 100Mbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
   resources: irq:41 ioport:2000(size=256) memory:c0004000-c0004fff memory:c0000000-c0003fff

---

### Post by wildmanne39 on 2013-08-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by rchod on 2013-08-08
I really thank you for your help, here is the generated file

---

### Post by wildmanne39 on 2013-08-08
To start with you link quality is very low, how close to the router are you? is there a wall or anything between the router and your computer?

Next in the dmesg it says > disabling HT as WMM/QoS is not supported by the APtry changing your encryption in the router to just wpa2 AES if you have that option. May also say CCMP I believe instead of AES.
Thanks

---

### Post by rchod on 2013-08-17
the router is in the room above me, so there's one wall between the[COLOR=#000000] computer and the router.  I don't have access to the router because it's not mine, isn't there a solution by chaging some options in ubuntu ?[/COLOR]

---

### Post by richaustin on 2013-08-17
This sounds like the same thing I had at one point with my HP G72 laptop. Even the speed, 0.9, is about the same. I found it was a rubbish driver - it was also supplied with Windows 8 actually. The fix I found was at this url:

[http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html](http://www.upubuntu.com/2012/10/how-to-fix-unity-and-wireless-problems.html)

It  worked like a dream - I went from 0.9 to 10 in a few seconds! Strangely I haven't had the issue in the last few installs of either Windows or Ubuntu. Hope this helps resolve the problem!

[Quick Edit here - for what it's worth, the fix in Windows 8 was actually to download the old driver from HP and tell Win Update to ignore the "Update".]

Richard

---

### Post by wildmanne39 on 2013-08-20
That setting really needs to bechanged.

---

### Post by wildmanne39 on 2013-08-20
You can also set your wireless settings to match the screenshots but it probably will not completely make up for not changing that setting. I will look and see if changing any driver parameters might help.

Okay you can also run this command, that is all I know to try, with the ceiliing between the router and your device the link quaility is low I am not sure how much this will help.
```
echo "options rtl8723ae ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8723ae .conf
sudo modprobe -rfv rtl8723ae
sudo modprobe -v rtl8723ae
```

---

### Post by rchod on 2013-09-21
thanks for your reply, i did the last commands you give me but the nothing changed, and i changed the settings to match the snap shots but it didn't help much, i just wonder why in win7 i have a speed of 4.1 Mb/s and in ubuntu i have 1.1~1.5 Mb/s ?

---

### Post by rchod on 2013-09-22
so first of all i want to thank you for your help Mr Wild Man, i really appreciated.

I finally found a solution to this hell, so simply the problem was in the built -in ubuntu driver it was not working good, the connection was so slow (max=0.9Mbps), now i installed the ]the official Linux driver available unofficially (via Dropbox). 
the link to the full answer is here [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/165002#165002)

but for me the driver didn't compile, it gave me some errors to i looked again and found this driver that finally worked like a charm  [http://askubuntu.com/questions/292751/issues-installing-wireless-network-driver](http://askubuntu.com/questions/292751/issues-installing-wireless-network-driver), now i have 3.8~4.0 Mbps so i'm really glad :)

---

### Post by varunendra on 2013-09-23
Thanks for the solution rchod.

It would be a lot more helpful to others if you also mark the thread as [SOLVED] (using "Thread Tools" link above the top post). :)

---

