---
title: "WI-FI has disapeared"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by curupira on 2009-07-01
Hello fellows,
I have just take a new notebook and it came with a Mandriva linux with all devices working fine. I decided to install Debian wich I had some previous experience. I tryied hard to configure the wireless rtl8187b but gave up after some frustrated error message. so I installed the ubuntu 9.04 and reconized all devices easily. I took the follow information from ubuntu and come back to try install debian with these information:



dmesg:(part that I think is important)

Jun 19 23:20:34 ubuntu kernel: [   59.776276] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
Jun 19 23:20:34 ubuntu kernel: [   59.812801] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
Jun 19 23:20:34 ubuntu kernel: [   59.858524] cfg80211: World regulatory domain updated:
Jun 19 23:20:34 ubuntu kernel: [   59.858530] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 19 23:20:34 ubuntu kernel: [   59.858532] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 23:20:34 ubuntu kernel: [   59.858534] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 23:20:34 ubuntu kernel: [   59.858536] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 23:20:34 ubuntu kernel: [   59.858538] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 23:20:34 ubuntu kernel: [   59.858540] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 23:20:34 ubuntu kernel: [   60.094277] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 19 23:20:34 ubuntu kernel: [   60.126937] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
Jun 19 23:20:34 ubuntu kernel: [   60.139323] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
Jun 19 23:20:34 ubuntu kernel: [   60.139324]          hardware, use at your own risk
Jun 19 23:20:34 ubuntu kernel: [   60.214897] phy0: hwaddr 00:22:43:8a:9a:4e, RTL8187BvE V0 + rtl8225z2
Jun 19 23:20:34 ubuntu kernel: [   60.214925] usbcore: registered new interface driver rtl8187
Jun 19 23:20:34 ubuntu kernel: [   63.292356] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
Jun 19 23:20:39 ubuntu kernel: [   70.496398] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 19 23:20:39 ubuntu kernel: [   70.496402] Bluetooth: BNEP filters: protocol multicast
Jun 19 23:20:39 ubuntu kernel: [   70.685317] Bridge firewalling registered
Jun 19 23:20:47 ubuntu kernel: [   78.852084] lp: driver loaded but no devices found
Jun 19 23:20:48 ubuntu kernel: [   79.112071] ppdev: user-space parallel port driver
Jun 19 23:20:49 ubuntu kernel: [   80.101647] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 23:20:57 ubuntu kernel: [   88.295223] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jun 19 23:21:05 ubuntu kernel: [   96.149427] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 23:21:05 ubuntu kernel: [   96.176026] eth0: auto-negotiating...
Jun 19 23:21:15 ubuntu kernel: [  106.200025] eth0: auto-negotiating...
Jun 19 23:21:25 ubuntu kernel: [  116.224030] eth0: auto-negotiating...
Jun 19 23:21:35 ubuntu kernel: [  126.248031] eth0: auto-negotiating...
Jun 19 23:21:45 ubuntu kernel: [  136.272029] eth0: auto-negotiating...
Jun 19 23:21:55 ubuntu kernel: [  146.296026] eth0: auto-negotiating...
Jun 19 23:22:05 ubuntu kernel: [  156.320029] eth0: auto-negotiating...
Jun 19 23:22:10 ubuntu kernel: [  161.252032] usb 1-4: new high speed USB device using ehci_hcd and address 4
Jun 19 23:22:10 ubuntu kernel: [  161.386621] usb 1-4: configuration #1 chosen from 1 choice
Jun 19 23:22:10 ubuntu kernel: [  161.570543] Initializing USB Mass Storage driver...
Jun 19 23:22:10 ubuntu kernel: [  161.570703] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 19 23:22:10 ubuntu kernel: [  161.570799] usbcore: registered new interface driver usb-storage
Jun 19 23:22:10 ubuntu kernel: [  161.570802] USB Mass Storage support registered.
Jun 19 23:22:15 ubuntu kernel: [  166.344042] eth0: auto-negotiating...
Jun 19 23:22:15 ubuntu kernel: [  166.568720] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
Jun 19 23:22:15 ubuntu kernel: [  166.571818] sd 4:0:0:0: [sdb] 3911616 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Jun 19 23:22:15 ubuntu kernel: [  166.573318] sd 4:0:0:0: [sdb] Write Protect is off
Jun 19 23:22:15 ubuntu kernel: [  166.580961] sd 4:0:0:0: [sdb] 3911616 512-byte hardware sectors: (2.00 GB/1.86 GiB)
Jun 19 23:22:15 ubuntu kernel: [  166.582457] sd 4:0:0:0: [sdb] Write Protect is off
Jun 19 23:22:15 ubuntu kernel: [  166.582482]  sdb: sdb1
Jun 19 23:22:15 ubuntu kernel: [  166.583317] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jun 19 23:22:15 ubuntu kernel: [  166.583686] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jun 19 23:22:25 ubuntu kernel: [  176.368041] eth0: auto-negotiating...
Jun 19 23:22:32 ubuntu kernel: [  183.885624] ACPI Exception (thermal-0479): AE_ERROR, ACPI thermal trip point state changed
Jun 19 23:22:32 ubuntu kernel: [  183.885632] Please send acpidump to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
Jun 19 23:22:32 ubuntu kernel: [  183.885637]  [20080926]
Jun 19 23:22:35 ubuntu kernel: [  186.392043] eth0: auto-negotiating...
Jun 19 23:22:45 ubuntu kernel: [  196.416044] eth0: auto-negotiating...
Jun 19 23:22:55 ubuntu kernel: [  206.440040] eth0: auto-negotiating...
Jun 19 23:23:05 ubuntu kernel: [  216.464042] eth0: auto-negotiating...





