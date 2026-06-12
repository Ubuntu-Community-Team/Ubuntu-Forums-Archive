---
title: "Unable to connect to Windows Ad-Hoc from 11.10I am a newbie to Ubuntu, and loving it"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by 5hahiL on 2012-04-14
I am a newbie to Ubuntu, and loving it except for this AdHoc  issue which has been bugging me for a month. I have found numerous posts  on the issue with no real solutions, so let me be a bit more specific  regarding the issue, and hopefully someone can help me out.
  I have a Broadcom Driver on a Dell Inspiron and the Wifi works great.  The AdHoc works on a parallel installation of Windows 7, so that should  mean the card supports AdHoc. My friends laptop running 11.10 is able  to connect to the network via Adhoc with no issues, hence the network is  setup right. Of the many things i have tried so far, I got the **ndiswrapper**, tried all possible configurations (manual configuration) in network manager, even tried the **wicd** manager
  The latest breakthrough was when I tried **sudo iwconfig wlan0 mode ad-hoc**
  > Error for wireless request "Set Mode" (8B06) :     SET failed on device wlan0 ; Operation not supported.
 so i tried **iwconfig wlan0** and got
> 
  wlan0     IEEE 802.11bgn  ESSID:off/any             Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm              Retry  long limit:7   RTS thr:off   Fragment thr:off           Power Management:off   
So the Mode is forced to ***Managed*** instead of ***Ad-Hoc***
  So, where do I go from here?
  Additional Information:
  The output for **sudo lshw -C network** is
    > *-network                       description: Wireless interface        product: BCM4313 802.11b/g/n Wireless LAN Controller        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        logical name: wlan0        version: 01        serial: 70:f1:a1:89:e7:1a        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-17-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn        resources: irq:17 memory:f0500000-f0503fff   *-network        description: Ethernet interface        product: AR8152 v1.1 Fast Ethernet        vendor: Atheros Communications        physical id: 0        bus info: pci@0000:04:00.0        logical name: eth0        version: c1        serial: b8:ac:6f:65:e4:3e        capacity: 100Mbit/s        width: 64 bits        clock: 33MHz        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair        resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

---

