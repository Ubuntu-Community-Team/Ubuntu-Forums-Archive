---
title: "Cannot get wireless operational"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by hailholyghost on 2009-01-12
Hey, I have had Hardy Heron 8.04/Windows XP partition on my Inspiron E1505 for a while now, and haven't been able to get Ubuntu on the internet after numerous attempts.  The computer's wireless card works perfectly on Windows.  The router is a Cisco Linksys Wireless N, model #WRT310N.

I've tried many different solutions that have worked for others, but not for my Inspiron.  When I left-click the nm-applet 0.6.6, no wireless networks show up.

Other posters have entered the following commands in the terminal, so I am too:

sudo lshw -C network

  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ce:38:54
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:1a:92:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:ce:38:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82092 (80.1 KB)  TX bytes:82092 (80.1 KB)

Anyone's time and effort is greatly appreciated :-)!

---

### Post by pytheas22 on 2009-01-13
Probably you just need to install firmware before your card will work.  Please plug into the Internet via the ethernet, then run these commands:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

That should download and install the firmware for you.  If after a reboot you still can't see wireless networks, please post the output of these commands:
```

ls /lib/firmware
dmesg | grep -e b43 -e wlan -e adio
sudo iwlist scan
```

If it's totally impossible for you to get a wired connection, let me know and we can work around it.

---

### Post by Jion_Wansu on 2009-01-14
home@Home:~$ ls /lib/firmware
2.6.27-11-generic                   dvb-usb-vp702x-01.fw
2.6.27-9-generic                    dvb-usb-vp7045-01.fw
acx                                 dvb-usb-wt220u-02.fw
aic94xx-seq.fw                      dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502_3com-wpa.bin         ipw2100-1.3.fw
atmel_at76c502.bin                  ipw2100-1.3-i.fw
atmel_at76c502d.bin                 ipw2100-1.3-p.fw
atmel_at76c502d-wpa.bin             ipw2200-bss.fw
atmel_at76c502e.bin                 ipw2200-ibss.fw
atmel_at76c502e-wpa.bin             ipw2200-sniffer.fw
atmel_at76c502-wpa.bin              isl3877
atmel_at76c503-i3861.bin            isl3886
atmel_at76c503-i3863.bin            isl3887usb_bare
atmel_at76c503-rfmd-0.90.2-140.bin  isl3890
atmel_at76c503-rfmd-acc.bin         isl3890usb
atmel_at76c503-rfmd.bin             iwlwifi-3945-1.ucode
atmel_at76c504_2958-wpa.bin         iwlwifi-3945.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-4965-1.ucode
atmel_at76c504.bin                  iwlwifi-4965-2.ucode
atmel_at76c504c-wpa.bin             iwlwifi-5000-1.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
b43                                 rt2561.bin
b43legacy                           rt2561s.bin
bcm2033-fw.bin                      rt2661.bin
bcm2033-md.bin                      rt73.bin
dvb-fe-or51132-qam.fw               v4l-cx23418-apu.fw
dvb-fe-or51132-vsb.fw               v4l-cx23418-cpu.fw
dvb-fe-or51211.fw                   v4l-cx23418-dig.fw
dvb-fe-tda10046.fw                  v4l-cx2341x-dec.fw
dvb-ttpci-01.fw                     v4l-cx2341x-enc.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-init.mpg
dvb-usb-bluebird-01.fw              v4l-cx25840.fw
dvb-usb-dib0700-1.10.fw             v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-29xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           zd1201-ap.fw
dvb-usb-dtt200u-01.fw               zd1201.fw
dvb-usb-tvwalkert.fw                zd1211
dvb-usb-umt-010-02.fw
home@Home:~$ dmesg | grep -e b43 -e wlan -e adio
[   25.796242] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[   25.811971] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
home@Home:~$ sudo iwlist scan
sudo: unable to resolve host Home
[sudo] password for Home: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

home@Home:~$

---

### Post by pytheas22 on 2009-01-14
Jion_Wansu: I'm assuming you're a different person than the original poster here.  Your problem is that your wireless card is not turned on:
```

[ 25.796242] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[ 25.811971] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
```

There should be a button somewhere on your computer to enable the wireless, or a software switch (like Function+F2) that you use.  Please try flipping this and see if it solves the problem.  There may also be an option in your BIOS to force the wireless to be always on; please check that if the switch doesn't seem to work.

---

