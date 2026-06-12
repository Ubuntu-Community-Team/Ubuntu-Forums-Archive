---
title: "No wireless"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by strauzen on 2009-10-18
I'm sorry for I know this has been said many times, this is my first time trying linux and I've got no wireless conection, my terminal knowledge is less than minimum and I haven't been able to solve the problems with the threads I've read, can anbody help?

---

### Post by coffeeaddict22 on 2009-10-18
Hi,
Welcome to Ubuntu!
We all learnt once (and are still learning).  Failure is not in being ignorant, it's in not trying to learn.

Anyway.  The terminal is nice because the output is a whole lot more explicit than a picture.  Find one (Applications/Accessories/Terminal); I have it copied to the bar at the top of the screen.  If you right-click that's one of the options.
In it, type in ```
lspci
``` and have a look through the output.  Down the bottom usually there's a line that says something like```
Network controller: 
``` with some stuff after it; that's the card you want to get working.
Next, type in ```
lshw -C network
```
That'll give you a whole lot more info.  Don't worry about the warning about being superuser; you can run it with sudo in front (sudo lshw -C network) but the extra info isn't worth it at this point.
In a terminal, there's an extensive help system.  If you want to know more about any command, type "man xxxx" where xxxx is the command you're interested in.  The information will be enough to keep you busy, as a rule.  If you don't know exactly what command to use, try "apropos xxxx", eg apropos wireless, and it'll return a list of possible commands.

Post back the output of the above commands and we'll go from there.

---

### Post by strauzen on 2009-10-18
thanks for the help, lets see, theese are the results I got after typing the commands you told me:

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:13:c5:e4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:1b:fc:45:ab:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.5 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8e:89:5d:c4:56:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

As you seem to know a bunch abouut these If I may ask, I tried to download some drivers for my graphic card, a Gforce Go 7300, and when I pushed the download button from the nvidia web page (for linux 32bits) a blanck window openned with a lot of text and it did nothing else. I think it didn't install anything and I don't really know how to do it now...

---

### Post by coffeeaddict22 on 2009-10-18
You can always ask.  I don't know much more than you.

The easiest way to enable restricted video drivers in Ubuntu is System/Hardware Drivers, and enable them there.  If you're there for the video, Check your wireless isn't turned off there either.

Back to the wireless.  To quote your post: 

vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 02
...

The problem is there isn't a physical id, and wmaster0 is usually (but not always) a bad sign meaning driver troubles.  The system is seeing your card(otherwise it wouldn't come up in lspci), but not using it.

Googling around, enabling linux-backports-modules might be an idea.  Open Synaptic, don't get too distracted with all the stuff you can get, and search for linux-backports-modules; install it and see if that works.

---

### Post by chili555 on 2009-10-19
With all due respect to my esteemed colleague coffeeaddict22, wmaster0 is a dummy interface that is set up for some reason or another. It is not, that I have ever seen, a sign of a driver problem. I have seen hundreds of lshw listings, many for 3945ABG, which I am using right now. Healthy ones always show wmaster0, even though the actual operating interface is wlan0. Verify with:```
iwconfig wlan0
```lshw will either show an interface, if it has been associated with a driver, or no interface and the heading UNCLAIMED if no driver has attached.

Your 3945ABG looks healthy and ready to connect. However, Network Manager will not allow a wireless connection if you have a wired connection, which you do:> driver=8139too driverversion=0.9.28 ip=192.168.1.5Please see here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)  Especially this part:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them;Please unplug the ethernet cable and, just to be safe, reboot and then click the Network Manager icon. Do you see your wireless network? Can you connect?

---

### Post by strauzen on 2009-10-19
Ok in hardware drivers I have absolutly nothing, and without underestimating coffeadict dvise before installing or searching for anything I'll try other solutions.

Ive connected and disconnected the wired conection and I saw my neighbour wifi (im standing right next to mine), but I was unable to find mine. A friend of mine came by with his laptop and he didn't have any problems to find and connect to my wifi with the same version (and same instalation cd) as my ubuntu so I don't understand why I can see 1 wireless conection and why it works now and it didn't before

I leave you here what I got from iwconfig wlan 0 as I'm unable to understand most of it:

iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and now that I can see some wifi (my neighbours) Ill leave you the lshw command results too If it can help:

lshw
WARNING: you should run this program as super-user.
wintermute                
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2013MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 996MHz
          capacity: 996MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: G72M [Quadro NVS 110M/GeForce Go 7300]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1b:77:13:c5:e4
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:06:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:06:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ricoh-mmc latency=0 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:06:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@0000:06:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:06:07.0
                logical name: eth0
                version: 10
                serial: 00:1b:fc:45:ab:22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.5 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:c5:4a:80:76:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

thanks for you help.

---

### Post by chili555 on 2009-10-19
Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist wlan0 scan
```Do you now see your own network? If so, we can make this permanent.

