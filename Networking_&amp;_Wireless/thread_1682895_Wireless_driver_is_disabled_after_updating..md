---
title: "Wireless driver is disabled after updating."
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by Mbroadstone on 2011-02-06
I have a Dell Inspiron Mini 1018 that I have just installed 10.10 desktop version.  The wireless card is a realtek 8101/8102 but I have found that the 8192 driver available with the following command works just fine.
 
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
O.K.  When I freshly installed Ubuntu and got the aforemention driver everything works great.  As soon as I update, the additional drivers list it as available but not currently in use.  Nothing I have tried can get the thing working again.  Help!

---

### Post by manmk on 2011-02-28
I have similar problem and I am unable to reinstall the factory image.    	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }   I recently bought Dell Insp Mini10 with Ubuntu 10.04 OS. When I started the netbook, everything woked fine including the wireless. However, when I updated system with update manager, the wireless device stopped working ( I made sure that its not hardware off). I saw lot of different solutions offered and tried couple of them, particularly installing the NDIS wrapper described on the [https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper). I installed the windows driver (net8192ce) from realtek and it detects the hardware, but wireless is still not working. It simply doesn't detect any network.
 I am new to ubuntu/Linux so not sure how to proceed further. Please help
 

 

 **Model: Dell Inspiron Mini 1018**
 

 **lspci**
 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge 
 00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
 05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 
 07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) 
 

 **lsusb:**
 Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device 
 Bus 001 Device 002: ID 064e:810f Suyin Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 **ifconfig **
 eth0      Link encap:Ethernet  HWaddr 5c:26:0a:16:4a:1b   
           inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::5e26:aff:fe16:4a1b/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:2015 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:2074 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:1940403 (1.9 MB)  TX bytes:313353 (313.3 KB) 
           Interrupt:27 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
 

 **iwconfig **
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  
 pan0      no wireless extensions. 
 

 **lsmod **
 Module                  Size  Used by 
 binfmt_misc             6587  1  
 rfcomm                 33421  4  
 ppdev                   5259  0  
 sco                     7885  2  
 bridge                 45614  0  
 stp                     1655  1 bridge 
 bnep                    9436  2  
 l2cap                  30624  16 rfcomm,bnep 
 dm_crypt               11331  0  
 joydev                  8740  0  
 snd_hda_codec_realtek   203408  1  
 snd_hda_intel          22005  2  
 snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
 snd_hwdep               5412  1 snd_hda_codec 
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss 
 snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
 snd_seq_dummy           1338  0  
 snd_seq_oss            26722  0  
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi 
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 snd_timer              19098  2 snd_pcm,snd_seq 
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                63245  0  
 dell_wmi                1793  0  
 uvcvideo               57310  0  
 soundcore               6620  1 snd 
 dcdbas                  5422  0  
 btusb                  10957  2  
 videodev               34361  1 uvcvideo 
 v4l1_compat            13251  2 uvcvideo,videodev 
 bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb 
 serio_raw               3978  0  
 ndiswrapper           184677  0  
 snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
 lp                      7028  0  
 parport                32635  2 ppdev,lp 
 dm_raid45              81647  0  
 xor                    15028  1 dm_raid45 
 fbcon                  35102  71  
 tileblit                2031  1 fbcon 
 font                    7557  1 fbcon 
 bitblit                 4707  1 fbcon 
 softcursor              1189  1 bitblit 
 vga16fb                11385  0  
 vgastate                8961  1 vga16fb 
 i915                  287458  4  
 drm_kms_helper         29329  1 i915 
 drm                   162409  5 i915,drm_kms_helper 
 i2c_algo_bit            5028  1 i915 
 usb_storage            39553  0  
 intel_agp              24375  2 i915 
 video                  17375  1 i915 
 output                  1871  1 video 
 r8169                  34108  0  
 ahci                   32200  2  
 agpgart                31724  2 drm,intel_agp 
 mii                     4381  1 r8169 
 

 **dmseg**
 

 [ 2165.140971] r8169: eth0: link up 
 [ 2165.141847] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
 [ 2176.033040] eth0: no IPv6 routers present 
 [ 2176.727071] r8169: eth0: link down 
 [ 2178.110635] r8169: eth0: link down 
 [ 2178.111395] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [ 2178.342151] r8169: eth0: link up 
 [ 2178.343069] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
 [ 2178.392702] r8169: eth0: link up 
 [ 2184.007858] r8169: eth0: link up 
 [ 2184.205924] r8169: eth0: link up 
 [ 2185.746175] r8169: eth0: link up 
 [ 2186.279859] __ratelimit: 6 callbacks suppressed 
 [ 2186.279888] type=1503 audit(1298886322.570:14):  operation="open" pid=2212 parent=2183 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf" 
 [ 2195.968102] eth0: no IPv6 routers present 
 [ 2227.327335] r8169: eth0: link down 
 [ 2229.071080] r8169: eth0: link up 
 [ 2747.295778] r8169: eth0: link down 
 [ 2748.921417] r8169: eth0: link up 
 [ 2838.184175] r8169: eth0: link down 
 [ 2839.872742] r8169: eth0: link up 
 

 **sudo lshw -C network **
   *-network                
        description: Ethernet interface 
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:05:00.0 
        logical name: eth0 
        version: 05 
        serial: 5c:26:0a:16:4a:1b 
        size: 100MB/s 
        capacity: 100MB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.36 latency=0 link=yes multicast=yes port=MII speed=100MB/s 
        resources: irq:27 ioport:2000(size=256) memory:f0f2c000-f0f2cfff(prefetchable) memory:f0f18000-f0f1bfff(prefetchable) 
   *-network UNCLAIMED 
        description: Network controller 
        product: Realtek Semiconductor Co., Ltd. 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:07:00.0 
        version: 01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: ioport:3000(size=256) memory:f0100000-f0103fff 
 

 **iwlist scan **
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 pan0      Interface doesn't support scanning. 
 

 **lsb_release -d **
 Description:	Ubuntu 10.04.2 LTS 
 

 **uname -mr **
 2.6.32-28-generic i686 
 **sudo /etc/init.d/networking restart **
 Reconfiguring network interfaces...
 
[LIST]   Ignoring unknown interface 	eth0=eth0.
[/LIST]

---

### Post by kevdog on 2011-02-28
I'm assuming this is your wireless adapter??

*-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:07:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:3000(size=256) memory:f0100000-f0103fff 

Unclaimed means the proper kernel module or driver is not installed.  You may need to look around what driver is needed for your hardware.  And second why is ndiswrapper loaded as one of your kernel modules in lsmod??

---