### Post by DutchSpeed on 2009-01-14
I feel like I'm having a similar problem.  I know that my radio is off I just can't seem to be able to get it turned back on.  I have a Dell Inspiron and it has a blue Fn button and when operating under windows I could hit that and F2 to turn it on and off but from what I researched Ubuntu doesn't recognize that action.  Therefore, I'm including what I found in the terminal when checking to see if the wireless radio is even on.  Any help would be greatly appreciated.  P.S. it used to work fine then the other day after connecting through a land line it stopped working.  

  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:da:c6:28
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.19 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:88:69:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off


Thanks again for any help!

---

### Post by onederer on 2009-01-14
I have an HP Pavillion dv6000, with a 64-bit Athlon chip. I'm running Kubuntu 8.04 "live" DVD. I have an atheros wireless card in this laptop.
I've tried everything that I could find on the Internet for making this wireless card to work.  Right now, I'm using the eth0 card with a cat-5 cable to the router, to write this.

I've run out of patience, and effort to make this laptop run wirelessly, by using the "live" dvd.  I will not install an OS unless that I can be sure that it can drive the wireless card, for this laptop. Has anyone succeeded to make a wireless card work when using the "live" mode of this OS?

Does anyone know how to make it work, step-by-step?  I observed that the card is listed when I do an "lspcs" I've checked the "lsmod" printout, and find that the modules are mounted.  I've tried ndiswrapper, and a few other means of setups like "MadWifi", without any success. ifconfig, only shows the "lo" setup and the "eth0" setup.  I can't get it to accept and or display a working wireless setup.  If it's a situation that I have to restart the computer, then running wireless is not feaseable with a live version disk, since everything gets lost once the computer is rebooted.

Any help will be highly appreciated.  Please send a copy of your response to zonofabeeATgmailDOTcom. Thanks!

---

### Post by pytheas22 on 2009-01-14
**DutchSpeed**: please try flipping the switch a few times to enable wireless, then post the output of:
```

dmesg
sudo iwlist scan
```

It will be pretty long, but please post it all.  *lshw* doesn't mention your radio being turned off, which is interesting because usually it would.

Also, did you check to see if there's an option in BIOS to force the radio to be always on?
[B]
onederer[/B]: if you used Ubuntu 8.10 instead of 8.04, there's a good chance that your card would work out-of-the-box, as 8.10 expanded support for a lot of Atheros cards.

If that doesn't help or you can't use Ubuntu 8.10 for some reason, please tell me the output of this command:
```

lspci -nn
```

With that information we can find specific instructions.  Also, please start a new thread (and tell me the URL) because your problem is probably different than the other ones here and I don't want things to become too convoluted.
> 
Please send a copy of your response to zonofabeeATgmailDOTcom. Thanks!

I don't like to reply via private email because it's better to have a conservation publicly, so that other people can benefit too.  Please start a new thread and we can work there.

---

### Post by Jion_Wansu on 2009-01-14
> **pytheas22 said:**
> Jion_Wansu: I'm assuming you're a different person than the original poster here.  Your problem is that your wireless card is not turned on:
```

[ 25.796242] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
[ 25.811971] iwl3945 0000:0c:00.0: Radio disabled by HW RF Kill switch
```

There should be a button somewhere on your computer to enable the wireless, or a software switch (like Function+F2) that you use.  Please try flipping this and see if it solves the problem.  There may also be an option in your BIOS to force the wireless to be always on; please check that if the switch doesn't seem to work.

Nope, I tried "turning it on" in BIOS and it will not work. It's weird that all of a sudden it does not work anymore with the computer. Are there any other ideas out there anyone?

appreciate the help!!!

It's an internal card, meaning I'd have to unscrew the whole laptop and take everything apart to get to it...

Latitude D820 Laptop.


EDIT: You guys ever get that feeling where you're a complete idiot? Where 10 hours of work could have been solved in about 2 minutes? That just happened to me!!!

I read the reply again then thought about external switches. Lo and behold. On the left side of the laptop is an actual switch which I just needed to turn on...Wow!!!

---

### Post by hailholyghost on 2009-01-14
pytheas22, THANK YOU SO MUCH!!!!  I am now on my Ubuntu partition, on the internet! MUCHAS GRACIAS!!!:):popcorn:

---

### Post by onederer on 2009-01-16
> **pytheas22 said:**
> **DutchSpeed**: please try flipping the switch a few times to enable wireless, then post the output of:
```

dmesg
sudo iwlist scan
```

It will be pretty long, but please post it all.  *lshw* doesn't mention your radio being turned off, which is interesting because usually it would.

Also, did you check to see if there's an option in BIOS to force the radio to be always on?
[B]
onederer[/B]: if you used Ubuntu 8.10 instead of 8.04, there's a good chance that your card would work out-of-the-box, as 8.10 expanded support for a lot of Atheros cards.

