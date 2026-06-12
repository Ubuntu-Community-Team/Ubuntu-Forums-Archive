---
title: "Wireless Connectivity with 11.04"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by Sovietfiction on 2011-03-11
Edit: Accidentally overlooked the how to so I tried adding some additional info.  Also when I attempted to activate the driver from it alerted me to check /var/log/jockey.log for details yet it is unknown to me where to find it.

Machine Brand and Model
     HP Pavilion dv4-1465dx
Wireless Brand, Model and Wireless Chipset
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 090c:c371 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Checked modules

Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  963 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60497  1 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17364  0 
rc_rc6_mce             12454  0 
psmouse                59039  0 
memstick               15816  1 jmb38x_ms
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ene_ir                 22309  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
rc_core                25760  9 rc_rc6_mce,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ene_ir
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  446597  3 
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  46630  0 
drm_kms_helper         40745  1 i915
drm                   180083  4 i915,drm_kms_helper
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

Network Configuration

 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d8500000-d8503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:ad:99:63
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.111 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:3000(size=256) memory:d2410000-d2410fff memory:d2400000-d240ffff memory:d2420000-d243ffff

Scanned for networks

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Ubuntu Version
Description:    Ubuntu Natty (development branch)

Kernel/architecture
2.6.38-6-generic-pae i686

Restarting Network
bash: sudo/etc/init.d/networking: No such file or directory





Hello gentle people! I just upgraded to 11.04 Alpha 3 on my HP Pavilion dv4-1465dx and updating my wireless driver is turning out to be quite the bother. I have attempted the command sudo apt-get install linux-backports-modules-wireless-maverick-generic and I am finding it can not locate the package.  I tried a similar command with narwhal but was also unsuccessful.
 

 Using lspci | grep [Nn]etwork it comes back with:
 

 02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
 

 I attempted changing my firmware-b43-installer to firmware-b43-lpphy-installer and had no success.
 

 ifconfig gives me this:
 

 eth0      Link encap:Ethernet  HWaddr 00:23:5a:ad:99:63   
           inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::223:5aff:fead:9963/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:432 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:478 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:254070 (254.0 KB)  TX bytes:86371 (86.3 KB) 
           Interrupt:45 Base address:0xc000  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)   
 

 I also tried dmesg and was not sure what information to include but here is the bits related to network management
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> (eth0): device state change: 3 -> 4 (reason 0) 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> (eth0): device state change: 4 -> 5 (reason 0) 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> (eth0): device state change: 5 -> 7 (reason 0) 
 Mar 11 13:26:13 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds) 
 Mar 11 13:26:14 BATCOUNTRY NetworkManager[593]: <info> dhclient started with pid 1601 
 Mar 11 13:26:14 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
 Mar 11 13:26:14 BATCOUNTRY dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1 
 Mar 11 13:26:14 BATCOUNTRY dhclient: Copyright 2004-2010 Internet Systems Consortium. 
 Mar 11 13:26:14 BATCOUNTRY dhclient: All rights reserved. 
 Mar 11 13:26:14 BATCOUNTRY dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 
 Mar 11 13:26:14 BATCOUNTRY dhclient:  
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> (eth0): DHCPv4 state changed nbi -> preinit 
 Mar 11 13:26:15 BATCOUNTRY dhclient: Listening on LPF/eth0/00:23:5a:ad:99:63 
 Mar 11 13:26:15 BATCOUNTRY dhclient: Sending on   LPF/eth0/00:23:5a:ad:99:63 
 Mar 11 13:26:15 BATCOUNTRY dhclient: Sending on   Socket/fallback 
 Mar 11 13:26:15 BATCOUNTRY dhclient: DHCPREQUEST of 192.168.1.111 on eth0 to 255.255.255.255 port 67 
 Mar 11 13:26:15 BATCOUNTRY dhclient: DHCPACK of 192.168.1.111 from 192.168.1.1 
 Mar 11 13:26:15 BATCOUNTRY dhclient: bound to 192.168.1.111 -- renewal in 38194 seconds. 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> (eth0): DHCPv4 state changed preinit -> reboot 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled... 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started... 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   address 192.168.1.111 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   prefix 24 (255.255.255.0) 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   gateway 192.168.1.1 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   nameserver '209.18.47.61' 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   nameserver '209.18.47.62' 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info>   domain name 'twmi.rr.com' 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Scheduling stage 5 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Done scheduling stage 5 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete. 
 Mar 11 13:26:15 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
 Mar 11 13:26:15 BATCOUNTRY avahi-daemon[577]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.111. 
 Mar 11 13:26:15 BATCOUNTRY avahi-daemon[577]: New relevant interface eth0.IPv4 for mDNS. 
 Mar 11 13:26:15 BATCOUNTRY avahi-daemon[577]: Registering new address record for 192.168.1.111 on eth0.IPv4. 
 Mar 11 13:26:16 BATCOUNTRY NetworkManager[593]: <info> (eth0): device state change: 7 -> 8 (reason 0) 
 Mar 11 13:26:16 BATCOUNTRY NetworkManager[593]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS. 
 Mar 11 13:26:16 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) successful, device activated. 
 Mar 11 13:26:16 BATCOUNTRY NetworkManager[593]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
 Mar 11 13:26:28 BATCOUNTRY ntpdate[1684]: adjust time server 91.189.94.4 offset -0.347058 sec 
 

 

 I have been shooting in the dark and would appreciate any help. I would be happy to supply any additional information as well.

---

