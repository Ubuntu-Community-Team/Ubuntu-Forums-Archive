---
title: "Noob: 9.04 on IBM T43 (mainly WiFi)"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by tklchoi on 2009-05-08
[FONT=Verdana]Hello everyone, I'm a new user on this forum and i need help.[/FONT]

***My situation***

I installed the new Ubuntu 9.04 earlier this week with high hopes that everything would run great because I have had success in release 8.04. When I tried to get my wireless working on the already installed network manager and other one "wicd network manager," I couldn't get my wireless to connect properly. I have been reading around spending countless hours trying to figure out how to set my laptop up with a proper configuration. (I am using a WPA key)

After a while, i decided to try and install the_** iwp2200abg**_...etc. drivers for my IBM T43 through terminal, and boy was that a bad decision :(, When i booted up my laptop, the splash screen was all messed up, all the colors were wrong and there were many lines running horizonally across my screen. So i decided to do a fresh install since it didn't take long to install the first time around.

I must have done something really bad...and btw i couldn't create directories in my file system (does this have anything to do with not being administrator? (because i am the only user on my laptop) so i must've done something wrong.

What i have trouble with: the intel drivers that need to be installed because they come in .tgz format and i dont know how to use/install that.

other problems: as some of you might know, T43 wifi antenna's need to be turned on using Fn+F5, but when i do that, either the Bluetooth light turns on and the wifi light barely blinks, or the wifi light doesnt go on at all. How do i get it so that it the wifi is always set to on mode?

some info about my T43 hardware that i said earlier might be wrong so here is my hardware copied from terminal:

```
terence@TKLC-laptop:~$ sudo lshw
[sudo] password for terence: 
tklc-laptop               
    description: Notebook
    product: 266872U
    vendor: IBM
    version: ThinkPad T43
    serial: L3YWMAF
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=5595D681-48FD-11CB-8AE4-C5C18DB1CE57
  *-core
       description: Motherboard
       product: 266872U
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: VF07368716F
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1YET62WW (1.27 ) (05/18/2006)
          size: 144KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 2.00GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.13.8
          slot: None
          size: 2GHz
          capacity: 2GHz
          width: 32 bits
          clock: 533MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 915GM/PM Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 11
                serial: 00:16:41:a7:fa:5c
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751m-v3.46a ip=192.168.2.10 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 8d
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00d0c0b0-b00d0c0af
           *-network
                description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:0b:02.0
                logical name: eth1
                version: 05
                serial: 00:16:6f:ac:8f:09
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: FUJITSU MHV2080A
                vendor: Fujitsu
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0084
                serial: NT20T68296T4
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=cccdcccd
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 229a8369-f989-4e14-8a0a-1280e8778e75
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-05-08 19:52:32 filesystem=ext3 modified=2009-05-08 20:52:31 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-08 19:53:32 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3153MiB
                   capacity: 3153MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3153MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-822S
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.61
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:9e:54:ed:36:d0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
terence@TKLC-laptop:~$ 

```As you can probably tell by now i am a [COLOR=Red]*[SIZE=3]**REAL BIG NOOB**[/SIZE]*[/COLOR] :) so can someone please tell me how to properly set up my T43. Links to guides? How-To's? or just explain in this thread. I really don't want to screw up this time...

ugh...WHY DID I PICK 9.04?! :sad:


Thank you in advance!

---

### Post by chili555 on 2009-05-08
First of all, the ipw2200 drivers, which are installed by default work very well. You shouldn't need a tar.gz file.

On my T40, which also uses the ipw2200 driver, the FN+F5 key combination toggles bluetooth only, wireless only or both. If the wireless LED is flickering, I believe it's on. Does the terminal command:```
iwconfig
```show a wireless interface, eth1 perhaps? If so, your almost done!

Here is a  link that might help. [http://www.thinkwiki.org/wiki/Category:T43](http://www.thinkwiki.org/wiki/Category:T43)

Post back if you get stuck.

---

### Post by tklchoi on 2009-05-08
ok, so i ran the command and here is what i got:

next to eth1 it says "unnassociated"

```
terence@TKLC-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:"BELL126"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