If that doesn't help or you can't use Ubuntu 8.10 for some reason, please tell me the output of this command:
```

lspci -nn
```

With that information we can find specific instructions.  Also, please start a new thread (and tell me the URL) because your problem is probably different than the other ones here and I don't want things to become too convoluted.


I don't like to reply via private email because it's better to have a conservation publicly, so that other people can benefit too.  Please start a new thread and we can work there.

Hi,

Here's the lspci -nn:

00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

Hope that this helps.  I didn't know that there was a newer version. The latest version that I was trying to download kept on bombing out. I tried 5 times before giving up. And I don't think that there is a KDE version.
Could it be that it is impossible to run wireless using the "Live" version of the OS?

---

### Post by pytheas22 on 2009-01-16
> 
Hope that this helps. I didn't know that there was a newer version. The latest version that I was trying to download kept on bombing out. I tried 5 times before giving up. And I don't think that there is a KDE version.
Could it be that it is impossible to run wireless using the "Live" version of the OS?

Your card should probably work out-of-the-box in Kubuntu 8.10 (the KDE version), which you can download [here]("http://www.kubuntu.org/getkubuntu/download").  If for some reason the file transfer keeps dropping out, try using the torrent instead of the direct download.

Wireless cards will work from the live CD if you configure everything properly.  The problem is just that sometimes you need to reboot for changes to take effect, but you can work around that if you really want.  Try running these commands to install a driver for your card (in either 8.04 or 8.10) from the live CD (you will need to be online via ethernet for this to work):
```

wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
sudo ./madwifi.sh
sudo rmmod ath_pci
sudo modprobe ath_pci
```

Does that get your wireless working?  If not, what is the output of:

```
dmesg | grep -e ath -e adio
sudo iwlist scan
lshw -C Network
```

---

### Post by onederer on 2009-01-16
> **pytheas22 said:**
> Your card should probably work out-of-the-box in Kubuntu 8.10 (the KDE version), which you can download [here]("http://www.kubuntu.org/getkubuntu/download").  If for some reason the file transfer keeps dropping out, try using the torrent instead of the direct download.

Wireless cards will work from the live CD if you configure everything properly.  The problem is just that sometimes you need to reboot for changes to take effect, but you can work around that if you really want.  Try running these commands to install a driver for your card (in either 8.04 or 8.10) from the live CD (you will need to be online via ethernet for this to work):
```

wget http://kolmoskone.homelinux.org/~kaja/kamaa/madwifi.sh -O madwifi.sh
chmod +x madwifi.sh
sudo ./madwifi.sh
sudo rmmod ath_pci
sudo modprobe ath_pci
```

Does that get your wireless working?  If not, what is the output of:

```
dmesg | grep -e ath -e adio
sudo iwlist scan
lshw -C Network
```
Here's the result of the first problem that was encountered. The instructions for the error came from completing the command example that you gave me.  This is what came from the conosle:

ubuntu@ubuntu:~$ sudo ./madwifi.sh --info to the forum.
Found at least one Atheros device.
Linux ubuntu 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
Distro: Debian
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137a
        Flags: fast devsel, IRQ 19
        Memory at f6000000 (64-bit, non-prefetchable) [size=64K]

ath_pci               249536  0
wlan                  253472  1 ath_pci
ath_hal               280320  1 ath_pci
[102765.115457] ath_pci: driver unloaded
[102765.523014] ath_hal: driver unloaded
[  117.537199] ath_hal: module license 'Proprietary' taints kernel.
[  117.538083] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  118.184327] ath_pci: 0.9.4
[618439.630338] ath_pci: HAL doesn't support MAC revision 0xffffffff
wifi0: 0 ath0: 0

Here's dmesg results:

ubuntu@ubuntu:~$ dmesg | grep -e ath -e adio
[  117.537199] ath_hal: module license 'Proprietary' taints kernel.
[  117.538083] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  118.184327] ath_pci: 0.9.4
[102765.115457] ath_pci: driver unloaded
[102765.523014] ath_hal: driver unloaded
[102783.528750] ath5k_pci 0000:03:00.0: registered as 'phy0'
[102783.537781] ath5k phy0: failed to wakeup the MAC Chip
[102783.538011] ath5k_pci: probe of 0000:03:00.0 failed with error -5
[618439.630338] ath_pci: HAL doesn't support MAC revision 0xffffffff
[618761.554775] ath_pci: HAL doesn't support MAC revision 0xffffffff
ubuntu@ubuntu:~$ 

