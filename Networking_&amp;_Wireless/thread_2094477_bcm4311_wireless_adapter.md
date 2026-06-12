---
title: "bcm4311 wireless adapter"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by burdock on 2012-12-13
Hello,

I recently was given an HP Compaq 6715b laptop containing the broadcom BCM4311kfbg wireless adapter and, for the life of me, I cant get the wireless apapter to work.

The computer has those touch sensitive buttons that light up when you activate the corresponding function. The volume buttons light up as they should as well as the "info" button and the "presentation" button...but the wireless button never lights up and the "wireless adapter is on" led is always off. 

Ive tried installing the STA drivers, using b43-fwcutter...and a bunch of other work arounds that I have found on the internet but I cant get any of them to work.

I cant even get lspci to list the device.

Here is my lspci output:

```
cole@Neptune:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI Device 7914
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
02:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)
02:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 02)
10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
cole@Neptune:~$ 

```

I am certain this is the wireless adapter I have because I physically looked at the piece of hardware and pulled that model number off of it.

I am running Ubuntu 12.10 x64.

I know these broadcom drivers have been touched on thousands of times...but I'm struggling here and would appreciate some help.

Thanks,
Cole

---

### Post by burdock on 2012-12-14
anyone?

---

### Post by Bucky Ball on 2012-12-14
Please provide the output of this command:

```
sudo lshw -C network
```

Have you looked in Additional Drivers after updating with a cable? This card *should* work 'out of the box'. When you installed b43-fwcutter, did you also install firmware-b43-installer? You then need to restart ...

---

### Post by burdock on 2012-12-14
This is what i got. Thanks for your assistance.

```
cole@Neptune:~$ sudo lshw -C network
[sudo] password for cole: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:78:ac:ff
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=sb v2.09 ip=192.168.0.12 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:d0000000-d000ffff
cole@Neptune:~$

```

---

### Post by Bucky Ball on 2012-12-14
Strange. No sign of the card at all. You say you pulled it out to have a look; are you sure it's seated and the two wires are connected properly? Has it been known to work in the recent past? 

As this is a hand-me-down, perhaps the card is dead on arrival in your hands ... as mentioned previously, do you have b43-fwcutter and firmware-b43-installer installed and then restart?

---

### Post by burdock on 2012-12-14
Its in there and it was working with windows. I think (THINK) it may have been working with one of the live cd's I tried before install ubuntu...i tried a bunch of them though so no idea which one it would have been.

---

### Post by burdock on 2012-12-14
Ack! Sorry about that image. Didnt realize it wouldnt automatically resize.

---

### Post by Bucky Ball on 2012-12-14
> **burdock said:**
> Ack! Sorry about that image. Didnt realize it wouldnt automatically resize.

Please remove image and instead attach it by hitting 'Go Advanced' and clicking the paperclip icon. Cheers. ;)

Apart from that, yes, the two wires appear to be connected properly. Does it work when you 'Try Ubuntu' from the LiveCD?

---

### Post by burdock on 2012-12-15
I tried a handful of different live CD's and didnt get any wireless with any of them.

---

### Post by Bucky Ball on 2012-12-15
I'm leaning toward hardware failure as this should be working with little, if any, effort. Your machine, on the other hand, doesn't detect it in anyway. 

Is there a possibility of testing it on another machine? Have you tried pulling it out again and reseating?

---

### Post by burdock on 2012-12-15
I will do a wipe in the morning and install windows and see what I get. This is a fresh linux install so I wont need to back anything up.

---

### Post by Bucky Ball on 2012-12-16
That's one plan. If you have the room you could install Windows on another partition and leave Ubuntu there. You would then need to reinstall grub or easier, use Boot Repair to get them both booting:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by burdock on 2012-12-18
Sorry for the long wait for an update. I dual booted with windows 7 and installed drivers. No wireless functionality in windows 7. I could swear up and down that the card worked when my folks gave me the laptop, but maybe I did something to it that fried it. Currently, I am looking for another machine to test the card in.

Thanks for the help, regardless.

---

### Post by burdock on 2012-12-19
Wait just a gosh darn minute. 

After my previous post, I was searching online for a new wireless adapter when I happened to stumble across a post on the HP forums talking about the machine "losing" its wireless adapter in windows. A few of the posts mentioned resetting the bios to defaults and then rebooting. I tried this and Viola!...I know have working wireless under Windows 7, as you can see by the picture I have attached.

I will try rebooting into the linux side of things and see what happens.

---

### Post by burdock on 2012-12-19
Well I'll be!

Rebooted into Ubuntu (actually Bodhi...) and now I have wireless connectivity.

I have no idea as to what caused this problem or if it is going to occur again.

If any ubuntu dev's are interested in this, I would be willing to cooperate with whatever you should need in order to make improvements.

If not, then again, thanks for the help, regardless.

Merry Christmas, everyone!

---

### Post by Bucky Ball on 2012-12-19
Ha! Nice one and lucky find. All good. Was the BIOS setting at your end and nothing to do with Win or Ubuntu so no help to the devs.

Helping is what these forums are all about, so please mark your thread as 'Solved' from Thread Tools to help others. ;)

Merry xmas and nice to see an old machine resurrected; now there's one from santa ...

(Incidentally, age is generally no barrier when it comes to Ubuntu (or Linux generally). It prides itself on giving new life to machines that other OSs forget because they don't have the appropriate specs. Old hardware is generally not the issue with Linux and if it doesn't work 'out of the box' then there are generally workarounds ...)

---

### Post by burdock on 2012-12-19
The interesting thing is that I am generally no stranger to tinkering around in the bios, and I looked at this one twice and didnt see anything that I thought would affect the wireless.

Oh well, I suppose..just glad it is working now.

---

