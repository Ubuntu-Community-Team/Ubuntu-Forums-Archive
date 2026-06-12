---
title: "disconnecting wireless &amp; slow internet, ralink (rt 3090),  ubuntu 11.04 on msi cr620"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by TheJellyBean on 2011-05-04
Hi  
After putting ubuntu 11.04 on my laptop (msi cr620) the wireless will randomly disconnect and then will not reconnect unless you restart it or put it on standby and start it again. Once connected it is very slow to load up pages, even google (I have tried using fedora and it was a lot faster it just seems to be ubuntu). 

```

05:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIeiwconfig
lo        no wireless extensions.
``````

wlan0     IEEE 802.11bgn  ESSID:"satyam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: F0:7D:68:40:DB:6E   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:219  Invalid misc:20   Missed beacon:0
```
```

sudo lshw -C network
[sudo] password for step: 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 6c:62:6d:1b:e2:98
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.0.109 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f4000000-f400ffff
```I'm a newbie at this so I don't know how much of the above is helpful but if anyone can help I would really appreciate it.
Thanks 
Steph

---

### Post by jubberz on 2011-05-04
I'm having the exact same problem :( Switched back to 10.10 for the time being. I'm pretty new to Ubuntu too so any help would be appreciated!

---

### Post by frogpr on 2011-05-05
Had exactly the same problems, ralink 3090 almost unusable in 11.04. Have an HP ProBook 4520s with ralink 3090 wifi.
Solved it by blacklisting ALL rt drivers (i.e. rt2x00lib,rt2800pci,rt2x00usb,rt2x00pci,rt3390sta) EXCEPT rt2860sta.

You need to add these drivers at the end of /etc/modprobe.d/blacklist.conf. 

The rt2860sta works flawlessly, fast and stable (not a single disconnect so far), suspend and resume work as well.

Cheers

---

### Post by apeetso on 2011-05-11
Umh, I use Asus K50IN series laptop and my network keeps disconnecting and not reconnecting aswell.
If what you, **frogpr**, said really works, then could you maybe write down what it is that I have to do (or anyone else), in more detail, because really I'm new to the whole scene and have no clue how to do these things.

Thank you in advance.

---

### Post by chili555 on 2011-05-11
> **apeetso said:**
> Umh, I use Asus K50IN series laptop and my network keeps disconnecting and not reconnecting aswell.
If what you, **frogpr**, said really works, then could you maybe write down what it is that I have to do (or anyone else), in more detail, because really I'm new to the whole scene and have no clue how to do these things.

Thank you in advance.It depends on your wireless card. Please post:```
lspci -nn
```We'll be in a better position to proceed once we see the result.

---

### Post by apeetso on 2011-05-11
This is what it says:

```
[FONT=monospace]00:00.0 Host bridge [0600]: nVidia Corporation MCP79 Host Bridge [10de:0a83] (rev b1)
00:00.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a88] (rev b1)
00:03.0 ISA bridge [0601]: nVidia Corporation MCP79 LPC Bridge [10de:0aae] (rev b3)
00:03.1 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0aa4] (rev b1)
00:03.2 SMBus [0c05]: nVidia Corporation MCP79 SMBus [10de:0aa2] (rev b1)
00:03.3 RAM memory [0500]: nVidia Corporation MCP79 Memory Controller [10de:0a89] (rev b1)
00:03.5 Co-processor [0b40]: nVidia Corporation MCP79 Co-processor [10de:0aa3] (rev b1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP79 OHCI USB 1.1 Controller [10de:0aa5] (rev b1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP79 EHCI USB 2.0 Controller [10de:0aa6] (rev b1)
00:08.0 Audio device [0403]: nVidia Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Bridge [10de:0aab] (rev b1)
00:0b.0 SATA controller [0106]: nVidia Corporation MCP79 AHCI Controller [10de:0ab9] (rev b1)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac4] (rev b1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0aa0] (rev b1)
00:15.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac6] (rev b1)
00:16.0 PCI bridge [0604]: nVidia Corporation MCP79 PCI Express Bridge [10de:0ac7] (rev b1)
03:00.0 VGA compatible controller [0300]: nVidia Corporation C79 [GeForce G102M] [10de:0873] (rev b1)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  01)
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285  Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)[/FONT]
```[FONT=monospace] 
[/FONT]