Here's the iwlist scan results:   

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Here's the lshw -C Network:

ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:46:4d:c8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0    The suggestion was to run it as sudo. There was no output in root mode.


Hope this helps.  The WIFI still doesn't work. And when I tried downloading the latest, torrent was the slowest, and worst to drop out.
I have high speed Internet, but that didn't make any difference. It was downloading slower than if I had dial-up.

Cheers!

---

### Post by pytheas22 on 2009-01-17
It seems that madwifi doesn't support your hardware, even using the latest code.  That's strange.  How new is your computer?

In any guess, I guess we can try using compat-wireless instead (it's a different driver that should also support your card).  Please download [this file]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Then run these commands from the 8.04 live CD:
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjf compat-wireless-old.tar.bz2
cd compat-wireless*
make ###will take a few minutes here to build the driver
sudo make unload
sudo make load
sudo make install
sudo modprobe -r ath_pci ath5k ath9k
sudo modprobe ath5k
iwconfig
sudo rmmod ath5k
sudo modprobe ath_pci
iwconfig
sudo rmmod ath_pci
sudo modprobe ath9k
iwconfig
sudo rmmod ath9k
dmesg | grep -e ath -e wlan -e adio -e HAL
```

Please post all output.  The steps above have you trying three different cards to see if one of them will work for you.

---

### Post by onederer on 2009-01-19
> **pytheas22 said:**
> It seems that madwifi doesn't support your hardware, even using the latest code.  That's strange.  How new is your computer?

In any guess, I guess we can try using compat-wireless instead (it's a different driver that should also support your card).  Please download [this file]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Then run these commands from the 8.04 live CD:
```

sudo apt-get install build-essential
cd ~/Desktop
tar xjf compat-wireless-old.tar.bz2
cd compat-wireless*
make ###will take a few minutes here to build the driver
sudo make unload
sudo make load
sudo make install
sudo modprobe -r ath_pci ath5k ath9k
sudo modprobe ath5k
iwconfig
sudo rmmod ath5k
sudo modprobe ath_pci
iwconfig
sudo rmmod ath_pci
sudo modprobe ath9k
iwconfig
sudo rmmod ath9k
dmesg | grep -e ath -e wlan -e adio -e HAL
```

Please post all output.  The steps above have you trying three different cards to see if one of them will work for you.

Here's the entire output, the beginning is not complete because it was all that the console could display.
I've had this computer for about three months now.
It would no accept any of the possibilities. I suppose that you can do better than I, at understanding all the meanings of all these outputs. I had tried compat before, with negative results. So, here we go:

CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/dma.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/qcu.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/pcu.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/phy.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/reset.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/attach.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/base.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/hw.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/phy.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/regd.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/beacon.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/recv.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/xmit.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/rc.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/core.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/tables.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/tables_nphy.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_common.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.o
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.c: In function ‘b43_gphy_op_recalc_txpower’:
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_g.c:3191: warning: unused variable ‘dbm’
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_a.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_n.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/phy_lp.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/sysfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/xmit.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/lo.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/wa.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/dma.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/pio.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/rfkill.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/leds.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/pcmcia.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/ilt.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/phy.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/radio.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/sysfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/xmit.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/debugfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/dma.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/pio.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945-base.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-3945-led.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-agn.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-agn-rs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-4965.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-core.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-eeprom.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-hcmd.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-power.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-rx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-tx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-sta.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-calib.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-scan.o
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-scan.c:92: warning: ‘iwl_escape_essid’ defined but not used
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl-led.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/wext.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/rx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/tx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.o
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c: In function ‘lbs_set_channel’:
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmd.c:841: warning: unused variable ‘old_channel’
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/cmdresp.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/scan.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/11d.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/debugfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/persistcfg.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/ethtool.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/assoc.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_cs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_sdio.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/if_usb.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00dev.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.o
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c: In function ‘rt2x00mac_conf_tx’:
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00mac.c:557: warning: comparison is always true due to limited range of data type
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00config.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00queue.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.o
/home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00rfkill.c:64: warning: ‘rt2x00rfkill_get_state’ defined but not used
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00firmware.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_chip.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_ieee80211.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_mac.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al2230.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_rf2959.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_al7230b.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf_uw2453.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_rf.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd_usb.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/scan.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/sprom.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/pci.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/pcihost_wrapper.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/pcmcia.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/driver_chipcommon.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/driver_pcicore.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/b43_pci_bridge.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_module.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_tx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_rx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_wx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_geo.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/main.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/wext.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/sta_info.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/wep.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/wpa.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mlme.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/iface.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/rate.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/michael.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/tkip.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/aes_ccm.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/cfg.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/rx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/tx.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/key.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/util.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/event.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/led.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_sta.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_netdev.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/debugfs_key.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mesh.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_plink.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mesh_hwmp.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/rc80211_pid_debugfs.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/built-in.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/core.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/sysfs.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/radiotap.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/util.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/reg.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/compat.o
  CC [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/nl80211.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.o
  LD      /home/ubuntu/Desktop/compat-wireless-2.6-old/built-in.o
  Building modules, stage 2.
  MODPOST 45 modules
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/b44.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/b44.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ar9170/ar9170.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ar9170/ar9170.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  CC      /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.mod.o
  LD [M]  /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo make unload
MadWifi driver is loaded, going to try to unload it...
Unloading "ath_pci"
Unloading "wlan"
Unloading "ath_hal"
Unloading ipw2100...
Unloading ipw2200...
Unloading libertas_cs...
Unloading usb8xxx...
Unloading adm8211...
Unloading zd1211rw...
Unloading b43...
Unloading b43legacy...
Unloading iwl3945...
Unloading ath5k...
Unloading p54pci...
Unloading p54usb...
Unloading rt2400pci...
Unloading rt2500pci...
Unloading rt61pci...
Unloading rt2500usb...
Unloading rt73usb...
Unloading rtl8180...
Unloading rtl8187...
Unloading at76_usb...
Unloading rndis_wlan...
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo make load

Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Disabling ath_pci ...   [OK]    Module disabled:
/lib/modules/2.6.24-16-generic/net/ath_pci.ko
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo make install

Module ath5k not detected -- this is fine
Enabling ath_pci ...    [OK]    Module enabled:
/lib/modules/2.6.24-16-generic/net/ath_pci.ko
Disabling b43 ...       [OK]    Module disabled:
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
Disabling b43legacy ... [OK]    Module disabled:
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Enabling bcm43xx ...    [OK]    Module enabled:
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-16-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-16-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-16-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-16-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-16-generic/build M=/home/ubuntu/Desktop/compat-wireless-2.6-old modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/ubuntu/Desktop/compat-wireless-2.6-old/config.mk:53: "WARNING: You are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support"
  Building modules, stage 2.
  MODPOST 45 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make -C /lib/modules/2.6.24-16-generic/build M=/home/ubuntu/Desktop/compat-wireless-2.6-old "INSTALL_MOD_DIR=updates"  \
                modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/misc/eeprom_93cx6.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/b44.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/cdc_ether.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/rndis_host.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/usb/usbnet.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/adm8211.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ar9170/ar9170.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/at76_usb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43/b43.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2100.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/ipw2200.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8180.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/rtl8187.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/drivers/ssb/ssb.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_ccmp.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_tkip.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/ieee80211/ieee80211_crypt_wep.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/mac80211/mac80211.ko
  INSTALL /home/ubuntu/Desktop/compat-wireless-2.6-old/net/wireless/cfg80211.ko
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'

Note: madwifi detected, we're going to disable it. If you would like to enable it later you can run:
    sudo athenable madwifi

Running athenable ath5k...
Disabling ath_pci ...   [OK]    Module disabled:
/lib/modules/2.6.24-16-generic/net/ath_pci.ko

Currently detected wireless subsystem modules:

/lib/modules/2.6.24-16-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.24-16-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ar9170/ar9170.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/at76_usb.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-16-generic/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-16-generic/updates/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-16-generic/updates/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8180.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure run:

make load

ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ make unload
Unloading ipw2100...
FATAL: Error removing ipw2100 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2100.ko): Operation not permitted
Unloading ipw2200...
FATAL: Error removing ipw2200 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2200.ko): Operation not permitted
Unloading libertas_cs...
FATAL: Error removing libertas_cs (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko): Operation not permitted
Unloading usb8xxx...
FATAL: Error removing usb8xxx (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/libertas/usb8xxx.ko): Operation not permitted
Unloading libertas...
FATAL: Module libertas is in use.
Unloading ieee80211_crypt...
FATAL: Module ieee80211_crypt is in use.
Unloading ieee80211...
FATAL: Module ieee80211 is in use.
Unloading adm8211...
FATAL: Error removing adm8211 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/adm8211.ko): Operation not permitted
Unloading zd1211rw...
FATAL: Error removing zd1211rw (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko): Operation not permitted
Unloading b43...
FATAL: Error removing b43 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43/b43.ko): Operation not permitted
Unloading b43legacy...
FATAL: Error removing b43legacy (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Operation not permitted
Unloading ssb...
FATAL: Module ssb is in use.
Unloading iwl3945...
FATAL: Error removing iwl3945 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
Unloading ath5k...
FATAL: Error removing ath5k (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ath5k/ath5k.ko): Operation not permitted
Unloading p54pci...
FATAL: Error removing p54pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/p54/p54pci.ko): Operation not permitted
Unloading p54usb...
FATAL: Error removing p54usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/p54/p54usb.ko): Operation not permitted
Unloading p54common...
FATAL: Module p54common is in use.
Unloading rt2400pci...
FATAL: Error removing rt2400pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Operation not permitted
Unloading rt2500pci...
FATAL: Error removing rt2500pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Operation not permitted
Unloading rt61pci...
FATAL: Error removing rt61pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Operation not permitted
Unloading rt2500usb...
FATAL: Error removing rt2500usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Operation not permitted
Unloading rt73usb...
FATAL: Error removing rt73usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Operation not permitted
Unloading rt2x00usb...
FATAL: Module rt2x00usb is in use.
Unloading rt2x00lib...
FATAL: Module rt2x00lib is in use.
Unloading rtl8180...
FATAL: Error removing rtl8180 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8180.ko): Operation not permitted
Unloading rtl8187...
FATAL: Error removing rtl8187 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8187.ko): Operation not permitted
Unloading at76_usb...
FATAL: Error removing at76_usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/at76_usb.ko): Operation not permitted
Unloading rndis_wlan...
FATAL: Error removing rndis_wlan (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rndis_wlan.ko): Operation not permitted
Unloading rndis_host...
FATAL: Module rndis_host is in use.
Unloading cdc_ether...
FATAL: Module cdc_ether is in use.
Unloading usbnet...
FATAL: Module usbnet is in use.
Unloading eeprom_93cx6...
FATAL: Module eeprom_93cx6 is in use.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ make load
Unloading ipw2100...
FATAL: Error removing ipw2100 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2100.ko): Operation not permitted
Unloading ipw2200...
FATAL: Error removing ipw2200 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ipw2200.ko): Operation not permitted
Unloading libertas_cs...
FATAL: Error removing libertas_cs (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/libertas/libertas_cs.ko): Operation not permitted
Unloading usb8xxx...
FATAL: Error removing usb8xxx (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/libertas/usb8xxx.ko): Operation not permitted
Unloading libertas...
FATAL: Module libertas is in use.
Unloading ieee80211_crypt...
FATAL: Module ieee80211_crypt is in use.
Unloading ieee80211...
FATAL: Module ieee80211 is in use.
Unloading adm8211...
FATAL: Error removing adm8211 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/adm8211.ko): Operation not permitted
Unloading zd1211rw...
FATAL: Error removing zd1211rw (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko): Operation not permitted
Unloading b43...
FATAL: Error removing b43 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43/b43.ko): Operation not permitted
Unloading b43legacy...
FATAL: Error removing b43legacy (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko): Operation not permitted
Unloading ssb...
FATAL: Module ssb is in use.
Unloading iwl3945...
FATAL: Error removing iwl3945 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Operation not permitted
Unloading ath5k...
FATAL: Error removing ath5k (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/ath5k/ath5k.ko): Operation not permitted
Unloading p54pci...
FATAL: Error removing p54pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/p54/p54pci.ko): Operation not permitted
Unloading p54usb...
FATAL: Error removing p54usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/p54/p54usb.ko): Operation not permitted
Unloading p54common...
FATAL: Module p54common is in use.
Unloading rt2400pci...
FATAL: Error removing rt2400pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko): Operation not permitted
Unloading rt2500pci...
FATAL: Error removing rt2500pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko): Operation not permitted
Unloading rt61pci...
FATAL: Error removing rt61pci (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt61pci.ko): Operation not permitted
Unloading rt2500usb...
FATAL: Error removing rt2500usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko): Operation not permitted
Unloading rt73usb...
FATAL: Error removing rt73usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko): Operation not permitted
Unloading rt2x00usb...
FATAL: Module rt2x00usb is in use.
Unloading rt2x00lib...
FATAL: Module rt2x00lib is in use.
Unloading rtl8180...
FATAL: Error removing rtl8180 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8180.ko): Operation not permitted
Unloading rtl8187...
FATAL: Error removing rtl8187 (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rtl8187.ko): Operation not permitted
Unloading at76_usb...
FATAL: Error removing at76_usb (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/at76_usb.ko): Operation not permitted
Unloading rndis_wlan...
FATAL: Error removing rndis_wlan (/lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/rndis_wlan.ko): Operation not permitted
Unloading rndis_host...
FATAL: Module rndis_host is in use.
Unloading cdc_ether...
FATAL: Module cdc_ether is in use.
Unloading usbnet...
FATAL: Module usbnet is in use.
Unloading eeprom_93cx6...
FATAL: Module eeprom_93cx6 is in use.
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo make unload
Unloading ipw2100...
Unloading ipw2200...
Unloading libertas_cs...
Unloading usb8xxx...
Unloading adm8211...
Unloading zd1211rw...
Unloading b43...
Unloading b43legacy...
Unloading iwl3945...
Unloading ath5k...
Unloading p54pci...
Unloading p54usb...
Unloading rt2400pci...
Unloading rt2500pci...
Unloading rt61pci...
Unloading rt2500usb...
Unloading rt73usb...
Unloading rtl8180...
Unloading rtl8187...
Unloading at76_usb...
Unloading rndis_wlan...
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo make load
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
WARNING: Error inserting iwlwifi_mac80211 (/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl4965 (/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Disabling bcm43xx ...   [OK]    Module disabled:
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
Enabling b43 ...        [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
Preferred module:       /lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43/b43.ko
Enabling b43legacy ...  [OK]    Module renamed but another module file is being preferred
Renamed module:         /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
Preferred module:       /lib/modules/2.6.24-16-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
b43 loaded successfully
b43legacy loaded successfully
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo modprobe -r ath_pci ath5k ath9k
FATAL: Module ath_pci not found.
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo modprobe ath5k
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo modprobe ath5k
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo modprobe ath9k
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ sudo rmmod ath9k
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$ dmesg | grep -e ath -e wlan -e adio -e HAL
[  117.537199] ath_hal: module license 'Proprietary' taints kernel.
[  117.538083] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  117.918252] wlan: 0.9.4
[  118.184327] ath_pci: 0.9.4
[  118.212550] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[102765.115457] ath_pci: driver unloaded
[102765.500290] wlan: driver unloaded
[102765.523014] ath_hal: driver unloaded
[102782.118493] usbcore: registered new interface driver rndis_wlan
[102783.528750] ath5k_pci 0000:03:00.0: registered as 'phy0'
[102783.537781] ath5k phy0: failed to wakeup the MAC Chip
[102783.538011] ath5k_pci: probe of 0000:03:00.0 failed with error -5
[103123.821492] wlan: 0.9.4
[618390.543868] wlan: driver unloaded
[618439.630338] ath_pci: HAL doesn't support MAC revision 0xffffffff
[618761.554775] ath_pci: HAL doesn't support MAC revision 0xffffffff
[714088.169490] usbcore: deregistering interface driver rndis_wlan
[714108.924080] usbcore: registered new interface driver rndis_wlan
[714124.240907] ath5k_pci 0000:03:00.0: registered as 'phy0'
[714124.244927] ath5k phy0: failed to wakeup the MAC Chip
[714124.245214] ath5k_pci: probe of 0000:03:00.0 failed with error -5
[714233.873256] usbcore: deregistering interface driver rndis_wlan
[714243.529779] usbcore: registered new interface driver rndis_wlan
[714245.117118] ath5k_pci 0000:03:00.0: registered as 'phy0'
[714245.127148] ath5k phy0: failed to wakeup the MAC Chip
[714245.127378] ath5k_pci: probe of 0000:03:00.0 failed with error -5
[714378.158529] ath9k: 0.1
[714414.002833] ath9k: driver unloaded
ubuntu@ubuntu:~/Desktop/compat-wireless-2.6-old$

Cheers!

---

### Post by pytheas22 on 2009-01-19
That almost worked.  It seems that there's a stupid bug with the ath5k driver that prevented it from working properly.  Please try running these commands (after a fresh reboot of your live session) to get a different version of ath5k, which will hopefully work:
```

sudo apt-get install linux-backports-modules-intrepid-generic
sudo rmmod ath_pci
sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath5k
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

Please post all output.

---

### Post by onederer on 2009-01-20
> **pytheas22 said:**
> That almost worked.  It seems that there's a stupid bug with the ath5k driver that prevented it from working properly.  Please try running these commands (after a fresh reboot of your live session) to get a different version of ath5k, which will hopefully work:
```

sudo apt-get install linux-backports-modules-intrepid-generic
sudo rmmod ath_pci
sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath5k
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

Please post all output.

Greetings:

Well, I guess that it didn't go over very well. The system can't find "backports".  I enabled all the repositories listed, available.

ubuntu@ubuntu:~/firefox$ sudo apt-get install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid-generic
ubuntu@ubuntu:~/firefox$ sudo apt-get install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree... 50%












Building dependency tree
Reading state information... Done






E: Couldn't find package "linux-backports-modules-intrepid-generic"

ubuntu@ubuntu:~/firefox$ sudo rmmod ath_pci
ubuntu@ubuntu:~/firefox$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
ubuntu@ubuntu:~/firefox$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
ubuntu@ubuntu:~/firefox$ sudo modprobe ath5k
FATAL: Module ath5k not found.
ubuntu@ubuntu:~/firefox$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ubuntu@ubuntu:~/firefox$ dmesg | grep -e ath -e wlan
[  125.056672] ath_hal: module license 'Proprietary' taints kernel.
[  125.060968] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  125.507769] wlan: 0.9.4
[  125.648876] ath_pci: 0.9.4
[ 6408.568373] ath_pci: driver unloaded


So this is how it stands right now.

Cheers!

---

### Post by pytheas22 on 2009-01-20
Oh, sorry, the reason it can't find that package is because you're on Ubuntu 8.04.  I was thinking you were using 8.10.  Sorry for the mistake.  Please try running these commands; they should work:
```

sudo apt-get update
sudo apt-get install linux-backports-modules-hardy-generic
sudo rmmod ath_pci
sudo rmmod ath5k
sudo rmmod ath9k
sudo modprobe ath5k
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

The only thing is that I'm not sure whether linux-backports-modules-hardy-generic contains the ath5k module, but I guess we'll find out.

---

### Post by Blandula on 2009-01-21
I have the same Atheros WiFi card in my new Toshiba Satellite laptop and could not connect with 8.04 LTS. I upgraded to 8.10 with no success. Finally, I followed instructions on how to install an alternate driver set here:
[http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download")

Despite Wireless Kernel's statement that wget won't work, it did, and I used that to download the appropriate tarball from their archive. Note that you should use the actual name of the downloaded file in the tar command rather than the $(date -I) variant the instructions indicate.

Before I did the install, though, I blacklisted ath_hal and ath_pci using instructions from [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") and from snippets on this thread. Pytheas22, your insights were quite helpful and I thank you.

I can post more information if either of you needs more.

Thanks again,
Blandula

---

### Post by Blandula on 2009-01-21
Well, the driver works, but I have to manually load it after a reboot. I am sure there is a way to automate it, but I'm too beat to figure it out right now. I have to open terminal, go into the compat* directory, and do
[INDENT]sudo make load[/INDENT]

The wireless hooks up as soon as it's done. I'm pretty sure it's the new ath5k driver that does it, so I just have to figure out how to make the system load it automatically - help is welcome.

Blandula
Still happy to have WiFi

---

### Post by pytheas22 on 2009-01-21
> Well, the driver works, but I have to manually load it after a reboot. I am sure there is a way to automate it, but I'm too beat to figure it out right now. I have to open terminal, go into the compat* directory, and do

    sudo make load

The wireless hooks up as soon as it's done. I'm pretty sure it's the new ath5k driver that does it, so I just have to figure out how to make the system load it automatically - help is welcome.

Blandula
Still happy to have WiFi

I'm glad that compiling the newer version of compat-wireless solved it for you.  It didn't seem to work for onederer, but that may be because he or she is using Ubuntu 8.04, not 8.10 like you.

To make the drivers load permanently, it should be sufficient to cd into the compat-wireless directory, then run:
```

sudo make install
echo ath5k | sudo tee -a /etc/modules
```

This would make ath5k load at every boot, I think.  If that doesn't work, you could also write a [boot script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") to call the 'sudo make load' command at boot.

Also, just in case you don't realize it, keep in mind that when you update your kernel via Ubuntu updates, you will need to recompile compat-wireless to match the new kernel.

---

### Post by letriste on 2009-01-21
**EDIT**

Go [HERE]("http://ubuntuforums.org/showthread.php?p=6592918#post6592918") instead

*** HIJACKING THREAD ***

or I'll start my own if asked to.

I had my wireless working on 8.10 on my Thinkpad T61p, except that I couldn't hook up to the wlan at school, bu it worked fine at home. But a week ago the list of available networks just dropped out of the network manager, never to be seen again. the funny thing is, the list DOES appear when using "iwlist scan", but it doesn't WORK.

also, the bluetooth, which is connected to the same switch (or <fn><F5>) works just fine...

some output:
> 
 $ dmesg | grep -e b43 -e wlan -e adio
[   10.808787] wlan: 0.9.4
[   12.163847] wifi0: mac 10.3 phy 6.1 radio 10.2
[   12.300983] thinkpad_acpi: radio switch found; radios are enabled

 $ lspci | grep net
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)


---

