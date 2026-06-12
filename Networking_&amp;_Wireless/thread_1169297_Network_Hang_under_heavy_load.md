---
title: "Network Hang under heavy load"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by techie2go on 2009-05-25
Hi
i had installed 8.04 with kernel 2.6.24-19-generic
i upgraded to 8.10 and then to 9.04 
the network (wired lan) hangs under heavy load, while transferring files, the transfer starts at 10MBps and stalls after 4/5 seconds this is happening in all types of network transfer http/sftp/nfs.

all i had to do is restart the network through 
/etc/init.d/networking restart
and it'll work fine till the next heavy transfer

the network address gets assigned from DHCP server, the behavior does not change even if i use static IP, 

also i am not using networkmanager.

now i am running 2.6.24-19-generic kernel without any problem the following are the other kernels installed (both 8.10 and 9.04 kernels) 
vmlinuz-2.6.28-10-generic
vmlinuz-2.6.28-11-generic
vmlinuz-2.6.28-12-generic
vmlinuz-2.6.28-4-generic
vmlinuz-2.6.28-6-generic
vmlinuz-2.6.28-7-generic
vmlinuz-2.6.28-8-generic
and the network hang remains in all the above

$ lspci

> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

thanks

---

### Post by puppywhacker on 2009-05-25
I once had a network interface that would hang the whole computer. My problem was heat related. Heavy network traffic would cause too much strain on the south bridge that it freeze up (or better melt down).

Dodgy hardware :(

It might also have to do with DMA or Buffers.

---

### Post by techie2go on 2009-05-30
dma is enabled, and not to mention again it works with old kernel that came with 8.04

---

### Post by cariboo on 2009-05-30
I had the same problem as you on my server, unfortunately it is located in my stand alone garage, so every time it stopped working I'd have to go out there and restart networking. Replacing the network card solved the problem.

---