iwconfig:

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0







ifconfig:

eth0      Link encap:Ethernet  EndereÃ§o de HW 00:90:f5:76:c9:71  
          UP BROADCAST MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:19 EndereÃ§o de E/S:0xdead 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereÃ§o inet6: ::1/128 Escopo:MÃ¡quina
          UP LOOPBACK RUNNING  MTU:16436  MÃ©trica:1
          pacotes RX:16 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:16 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:0 
          RX bytes:1168 (1.1 KB) TX bytes:1168 (1.1 KB)

wlan0     Link encap:Ethernet  EndereÃ§o de HW 00:22:43:8a:9a:4e  
          UP BROADCAST MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0  Link encap:NÃ£o Especificado  EndereÃ§o de HW 00-22-43-8A-9A-4E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)








I decided to come back to Debian and tryed some advices that i found on the internet. Than I think I made some really bad thing and now, please see what i find on Ubuntu (I took off Debian and come bak to ubuntu 9.04):




dmesg2:
[    9.703780] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x202000
[    9.740496] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   10.204204] EXT3 FS on sda1, internal journal
[   11.051198] kjournald starting.  Commit interval 5 seconds
[   11.051362] EXT3 FS on sda6, internal journal
[   11.051367] EXT3-fs: mounted filesystem with ordered data mode.
[   11.304310] type=1505 audit(1246444722.374:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1919
[   11.348382] type=1505 audit(1246444722.418:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1923
[   11.348565] type=1505 audit(1246444722.418:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1923
[   11.348615] type=1505 audit(1246444722.418:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1923
[   11.348655] type=1505 audit(1246444722.418:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1923
[   11.471959] type=1505 audit(1246444722.542:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1928
[   11.472248] type=1505 audit(1246444722.542:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1928
[   11.499642] type=1505 audit(1246444722.570:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1932
[   13.249690] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.249694] Bluetooth: BNEP filters: protocol multicast
[   13.266544] Bridge firewalling registered
[   14.885411] ACPI Exception (thermal-0479): AE_ERROR, ACPI thermal trip point state changed
[   14.885418] Please send acpidump to [EMAIL="linux-acpi@vger.kernel.org"]linux-acpi@vger.kernel.org[/EMAIL]
[   14.885421]  [20080926]
[   14.905363] ppdev: user-space parallel port driver
[   18.928564] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.948391] eth0: auto-negotiating...
[   29.772172] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   38.972031] eth0: auto-negotiating...
[   48.996029] eth0: auto-negotiating...
[   59.020029] eth0: auto-negotiating...
[   69.044029] eth0: auto-negotiating...
[   79.068041] eth0: auto-negotiating...






ifconfig2:

eth0      Link encap:Ethernet  EndereÃ§o de HW 00:90:f5:76:c9:71  
          inet end.: 10.167.65.78  Bcast:10.167.65.255  Masc:255.255.255.0
          endereÃ§o inet6: fe80::290:f5ff:fe76:c971/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  MÃ©trica:1
          pacotes RX:102 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:46 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:1000 
          RX bytes:12164 (12.1 KB) TX bytes:6059 (6.0 KB)
          IRQ:19 EndereÃ§o de E/S:0xdead 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereÃ§o inet6: ::1/128 Escopo:MÃ¡quina
          UP LOOPBACK RUNNING  MTU:16436  MÃ©trica:1
          pacotes RX:12 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:12 erros:0 descartados:0 excesso:0 portadora:0
          colisÃµes:0 txqueuelen:0 
          RX bytes:888 (888.0 B) TX bytes:888 (888.0 B)




iwconfig2:

lo         no wireless extensions

eth0         no wireless extensions

pan0         no wireless extensions




Anyone could help me on this big issue?

I thank you very much!
Regards,
curupira

---

