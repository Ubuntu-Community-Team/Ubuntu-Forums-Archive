---
title: "network icon disappeared"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by ganewbie on 2010-07-11
I am new to UBUNTU and have 10.4 installed in a new computer. All was good until last night I think I missed it up when the internet did not work and I have deleted the eth0 profile and I cannot get it back.
Here are some screen that I have captured and it might help you guys to help me. Please note that I have no idea of what I am posting but I got it from the forum.
/etc/NetworkManager/NetworkManager.conf
[main] 
plugins=ifupdown,keyfile 
no-auto-default=6c:f0:49:b1:7b:85, 
[ifupdown] 
managed=false
**********************************************************************************
sudo lshw -c network 
george@george-desktop:~$ 
[sudo] password for george: 
*-network DISABLED 
description: Ethernet interface 
product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 03 
serial: 6c:f0:49:b1:7b:85 
size: 100MB/s 
capacity: 1GB/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s 
resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdaf8000-fdafbfff(prefetchable) memory:fda00000-fda1ffff(prefetchable) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;[/SIZE][/FONT]
[/SIZE][/FONT]george@george-desktop:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate 
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) 
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9715 
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;[/SIZE][/FONT]
[/SIZE][/FONT]george@george-desktop:~$ iwconfig 
lo no wireless extensions. 
eth0 no wireless extensions. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]&#12288;Thanks in advance,[/FONT][/SIZE]
[/SIZE][/FONT]

---

### Post by Iowan on 2010-07-11
If the Network Manager icon disappeared, you might need to add a Notification Area to the top panel.

---

### Post by ganewbie on 2010-07-11
> **Iowan said:**
> If the Network Manager icon disappeared, you might need to add a Notification Area to the top panel.
 
Sounds good by HOW? I am green.
Forgot to mention that I do not have internet as well, hope the title is not missleading

---

### Post by Iowan on 2010-07-11
Right-click the panel, select "Add to Panel", then select "Notification Area".

---

### Post by ganewbie on 2010-07-11
> **Iowan said:**
> Right-click the panel, select "Add to Panel", then select "Notification Area".
 Thanks for the quick reply, I have done it and it shows an icone that expects a cell phone for sync but nothing for network, I used to have an icone that shows the network status that I think disappeared when I deleted eth0.

---

### Post by Iowan on 2010-07-11
You can try a restart/reboot. Frequently, a new Auto eth0 connection will be created. If that doesn't help (despite a lot of wishful thinking from here), you might be able to reconstruct the connection. If you right-click the icon, you should be able to "Edit connections...". If "Auto eth0" doesn't exist, you can "Add" it back.

---

### Post by danbh on 2010-07-12
hey there, I'm having a similar bug, and I am looking for those with similar experience.  Are you experiencing any and all of the following:
- No network icon?
- no connection?
- reboot doesn't help?
- nm-applet and network-manager/NetworkManager whatever, are all running?

If so, I have a workaround for you to try.  Thanks.

---

### Post by ganewbie on 2010-07-12
> **Iowan said:**
> You can try a restart/reboot. Frequently, a new Auto eth0 connection will be created. If that doesn't help (despite a lot of wishful thinking from here), you might be able to reconstruct the connection. If you right-click the icon, you should be able to "Edit connections...". If "Auto eth0" doesn't exist, you can "Add" it back.

Thanks again for the help but how do I do this? I would like to add it manually.

---

### Post by Iowan on 2010-07-12
I'll need to check my Ubuntu machine when I get home, but in brief, the **Add** option will ask for parameters - one of which will be MAC address. **ifconfig -a** *might* show that address... 
(More details in 3-4 hours...)

---

### Post by ganewbie on 2010-07-12
@Iowan, I am still waiting however I was trying to reinstall Network Mnanager but no luck so far.

---

### Post by Iowan on 2010-07-12
Right-click the Network Manager icon.
Select "**Edit connections...**".
Select the "**Wired**" tab.
Click "**Add**".
Click in the "**Connection name:**" box - enter your choice (Auto eth0).
Check the "**Connect automatically**" box.
Click in the "**MAC address:**" box and enter your interface MAC address (00:01:02:03:04:05). (Yours will be different)
I'd start with "**MTU:**" set for **automatic**.
I'd also check the "**Available to all users**" box.
Click the "**IPv4 Settings**" tab.
My workstation has "**Method:**" set for "**Automatic (DHCP)**".
Under the "**IPv6 Settings**" tab, I have "**Method:**" set to "**Ignore**".
Click "**Apply**", then "**Close**" the Network Connections window.

You can restart Network Manager, or reboot... and keep your fingers crossed (just kidding about the last part - though it won't hurt...).

---

### Post by ganewbie on 2010-07-12
I do not have the Network Manager, I have uninstalled it by mistake.

---

### Post by Iowan on 2010-07-12
Deleting Network Manager is a little different from deleting the eth0 profile...
You *might* be able to set up networking via */etc/network/interfaces*, but another thread I saw attempting that wasn't having much luck. 
Try ```
sudo nano /etc/networking/interfaces
```
Or if you'd rather a graphical editor, use ```
gksudo gedit /etc/networking/interfaces
```
Make it look something like:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```
Save the file, and restart/reboot. Good luck!

---

### Post by ganewbie on 2010-07-12
Thanks, How do I know my MAC address?

---

### Post by Iowan on 2010-07-12
Shouldn't need it for */etc/network/interfaces*, but (from a terminal) **sudo lshw -C network** should show information about your interfaces. Mine looks *something* like:```
 *-network               
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 64
       serial: [COLOR="Red"]00:5a:b4:1c:12:34[/COLOR]
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
```MAC address is highlighted.

---

### Post by ganewbie on 2010-07-15
I keep trying to add new wired profiles but no luck so far, I enter all the information and save it but it does not save or keep my profile for unknown reason. Is there anything else, I am trying Detnate's way of getting it to work and so far it works but not easy for kids to do.

---

### Post by Iowan on 2010-07-15
I keep forgetting the "magic key"... There's a thread that mentions it - I *think* it's the [ENTER] key that you must hit after entering data to make it "stick". Just clicking in the next box isn't enough.

---

### Post by ganewbie on 2010-07-18
Thanks but I am still cannot do.

---

