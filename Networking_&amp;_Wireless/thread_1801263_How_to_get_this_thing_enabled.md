---
title: "How to get this thing enabled?"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by b1tchacked on 2011-07-10
*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:ee:14:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3400000-d340ffff

I tried reading many posts but did not work.....and i am newbie:( and am on ubuntu 11.04

---

### Post by chili555 on 2011-07-10
DISABLED often, but not always, means that your wireless switch is in the Off position or that a piece of software *thinks* it's off. Let's see what the system thinks. Please post:```
rfkill list all
```What kind of Dell or Acer is it?

---

### Post by b1tchacked on 2011-07-11
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

Laptop - Sony vaio Y-Series

---

### Post by chili555 on 2011-07-11
An Acer module on a Sony laptop? Hmmm. The doctor has seen these cases before. Please do:```
lsmod | grep acer
```Is the module acer-wmi loaded? If so, please do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all
```Now does your wireless work? If so, we'll tweak one file to make it permanent.

---

### Post by b1tchacked on 2011-07-11
0: sony-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

All were yes earlier after restart , this is what happenned?

---

### Post by b1tchacked on 2011-07-11
I think something wrong with the drivers , can you help with the drivers....

---

### Post by chili555 on 2011-07-11
Why did you restart? Why do you think there is a problem with the driver; do you think the driver is going to magically work the wireless switch???> 0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
1: sony-wifi: Wireless LAN
Soft blocked: yes
Hard blocked: no
2: sony-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no
3: acer-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: no
4: [COLOR="Red"]phy0: Wireless LAN
Soft blocked: yes
**Hard blocked: yes**[/COLOR]
What are the results if you issue the commands above and do *NOT* restart?

---

### Post by b1tchacked on 2011-07-11
getting that switched to **no** did not help me connect to a wireless device....

---

### Post by chili555 on 2011-07-11
It's never going to connect, nor are we going to be able to do any troubleshooting with it at [COLOR="Red"]hard blocked: yes[/COLOR]. Never. When you reboot, the temporary test I suggested goes away, as you saw.> did not help me connect to a wireless device.... Did you see networks when you clicked the Network Manager icon? Did you click yours? Did it try? Were you asked for your encryption key?

---

### Post by b1tchacked on 2011-07-12
system         VPCYA15FG (N/A)
/0                              bus            VAIO
/0/0                            memory         1MiB BIOS
/0/6                            memory         4GiB System Memory
/0/6/0                          memory         2GiB SODIMM DDR3 800 MHz (1.2 ns)
/0/6/1                          memory         2GiB SODIMM DDR3 800 MHz (1.2 ns)
/0/c                            processor      Intel(R) Core(TM) i3 CPU       U 
/0/c/d                          memory         3MiB L3 cache
/0/c/e                          memory         128KiB L1 cache
/0/c/f                          memory         512KiB L2 cache
/0/100                          bridge         Core Processor DRAM Controller
/0/100/2                        display        Core Processor Integrated Graphic
/0/100/16                       communication  5 Series/3400 Series Chipset HECI
/0/100/1a                       bus            5 Series/3400 Series Chipset USB2
/0/100/1b                       multimedia     5 Series/3400 Series Chipset High
/0/100/1c                       bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c/0          wlan0      network        AR9285 Wireless Network Adapter (
/0/100/1c.2                     bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.2/0        eth0       network        AR8131 Gigabit Ethernet
/0/100/1d                       bus            5 Series/3400 Series Chipset USB2
/0/100/1e                       bridge         82801 Mobile PCI Bridge
/0/100/1f                       bridge         Mobile 5 Series Chipset LPC Inter
/0/100/1f.2          scsi0      storage        5 Series/3400 Series Chipset 4 po
/0/100/1f.2/0.0.0    /dev/sda   disk           320GB SAMSUNG HM321HI
/0/100/1f.2/0.0.0/1  /dev/sda1  volume         9487MiB Windows NTFS volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume         100MiB Windows NTFS volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume         288GiB Windows NTFS volume
/0/100/1f.3                     bus            5 Series/3400 Series Chipset SMBu
/0/100/1f.6                     generic        5 Series/3400 Series Chipset Ther
/0/101                          bridge         Core Processor QuickPath Architec
/0/102                          bridge         Core Processor QuickPath Architec
/0/103                          bridge         Core Processor QPI Link 0
/0/104                          bridge         Core Processor QPI Physical 0
/0/105                          bridge         Core Processor Reserved
/0/106                          bridge         Core Processor Reserved
/0/1                 scsi4      storage        
/0/1/0.0.0           /dev/sdb   disk           SCSI Disk
/0/1/0.0.1           /dev/sdc   disk           SCSI Disk

---

### Post by b1tchacked on 2011-07-12
system         VPCYA15FG (N/A)
/0                              bus            VAIO
/0/0                            memory         1MiB BIOS
/0/6                            memory         4GiB System Memory
/0/6/0                          memory         2GiB SODIMM DDR3 800 MHz (1.2 ns)
/0/6/1                          memory         2GiB SODIMM DDR3 800 MHz (1.2 ns)
/0/c                            processor      Intel(R) Core(TM) i3 CPU       U 
/0/c/d                          memory         3MiB L3 cache
/0/c/e                          memory         128KiB L1 cache
/0/c/f                          memory         512KiB L2 cache
/0/100                          bridge         Core Processor DRAM Controller
/0/100/2                        display        Core Processor Integrated Graphic
/0/100/16                       communication  5 Series/3400 Series Chipset HECI
/0/100/1a                       bus            5 Series/3400 Series Chipset USB2
/0/100/1b                       multimedia     5 Series/3400 Series Chipset High
/0/100/1c                       bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c/0          wlan0      network        AR9285 Wireless Network Adapter (
/0/100/1c.2                     bridge         5 Series/3400 Series Chipset PCI 
/0/100/1c.2/0        eth0       network        AR8131 Gigabit Ethernet
/0/100/1d                       bus            5 Series/3400 Series Chipset USB2
/0/100/1e                       bridge         82801 Mobile PCI Bridge
/0/100/1f                       bridge         Mobile 5 Series Chipset LPC Inter
/0/100/1f.2          scsi0      storage        5 Series/3400 Series Chipset 4 po
/0/100/1f.2/0.0.0    /dev/sda   disk           320GB SAMSUNG HM321HI
/0/100/1f.2/0.0.0/1  /dev/sda1  volume         9487MiB Windows NTFS volume
/0/100/1f.2/0.0.0/2  /dev/sda2  volume         100MiB Windows NTFS volume
/0/100/1f.2/0.0.0/3  /dev/sda3  volume         288GiB Windows NTFS volume
/0/100/1f.3                     bus            5 Series/3400 Series Chipset SMBu
/0/100/1f.6                     generic        5 Series/3400 Series Chipset Ther
/0/101                          bridge         Core Processor QuickPath Architec
/0/102                          bridge         Core Processor QuickPath Architec
/0/103                          bridge         Core Processor QPI Link 0
/0/104                          bridge         Core Processor QPI Physical 0
/0/105                          bridge         Core Processor Reserved
/0/106                          bridge         Core Processor Reserved
/0/1                 scsi4      storage        
/0/1/0.0.0           /dev/sdb   disk           SCSI Disk
/0/1/0.0.1           /dev/sdc   disk           SCSI Disk

The wireless connections things are all like invisible cant be clicked at... and i cant detect a wireless connection in the edit connections menu available in the menu at the desktop

---

### Post by chili555 on 2011-07-12
> /0/100/1c/0 wlan0 network AR9285 Wireless Network Adapter (If a network device has been assigned an interface, in this case wlan0, it has a working driver, in your case ath9k.

I have done my best to try to help you and you haven't answered my questions. I don't understand why you come on this forum, ask 'How to get this thing enabled' and then reject the suggestions given to you by a very experienced person.

I wish you good luck.

---

### Post by b1tchacked on 2011-07-12
I did not notice this when you first sent me that list of commands..
sudo rmmod -f acer -wmi


rmmod: invalid option -- 'm'
Usage: rmmod [-fhswvV] modulename ...
 -f (or --force) forces a module unload, and may crash your
    machine.  This requires the Forced Module Removal option
    when the kernel was compiled.
 -h (or --help) prints this help text
 -s (or --syslog) says use syslog, not stderr
 -v (or --verbose) enables more messages
 -V (or --version) prints the version code
 -w (or --wait) begins a module removal even if it is used
    and will stop new users from accessing the module (so it
    should eventually fall to zero).

This is what i got even though we used the option 'f' it is talking about something 'm'.

I am extremely sorry for acting like a n00b.

---

### Post by chili555 on 2011-07-12
> sudo rmmod -f acer -wmiPlease make sure it is not separated like acer    -wmi. It is, instead:```
sudo rmmod -f acer-wmi
```acer-wmi has no spaces in it. Then do:```
sudo rfkill unblock all
rfkill list all
```Now is it hard blocked: no? If so, does your wireless work? Can you connect? If so, we will need to change one file to make it permanent. Do not restart until we diagnose and fix this.

I will be away for about an hour but I am not forgetting you.

---

### Post by b1tchacked on 2011-07-13
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

And i can connect , lets make it permanent..
And i need some tips to understand unix and all this command set..
Help me out how do i start and learn...

---

### Post by chili555 on 2011-07-13
> And i can connect , lets make it permanent..Excellent! In a terminal, please do:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```I was starting to get worried when I didn't hear from you. I'm glad it's all sorted out now.

You might check: [http://www.amazon.com/Ubuntu-Unleashed-2011-Covering-10-10/dp/0672333449/ref=sr_1_1?ie=UTF8&qid=1310584476&sr=8-1](http://www.amazon.com/Ubuntu-Unleashed-2011-Covering-10-10/dp/0672333449/ref=sr_1_1?ie=UTF8&qid=1310584476&sr=8-1)

[http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)

[http://ubuntuhowtos.com/](http://ubuntuhowtos.com/)

---

### Post by b1tchacked on 2011-07-14
The previous one was solved perfectly and help me out whether i have proper graphic drivers installed for my pc.. by some diagnosis and help me out if it is not installed

---

