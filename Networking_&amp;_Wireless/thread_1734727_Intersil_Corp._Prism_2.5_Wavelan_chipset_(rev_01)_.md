---
title: "Intersil Corp. Prism 2.5 Wavelan chipset (rev 01) Not Working"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by azb8496 on 2011-04-20
I have this D-Link wireless PCI card installed, which works with xp, but I have had no luck with Ubuntu 10.10. I have scoured the internet trying everything others have with no success. The network manager sees no networks and a lspci gives me:
 
03:08.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
 
This is the second wireless card I've tried with Ubuntu and I still can't get anywhere. Any ideas?

---

### Post by azb8496 on 2011-04-21
Will post more info soon.  Just kind of a pain because I have to save the outputs by way of text files and then transfer those to my networked puter (Vista X64 btw, it's not bad, just terribly priced!) by way of usb hard drive; and then open and paste to the forum.  These are computers, I'm NOT SUPPOSE TO HAVE TO GET UP IN ORDER TO LEARN OR FIX PROBLEMS! j/k, I have discovered wheels on my computer chair, so there will be no getting up anyways; score!  Seeyasoon!

---

### Post by azb8496 on 2011-04-21
[COLOR=black]Okay, so here's all the info I gathered from following the thread procedures (the ones left blank I couldn't figure out yet, that's why they call me a newbie):[/COLOR]
 
[COLOR=navy]1 ) Machine Brand and Model (PC/Laptop):[/COLOR]
[COLOR=red]Code:[/COLOR]
[COLOR=red]Get it from your product information.[/COLOR]
 
[COLOR=green]Motherboard from a Compaq Presario (not sure of the model number, don't want to open up the case unless I really have to), AMD Sempron 3400+ CPU, 2 X 256 MB DDR2 SDRAM, 250 GB Toshiba HDD (not alot is from the original computer).[/COLOR]
 
 
[COLOR=navy]2 ) Wireless Brand, Model and Wireless Chipset:[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ lspci[/COLOR]
 
[COLOR=green]00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)[/COLOR]
[COLOR=green]00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)[/COLOR]
[COLOR=green]00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)[/COLOR]
[COLOR=green]00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)[/COLOR]
[COLOR=green]00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)[/COLOR]
[COLOR=green]00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)[/COLOR]
[COLOR=green]00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)[/COLOR]
[COLOR=green]00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)[/COLOR]
[COLOR=green]00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)[/COLOR]
[COLOR=green]00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)[/COLOR]
[COLOR=green]00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)[/COLOR]
[COLOR=green]00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)[/COLOR]
[COLOR=green]00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)[/COLOR]
[COLOR=green]00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)[/COLOR]
[COLOR=green]00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)[/COLOR]
[COLOR=green]00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)[/COLOR]
[COLOR=green]00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)[/COLOR]
[COLOR=green]00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)[/COLOR]
[COLOR=green]00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)[/COLOR]
[COLOR=green]00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)[/COLOR]
[COLOR=green]00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)[/COLOR]
[COLOR=green]00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)[/COLOR]
[COLOR=green]00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)[/COLOR]
[COLOR=green]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/COLOR]
[COLOR=green]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/COLOR]
[COLOR=green]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/COLOR]
[COLOR=green]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/COLOR]
[COLOR=green]03:08.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)[/COLOR]
 
[COLOR=red]$ lsusb(hint) use grep to get only information about the Wireless[/COLOR]
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ lspci -nn | grep 'Wireless Brand'[/COLOR]
 
[COLOR=navy]3 ) check interface:[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ ifconfig[/COLOR]
 
[COLOR=green]eth0 Link encap:Ethernet HWaddr 00:18:f3:a5:bb:49 [/COLOR]
[COLOR=green]UP BROADCAST MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=green]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=green]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=green]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=green]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/COLOR]
[COLOR=green]Interrupt:23 Base address:0xc000 [/COLOR]
[COLOR=green]lo Link encap:Local Loopback [/COLOR]
[COLOR=green]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=green]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=green]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=green]RX packets:132 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=green]TX packets:132 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=green]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=green]RX bytes:10416 (10.4 KB) TX bytes:10416 (10.4 KB)[/COLOR]
 
[COLOR=red]$ iwconfig(hint) if the Wireless interface name is wlan0 you can also use[/COLOR]
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ iwconfig wlan0[/COLOR]

 
[COLOR=navy]4 ) Check for modules:[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red][COLOR=red]$ lsmod(hint) search[/COLOR] for the Wireless module[/COLOR]
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ lsmod | grep "wlan_module_name"[/COLOR]
 
 
[COLOR=navy]5 ) Kernel boot messages[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ dmesg(hint) the same as in (4)[/COLOR]
 
 
[COLOR=navy]6 ) Network configuration[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ sudo lshw -C network[/COLOR]
 
[COLOR=green]*-network DISABLED [/COLOR]
[COLOR=green]description: Wireless interface[/COLOR]
[COLOR=green]product: Prism 2.5 Wavelan chipset[/COLOR]
[COLOR=green]vendor: Intersil Corporation[/COLOR]
[COLOR=green]physical id: 8[/COLOR]
[COLOR=green]bus info: [/COLOR][COLOR=green]pci@0000:03:08.0[/COLOR]
[COLOR=green]logical name: wifi0[/COLOR]
[COLOR=green]version: 01[/COLOR]
[COLOR=green]width: 32 bits[/COLOR]
[COLOR=green]clock: 33MHz[/COLOR]
[COLOR=green]capabilities: pm bus_master cap_list logical wireless ethernet physical[/COLOR]
[COLOR=green]configuration: broadcast=yes driver=hostap firmware=0.0.0 latency=32 multicast=yes wireless=IEEE 802.11-DS[/COLOR]
[COLOR=green]resources: irq:16 memory:fdcff000-fdcfffff[/COLOR]
 
[COLOR=navy]7 ) Scan for networks:[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ iwlist scan(hint) the same as in (3)[/COLOR]
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ iwlist scan wlan0[/COLOR]
 
[COLOR=navy]8 ) Ubuntu Version: [/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ lsb_release -d[/COLOR]
 
[COLOR=green]Ubuntu 10.10[/COLOR]
 
 
[COLOR=navy]9 ) Kernel/architecture (including 32 vs. 64 bit): [/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ uname -mr[/COLOR]
 
[COLOR=green]2.6.35-22-generic i686[/COLOR]
 
 
[COLOR=navy]10 ) Restarting the network:[/COLOR]
 
[COLOR=red]Code:[/COLOR]
[COLOR=red]$ sudo /etc/init.d/networking restart[/COLOR]
 
[COLOR=green]* Reconfiguring network interfaces... [ OK ][/COLOR]
 
 
Hope this helps you guys help me :)

---

### Post by ctyonahl on 2011-04-25
I started my own thread along along these lines: [http://ubuntuforums.org/showthread.php?t=1738941](http://ubuntuforums.org/showthread.php?t=1738941)

---