---

### Post by chili555 on 2011-05-11
You have an Atheros card; you have nothing in common with the title of this thread aside from disconnects. I suggest you search this forum for 'ath9k disconnects' and, if you can't find a solution, start a new thread.

---

### Post by apeetso on 2011-05-11
Okay, I will, thank you!

---

### Post by Arsic on 2011-05-20
> **frogpr said:**
> Had exactly the same problems, ralink 3090 almost unusable in 11.04. Have an HP ProBook 4520s with ralink 3090 wifi.
Solved it by blacklisting ALL rt drivers (i.e. rt2x00lib,rt2800pci,rt2x00usb,rt2x00pci,rt3390sta) EXCEPT rt2860sta.

You need to add these drivers at the end of /etc/modprobe.d/blacklist.conf. 

The rt2860sta works flawlessly, fast and stable (not a single disconnect so far), suspend and resume work as well.

Cheers

So now my rt3090 is using rt2860sta drivers as shown by sudo lshw -C network and iwconfig. Still looking for disconnects, but the biggest problem is now it's not running at 802.11n speeds. iwconfig shows 54 Mb/s.

Edit: yeah I'm still getting disconnects. I started this netbook off with 10.10 and the problem was pretty much the same. Had to do sudo /etc/init.d/networking restart && sudo service network-manager restart as a temporary fix, but it tends to disconnect more often after that.

Seems to be all right when on WPA2-AES. WPA2-TKIP was the one giving it problems.

---

### Post by davidcmc on 2011-05-27
> **frogpr said:**
> Had exactly the same problems, ralink 3090 almost unusable in 11.04. Have an HP ProBook 4520s with ralink 3090 wifi.
Solved it by blacklisting ALL rt drivers (i.e. rt2x00lib,rt2800pci,rt2x00usb,rt2x00pci,rt3390sta) EXCEPT rt2860sta.

You need to add these drivers at the end of /etc/modprobe.d/blacklist.conf. 

The rt2860sta works flawlessly, fast and stable (not a single disconnect so far), suspend and resume work as well.

Cheers

I'd just like to say THANK YOU.
Me and my sister (each one) have an Asus 1015 PEM.
Mine has an Atheros chip, while her netbook has a Ralink chip.
After updating Ubuntu to 11.04, my netbook continued to work perfectly, while her netbook started to show problems in wireless (the same as topic author).

I've just blacklisted those drivers in her netbook and, at least until now, wireless is working perfectly again!
Ubuntu 11.04 is using RT2860STA driver in her netbook, according to iwconfig.

Thank you, again.

---

### Post by riyasmp on 2011-05-29
hi guys 

I have got the same problem with the my hp dv3150 laptop running ubuntu 11.04. it keeps disconnecting frequently. but the intresting this is that when pluged on to the electricty there is no disconnection at all.

when running on battery the problem occurs frequently and very annoying. Has any one noticed the same problem?

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:70:61:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c3400000-c340ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:38:59:c4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff memory:c1410000-c141ffff


thanks in advance

with regards

---

