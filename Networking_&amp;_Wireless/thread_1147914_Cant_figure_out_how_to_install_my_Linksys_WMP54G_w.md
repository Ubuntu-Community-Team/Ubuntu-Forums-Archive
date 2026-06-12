---
title: "Cant figure out how to install my Linksys WMP54G wireless card"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by kydell on 2009-05-03
Let me start by saying I am a complete noob to ubuntu, so i dont need to be told that, i already know. 

I have been searching around all day but i still cannot find a working solution to my problem. My problem is, i bought a Linksys WMP54G wireless card, but I cannot figure out how to install it. I asked the guy at Best Buy if it worked with Kubuntu and he said yes, and I beleive him i just dont think I have figured it out yet.

Anyways, Im going to need complete instructions to install this because I have no knowledge of linux. But if anyone could help it would be greatly appreciated.

I'm currently running Kubuntu 9.04 on a computer i built. I have the wireless card in the PCI slot (i know I am supposed to wait and run the CD, but following another sites [BAD] instructions i put it in already). 

Someone please help :(

---

### Post by shane8002 on 2009-05-03
What version is it?

---

### Post by pytheas22 on 2009-05-03
If you open a terminal from the Applications>Accessories menu in Ubuntu, run the following commands and post the output here, I'll try to provide instructions for getting your wireless working:
```

lspci -nn
lshw -C Network
uname -rm
```

If you don't have any Internet connection currently available on Ubuntu, save the output into a text file and transfer it to another computer in order to post here.

---

### Post by kydell on 2009-05-04
Thanks a lot pytheas22! This is very generous of you and I really appreciate it. Here is the output:

```
kydell@kydell-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G35 Express DRAM Controller [8086:2980] (rev 03)                                                                
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G35 Express Integrated Graphics Controller [8086:2982] (rev 03)                                   
00:02.1 Display controller [0380]: Intel Corporation 82G35 Express Integrated Graphics Controller [8086:2983] (rev 03)                                          
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC Gigabit Network Connection [8086:104b] (rev 02)                                                   
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)                                               
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)                                               
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)                                              
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)                                                    
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)                                                       
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)                                                       
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 02)                                                       
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)                                               
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)                                               
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)                                               
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)                                              
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev f2)                                                                              
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller [8086:2810] (rev 02)                                                  
00:1f.2 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller [8086:2820] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller [8086:2825] (rev 02)
03:00.0 IDE interface [0101]: JMicron Technologies, Inc. JMB368 IDE controller [197b:2368]
04:05.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW323 [11c1:5811] (rev 70)
kydell@kydell-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:83:93:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-0 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:b8:7d:fc:85:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kydell@kydell-desktop:~$ uname -rm
2.6.28-11-generic i686
```

---

### Post by pytheas22 on 2009-05-04
I actually don't see any wireless cards listed in the output you posted.  A wireless device should be listed even if there are no drivers currently installed for it, and unfortunately I can't tell you which driver you need to install until I see the line from your 'lspci -nn' output that describes the wireless card.

There are three things that could be wrong: 1) it's not a PCI device, but rather PCMCIA or USB; 2) it's not inserted properly into your motherboard; or 3) there's a problem with the hardware.  Are you sure it's a PCI device (if so, it would be housed completely inside your computer case)?  Could you make sure it's fully inserted?  If you have any other operating systems on this computer, does it work under them?

---

### Post by ags0082 on 2009-05-04
Yeah, the lspci output should have shown something like this:

```
02:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```I have the same wireless card and it was auto-setup for me during the install of 9.04.

-AGS

---

### Post by kydell on 2009-05-04
When i screwed it on it came up a little bit, but i pushed it down and found a network controller:

```
04:03.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```

But I havent installed any drivers, thats the problem, i wouldn't know where to begin with that.

---

### Post by pytheas22 on 2009-05-04
Thanks, that's the information I needed.  Your card has a Ralink 2561 chipset.  Ubuntu should actually already have a driver for it built-in; I suspect that the only reason it didn't work out-of-the-box is because it wasn't inserted into the computer.  If you left-click on the NetworkManager icon in the upper-right corner of your screen, do you see a list of wireless networks?  If not, what is the output now (with the card properly put into place) of the commands:
```

lshw -C Network
lspci -nn
sudo iwlist scan
```

If for some reason Ubuntu isn't auto-configuring the card, we can install drivers manually, but that should not be necessary with a Ralink-based device.

---

### Post by JvP on 2009-05-05
I have one of these cards and have the same issue, not detecting wlans driver does not seems to be loaded. On my way to run those commands my self.
Edit: Whops mine is a rt2500 but its either not working in 9.04

---

### Post by JvP on 2009-05-05
```
root@Slave:~# lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wmaster0
       version: 01
       serial: 26:82:b7:8c:03:9a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 10
       serial: 00:10:a7:13:62:44
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:55:5c:a7:7e:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


```
root@Slave:~# lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:05.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
00:09.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:09.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:09.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51)
00:0d.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
00:0e.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
00:0f.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233A ISA Bridge [1106:3147]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV43 [GeForce 6600 GT] [10de:00f1] (rev a2)

```

```
root@Slave:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanni

```

lshw -C network says product: RT2800 802.11n PCI
lspci -nn 00:0d.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01) uhm what ?

Btw:Sorry for hijacking your thread but i am a bit desperate to get this working.

---

### Post by pytheas22 on 2009-05-05
JvP: I'm not sure what's wrong with your card, but I'm guessing it might have to do with it being claimed by the wrong driver.  It's strange that lspci says it has an rt2500 chipset, while lshw says rt2800.  If it does indeed have an rt2800 chipset, it needs the rt2800 driver, but it's currently using rt2500.  It might help to blacklist rt2500 by typing:
```

echo blacklist rt2500pci | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist rt2500usb | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Then reboot and see if it works better.

Note that because I haven't updated my own system yet, I'm not actually sure if the rt2800 driver exists by default in Jaunty--you may need to compile it manually--but I plan to do the upgrade to Jaunty in a few hours and can help you better then, if necessary.

---

### Post by JvP on 2009-05-06
Will try that when i get back home, but it IS a rt2500 chip aka the wmp54g rev 4 as far as i remember. I find this issue a bit strange.

---

