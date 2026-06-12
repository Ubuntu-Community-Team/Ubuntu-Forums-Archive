---
title: "Lost eth0"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by hfxrzw on 2010-03-13
Hi, I have looked, but couldn't find an answer. I mostly use my laptop wireless, but wanted to use the wired network some days ago. That's when I noted I had lost the functionality of the network card. Initialy it didn't show 'eth0' but 'ifupdown' in the network manager. Tried to add the network card manually it only installed as eth1 and didn't work. after a lot of searching and reading I got rid of the ifupdown and managed to install a eth0 in network manager, but it doesn't work. When I connect the network wire the green light at the port comes on and you see the yellow light come on on occassion, but there is no network functionality. I have a clean iftab except for the loopback.
Any tips highly appreciated!!!

Thanks, Rene

---

### Post by Iowan on 2010-03-13
I presume **ifconfig -a** (from a terminal) will show no IP address for eth0 - what does **sudo lshw -C network** show?

---

### Post by hfxrzw on 2010-03-13
ifconfig -a gives:

eth0      Link encap:Ethernet  HWaddr 00:16:6f:52:dd:0e  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe52:dd0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2095 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3505494 (3.5 MB)  TX bytes:250970 (250.9 KB)
          Interrupt:21 Base address:0x4000 Memory:d0000000-d0000fff 

But no eth0 in network connections. I think the above listed is my wireless connection.

The second command only shows the wireless. Thanks!

---

### Post by hfxrzw on 2010-03-13
It looks like my wireless is now used as Eth0 instead of using my wired as such. Ubuntu does not seem to 'see' my wired network although it is powered. Anybody?? Nice please?? Cheers, Rene.

---

### Post by Iowan on 2010-03-14
Seems odd to have eth0 as wireless (although my laptop has eth1 as wireless). It's possible that there is a driver problem for the wired card. Post results of **sudo lshw -C network**.

---

### Post by hfxrzw on 2010-03-14
Result of command:

root@ubuntu-laptop:~# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth0
       version: 05
       serial: 00:16:6f:52:dd:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.103 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:d0000000-d0000fff

Hope it clarifies, it seems to only show the wireless card of the laptop, not the wired card.

Cheers, Rene.

PS It seems that an awful lot of people have problems with eth0 after the latest upgrades??

---

### Post by Iowan on 2010-03-15
> **hfxrzw said:**
> Hope it clarifies, it seems to only show the wireless card of the laptop, not the wired card.Yup - the machine doesn't acknowledge having a wired interface...
Hmmm...:-k

---

### Post by hfxrzw on 2010-03-16
Indeed, so what now? It's on in the bios.

---

### Post by Iowan on 2010-03-16
What chipset is it using? Hard to imagine one that doesn't show up on the "radar".

---

### Post by wilee-nilee on 2010-03-16
> **hfxrzw said:**
> It looks like my wireless is now used as Eth0 instead of using my wired as such. Ubuntu does not seem to 'see' my wired network although it is powered. Anybody?? Nice please?? Cheers, Rene.

I had the same problem with a acer aspire D250 netbook. The wireless went out on all 3 OS. I found that there was a bios update so short of returning the computer the bios update got the wired working again. Use your own methodology here and be careful with flashing the bios if thats your solution.

---

### Post by hfxrzw on 2010-03-17
Thanks for that! I had the machine running on wired before, but after the last upgrade of Ubuntu it is no longer working. Therefore I have the impression it has to do with Ubuntu and not the machine. But I'll see if there's a bios upgrade available.
BTW how do you find out what the chipset is if Ubuntu doesn't recognise the card?
Cheers, Rene.

---

### Post by bkratz on 2010-03-17
> **hfxrzw said:**
> Thanks for that! I had the machine running on wired before, but after the last upgrade of Ubuntu it is no longer working. Therefore I have the impression it has to do with Ubuntu and not the machine. But I'll see if there's a bios upgrade available.
BTW how do you find out what the chipset is if Ubuntu doesn't recognise the card?
Cheers, Rene.

Does the ethernet controller show up when you do a

lspci -nn

in the terminal?

---

### Post by hfxrzw on 2010-03-17
This is the response to that:
root@ubuntu-laptop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
02:06.5 Communication controller [0780]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller [104c:8035]

Does that help? I think I see the wireless, but don't recognise the wired card.
Cheers, Rene.

---

### Post by wilee-nilee on 2010-03-17
> **hfxrzw said:**
> Thanks for that! I had the machine running on wired before, but after the last upgrade of Ubuntu it is no longer working. Therefore I have the impression it has to do with Ubuntu and not the machine. But I'll see if there's a bios upgrade available.
BTW how do you find out what the chipset is if Ubuntu doesn't recognise the card?
Cheers, Rene.

mine was actually loss of wired, I mistakenly said wireless in my first post. The card in my machine always worked out of the box.

Flashing my bios though because I had changed to a IDE HD in bios went back to acpi (sata), so when I restarted I could get into Lucid but had lost access to XP and W7 so I just reinstalled which is my way of cutting to the chase, no waiting for answers.

---

### Post by zaurum on 2010-03-25
Hi there,

I am experiencing similar problems on two machines using wired connections. 

One is running Xubuntu 9.04 and sporadically fails to connect to the router. This one is configured to use a static IP.

The other one never had this issue running Ubuntu 9.04. After the upgrade to 9.10 a few days ago, the same thing happens. Sometimes, the laptop fails to obtain a dynamic IP. If I click "disable eth0" and then click "enable eth0", everything works like a charm.

The two machines are in two different physical locations, use different hardware, different routers to connect to, etc.

Any hints as to what may cause these issues?

Regards,
zaurum

---

