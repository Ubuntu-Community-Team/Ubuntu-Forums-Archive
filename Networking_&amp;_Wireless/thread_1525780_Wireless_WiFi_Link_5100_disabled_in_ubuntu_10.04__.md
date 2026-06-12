---
title: "Wireless WiFi Link 5100 disabled in ubuntu 10.04  LTS"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by agan on 2010-07-07
Hello there,
           posting this after great struggle. My lap top dell latitude E6400 with Wireless WiFi Link 5100 adapter was working perfect with Ubuntu 10.04 LTS. I did lots of addition and deletion of tools wired as well wireless. Now its not working I am posting the out puts 

**1. iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

**2. ifconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr 00:24:d6:77:12:74  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
**3.lshd -C network** 
*-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:f4:4f:ad
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.7-7 ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:77:12:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1ffe000-f1ffffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
4. **ifconfig wlan0 up**
SIOCSIFFLAGS: No such file or directory

**5. uname -r**
2.6.32-24-generic

6. **dmesg | grep -i wireless**

[    8.281693] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    8.281961] iwlagn 0000:0c:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54

7. iwlwifi-5000-1.ucode and iwlwifi-5000-2.ucode request fail message also appears while testing.

pse help, can i roll back to 2.6.32-21-generic, will it help?

---

### Post by cavalier911 on 2010-07-07
First the obvious,are you sure the wireless card is powered on. I own a dell inspirion E1505 , the keycombo Fn+F2 toggles the wifi off/on,there is a green indicator to the left of the power button when mine is on.

> 7. iwlwifi-5000-1.ucode and iwlwifi-5000-2.ucode request fail message also appears while testing.

Refresh the kernel module map:

```
sudo depmod -a
```

The wireless card iwlagn module requires iwlwifi-5000-1.ucode or iwlwifi-5000-2.ucode firmware it can't find.

See if the firmware is present:

```
sudo find / -iname iwlwifi-5000*
```

The iwlwifi-5000-2.ucode firmware here:
 [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz)

Extract with gunzip,then tar -xvf.

```
md5sum iwlwifi-5000-2.ucode
```
**10ca882a6e16e0d79e5f4b2b1b516e4e iwlwifi-5000-2.ucode** 

Matches what is on my install of Lubuntu Lucid 2.6.32-21-generic

Verify your firmware if present matches md5sum.
```
md5sum /lib/firmware/iwlwifi-5000-2.ucode

```

If your firmware is corrupt or missing, replace it.

Unload iwlagn module.
```
sudo modprobe -r iwlagn
```

Reload iwlagn module.
```
sudo modprobe iwlagn
```

Verify no firmware loading error in dmesg.

Verify interface:
```
iwconfig
```

Bring up the interface:
```
sudo ifconfig wlan0 up
```

With your access point on verify radio works:
```
iwlist wlan0 scanning
```

If the firmware is present and good but you still get dmesg error about loading look here: [https://wiki.ubuntu.com/KernelTeam/Firmware](https://wiki.ubuntu.com/KernelTeam/Firmware)

Report back with your progress.

---

### Post by agan on 2010-07-07
Thank you so much for the prompt reply, this solution works. May be it will help others too. Lots of people are searching for this issue.

               Thanks anyway,

                           GRT UBUNTU FORUM

                                      AGAN

---

### Post by agan on 2010-07-26
Hello
       there, i have my wireless card working and detecting the network and getting assocaited. But I cant inject packets using aireplay-ng? when i do injection testing it gives 0%. Can anyone help

---

### Post by Saccheri on 2010-08-20
Impressive post from [cavalier911]("http://www.uluga.ubuntuforums.org/member.php?u=847951"), but I'm still having issues with this driver on a Dell 630 laptop.

I need to start the machine with wireless turned off. If I then boot into Ubuntu and switch wireless on everything works fine. If I boot with wireless on it gets reported as DISABLED in Ubuntu. Nothing above managed to change that and there are no error messages anywhere. If you turn wireless off/on that makes no difference - you must **boot with wireless off** to get it to work.

I hate this bug. You might stand a chance to fix this if you know about kernel modules but your average punter isn't going to stand a chance. Stuff like this really undermines Linux so like to help nail this if possible.

Any ideas?

Thanks,

Steve

---

### Post by moussena on 2010-12-01
I installed ubuntu 10.04 on my laptop. When I first did, I had the version 2.6.32-24-generic and the wireless worked. But when I upgraded to 2.6.32-26-generic, the wireless stopped working. I used the procedure described here and I got it fixed after few attempts. Unfortunately, after an upgrade I made yesterday, the wireless stopped working again and the procedure described here didn't fix it.

I have a DELL M4400 laptop.

Regards,
Mohand

---

### Post by moussena on 2010-12-01
Regarding fault I reported, I found out that the "Network Manager" has a problem. I could not connect using wireless despite all printouts suggesting that the wireless interface is up and should normally be working.

I downloaded "Wicd Network Manager" and I managed to connect using wireless. The "Network Manager" is still not able to do so.

Regards,
Mohand

---