### Post by t0mppa on 2009-05-08
A few things unrelated to getting your wireless up and running - chili555 knows his way through that better than I.

1) Getting UNCLAIMED messages in the lshw means that the device does not have drivers associated with it. Basically this means that there might be some workaround being applied, but it's not a very stable state of existence. And this is especially nasty, since one of the devices falling to this category is your graphics card, which is probably what caused the issues you described after installing that driver by hand. ATI Catalyst 9.4 dropped support of older cards though and the older versions of Catalyst don't work in 9.04, so I suggest a trip to the Multimedia & Video forums to solve this one.

2) Ubuntu conveniently protects itself from you doing something silly without realising it by having a super user account that you need to activate first to do administrative duties. That's why you can't create directories or edit files in places where doing that could cause trouble without first logging in to the super user account.

You as the first user are automatically set up as a member of the super user group though, so you can login as root (equivalent of administrator) with your own password, when required. To accomplish that on the terminal, just write sudo in front of the command you're executing. If you were trying to create the directories with the File Browser, you can get super user access to it by opening a terminal and running 'gksudo nautilus &'.

3) Having the wireless work and having the wireless indicator led work are two different things, you'll most likely have to set them up separately.

---

### Post by tklchoi on 2009-05-09
ok so far i only managed to figure out my wireless light issue, it is now up and running fine, it is just that it is hard to ketch the wifi light when it is on because there is a very long pause.

I will deal with my ATI X300 driver issue later. Right now I am still searching a soloution to my main problem.

---

### Post by chili555 on 2009-05-09
Your *iwconfig* shows that your wireless interface is up and running and ready to connect. You should be able to click on the Network Manager icon and see your wireless network and connect.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by tklchoi on 2009-05-09
There is trouble getting my WPA password to confirm, i think it is timing out, and also something related to network manager asks for permission to my WPA keyring. i dont know what that is. any ideas?

---

### Post by mudguts on 2009-05-09
On my T40, 9.04 installed the Wi-Fi easily enough.  In fact, I didn't have to do anything.  It's almost like the gods of linux installed it themselves.

---

### Post by tklchoi on 2009-05-09
anything else i could try? because nothing seems to be working for me.

---

### Post by chili555 on 2009-05-10
NetworkManager stores any encryption keys in the gnome-keyring manager. If your are prompted to enter the keyring password, it is, unless you have established a different password (doubtful), your user password. Please accept when asked to access your keyring.

When you are trying to enter your WPA password, do you see options for WPA-Personal or WPA-Enterprise? Any other options? Are you sure you are entering the right password in the right field?

What, exactly, have you tried that is not working?

---

### Post by tklchoi on 2009-05-10
i am using WPA Personal, and for some reason now it says my device is not managed.

---

### Post by chili555 on 2009-05-10
Please open a terminal and do:```
sudo gedit /etc/network/interfaces
```Delete anything in there ***except***:```
auto lo
iface lo inet loopback
```Proofread, save and close gedit. Reboot. Now is your wireless interface 'unmanaged'?

---

### Post by tklchoi on 2009-05-10
thanks Chili, device is now managed.

Now after i select my own connection how do i set it up so that i connect to it every time i am not connected through ethernet? WPA: personal

---

### Post by chili555 on 2009-05-10
Right-click on Network Manager icon, click on 'Edit Connections' which brings up the network connections having various options to control.

Choose eth1, your wireless interface. Click on 'Edit.' When the box pops up, make sure the box for 'connect automatically' is checked. Save and close everything.

---

### Post by tklchoi on 2009-05-10
when i edit my eth1 it asks if i want to allow nm-connection-editor to access my password for my SSID in the default keyring...?

---

### Post by chili555 on 2009-05-10
Yes, indeedy. I don't think you can get there any other way.

---

### Post by tklchoi on 2009-05-10
GOOD NEWS!

i fixed the problem myself by using a belkin router rather than the one provided by my ISP. I entered the WEP and it worked!

thanks for your help! :)

---

### Post by chili555 on 2009-05-10
Great! Glad it's working for you. Enjoy your Ubuntu experience.

---