---

### Post by coffeeaddict22 on 2009-10-20
Hi Chili,
I'm no driver guru, but I'm reasonably certain about wmaster.  Have a look at this page: 
[http://linuxwireless.org/en/developers/Documentation/mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211")

Coffee.

---

### Post by chili555 on 2009-10-20
> **coffeeaddict22 said:**
> Hi Chili,
I'm no driver guru, but I'm reasonably certain about wmaster.  Have a look at this page: 
[http://linuxwireless.org/en/developers/Documentation/mac80211]("http://linuxwireless.org/en/developers/Documentation/mac80211")

Coffee.It says:> This information is no longer relevant as – since kernel version 2.6.32 – the master interface is no longer created.We will presumably see kernel 2.6.32 in Kaola. I, for one, am still stuck in the ancient, crusty old Jaunty:```
chili@LAPTOP60:~$ uname -r
2.6.28-15-generic
```And my *lshw* clearly shows wmaster0 on a perfectly operating 3945ABG with which I am sending this reply:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
---snip---I will be glad to have wmaster0 go away; it's confusing.

---

### Post by t0mppa on 2009-10-20
> **strauzen said:**
> Ive connected and disconnected the wired conection and I saw my neighbour wifi (im standing right next to mine), but I was unable to find mine.

If chili555's advice above (post #7) doesn't help, then one possibility is a channel mix-up. To test for that, you should check [LIST=1]
[*]what channel your AP (Access Point, i.e., wireless router) is using by connecting to it with another computer and checking the connection details or by looking at the router configuration
[*]if it's outside the range of channels your system is checking by running **iwlist channel** from terminal to get a list of channels that are being checked during scans
[/LIST]

The way it goes is that in US you can only use channels 1-11, in Europe also 12 & 13 are available and in Japan there's channel 14 as well. And for some reason Ubuntu (or the mac80211 stack to be specific) doesn't always correctly detect your location, which means that if your AP is using for instance channel 13 and your system is only checking the first 11 channels, then it obviously isn't going to find your network, no matter what you do with the drivers.

As for the wmaster0 debate, I agree with chili555. It not showing up on any but leading edge kernels with drivers using the mac80211 stack would be a sign of driver trouble.

---

### Post by strauzen on 2009-10-20
ok t0mmpa im sorry but I don't understand what you ask me to do, I'm a total noob.

Chili I tried you solution and it did detect my wifi, but another problem came up, I'm sure I got the password and type of password correct but it seems it didn't recognice it, it didn't stop asking for it after triying to connect.

---

### Post by t0mppa on 2009-10-21
Well, the channels are sets of frequencies used by the wireless routers to broadcast/receive traffic from their network on. There's a bunch of them, so that if one has too much traffic already thanks to your neighbours, you can swap to another.

Like I said earlier though, it was only relevant in case disabling the hw scan didn't work, which it did, thus don't worry about it. Just thought I'd mention it, since I stumbled upon the thread, it could've been an issue and it also is not something people usually think of. I believe no routers use those high end channels by default though, so it's more of a problem for people who switch from another OS and have configured their router to use one of the less common frequencies, but have then forgotten they did so.

Anyway, didn't mean to derail the conversation, so I'll leave you to the helpful hands of chili555, as he knows much more about the Intel drivers (and likely most other things Linux) than me.

---

### Post by strauzen on 2009-10-21
Thanks for the explanation ^^

---

### Post by chili555 on 2009-10-22
> I'm sure I got the password and type of password correct but it seems it didn't recognice it, it didn't stop asking for it after triying to connect.Let's troubleshoot. Is it a WPA password or WEP? If it's WEP, how many characters is it?

---

### Post by strauzen on 2009-10-22
It's WEP, the lengh I think (im not at home) its 40/128k could it be?

I know it had two numbers, even so when I get home I'll look at it, thanks.

---

### Post by strauzen on 2009-11-04
It is the password I said it was, and the same as before, wireless conection asks for it once and again even if I put it right, I have no idea of what to do

---

### Post by chili555 on 2009-11-04
How many characters is it? Numbers and letters? Where are you putting it in the Network Manager icon?

---

### Post by strauzen on 2009-11-04
it's 10 characters long, numbers and letters some of them capitals, when I connect to the network a window appears asking for it, after I put it it tries again to connect (I can see the connection turning arount where the wifi is signalled, one of the circles green the other one gray) and it asks for it again, and that goes on and on and on

---

