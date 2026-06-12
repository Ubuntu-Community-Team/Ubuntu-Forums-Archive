---
title: "Cannot connect, possibly can't detect NIC"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by acotm on 2009-12-13
Hi, I'm completely new to Linux. I just installed Ubuntu 9.10. 
 
I am unable to connect to the Internet. I am unable to ping ubuntu.com or google.com. I receive a message that says "The address [] cannot be found." When I ping my router at 192.168.1.1, I don't get the error, but 0 packets are transmitted and 0 are received. I have no idea if this is correct, but I'm guessing that my NIC card is not recognized? I've searched these forums and I can't find a solution, so I'm hoping someone can point me in the right direction. I've pasted the output of ifconfig and lspci below:
 
ifconfig:
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
 
Thanks for your help and I apologize if I've posted in the wrong place or if the solution is posted somewhere else.

---

### Post by uncaspi on 2009-12-13
Seems that no cards are recognized. Will you please post sudo lshw -C network  and dmesg | grep -e eth -e wlan;)

---

### Post by acotm on 2009-12-13
sudo lshw -C network flashes PCI (sysfs) for a second and then goes back to the command prompt.  
 
What was the second thing to try?  A smiley got in the way at the end.

---

### Post by uncaspi on 2009-12-13
dmesg | grep -e eth -e wlan

---

### Post by uncaspi on 2009-12-13
Also please post /etc/udev/rules.d/70-persistent-net.rules

---

### Post by acotm on 2009-12-13
dmesg | grep -e eth -e wlan returns
[ 0.427472] ACPI Error (psparse-0537): Method parse/execurtion failed [\_PR_.CPU1._PDC] (Node f799e150), AE_INVALID_TABLE_LENGTH
 
/etc/udev/rules.d/70-persistent-net.rules returns
Permission denied
 
Thanks for the help.

---

### Post by uncaspi on 2009-12-13
Your NIC's are not recognized. You could look in dmesg to see if there are any interrupt conflicts or errors. Also search the threads for your laptop or whatever you have, and do the same for your nic. When you get permission denied you must type sudo at the beginning of the line.
sudo gedit /etc/udev/rules.d/70-persistent-net.rules or perhaps you don't need sudo in this case. You can use gedit or pico as text editors at your choice.

---

### Post by acotm on 2009-12-13
Thanks.  When I do sudo gedit with the command you posted previously, I get:
 
# PCI device 0x1106:0x3065 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:ec:e3:50:4d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
 
I will start searching threads for specifics about my NIC.

---

### Post by uncaspi on 2009-12-13
Thanks you at least got Ethernet card eth0
Did you use uppercase C when you typed sudo lshw -C network

---

### Post by Iowan on 2009-12-14
> **uncaspi said:**
> sudo gedit /etc/udev/rules.d/70-persistent-net.rules or perhaps you don't need sudo in this case. You can use gedit or pico as text editors at your choice. Hopefully not too far off-topic:
Use [**gksudo**]("http://www.psychocats.net/ubuntu/graphicalsudo") with **gedit**, **sudo** with **nano** (or **pico**).

---

