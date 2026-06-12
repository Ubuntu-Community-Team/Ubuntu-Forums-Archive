---
title: "Connecting to WIFI. Can't enable wireless hardware. UBUNTU 10.10"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by gchdevon on 2010-11-07
[B]Connecting to WIFI. Can't enable wireless hardware. UBUNTU 10.10

I did also post this query in absolute beginner because that is what i am with UBuntu. Sorry if this is against the protocols but I did not have any responses there although it was only a few hours ago. I'm not complaining just that it would have been good to be able to get it sorted today as I will not be able to get back to it for several days.
[/B] 			
 			However I  did try and research on this forum and I soon reached the limits of my  understanding.

My wireless card is Intel PRO/ Wireless 3945 ABG [golan].

According to the info on this forum it should work "out of the box".

However following instructions on UBUNTU documentation, I get to a box that says "no wireless extensions".

The documentation then says I must configure my wireless card. At this  point I lose the plot and seem to be directed to a number of different  pages asking me to do things I don't understand.

I am able to connect to internet with cable.

As part of trying to work this out I installed an application called  WIFI radar. It cannot detect anything, unsurprisingly if the wireless  card is not enabled.

If somebody does kindly respond I hope they don't mind if I have to clarify some of the terms they might use.

Thanks.
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=10085023") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=10085023")

---

### Post by Karakh on 2010-11-07
Can you post the output of the "ifconfig" and the "iwconfig" commands?

EDIT: And this is probably a silly question, but are you sure that the card is "turned on". Most laptops have a button/keyboard-combo to enable/disable the wifi card.

---

### Post by gchdevon on 2010-11-08
This is the result of putting ifconfig in TERMINAL. 


