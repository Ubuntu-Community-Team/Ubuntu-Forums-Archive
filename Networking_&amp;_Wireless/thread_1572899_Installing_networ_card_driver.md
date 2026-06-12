---
title: "Installing networ card driver"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by iz10000-2 on 2010-09-11
I downloaded/installed Ubuntu 10.10 but the network card not showing in ifconfig. The network card is built-in the ASUS motherboard P4S800-MX. I went to the ASUS website [http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us) and select Motherboard, Socket478 and P4S800-MX. Then I select OS Linux and downloaded the LAN driver. I am new to Linux. Does anyone know if this driver can be used and how to get it installed if yes? Thanks.
 
Found the buit-in NIC was disabled in BIOS. It shows up in ifconfig after enabled.

---

### Post by MaindotC on 2010-09-12
There are two drivers to d/l so you'll need to determine which card you have.  For future reference, please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) as it lists several commands you should know for determining this information and helping you set up your wireless card.

Post the output of:```
lspci | grep Network
lshw -C network

```

Edit:  I finally downloaded the huge driver file from their site.  Amazing how you have to specify you want a file for a Linux o/s but they send you a file that has a driver for every possible operating system.  Once you download the zip file, extract it and go to the Linux directory.  There are directions there for installing the file.  Please follow them.

---

### Post by iz10000-2 on 2010-09-12
After issue the following, there is nothing listed (there is no issue to install Windows on this PC)
 
lspci | grep Network
lshw -C network
 
Downloaded the newer one from the web but not quit clear how to install it. e.g. which the directory in Ubuntu 10.10 exactly the driver should be copied to.

---

### Post by MaindotC on 2010-09-12
> **iz10000-2 said:**
> After issue the following, there is nothing listed (there is no issue to install Windows on this PC)
 
lspci | grep Network
lshw -C networkJust post the output of lscpi and lshw -C network.  If you do not get any output then you issued the command improperly.

> Downloaded the newer one from the web but not quit clear how to install it. e.g. which the directory in Ubuntu 10.10 exactly the driver should be copied to.


> **strAlan said:**
> Once you download the zip file, extract it and go to the Linux directory.  There are directions there for installing the file.  Please follow them.

---

