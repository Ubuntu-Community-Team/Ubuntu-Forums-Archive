---
title: "WiFi not working on 9.10"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Linux_Ubunt on 2009-11-22
I just installed Ubuntu 9.10 (64 bit) on my laptop and noticed that I can't connect to internet. After digging it little deeper, I found that that there is some issues with wireless card.

My Laptop info

Dell Inspiron E1505. (64 bit)
Network devices 
1) Broadcom 440x10/100 Integrated Controller
2) Broadcom 802.11g Network adapter

Before installing it to my hard drive, I had tried Ubuntu 9.04 (64 bit) thr' LiveCd as well as on USB, and Icould connect to internet after activating my card then. But when it comes to 9.10 it doesn't work.

following is the output of few of the commands which may be helpful for someone to figure out exactly what;s wrong with my setup

1) lshw

  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:4c:d3:c6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:1d:3a:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


2)lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

3) iwconfig
          wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

After browsing I also found that broadcom cards do have some issues on linux, but then what puzzles me is how did it work on previous ubuntu version? My laptop does have switch to tun OFF wifi. But I know it is not turned OFF/disabled.

Thanks in advance.

---

### Post by Thomas Garman on 2009-11-23
I too have the exact same problem but I am using an Acer Aspire One with a Broadcom Wireless G card.
 
According to one of the other threads in the forum, all you should have to do (if you can connect to the internet using an ethernet cable, which I can) is run
 
sudo apt-get install b43-fwcutter
 
or maybe
 
sudo aptitude install b43-fwcutter
 
or somesuch thing but actually when I did that it basically turned my little Aspire One into a brick.  So I booted up into a rescue mode from Grub and purged the b43-fwcutter and then fixed broken packages and also ran the fix grub and then at the very least my computer would boot up again.
 
So, how to fix the wifi problem?
 
I just plugged a Belkin Wireless G USB stick into my Aspire One.  Ubuntu automatically recognizes it without any additional effort, and all of the wifi options work.
 
So, basically, I just use the internal Broadcom Wireless when I am booting into Windows on the Aspire One.  If I boot into Ubuntu, I just plug in a USB Belkin Wireless G.
 
I mean, seriously, I have been trying to get this stupid broadcom wireless card to work with Ubuntu, but why bother.

---

### Post by t0mppa on 2009-11-23
@Linux_Ubunt: The b43 driver needs a proprietary piece of firmware to work and Broadcom has such a license on it, that it cannot be distributed with the Linux kernel itself. Thus, you have to use the b43-fwcutter to get the firmware installed and have the driver working.

Another option is to use the Broadcom STA driver, which supports your chip. You should be able to find it from the proprietary drivers screen (System / Administration / Hardware Drivers), if not, install the *bcmwl-kernel-source* package through apt-get or Synaptic.

If you choose to go with the STA, there's one minor issue. Since you have a Broadcom wired card that uses the b44 driver, you're going to have to run a few extra commands to get any other driver than b43 associated with your wireless. That's because both b43 and b44 use the same ssb module and the wired driver (b44) gets loaded before any wireless drivers. Since b44 loads up ssb as a dependency and there's no wireless driver up yet, ssb also gets associated with the wireless interface as well, even if you don't use the b43.

To solve the issue, you need to unload all the relevant modules first and then reload them in a different order with:```
sudo modprobe -r b44 b43 ssb wl
sudo modprobe wl
sudo modprobe b44 ssb
```

@Thomas Garman: Installing it from the repositories is one way, but if that's not working for you, then see the [driver homepage on Linux wireless]("http://linuxwireless.org/en/users/Drivers/b43") for instructions how to do it manually. Also, if you have a BCM4311, BCM4312, BCM4321 or BCM4322 chip (can check the chip version and revision with **lspci -vnn | grep 14e4**) you can use the STA driver I mentioned above.

---

### Post by Linux_Ubunt on 2009-11-23
I remember on 9.04 there was STA driver and I was using it for browsing. Not sure why don't I see it in 9.10. But thanks for pointers I will try it out

---

### Post by Linux_Ubunt on 2009-11-23
Thanks, it fixed the issue.

---

### Post by Thomas Garman on 2009-11-24
Things change quickly.  I now realize that my problem here was I was trying do get everything to work before doing any updates on the Ubuntu install.  So, here is what actually got the Broadcom to work for my Aspire One.
 
I updated my ubuntu 9.10 install using the update manager.  I then l started "Hardware Drivers" and it automatically detected both the b43 and the STA drivers.  I started by trying the b43 drivers but the broadcom still wouldn't work, so I unstalled the b43 and tried the STA drivers.  Once the system had installed the STA drivers, the Broadcom came on and detected the wireless signals available.
 
So, before you do anything else, start off by Updating your Ubuntu with the Update Manager and you will probably find that many of the issues you were having already generated fixes that will install automatically.

---

### Post by kinley3 on 2009-11-24
> **Thomas Garman said:**
> I too have the exact same problem but I am using an Acer Aspire One with a Broadcom Wireless G card.
 
According to one of the other threads in the forum, all you should have to do (if you can connect to the internet using an ethernet cable, which I can) is run
 
sudo apt-get install b43-fwcutter
 
or maybe
 
sudo aptitude install b43-fwcutter
 
or somesuch thing but actually when I did that it basically turned my little Aspire One into a brick.  So I booted up into a rescue mode from Grub and purged the b43-fwcutter and then fixed broken packages and also ran the fix grub and then at the very least my computer would boot up again.
 
So, how to fix the wifi problem?
 
I just plugged a Belkin Wireless G USB stick into my Aspire One.  Ubuntu automatically recognizes it without any additional effort, and all of the wifi options work.
 
So, basically, I just use the internal Broadcom Wireless when I am booting into Windows on the Aspire One.  If I boot into Ubuntu, I just plug in a USB Belkin Wireless G.
 
I mean, seriously, I have been trying to get this stupid broadcom wireless card to work with Ubuntu, but why bother.

I was starting to consider this. Thank you for pushing me over the edge! :)

---

### Post by swisscow on 2009-12-31
> **Thomas Garman said:**
> Things change quickly.  I now realize that my problem here was I was trying do get everything to work before doing any updates on the Ubuntu install.  So, here is what actually got the Broadcom to work for my Aspire One.
 
I updated my ubuntu 9.10 install using the update manager.  I then l started "Hardware Drivers" and it automatically detected both the b43 and the STA drivers.  I started by trying the b43 drivers but the broadcom still wouldn't work, so I unstalled the b43 and tried the STA drivers.  Once the system had installed the STA drivers, the Broadcom came on and detected the wireless signals available.
 
So, before you do anything else, start off by Updating your Ubuntu with the Update Manager and you will probably find that many of the issues you were having already generated fixes that will install automatically.

Thanks for this. Avoided a lot of possibly painful messing around.:P

---