will@will-EasyNote-SB85:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:cc:17:78  
          inet addr:192.168.0.144  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fecc:1778/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10654743 (10.6 MB)  TX bytes:1674588 (1.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:44:1c:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

will@will-EasyNote-SB85:~$ 

This is result of iwconfig

 will@will-EasyNote-SB85:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
      

There is a wifi button. not a silly question, however it is on and comes on by default on start up.

---

### Post by uncaspi on 2010-11-08
Are you sure your radio is turned on? Try rfkill unblock wifi

---

### Post by gordintoronto on 2010-11-09
It wouldn't hurt if you told people what computer you have, brand and exact model.

Also: the command lspci should list your wireless adapter and give an exact identification.

---

### Post by gchdevon on 2010-11-10
Thank you for responding.
My computer has a button on the front that is the wifi button. It is on when it is lit. As far as I can tell that is all  I *ever had to do* when I had the previous operating system on it.

My computer Is a Packard Bell easynote sb85. I ran rfkill nothing happened, nothing changed.

I ran lspci, the network controller indicated is:
 Intel PRO/ Wireless 3945 ABG [golan]

---

### Post by gordintoronto on 2010-11-11
Could you provide more detail about this:
"However following instructions on UBUNTU documentation, I get to a box that says "no wireless extensions"."

Do you have a network manager icon at the top of your screen, near the right? Can you right-click on it and select "edit connections"?

---

### Post by gchdevon on 2010-11-11
> **gordintoronto said:**
> Could you provide more detail about this:
"However following instructions on UBUNTU documentation, I get to a box that says "no wireless extensions"."

Do you have a network manager icon at the top of your screen, near the right? Can you right-click on it and select "edit connections"?
I looked at the internet and this forum to try and get a solution to my issue. Basicly I ended up with what is in post #3. above. lwconfig > no wireless extensions.

I do have the network manager. I am currently connected by cable.

Going to edit connections brings up auto eth0 for wired connections. Wired brings up nothing. I do not have WIFI at home but when I try and use the laptop elsewhere it detects no wireless networks although I know they are there.

---

### Post by bkratz on 2010-11-11
In post 3 it says


This is result of iwconfig

[COLOR="Red"]will@will-EasyNote-SB85:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11abg ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm 
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
[/COLOR]

The comment about no wireless extensions is referring to your local loopback and ethernet connection.  That is why they don't have outputs. The Wlan0 is your wireless which really looks ok. Sometimes the light doesn't doesn't respond the way you are used to.  I believe it is worth disconnecting the wired connection and going to the terminal (applications>>accessories>>Terminal)  and trying

sudo iwlist scan

and see if you see networks available. I would try at home first and see if someone else has a network you can "see".

---

### Post by gchdevon on 2010-11-11
Thanks for responding.
There are a number of neighbours security enabled wifi networks that the laptop used to detect. 
I did "sudo iwlist " wlan0 came up with no results.

---

### Post by uncaspi on 2010-11-11
Will you please post the content of sudo /sbin/lshw -C network
to see which driver is assosiated with your card if any.

---

### Post by gchdevon on 2010-11-11
will@will-EasyNote-SB85:~$ sudo /sbin/lshw -C network
[sudo] password for will: 
sudo: /sbin/lshw: command not found
will@will-EasyNote-SB85:~$ sudo /sbin/lshw -c network
sudo: /sbin/lshw: command not found
will@will-EasyNote-SB85:~$

---

### Post by uncaspi on 2010-11-11
Try sudo lshw -C netwwork or type locate lshw to see the path

---

### Post by gchdevon on 2010-11-11
Not sure what this all means but here is the print out of both commands:

will@will-EasyNote-SB85:~$ sudo lshw -C network
[sudo] password for will: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:44:1c:d4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:49 memory:f4100000-f4100fff
  *-network
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:cc:17:78
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.162 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:f4000000-f4003fff ioport:5000(size=256)

will@will-EasyNote-SB85:~$ locate lshw
/usr/bin/lshw
/usr/share/app-install/desktop/lshw-gtk.desktop
/usr/share/app-install/icons/lshw-gtk.xpm
/usr/share/doc/lshw
/usr/share/doc/lshw/changelog.Debian.gz
/usr/share/doc/lshw/copyright
/usr/share/man/man1/lshw.1.gz
/var/lib/dpkg/info/lshw.list
/var/lib/dpkg/info/lshw.md5sums
will@will-EasyNote-SB85:~$

---

### Post by grahammechanical on 2010-11-11
There is a wireless  trouble shooting guide. It is at

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Note the command rfkill list       Look for Soft blocked: yes   or hard blocked: yes. This will tell you if the wireless device is switched off either by software or in hardware. 

Regards

---

### Post by gchdevon on 2010-11-12
Thanks grahammechanical. Here is printout of what you suggested also additional command that seemed relevant in the guide. I think I came accross that page previously when I was searching for a solution. Problem is I don't know what it all means.

will@will-EasyNote-SB85:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
will@will-EasyNote-SB85:~$ sudo iwconfig
[sudo] password for will: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
will@will-EasyNote-SB85:~$

---

### Post by uncaspi on 2010-11-12
Will you please posts the content of dmesg

---

### Post by gchdevon on 2010-11-12
This is a long one.


[    0.284530] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.284536] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.284543] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.284549] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.284556] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.284571] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.284586] system 00:07: [io  0x0680-0x069f] has been reserved
[    0.284592] system 00:07: [io  0x0800-0x080f] has been reserved
[    0.284598] system 00:07: [io  0x1000-0x107f] has been reserved
[    0.284604] system 00:07: [io  0x1180-0x11bf] has been reserved
[    0.284610] system 00:07: [io  0x1640-0x164f] has been reserved
[    0.284616] system 00:07: [io  0xfe00] has been reserved
[    0.322427] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80000000-0x801fffff 64bit pref]
[    0.322436] pci 0000:00:1c.2: BAR 14: assigned [mem 0x80200000-0x803fffff]
[    0.322443] pci 0000:00:1c.2: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.322450] pci 0000:00:1c.3: BAR 15: assigned [mem 0x80600000-0x807fffff 64bit pref]
[    0.322457] pci 0000:00:1c.5: BAR 15: assigned [mem 0x80800000-0x809fffff 64bit pref]
[    0.322465] pci 0000:00:1c.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.322472] pci 0000:00:1c.2: BAR 13: assigned [io  0x7000-0x7fff]
[    0.322478] pci 0000:00:1f.3: BAR 0: assigned [mem 0x80a00000-0x80a000ff]
[    0.322489] pci 0000:00:1f.3: BAR 0: set to [mem 0x80a00000-0x80a000ff] (PCI address [0x80a00000-0x80a000ff]
[    0.322497] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.322503] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.322509] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.322518] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.322526] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.322536] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.322543] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.322553] pci 0000:00:1c.0:   bridge window [mem 0xf4100000-0xf41fffff]
[    0.322562] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff 64bit pref]
[    0.322574] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.322581] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.322591] pci 0000:00:1c.1:   bridge window [mem 0xf2000000-0xf3ffffff]
[    0.322600] pci 0000:00:1c.1:   bridge window [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.322612] pci 0000:00:1c.2: PCI bridge to [bus 06-06]
[    0.322619] pci 0000:00:1c.2:   bridge window [io  0x7000-0x7fff]
[    0.322629] pci 0000:00:1c.2:   bridge window [mem 0x80200000-0x803fffff]
[    0.322638] pci 0000:00:1c.2:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.322650] pci 0000:00:1c.3: PCI bridge to [bus 07-07]
[    0.322657] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.322667] pci 0000:00:1c.3:   bridge window [mem 0xf4200000-0xf42fffff]
[    0.322676] pci 0000:00:1c.3:   bridge window [mem 0x80600000-0x807fffff 64bit pref]
[    0.322688] pci 0000:00:1c.5: PCI bridge to [bus 08-08]
[    0.322695] pci 0000:00:1c.5:   bridge window [io  0x5000-0x5fff]
[    0.322705] pci 0000:00:1c.5:   bridge window [mem 0xf4000000-0xf40fffff]
[    0.322714] pci 0000:00:1c.5:   bridge window [mem 0x80800000-0x809fffff 64bit pref]
[    0.322727] pci 0000:00:1e.0: PCI bridge to [bus 09-09]
[    0.322731] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.322742] pci 0000:00:1e.0:   bridge window [mem 0xf4300000-0xf43fffff]
[    0.322749] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.322777]   alloc irq_desc for 16 on node -1
[    0.322782]   alloc kstat_irqs on node -1
[    0.322794] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.322803] pci 0000:00:01.0: setting latency timer to 64
[    0.322821]   alloc irq_desc for 17 on node -1
[    0.322825]   alloc kstat_irqs on node -1
[    0.322834] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.322842] pci 0000:00:1c.0: setting latency timer to 64
[    0.322860] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.322869] pci 0000:00:1c.1: setting latency timer to 64
[    0.322887]   alloc irq_desc for 18 on node -1
[    0.322891]   alloc kstat_irqs on node -1
[    0.322899] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.322907] pci 0000:00:1c.2: setting latency timer to 64
[    0.322926]   alloc irq_desc for 19 on node -1
[    0.322930]   alloc kstat_irqs on node -1
[    0.322937] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.322946] pci 0000:00:1c.3: setting latency timer to 64
[    0.322965] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.322974] pci 0000:00:1c.5: setting latency timer to 64
[    0.322990] pci 0000:00:1e.0: setting latency timer to 64
[    0.323000] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.323005] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.323011] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.323016] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.323022] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.323027] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.323033] pci_bus 0000:02: resource 1 [mem 0xf4100000-0xf41fffff]
[    0.323039] pci_bus 0000:02: resource 2 [mem 0x80000000-0x801fffff 64bit pref]
[    0.323044] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.323050] pci_bus 0000:04: resource 1 [mem 0xf2000000-0xf3ffffff]
[    0.323055] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.323061] pci_bus 0000:06: resource 0 [io  0x7000-0x7fff]
[    0.323066] pci_bus 0000:06: resource 1 [mem 0x80200000-0x803fffff]
[    0.323071] pci_bus 0000:06: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.323077] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.323082] pci_bus 0000:07: resource 1 [mem 0xf4200000-0xf42fffff]
[    0.323087] pci_bus 0000:07: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.323092] pci_bus 0000:08: resource 0 [io  0x5000-0x5fff]
[    0.323097] pci_bus 0000:08: resource 1 [mem 0xf4000000-0xf40fffff]
[    0.323103] pci_bus 0000:08: resource 2 [mem 0x80800000-0x809fffff 64bit pref]
[    0.323108] pci_bus 0000:09: resource 1 [mem 0xf4300000-0xf43fffff]
[    0.323114] pci_bus 0000:09: resource 4 [io  0x0000-0xffff]
[    0.323119] pci_bus 0000:09: resource 5 [mem 0x00000000-0xffffffff]
[    0.323194] NET: Registered protocol family 2
[    0.323328] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.323841] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.324546] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.324856] TCP: Hash tables configured (established 131072 bind 65536)
[    0.324860] TCP reno registered
[    0.324867] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.324883] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.325044] NET: Registered protocol family 1
[    0.325337] pci 0000:01:00.0: Boot video device
[    0.325380] PCI: CLS 64 bytes, default 64
[    0.325422] Simple Boot Flag at 0x36 set to 0x1
[    0.325792] cpufreq-nforce2: No nForce2 chipset.
[    0.325854] Scanning for low memory corruption every 60 seconds
[    0.326061] audit: initializing netlink socket (disabled)
[    0.326079] type=2000 audit(1289568721.320:1): initialized
[    0.348230] highmem bounce pool size: 64 pages
[    0.348241] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.351411] VFS: Disk quotas dquot_6.5.2
[    0.351544] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.352815] fuse init (API version 7.14)
[    0.353006] msgmni has been set to 1683
[    0.358196] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.358203] io scheduler noop registered
[    0.358207] io scheduler deadline registered
[    0.358235] io scheduler cfq registered (default)
[    0.358500] pcieport 0000:00:01.0: setting latency timer to 64
[    0.358552]   alloc irq_desc for 40 on node -1
[    0.358557]   alloc kstat_irqs on node -1
[    0.358573] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.358723] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.358793]   alloc irq_desc for 41 on node -1
[    0.358797]   alloc kstat_irqs on node -1
[    0.358813] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.358987] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.359058]   alloc irq_desc for 42 on node -1
[    0.359062]   alloc kstat_irqs on node -1
[    0.359077] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.359258] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.359327]   alloc irq_desc for 43 on node -1
[    0.359331]   alloc kstat_irqs on node -1
[    0.359346] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.359526] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.359596]   alloc irq_desc for 44 on node -1
[    0.359600]   alloc kstat_irqs on node -1
[    0.359615] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    0.359792] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.359861]   alloc irq_desc for 45 on node -1
[    0.359865]   alloc kstat_irqs on node -1
[    0.359890] pcieport 0000:00:1c.5: irq 45 for MSI/MSI-X
[    0.360120] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.360461] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.360676] intel_idle: MWAIT substates: 0x22220
[    0.360681] intel_idle: does not run on family 6 model 15
[    0.360899] ACPI: AC Adapter [ACAD] (off-line)
[    0.361079] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.363533] ACPI: Lid Switch [LID]
[    0.363635] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.363644] ACPI: Power Button [PWRB]
[    0.363772] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.363779] ACPI: Power Button [PWRF]
[    0.364043] ACPI: Fan [FAN] (off)
[    0.364596] ACPI: acpi_idle registered with cpuidle
[    0.372939] Monitor-Mwait will be used to enter C-1 state
[    0.379838] Monitor-Mwait will be used to enter C-2 state
[    0.379893] Monitor-Mwait will be used to enter C-3 state
[    0.379905] Marking TSC unstable due to TSC halts in idle
[    0.381657] Switching to clocksource hpet
[    0.387919] thermal LNXTHERM:01: registered as thermal_zone0
[    0.387938] ACPI: Thermal Zone [THRM] (51 C)
[    0.388115] ERST: Table is not found!
[    0.388608] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.391861] brd: module loaded
[    0.393071] loop: module loaded
[    0.393437] ata_piix 0000:00:1f.1: version 2.13
[    0.393461] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.393527] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.393649] scsi0 : ata_piix
[    0.393806] scsi1 : ata_piix
[    0.395041] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.395048] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.395799] Fixed MDIO Bus: probed
[    0.395870] PPP generic driver version 2.4.2
[    0.395948] tun: Universal TUN/TAP device driver, 1.6
[    0.395952] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.396124] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.396159] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.396190] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.396225] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.396336] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.396417] ehci_hcd 0000:00:1a.7: debug port 1
[    0.400335] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.400366] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf4604800
[    0.404344] isapnp: Scanning for PnP cards...
[    0.453838] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.454201] hub 1-0:1.0: USB hub found
[    0.454212] hub 1-0:1.0: 4 ports detected
[    0.454388]   alloc irq_desc for 23 on node -1
[    0.454393]   alloc kstat_irqs on node -1
[    0.454405] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.454437] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.454444] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.454534] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.454580] ehci_hcd 0000:00:1d.7: debug port 1
[    0.458486] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.458520] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4604c00
[    0.506323] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.506696] hub 2-0:1.0: USB hub found
[    0.506706] hub 2-0:1.0: 6 ports detected
[    0.506886] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.506924] uhci_hcd: USB Universal Host Controller Interface driver
[    0.506988] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.507003] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.507010] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.507088] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.507151] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.507394] hub 3-0:1.0: USB hub found
[    0.507403] hub 3-0:1.0: 2 ports detected
[    0.507535]   alloc irq_desc for 21 on node -1
[    0.507540]   alloc kstat_irqs on node -1
[    0.507551] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.507562] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.507569] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.507638] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.507695] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.507932] hub 4-0:1.0: USB hub found
[    0.507941] hub 4-0:1.0: 2 ports detected
[    0.508081] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.508093] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.508100] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.508171] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.508209] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.508450] hub 5-0:1.0: USB hub found
[    0.508458] hub 5-0:1.0: 2 ports detected
[    0.508595] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.508606] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.508613] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.508688] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.508740] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.508979] hub 6-0:1.0: USB hub found
[    0.508988] hub 6-0:1.0: 2 ports detected
[    0.509140] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.509152] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.509159] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.509226] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.509264] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.509507] hub 7-0:1.0: USB hub found
[    0.509515] hub 7-0:1.0: 2 ports detected
[    0.509795] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.558268] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.563867] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.563879] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.563948] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.564000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.564055] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.564284] mice: PS/2 mouse device common for all mice
[    0.564668] rtc_cmos 00:08: RTC can wake from S4
[    0.564749] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.564792] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.565040] device-mapper: uevent: version 1.0.3
[    0.609498] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.616718] ata1.00: ATAPI: Optiarc DVD RW AD-7530B, NX02, max UDMA/33
[    0.632467] ata1.00: configured for UDMA/33
[    0.677104] device-mapper: multipath: version 1.1.1 loaded
[    0.677112] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.681395] EISA: Probing bus 0 at eisa.0
[    0.681408] Cannot allocate resource for EISA slot 1
[    0.681415] Cannot allocate resource for EISA slot 2
[    0.681420] Cannot allocate resource for EISA slot 3
[    0.681424] Cannot allocate resource for EISA slot 4
[    0.681429] Cannot allocate resource for EISA slot 5
[    0.681463] Cannot allocate resource for EISA slot 6
[    0.681468] Cannot allocate resource for EISA slot 7
[    0.681480] EISA: Detected 0 cards.
[    0.704392] cpuidle: using governor ladder
[    0.704619] cpuidle: using governor menu
[    0.705315] TCP cubic registered
[    0.705591] NET: Registered protocol family 10
[    0.706375] lo: Disabled Privacy Extensions
[    0.706903] NET: Registered protocol family 17
[    0.707879] Using IPI No-Shortcut mode
[    0.708001] PM: Resume from disk failed.
[    0.708031] registered taskstats version 1
[    0.708614]   Magic number: 2:787:533
[    0.708634] bdi 1:11: hash matches
[    0.708723] rtc_cmos 00:08: setting system clock to 2010-11-12 13:32:02 UTC (1289568722)
[    0.708727] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.708729] EDD information not available.
[    0.740698] Freeing initrd memory: 10508k freed
[    0.752449] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.787376] isapnp: No Plug & Play device found
[    0.788848] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[    0.799037] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.799044] Uniform CD-ROM driver Revision: 3.20
[    0.799255] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.799327] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.799436] Freeing unused kernel memory: 684k freed
[    0.800031] Write protecting the kernel text: 4932k
[    0.800106] Write protecting the kernel read-only data: 1976k
[    0.808035] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.823793] udev[87]: starting version 163
[    0.929473] ACPI: Battery Slot [BAT1] (battery present)
[    1.021714] sky2: driver version 1.28
[    1.021770] sky2 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.021788] sky2 0000:08:00.0: setting latency timer to 64
[    1.021829] sky2 0000:08:00.0: Yukon-2 FE chip revision 3
[    1.021950]   alloc irq_desc for 46 on node -1
[    1.021953]   alloc kstat_irqs on node -1
[    1.021973] sky2 0000:08:00.0: irq 46 for MSI/MSI-X
[    1.027522] sky2 0000:08:00.0: eth0: addr 00:1b:24:cc:17:78
[    1.034556] ahci 0000:00:1f.2: version 3.0
[    1.034580] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.034637]   alloc irq_desc for 47 on node -1
[    1.034641]   alloc kstat_irqs on node -1
[    1.034656] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.034746] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.034751] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.034758] ahci 0000:00:1f.2: setting latency timer to 64
[    1.040078] scsi2 : ahci
[    1.040276] scsi3 : ahci
[    1.040448] scsi4 : ahci
[    1.040684] ata3: SATA max UDMA/133 abar m2048@0xf4604000 port 0xf4604100 irq 47
[    1.040690] ata4: SATA max UDMA/133 abar m2048@0xf4604000 port 0xf4604180 irq 47
[    1.040695] ata5: SATA max UDMA/133 abar m2048@0xf4604000 port 0xf4604200 irq 47
[    1.040751] ahci 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.056157] ahci 0000:07:00.0: AHCI 0001.0000 32 slots 1 ports 3 Gbps 0x1 impl SATA mode
[    1.056166] ahci 0000:07:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.056179] ahci 0000:07:00.0: setting latency timer to 64
[    1.056374] scsi5 : ahci
[    1.056465] ata6: SATA max UDMA/133 abar m8192@0xf4200000 port 0xf4200100 irq 19
[    1.360128] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.360140] ata5: SATA link down (SStatus 0 SControl 300)
[    1.360167] ata4: SATA link down (SStatus 0 SControl 300)
[    1.360806] ata3.00: unexpected _GTF length (8)
[    1.376094] ata6: SATA link down (SStatus 0 SControl 300)
[    1.384054] usb 6-2: new low speed USB device using uhci_hcd and address 2
[    1.412745] ata3.00: ATA-8: TOSHIBA MK2565GSX, GJ003A, max UDMA/100
[    1.412752] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.413733] ata3.00: unexpected _GTF length (8)
[    1.413984] ata3.00: configured for UDMA/100
[    1.428378] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK2565GS GJ00 PQ: 0 ANSI: 5
[    1.428582] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.428729] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.428813] sd 2:0:0:0: [sda] Write Protect is off
[    1.428818] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.428852] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.429064]  sda: sda1 sda2 < sda5 >
[    1.506014] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.509436] sdhci: Secure Digital Host Controller Interface driver
[    1.509440] sdhci: Copyright(c) Pierre Ossman
[    1.511620] firewire_ohci 0000:09:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.577571] usbcore: registered new interface driver hiddev
[    1.590479] input: Acrox USB & PS/2 Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input4
[    1.590611] generic-usb 0003:0F62:1001.0001: input,hidraw0: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:1d.1-2/input0
[    1.590633] usbcore: registered new interface driver usbhid
[    1.590636] usbhid: USB HID core driver
[    1.653040] firewire_ohci: Added fw-ohci device 0000:09:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.653092] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.653123] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.654171] sdhci-pci 0000:09:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.655230] Registered led device: mmc0::
[    1.656291] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[    2.034421] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.148145] firewire_core: created device fw0: GUID 00004ce056241b00, S400
[   13.343019] udev[383]: starting version 163
[   13.423453] Adding 6142972k swap on /dev/sda5.  Priority:-1 extents:1 across:6142972k 
[   13.593227] Linux agpgart interface v0.103
[   13.671070] lp: driver loaded but no devices found
[   13.741572] lirc_dev: IR Remote Control driver registered, major 249 
[   13.741688] lirc_ite8709: module is from the staging directory, the quality is unknown, you have been warned.
[   13.773884] Linux video capture interface: v2.00
[   13.776855] cfg80211: Calling CRDA to update world regulatory domain
[   13.783756] lirc_ite8709 00:02: lirc_dev: driver lirc_ite8709 registered at minor = 0
[   13.787627] lirc_ite8709: device found : irq=10 io=0x260
[   13.838256] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b024)
[   13.839486] acpi device:02: registered as cooling_device3
[   13.855054] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input6
[   13.855564] usbcore: registered new interface driver uvcvideo
[   13.855569] USB Video Class driver (v0.1.0)
[   13.856764] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   13.856927] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   13.859511] nvidia: module license 'NVIDIA' taints kernel.
[   13.859515] Disabling lock debugging due to kernel taint
[   13.868917] cfg80211: World regulatory domain updated:
[   13.868922]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.868927]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.868931]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.868935]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.868939]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.868942]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.926042] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.067808]   alloc irq_desc for 22 on node -1
[   14.067813]   alloc kstat_irqs on node -1
[   14.067823] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.067894]   alloc irq_desc for 48 on node -1
[   14.067897]   alloc kstat_irqs on node -1
[   14.067911] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   14.067955] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.379663] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b2, caps: 0xa04713/0x200000/0x0
[   14.381077] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.381082] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   14.381162] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.381179] iwl3945 0000:02:00.0: setting latency timer to 64
[   14.436933] iwl3945 0000:02:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.436938] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.437063]   alloc irq_desc for 49 on node -1
[   14.437066]   alloc kstat_irqs on node -1
[   14.437101] iwl3945 0000:02:00.0: irq 49 for MSI/MSI-X
[   14.449824] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.474279] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   14.973576] type=1400 audit(1289568736.760:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=657 comm="apparmor_parser"
[   14.974555] type=1400 audit(1289568736.760:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=657 comm="apparmor_parser"
[   14.975087] type=1400 audit(1289568736.760:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=657 comm="apparmor_parser"
[   14.992321] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   15.181609] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.181623] nvidia 0000:01:00.0: setting latency timer to 64
[   15.181631] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.181850] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   15.196194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.206073] sky2 0000:08:00.0: eth0: enabling interface
[   15.206497] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.265856] type=1400 audit(1289568737.052:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=894 comm="apparmor_parser"
[   15.265919] type=1400 audit(1289568737.052:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=895 comm="apparmor_parser"
[   15.266903] type=1400 audit(1289568737.052:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=895 comm="apparmor_parser"
[   15.267438] type=1400 audit(1289568737.052:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=895 comm="apparmor_parser"
[   15.271233] type=1400 audit(1289568737.056:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=896 comm="apparmor_parser"
[   15.271676] type=1400 audit(1289568737.056:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=898 comm="apparmor_parser"
[   15.272937] type=1400 audit(1289568737.060:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=898 comm="apparmor_parser"
[   15.813786] ppdev: user-space parallel port driver
[   16.418917] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   16.852643] sky2 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   16.852895] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.194817] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   27.280075] eth0: no IPv6 routers present
will@will-EasyNote-SB85:~$

---

### Post by uncaspi on 2010-11-12
type lsmod and look if the driver iwl3945 is listed

---

### Post by iemcdoug on 2010-11-12
mine was recently doing this, fixed with

rfkill unblock wlan0

---

### Post by uncaspi on 2010-11-12
He have tried that. It would have been showed in dmesg if it was blocked.

---

### Post by gchdevon on 2010-11-12
thanks uncas. it is listed. here's the print out.

will@will-EasyNote-SB85:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  44 
joydev                  8735  0 
arc4                    1165  2 
iwl3945                85550  0 
iwlcore               127415  1 iwl3945
snd_hda_codec_conexant    29736  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231541  2 iwl3945,iwlcore
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lirc_ite8709            5336  0 
video                  18712  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
lirc_dev                9393  1 lirc_ite8709
output                  1883  1 video
cfg80211              144470  3 iwl3945,iwlcore,mac80211
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26360  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 nvidia,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19013  0 
firewire_ohci          21106  0 
sky2                   45127  0 
libahci                21667  3 ahci
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core

---

### Post by gchdevon on 2010-11-12
> **iemcdoug said:**
> mine was recently doing this, fixed with

rfkill unblock wlan0


Thanks. I had tried this already but I tried it again as I had done so much mucking about something might have changed. This time it came up with:

"Bogus unblock argument 'wlan0'."

---

### Post by uncaspi on 2010-11-12
The driver is loaded.
Found this on a thread and it's and you can try it.

cat /sys/class/ieee80211/phy0/rfkill*/state determines if the wireless switch is on or off. If it gives you a 0, then wireless is disabled. To enable it you need to run (as root) "echo 1 > /sys/class/ieee80211/phy0/rfkill*/state"

AS root just type sudo

---

### Post by gchdevon on 2010-11-12
this gets stranger and stranger. It gave me a "1", i assume this means it is turned on.

---

### Post by uncaspi on 2010-11-12
Yes it's turned on.

---

### Post by uncaspi on 2010-11-12
Do you have this directory?

cd /sys/class/net/wifi0

or goto cd /sys/class/net and look for your wifi device. cd and look if you get a file called link_mode

Do cat link_mode and see whats in it. 0 or 1

---

### Post by gchdevon on 2010-11-12
I put the first command in and it said no such file or directory.
Results:
will@will-EasyNote-SB85:~$ cd /sys/class/net/wifi0
bash: cd: /sys/class/net/wifi0: No such file or directory
will@will-EasyNote-SB85:~$ goto cd /sys/class/net
No command 'goto' found, did you mean:
 Command 'wgoto' from package 'wily' (universe)
 Command 'goo' from package 'goo' (universe)
 Command 'gotox' from package 'dvb-apps' (universe)
 Command 'gogo' from package 'gogo' (multiverse)
goto: command not found
will@will-EasyNote-SB85:~$ cd /sys/class/net
will@will-EasyNote-SB85:/sys/class/net$ cat link_mode
cat: link_mode: No such file or directory
will@will-EasyNote-SB85:/sys/class/net$ 

Thanks for your efforts. Do you think that it might be a fault with the computer? It would be a coincidence that the wireless hardware and the hard drive failed at the same time.

---

### Post by uncaspi on 2010-11-12
10.10 is not a good distro for wireless. 10.04 is much better.

What's in /sys/class/net directory?

---

### Post by gchdevon on 2010-11-12
> **uncaspi said:**
> 10.10 is not a good distro for wireless. 10.04 is much better.

What's in /sys/class/net directory?

What do I need to do to find that out?

---

### Post by uncaspi on 2010-11-12
Open a terminal and issue the cd command. cd /sys/class/net

then type ls

---

### Post by gchdevon on 2010-11-12
will@will-EasyNote-SB85:~$ cd /sys/class/net
will@will-EasyNote-SB85:/sys/class/net$ ls
eth0  lo  wlan0
will@will-EasyNote-SB85:/sys/class/net$

---

### Post by p1ggybank on 2011-01-06
> **uncaspi said:**
> Are you sure your radio is turned on? Try rfkill unblock wifi

You saved me at least... thank you

---

### Post by gchdevon on 2011-01-08
Well. thanks for responding. Is there a way to end the thread without indicating that it had been solved? It became clear that this was a hardware fault or something so esoteric that I wasn't going to get it sorted. My son took the  laptop away with him and he'll just use connected by cable at uni. 
The laptop has a light that comes on if the wifi is on. It was unable to detect any signals, I think that the piece of equipment to perform the action must be broken 
Thanks for everybody trying to help.

---

### Post by famicom2015 on 2011-01-08
I am having a problem im not sure if its just me, but i have a wireless adapter its:

belkin 802.11g - 54 mbps
model: f5d7050ed

i have a hp pavillion a303.uk 

i can connect with a wire but i cant only detect the router, when i try to log on to it to use wireless connection it never gives back a ip address, i have tried manually putting in the ip address ect...still nothing.

i have wifi rader, wicd and some other apps, all do the same 

its a wep, 

im stuck 

any help would be fab!

---

### Post by PatchesTheCaveman on 2011-01-09
Please reply with all the information requested by this post:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

With one exception:  run ```
sudo iwconfig
```
instead of *iwconfig*


Thanks!

---

### Post by mohdforever on 2011-05-23
hammody@hammody-ubuntu:~$ sudo iwlist scan
[sudo] password for hammody: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.

hammody@hammody-ubuntu:~$ 



what can i do now

by the way , i connected by wifi already but not using network manager 
i'm using "indicator-network" instead of.

i need to network manager.

please i need help

---

