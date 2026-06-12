---
title: "Please Help! I cant figure out how to finish my wireless setup."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by badbowtie03 on 2009-01-14
Hey everyone, I've tried everything that a beginner can do. I just cant figure this out. I kinda want to give up and just delete linux. I FINALLY got ubuntu working on my laptop after a ton of research. But now I just CANNOT get my wireless card to work. I downloaded ndiswrapper common, utils, and ndisgtk and set up my .inf file with my wireless card, but then when I click "configure wireless card" It says there is NO configuration utility found or something like that. I dont know what to do now. I've read through alot of documentation and I looked up on ubuntus website and it says to go to:

1. Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked.

but i dont have that!!! why not? how do i finish configuring my card? how do i search for networks in and around my house and school?

Someone please give me some dumbed down answers. thanks alot!

---

### Post by chex_m8 on 2009-01-14
In the upper right hand corner is where your network connections will be listed. One left click should bring up a menu with all the wireless networks available. Also try this, have your wireless card switched on before you boot the computer. Not sure why but this is the only way I can get mine to work. G. Luck

---

### Post by melojo on 2009-01-14
click on applications>accessories>terminal and post the output of the commands below.

```

lspci
sudo -C network
ifconfig

```

This will give us more info.

---

### Post by badbowtie03 on 2009-01-14
Well, I dont have the bar on top anymore... sorry. Once I got ubuntu working I started modding what the desktop looked like and deleted the top bar and arranged some things. Oh and I did the commands and this is what the terminal said: 

lspci
sudo -C network
ifconfig

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---------------------------

sudo -C network
sudo: illegal option `-C'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
danieldukejr@danieldukejr-laptop:~$ 

------------------------

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:9a:44:9a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)


Oh and quick question... when I minimize windows why do they go down to the bottom right by my recycle bin and dissappear? How do I get them to minimize to the taskbar so I can maximize them again? thanks alot for the help!

---

### Post by badbowtie03 on 2009-02-01
can anyone offer anymore help from what my last post shows? thanks alot!!

---

### Post by danni-la on 2009-02-01
I'm sorry but I can't help much with the wireless... still a noob so I don't know enough yet... from your first post though the network configuration in mine is in system - preferences - network configuration

for this problem...

> **badbowtie03 said:**
> 

Oh and quick question... when I minimize windows why do they go down to the bottom right by my recycle bin and dissappear? How do I get them to minimize to the taskbar so I can maximize them again? thanks alot for the help!

right click on the bottom panel - add to panel - windows list

Cheers Danni

---

### Post by badbowtie03 on 2009-02-01
thanks danni! that helped!

---