### Post by iz10000-2 on 2010-09-12
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL] 
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL] lspci | grep Network
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL] lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL] lshw
WARNING: you should run this program as super-user.
user-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1981MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: [EMAIL="cpu@0"]cpu@0[/EMAIL]
          version: 15.2.9
          size: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: [EMAIL="pci@0000:00:00.0"]pci@0000:00:00.0[/EMAIL]
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: [EMAIL="pci@0000:00:01.0"]pci@0000:00:01.0[/EMAIL]
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:e7800000-e7ffffff memory:f0000000-febfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: [EMAIL="pci@0000:01:00.0"]pci@0000:01:00.0[/EMAIL]
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:e7800000-e781ffff ioport:d800(size=128)
        *-isa
             description: ISA bridge
             product: SiS963 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: [EMAIL="pci@0000:00:02.0"]pci@0000:00:02.0[/EMAIL]
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: [EMAIL="pci@0000:00:02.1"]pci@0000:00:02.1[/EMAIL]
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:e600(size=32)
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: [EMAIL="pci@0000:00:02.5"]pci@0000:00:02.5[/EMAIL]
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:a400(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: [EMAIL="pci@0000:00:02.7"]pci@0000:00:02.7[/EMAIL]
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:9400(size=256) ioport:9000(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: [EMAIL="pci@0000:00:03.0"]pci@0000:00:03.0[/EMAIL]
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:9 memory:e7000000-e7000fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: [EMAIL="pci@0000:00:03.1"]pci@0000:00:03.1[/EMAIL]
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:e6800000-e6800fff
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: [EMAIL="pci@0000:00:03.3"]pci@0000:00:03.3[/EMAIL]
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:e6000000-e6000fff
[EMAIL="user@user-desktop:~$"]user@user-desktop:~$[/EMAIL]

---

### Post by iz10000-2 on 2010-09-12
Sorry, just found the onboard nic was disabled in bios.

---

### Post by MaindotC on 2010-09-12
Please mark the thread as solved and edit your 1st post to include an update so users don't have to read the entire thread to figure out what happened.

---

### Post by KositaQ on 2010-09-12
Well, here's mine and I am having the same problem on a Dell Inspiron 1525 and Ubuntu 10.4, wireless card should be the Marvell Pro/Wireless Belkin or something or other...It worked like a charm when I had Windows, but now Ubuntu cannot even detect the correct drivers....I don't get it but then again I do not have a clue either, but here we go:  :KS

This is the output for the first command:

~$ lspci | grep Network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

This is the output for the second command:

~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=XXX.XXX.X.X latency=0 multicast=yes
       resources: irq:27 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:fe7fe000-fe7fffff

---

### Post by MaindotC on 2010-09-12
Please post shell output in ```
 tags.[code]It should look like this
```

> **KositaQ said:**
> but now Ubuntu cannot even detect the correct drivers.

Intel typically provides support and drivers for their wireless cards.  You can find the support page for this card at [http://www.intel.com/p/en_US/support/highlights/wireless/4965agn](http://www.intel.com/p/en_US/support/highlights/wireless/4965agn)
```

~$ lspci | grep Network
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

This is the output for the second command:

~$ lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:5a:92:8d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [SIZE="6"]driver=iwlagn[/SIZE] latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:fe7fe000-fe7fffff
```

As you can see, the driver is already installed.  There is a note on the [developer's page that the driver is included in later kernels](http://www.intellinuxwireless.org/) so you should not have to install anything anyway.

The network device is disabled so you probably have a killswitch to turn it on or off, or it may be disabled in the BIOS.

---

### Post by chili555 on 2010-09-12
> *-network [COLOR="Red"]DISABLED[/COLOR]
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
This often means that the wireless switch is 'off.' What does this tell us?```
rfkill list all
```

---

### Post by KositaQ on 2010-09-12
Thank you all for the prompt reply....This is the output for the latest command from the latest post...

[HTML]~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

Now how do I turn wireless on? I checked the BIOS and it is enabled...what gives?

---

### Post by KositaQ on 2010-09-12
> **chili555 said:**
> This often means that the wireless switch is 'off.' What does this tell us?```
rfkill list all
```
Thank you all for the prompt reply....This is the output for the latest command from the latest post...

[HTML]~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
[/HTML]

Now how do I turn wireless on? I checked the BIOS and it is enabled...what gives?

---

### Post by MaindotC on 2010-09-12
It tells you on page 6 of the [manual](http://support.dell.com/support/edocs/systems/ins1525/en/SG/Y465HA01MR.pdf).

---

### Post by KositaQ on 2010-09-12
> **strAlan said:**
> It tells you on page 6 of the [manual](http://support.dell.com/support/edocs/systems/ins1525/en/SG/Y465HA01MR.pdf).


LOL!!! You are hilarious.. i really like your sarcasm.  :D

That is obvious, I have the switch on already, despite all of that it still cannot conenct...but I really do appreciate your patience and the prompt reply as well.  It does not connect, but I found another post somewhere on the Internet and I am trying it, thanks anyway  XD

 -> [http://forums.fedoraforum.org/showthread.php?t=207482](http://forums.fedoraforum.org/showthread.php?t=207482)

---

### Post by chili555 on 2010-09-12
Please try:```
sudo rmmod -f dell-laptop
```Now does your wireless come to life? If so, we can make this permanent.

---

### Post by KositaQ on 2010-09-12
> **chili555 said:**
> Please try:```
sudo rmmod -f dell-laptop
```Now does your wireless come to life? If so, we can make this permanent.

How? I even restarted the laptop, still no dice...I am thinking about reinstalling Ubuntu, 'cause I even tried to see if I can change the specs using Command Control....I just ran out of options.  Will have to stay wired, just like in 'The Matrix'  XD

---

### Post by MaindotC on 2010-09-12
Please don't re-install - that is not a valid solution and if you're going to use Ubuntu you need to learn how to troubleshoot these things without just re-imaging (that's typically how Windows machines are "fixed").  I know this is difficult and if manufacturers would provide a little more support for wireless devices then we wouldn't have to try and reverse engineer everything.  You just need the wireless card working, so I don't see any reason to re-install the whole operating system.  Besides, how would that solve the problem?

rfkill says the devices are "hard blocked".  According to the [rfkill documentation]("http://www.mjmwired.net/kernel/Documentation/rfkill.txt") it says:> - hard block: read-only radio block that cannot be overriden by software  This indicates that the wireless card is shut off from a hardware perspective which is why I told you how to enable it via the killswitch.

---

### Post by chili555 on 2010-09-13
Please make sure you locate the wireless switch on your laptop and that it is in the on position, not momentary. Open a terminal and do:```
sudo rmmod -f dell-laptop
rfkill list all
```Is the result changed? Is wireless still hard-blocked?

When you rebooted, the dell-laptop module reloaded, so please wait for further instructions or else repeat the rmmod step if you must reboot.

---

