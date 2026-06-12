---
title: "Ubuntu 9.10 cannot detect wireless network running in VMWare workstation 6.5"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by dknc on 2010-01-20
Hello, I am quite fresh to Linux, I just installed ubuntu desktop 9.10 VM in VMWare workstation 6.5 which runs in my windows xp. I failed to make the wireless network work in my ubuntu. I have searched around the internet and does see that wireless should be workable in a virtual machine. Also found a link in this forum as [http://ubuntuforums.org/showthread.php?t=1290663](http://ubuntuforums.org/showthread.php?t=1290663), which almost describes the same issue except we are on different version of ubuntu. I really could not understand the last post of this thread "followup... got it working. It was VMware. After installing ubuntu on its own partition everything works fine! Thanks", Does it mean that ubuntu vm should be placed in the same partition where VMWare workstation is installed, it does not make any sense to me.

My ubuntu failed to detect the wireless network whenever I configured the VMWare to use brighe or NAT mode. I also found some threads debating on the bugs in ubuntu network manager, so uninstalled this tool and installed [COLOR=Blue]wicd[/COLOR], but wicd does not work for me too. I also installed [COLOR=Blue]ndiswrapper[/COLOR], I have an [COLOR=Blue]intel pro wireless 3945 ABG network card[/COLOR], so I installed installed netw39x5, but in ndiswrapper administration window, it shows me no hardware present for this driver.

With a wired network, the network works well with wicd. My wireless net work works fine in my XP. Here is some information.

It is said wireless will only works in roaming mode, I did not find a place to manually confirm this setting.:(, For the old versions of ubuntu, there were some discussions about vmnet, which might be an issue, but I cannot get a latest workable source package of it.

It is really appreciated that someone can help me out. Forgive my poor English.;)


> 
dkn@dkn-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
[COLOR=Blue]02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)[/COLOR]
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware USB2 EHCI Controller



> eth0      Link encap:Ethernet  HWaddr 00:0c:29:da:c5:d4  
          inet6 addr: fe80::20c:29ff:feda:c5d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2286 (2.2 KB)  TX bytes:11751 (11.7 KB)
          Interrupt:18 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

>  *-network
                description: Ethernet interface
                product: 79c970 [PCnet32 LANCE]
                vendor: Advanced Micro Devices [AMD]
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 00:0c:29:da:c5:d4
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master rom ethernet physical logical
                configuration: broadcast=yes driver=vmxnet driverversion=2.0.1.1 firmware=N/A latency=64 maxlatency=255 mingnt=6 multicast=yes
                resources: irq:18 ioport:2000(size=128) memory:30000000-3000ffff(prefetchable)

---

### Post by cgb223 on 2010-01-30
having the same problem, I'll look arround

---

### Post by Durduman on 2010-02-10
Same problem as well... hail to the one that brings us our solution.

---

### Post by cgb223 on 2010-02-16
got it working

i upgraded to vmware workstation 7.0.1 (latest) and made sure to download the install file with tools (was like 500 megs but hey got internet working) then after upgrading just logged into the already existant ubuntu, and it was already connected. the only special thing i did there was disable my virtual floppy drive because i had no need for it (i dont think that should matter anyway).

hope that helps ^_^!

---

