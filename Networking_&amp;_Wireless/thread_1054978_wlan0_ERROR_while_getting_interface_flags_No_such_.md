---
title: "wlan0: ERROR while getting interface flags: No such device"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by Axel-P on 2009-01-30
I'm looking trough many treads to make my Broadcom BCM4328 802.11a/b/g/n working and this one:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72) 

 seems to work, but when I try to do sudo ifconfig wlan0 up it prompts: 
wlan0: ERROR while getting interface flags: No such device

please help!!!!!!!!!!!!

Thank you very much

---

### Post by freackout on 2010-01-15
> **Axel-P said:**
> I'm looking trough many treads to make my Broadcom BCM4328 802.11a/b/g/n working and this one:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72) 

 seems to work, but when I try to do sudo ifconfig wlan0 up it prompts: 
wlan0: ERROR while getting interface flags: No such device

please help!!!!!!!!!!!!

Thank you very muchsame error DIFFERENT DEVICE
possible mini pci wireless device not working properly. i have tried 4 operating systems on this pavillion dv6000 and no such luck, however i have a bios bug and apparently the ar5xx series even setting it up in windows the drivers wont recognise it as is :-there&#8217;s also a power saving option on the wireless adapter itself, that is turned to maximum by default. To turn it off, right click (in windows) my computer > properties > hardware tab > device manager&#8230; then find your wireless adapter in the list under Network Adapters, right click > properties > advanced tab. Select Power Save Mode from the list on the left and select Off from the drop down on the right. Press OK and close device manager. then install the drivers.. 
HOWEVER WITH YOUR BROARDCOM DEVICE hmmm ubuntu 804,904 910 (BCOM) work out of box. but 910 shipped too early FOR THE ar5xx needed update. & then works ok. Ive had the broadcom devices working fine for over 3 years now, however there are 32 & 64 bit drivers, sam linux was the first to work for me (as an easy setup) mint was next and ubuntu 7.10 onwards detects them along with debian 5.5. there are many ways to get them to work. nidiswapper-gtk is only one way. but that uses the windows driver. as from debian 5.5 equivalents there's no need for the windows driver. simply a matter of update hardware drivers will do it for you now with THREE SIMPLE CLICKS. stop doing it the hard way.

---

### Post by sabatore on 2011-02-05
I am Also getting the same error. i am trying to follow about 16 diffrent tutorials on how to run a few things and each one i try i end up with an error than i look through tutorials to fix the error than i find the new tutorial more useful but i get another problem and it keeps looping that cycle but now i cant get past this error im stumpted and getting very discouraged by the whole fiasco.

---

### Post by dineshs on 2011-02-05
Please post the result of ```
sudo lshw -C network
```

---

### Post by Orpheon on 2011-02-05
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:88:4b:af
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=84.73.147.251 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:33 ioport:de00(size=256) memory:fbdff000-fbdfffff(prefetchable) memory:fbdf8000-fbdfbfff(prefetchable)

---

### Post by MON3M on 2012-09-11
i have the same problem... what should i do?
anyone's here to help me plz?!

---

