---
title: "intel 82566dc-2 nic = no eth0 in ubuntu 10."
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by frankm on 2011-04-20
I've spent several hours searching the internet but have not been able to figure out a solution to this problem.  

I have an intel dg33tl motherboard w/built in intel 82566dc-2 nic.  modprobe seems to work and I dont see any errors in dmesg but no matter what I do there is no eth0 that shows up in ifconfig.  i've even tried adding the alias manually to modprobe.  below I will post the results of various commands.  I have tried both intel e1000e and intel e1000 drivers and neither seem to work but i notice that modprobe pauses for a few seconds after using e1000e.  Do you have any ideas?

LSPCI RESULTS
> 
lspci -nn |grep -i eth
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DC-2 Gigabit Network Connection [8086:294c] (rev 02)


DMESG RESULTS
> 
dmesg results:
[ 4126.218407] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10a-NAPI
[ 4126.218411] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[ 4126.218448] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 4126.218461] e1000e 0000:00:19.0: setting latency timer to 64
[ 4126.856065] e1000e 0000:00:19.0: PCI INT A disabled



LSHW RESULTS
> 

sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:e0400000-e041ffff memory:e0424000-e0424fff ioport:20e0(size=32)


MODPROBE RESULTS
> 

modprobe -c |grep e100
# replaced by e100
blacklist e100
alias eth0 e1000e
alias pci:v00008086d00001000sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001001sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001004sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001008sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001009sv*sd*bc*sc*i* e1000
alias pci:v00008086d0000100Csv*sd*bc*sc*i* e1000
alias pci:v00008086d0000100Dsv*sd*bc*sc*i* e1000
alias pci:v00008086d0000100Esv*sd*bc*sc*i* e1000
alias pci:v00008086d0000100Fsv*sd*bc*sc*i* e1000
alias pci:v00008086d00001010sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001011sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001012sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001013sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001014sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001015sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001016sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001017sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001018sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001019sv*sd*bc*sc*i* e1000
alias pci:v00008086d0000101Asv*sd*bc*sc*i* e1000
alias pci:v00008086d0000101Dsv*sd*bc*sc*i* e1000
alias pci:v00008086d0000101Esv*sd*bc*sc*i* e1000
alias pci:v00008086d00001026sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001027sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001028sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001029sv*sd*bc02sc00i* e100
alias pci:v00008086d00001030sv*sd*bc02sc00i* e100
alias pci:v00008086d00001031sv*sd*bc02sc00i* e100
alias pci:v00008086d00001032sv*sd*bc02sc00i* e100
alias pci:v00008086d00001033sv*sd*bc02sc00i* e100
alias pci:v00008086d00001034sv*sd*bc02sc00i* e100
alias pci:v00008086d00001038sv*sd*bc02sc00i* e100
alias pci:v00008086d00001039sv*sd*bc02sc00i* e100
alias pci:v00008086d0000103Asv*sd*bc02sc00i* e100
alias pci:v00008086d0000103Bsv*sd*bc02sc00i* e100
alias pci:v00008086d0000103Csv*sd*bc02sc00i* e100
alias pci:v00008086d0000103Dsv*sd*bc02sc00i* e100
alias pci:v00008086d0000103Esv*sd*bc02sc00i* e100
alias pci:v00008086d00001049sv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000104Asv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000104Bsv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000104Csv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000104Dsv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001050sv*sd*bc02sc00i* e100
alias pci:v00008086d00001051sv*sd*bc02sc00i* e100
alias pci:v00008086d00001052sv*sd*bc02sc00i* e100
alias pci:v00008086d00001053sv*sd*bc02sc00i* e100
alias pci:v00008086d00001054sv*sd*bc02sc00i* e100
alias pci:v00008086d00001055sv*sd*bc02sc00i* e100
alias pci:v00008086d00001056sv*sd*bc02sc00i* e100
alias pci:v00008086d00001057sv*sd*bc02sc00i* e100
alias pci:v00008086d00001059sv*sd*bc02sc00i* e100
alias pci:v00008086d0000105Esv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000105Fsv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001060sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001064sv*sd*bc02sc00i* e100
alias pci:v00008086d00001065sv*sd*bc02sc00i* e100
alias pci:v00008086d00001066sv*sd*bc02sc00i* e100
alias pci:v00008086d00001067sv*sd*bc02sc00i* e100
alias pci:v00008086d00001068sv*sd*bc02sc00i* e100
alias pci:v00008086d00001069sv*sd*bc02sc00i* e100
alias pci:v00008086d0000106Asv*sd*bc02sc00i* e100
alias pci:v00008086d0000106Bsv*sd*bc02sc00i* e100
alias pci:v00008086d00001075sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001076sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001077sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001078sv*sd*bc*sc*i* e1000
alias pci:v00008086d00001079sv*sd*bc*sc*i* e1000
alias pci:v00008086d0000107Asv*sd*bc*sc*i* e1000
alias pci:v00008086d0000107Bsv*sd*bc*sc*i* e1000
alias pci:v00008086d0000107Csv*sd*bc*sc*i* e1000
alias pci:v00008086d0000107Dsv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000107Esv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000107Fsv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000108Asv*sd*bc*sc*i* e1000
alias pci:v00008086d0000108Bsv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000108Csv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001091sv*sd*bc02sc00i* e100
alias pci:v00008086d00001092sv*sd*bc02sc00i* e100
alias pci:v00008086d00001093sv*sd*bc02sc00i* e100
alias pci:v00008086d00001094sv*sd*bc02sc00i* e100
alias pci:v00008086d00001095sv*sd*bc02sc00i* e100
alias pci:v00008086d00001096sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001098sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001099sv*sd*bc*sc*i* e1000
alias pci:v00008086d0000109Asv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010A4sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010A5sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010B5sv*sd*bc*sc*i* e1000
alias pci:v00008086d000010B9sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010BAsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010BBsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010BCsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010BDsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010BFsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010C0sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010C2sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010C3sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010C4sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010C5sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010CBsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010CCsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010CDsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010CEsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010D3sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010D5sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010D9sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010DAsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010DEsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010DFsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010E5sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010EAsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010EBsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010EFsv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010F0sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010F5sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010F6sv*sd*bc*sc*i* e1000e
alias pci:v00008086d000010FEsv*sd*bc02sc00i* e100
alias pci:v00008086d00001209sv*sd*bc02sc00i* e100
alias pci:v00008086d00001229sv*sd*bc02sc00i* e100
alias pci:v00008086d00001501sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001502sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001503sv*sd*bc*sc*i* e1000e
alias pci:v00008086d0000150Csv*sd*bc*sc*i* e1000e
alias pci:v00008086d00001525sv*sd*bc*sc*i* e1000e
alias pci:v00008086d00002449sv*sd*bc02sc00i* e100
alias pci:v00008086d00002459sv*sd*bc02sc00i* e100
alias pci:v00008086d0000245Dsv*sd*bc02sc00i* e100
alias pci:v00008086d000027DCsv*sd*bc02sc00i* e100
alias pci:v00008086d0000294Csv*sd*bc*sc*i* e1000e


IFCONFIG RESULTS
> 
sudo /sbin/ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6880 (6.8 KB)  TX bytes:6880 (6.8 KB)


---

### Post by frankm on 2011-04-21
*bump*
:confused:
anybody have any ideas?

---

### Post by brpylko on 2011-04-21
Is your ethernet plugged in? Sometimes device files disappear when the device is not connected/operational.

---

### Post by frankm on 2011-04-22
> **brpylko said:**
> Is your ethernet plugged in? Sometimes device files disappear when the device is not connected/operational.

it's plugged in.  any other ideas?

---