### Post by chili555 on 2011-05-29
> driver=rt2800pci Dr. Chili withdraws his stethoscope from riyasmp's body and says, "I'm afraid I don't like that one bit, but I think we can treat your condition." Please post:```
lsmod | grep rt2
iwconfig
```Thanks.

---

### Post by riyasmp on 2011-05-29
> **chili555 said:**
> Dr. Chili withdraws his stethoscope from riyasmp's body and says, "I'm afraid I don't like that one bit, but I think we can treat your condition." Please post:```
lsmod | grep rt2
iwconfig
```Thanks.

lsmod | grep rt2
rt2860sta             543010  0 
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Livebox-AEB9"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:7E:00:67:60   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:706  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2011-05-29
Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

---

### Post by riyasmp on 2011-05-29
> **chili555 said:**
> Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

the wireless has started working on battery now. But now the problem is its not booting on battery(unplugged). with electricity on its all working fine now. 

thanks a lot for your help chill.is this problem connected?

---

### Post by chili555 on 2011-05-29
> is this problem connected?I doubt it. I'm suspicious it's a glitch in power-saving settings. I'm glad the wireless is sorted.

---

### Post by riyasmp on 2011-05-29
thanks a lot chili55

Is there any helpful link that u can offer me on this regard. thanks a lot again for your help :D

with regards

---

### Post by chili555 on 2011-05-29
> **riyasmp said:**
> thanks a lot chili55

Is there any helpful link that u can offer me on this regard. thanks a lot again for your help :D

with regardsYou're asking your cardiologist about the flu. Sorry, I know little about power saving. I'd search General Help for 'boot battery.' I've found that you and I are almost never the only guys with the problem. Somebody has solved this.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by riyasmp on 2011-05-29
Chilli

you are not just a cardiologist you are an intervention cardiologist =D>=D>=D> 

i had some problem with "splash" on grub. i set it to no splash on etc/default/grub and everything is working flawlessly. 

thanks a lot chilli

---

### Post by 1doRa on 2011-05-31
> **frogpr said:**
> Had exactly the same problems, ralink 3090 almost unusable in 11.04. Have an HP ProBook 4520s with ralink 3090 wifi.
Solved it by blacklisting ALL rt drivers (i.e. rt2x00lib,rt2800pci,rt2x00usb,rt2x00pci,rt3390sta) EXCEPT rt2860sta.

You need to add these drivers at the end of /etc/modprobe.d/blacklist.conf. 

The rt2860sta works flawlessly, fast and stable (not a single disconnect so far), suspend and resume work as well.

Cheers
  WOW! words cant express how thankful I am :)
thanks alot man. works great on my HP Pavilion DV6-3124tx

---

### Post by 0656712 on 2011-06-01
> **chili555 said:**
> Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

thank you chili

---

### Post by Uri Stamonov on 2011-06-09
Hey guys

Firstly, thanks for all the great info here - this issue had me banging my head against the wall for a while!

Moving on, does anyone know if there are any fixes in the pipeline for the driver?

I'm happy to have the wireless working but would ideally like to be using the adapter at the N speeds, rather than 54g.

Thanks!

Uri

---

### Post by tuxonapogostick on 2011-06-14
> **riyasmp said:**
> hi guys 

I have got the same problem with the my hp dv3150 laptop running ubuntu 11.04. it keeps disconnecting frequently. but the intresting this is that when pluged on to the electricty there is no disconnection at all.

when running on battery the problem occurs frequently and very annoying. Has any one noticed the same problem?


I have exactly the same problem!

---

### Post by cabetza1 on 2011-07-09
Thanks, Good for MSI u135 with same card.

Before, my solution was  to keeping the wifi power management = off,  adding the file: &#8220;/etc/pm/power.d/wireless&#8221;

#!/bin/sh
/sbin/iwconfig wlan1 power off

---

### Post by undy on 2011-07-14
> **chili555 said:**
> Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

Anyone with the same problem and an eeepc  this was good medicine for my 901. 
Thanks,
Andy

---

### Post by ladi on 2011-08-27
> **chili555 said:**
> Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

works flawlessly after reboot :guitar: i wish i could write you a song **doctor** thank you!

---

### Post by Poptartzz on 2011-10-12
Hello, all. I'm new to the forum, and fairly new to any and all Linux based systems. I'm using the Joli OS 1.2 and I'm having some connectivity problems with the same card, RaLink 3090. I previously had Natty before Joli, and Windows 7 Starter before that (yuk). My problem is, however, I seem to be using the rt2860sta driver that is supposedly flawless, but I'm having disconnects as well. Granted, they are not as frequent as they were on Natty, but I never had any on Windows. I dread having to use such a heavy and slow OS, so I'm hoping my issue can be solved.

Here is what I get from 'sudo lshw -C network':
```
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:f0:6d:05:75:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=136.160.233.225 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:72:89:36
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```

If it means anything, it disconnects more often in public places, like my university, than anywhere else.

---

