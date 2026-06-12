---
title: "Wireless broke U/G from 8.10 to 9.10"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by Tonyr63 on 2010-01-08
My TP-LINK TL-WN610G not working following U/G to 9.10 which worked very well in Ubuntu 8.04 & 8.10.
The device manager instantly see the correct device as Atheros AR 5001 but it does not seem to even attempt connection. Here is some relevant information.
 
[sudo] password for anthony: 
*-network UNCLAIMED 
description: Ethernet controller 
product: Atheros AR5001X+ Wireless Network Adapter 
vendor: Atheros Communications Inc. 
physical id: 1 
bus info: pci@0000:02:00.0 
version: 01 
width: 32 bits 
clock: 33MHz 
capabilities: pm cap_list 
configuration: latency=0 maxlatency=28 mingnt=10 
resources: memory:18000000-1800ffff 
anthony@presario:~$ sudo iwlist scanning 
lo Interface doesn't support scanning. 
anthony@presario:~$ cat /etc/network/interfaces # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5). 
# The loopback network interface
auto lo
iface lo inet loopback 
# The primary network interface
auto eth0
#iface eth0 inet dhcp
anthony@presario:~$ cat etc/lsb-release
cat: etc/lsb-release: No such file or directory anthony@presario:~$ lspci -nn 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8601 [Apollo ProMedia] [1106:0601] (rev 05) 00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP] [1106:8601] 00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 22)
00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 10)
00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10)
00:07.4 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 30)
00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 20) 00:09.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2013] (rev 01) 00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01) 01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade i1 [1023:8520] (rev 6a) 02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01) anthony@presario:~$ anthony@presario:~$ dmesg | grep ound 
[ 0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it. 
[ 0.080270] ACPI: No dock devices found. 
[ 0.106757] pnp: PnP ACPI: found 11 devices 
[ 1.298243] isapnp: No Plug & Play device found 
[ 1.317097] hub 1-0:1.0: USB hub found 
[ 1.323083] device-mapper: multipath round-robin: version 1.0.0 loaded 
[ 1.331692] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[ 2.861613] usb-storage: device found at 3 
[ 16.961008] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:b103] 
anthony@presario:~$ dmesg | grep b43
anthony@presario:~$ dmesg | grep iwl
anthony@presario:~$ iwconfig 
lo no wireless extensions. 
anthony@presario:~$ sudo /etc/init.d/networking restart 
* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0. 
[ OK ] anthony@presario:~$ iwconfig 
lo no wireless extensions. 
&#12288;
I removed network manager and installed WICD which reports no wireless network found even though I am right behind the wireless router and all security has been disabled. The wireless interface is set to wlan0. What else can I do?
How can Ubuntu detect the correct device and not connect when this worked perfectly in version 8.10??
 
It appears from the activity on the forums that Wireless functionality is still very problematic in UBUNTU with little or no tools to troubleshoot through the UI.  I have lost 4 days tearing my hair out trying to resolve this.
 
:(

---

