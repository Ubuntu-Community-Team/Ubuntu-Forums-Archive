---
title: "HP envy m6 1225dx 13.04 wifi issues"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by lucknell on 2013-06-26
Hello world! 

The problem I am having with my HP running 13.04 is that the wifi works out the box but it is not picking up wifi as strong as in windows 8 (which I can no longer boot into but thats another issue for later) I hope someone can help me heres the techie stuff 






[COLOR=#000000]sudo lshw -C network


[/COLOR]  *-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:01:00.2
       logical name: eth0
       version: 0a
       serial: 6c:3b:e5:8c:1f:d9
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:50404000-50404fff memory:50400000-50403fff
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:3e:84:94:b4:40
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.8.0-25-generic firmware=0.34 ip=192.168.1.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:50500000-5050ffff


################################
lspci 



00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
01:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 0a)
02:00.0 Network controller: Ralink corp. Device 539b

Thank you in advance!

ps if you could help me boot back into windows 8 you are awesome!


[COLOR=#000000]
[/COLOR]

---

### Post by carl4926 on 2013-06-26
When you say not as strong?
Do you mean it's not working as well - speed? or do you just mean the signal meter looks less or shows a weaker signal?

Re: Windows

Can we see

```
sudo parted -l
```

---

### Post by lucknell on 2013-06-26
There are my partitions 
Model: ATA Hitachi HTS54107 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   693MB  273MB   fat32        EFI system partition          boot
 3      693MB   827MB  134MB                Microsoft reserved partition  msftres
 4      827MB   101GB  100GB   ntfs         Basic data partition
 6      101GB   101GB  499MB   ext4
 7      101GB   118GB  16.5GB  ext4
10      118GB   126GB  8481MB
 8      126GB   707GB  581GB   ext4
 9      707GB   718GB  10.6GB
 5      718GB   750GB  32.1GB  ntfs         Basic data partition          hidden




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 8481MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  8481MB  8481MB  linux-swap(v1)


As for the wireless the meter and the speed show a difference, it drops internet because my router antenna is bad and only works at 50% signal strength. 
I have a feeling its the RT2800 driver the kernel makes me use in 13.04 but Im not sure

---

### Post by carl4926 on 2013-06-26
Did you follow this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by lucknell on 2013-06-26
I'll try that now but is there anything I can do about my wireless?

Edit: Window 8 is now working but Im not running back to it the only reason I wanted to go back was to get the wireless card's name which is 

Ralink RT5390R

---

### Post by carl4926 on 2013-06-26
For accurate wireless info from Ubuntu, let us see

```
lspci -nnk | grep -iA2 net
```

---

### Post by lucknell on 2013-06-26
here you go

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
	Subsystem: Hewlett-Packard Company Device [103c:18a4]
	Kernel driver in use: r8169
02:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
	Subsystem: Hewlett-Packard Company Device [103c:18ed]
	Kernel driver in use: rt2800pci


Ive also found this [http://ubuntuforums.org/showthread.php?t=2138302](http://ubuntuforums.org/showthread.php?t=2138302) and noticed ukbeast's solution doesnt work because I get make errors

---

### Post by carl4926 on 2013-06-26
I'll have to come back to this later
But I can tell you my eeepc uses the rt2800pci driver and it's spot on

---

### Post by lucknell on 2013-06-26
Alright thank you for the support but Im right next to my router and thats the only way I can connect. Once I leave the room and go downstairs (this is a better router) I lose connectivity

---

### Post by carl4926 on 2013-06-26
You could try adding the Compat Wireless module, now called: linux-backports-modules
To match your kernel

---

### Post by Pyrophorus on 2013-06-26
I'm having the same kind of issue.

It works fine at home, 60-70% at school and not at all in a meeting hall.

It worked fine as a VM in Windows 8.

---

### Post by carl4926 on 2013-06-26
> **Pyrophorus said:**
> I'm having the same kind of issue.

It works fine at home, 60-70% at school and not at all in a meeting hall.

It worked fine as a VM in Windows 8.

It's generally not a good idea to jump in on a thread.
But what version of Ubuntu?

You need to check if these are N or G and encrypted or Not?

---

### Post by lucknell on 2013-06-26
how do I install the backports exactly?

---

### Post by carl4926 on 2013-06-26
I would use synaptic
Fist check which kernel you have  uname -a

You may need to install synaptic, then search for [COLOR=#000000]linux-backports-modules in synaptic, there will be a long list. Find the one to match your kernel[/COLOR]

---

### Post by lucknell on 2013-06-26
Linux lucknell-HP 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


thats the output and I cant find the backports in synaptic

---

### Post by Pyrophorus on 2013-06-26
> **carl4926 said:**
> It's generally not a good idea to jump in on a thread.
But what version of Ubuntu?

You need to check if these are N or G and encrypted or Not?

I thought, you should always search for solutions...

I'm using 13.04, home is encrypted, and uses an automatic settings of b/g/n/ the hall is not, school uses PEAP, with a username and password

---

### Post by carl4926 on 2013-06-26
I think you need the sources

[http://archive.ubuntu.com/ubuntu/dists/raring/](http://archive.ubuntu.com/ubuntu/dists/raring/)

[http://archive.ubuntu.com/ubuntu/dists/raring-updates/](http://archive.ubuntu.com/ubuntu/dists/raring-updates/)

---

### Post by lucknell on 2013-06-27
I added the sources (reading the errors helped me fix it up) and I still could not get the back ports are the packages not in the main?

---

### Post by carl4926 on 2013-06-27
> **lucknell said:**
> I added the sources (reading the errors helped me fix it up) and I still could not get the back ports are the packages not in the main?
Well I was working from a Mint machine, but those are the listed sources for the compat wireless and they are visible in Mint

---

### Post by lucknell on 2013-06-27
I added them but could it be in any other folder other than the main one? like multiverse?

---

### Post by carl4926 on 2013-06-27
The thing is, your wireless does work, it's just not performing well. Different results from different access points? Is that correct?
I'm no wireless expert and not sure what to suggest on it

I did find this
[https://wiki.ubuntu.com/Kernel/LinuxWireless](https://wiki.ubuntu.com/Kernel/LinuxWireless)

So you may need to adjust the sources I gave you

---

### Post by lucknell on 2013-06-28
No it gives the same results on each access point(bad speed and signal) it just one ap I have I cant connect to if im not in the same room as it because of the bad antenna (not related to this problem)

Edit: I got tried of the Ralink wifi card so I switched it with with my other computer's wifi card and it works fine (wifi switch light is blinking thought but I guess you cant win them all huh?) and the wifi switch didnt work on ubuntu anyway so Ill google that problem and find a fix. If anyone could fix the Ralink rt5390r cards driver on 13.04 and get it working I would love that but till then I am going to look for the solution to the issues above. Thanks for your time

---

