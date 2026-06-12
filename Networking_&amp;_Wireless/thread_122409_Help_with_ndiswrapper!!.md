---
title: "Help with ndiswrapper!!"
date: 2006-01-27
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-01-27
Hi.. I have a Cisco Aironet 350 PCMIA wireless card that works great with ubuntu out of the box, but it is not supported by WPAsupplicant, and I need to get WPA working on this card. 

I found out in another [post]("http://http//www.ubuntuforums.org/showthread.php?t=121617") that I can achive this using NDISwrapper with the windows driver as it supports WPA. I'm following these two howtos from the wiki ([1]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") & [2]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29")) but I'm having hard time following the first few steps as ndiswrapper keeps on showing "Hardware present: No". any help is appreciated.

what I need to know is:
1- how would i update my card firmware on linux, and could this be the problem??
2- why it is the card not showing on my lspci output?
3- why it is not showing as present on my ndiswrapper? 

Again, I appreciate all your help guys!!!

here is my outputs before inserting the card

```
$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:08.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:0a.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

$ dmesg |tail -n 25
[4294792.682000] ibm_acpi: bay device not present
[4294792.732000] ACPI: Battery Slot [BAT0] (battery absent)
[4294792.779000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294803.375000] IBM machine detected. Enabling interrupts during APM calls.
[4294803.375000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294803.375000] apm: overridden by ACPI.
[4294805.516000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377 0x4d0-0x4d7
[4294805.517000] cs: IO port probe 0x100-0x4ff: excluding 0x170-0x177 0x370-0x377 0x4d0-0x4d7
[4294805.519000] cs: IO port probe 0xc00-0xcf7: clean.
[4294805.519000] cs: IO port probe 0xc00-0xcf7: clean.
[4294805.520000] cs: IO port probe 0xa00-0xaff: clean.
[4294805.520000] cs: IO port probe 0xa00-0xaff: clean.
[4294805.992000] NET: Registered protocol family 10
[4294805.993000] Disabled Privacy Extensions on device c031eb40(lo)
[4294805.993000] IPv6 over IPv4 tunneling driver
[4294808.231000] Bluetooth: Core ver 2.7
[4294808.231000] NET: Registered protocol family 31
[4294808.231000] Bluetooth: HCI device and connection manager initialized
[4294808.231000] Bluetooth: HCI socket layer initialized
[4294808.341000] Bluetooth: L2CAP ver 2.7
[4294808.341000] Bluetooth: L2CAP socket layer initialized
[4294808.422000] Bluetooth: RFCOMM ver 1.5
[4294808.422000] Bluetooth: RFCOMM socket layer initialized
[4294808.422000] Bluetooth: RFCOMM TTY layer initialized
[4294816.350000] eth0: no IPv6 routers present

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A4:8E:36:E4
          inet6 addr: fe80::210:a4ff:fe8e:36e4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:28432 (27.7 KiB)  TX bytes:28432 (27.7 KiB)
``` 
here is my outputs after inserting the card

```
$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:08.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:0a.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
0000:00:0b.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

$ dmesg |tail -n 25
[4294805.520000] cs: IO port probe 0xa00-0xaff: clean.
[4294805.992000] NET: Registered protocol family 10
[4294805.993000] Disabled Privacy Extensions on device c031eb40(lo)
[4294805.993000] IPv6 over IPv4 tunneling driver
[4294808.231000] Bluetooth: Core ver 2.7
[4294808.231000] NET: Registered protocol family 31
[4294808.231000] Bluetooth: HCI device and connection manager initialized
[4294808.231000] Bluetooth: HCI socket layer initialized
[4294808.341000] Bluetooth: L2CAP ver 2.7
[4294808.341000] Bluetooth: L2CAP socket layer initialized
[4294808.422000] Bluetooth: RFCOMM ver 1.5
[4294808.422000] Bluetooth: RFCOMM socket layer initialized
[4294808.422000] Bluetooth: RFCOMM TTY layer initialized
[4294816.350000] eth0: no IPv6 routers present
[4294897.966000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294898.184000] airo:  Probing for PCI adapters
[4294898.189000] airo:  Finished probing for PCI adapters
[4294898.605000] airo: cmd= 111
[4294898.605000] airo: status= 7f11
[4294898.605000] airo: Rsp0= 2
[4294898.606000] airo: Rsp1= 0
[4294898.606000] airo: Rsp2= 0
[4294898.606000] airo: Doing fast bap_reads
[4294898.782000] airo: MAC enabled eth1 0:8:e3:5f:47:20
[4294898.783000] eth1: index 0x05: Vcc 5.0, Vpp 5.0, irq 3, io 0x0100-0x013f

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-109 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:369   Missed beacon:0

eth1      IEEE 802.11-DS  ESSID:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-109 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:379   Missed beacon:0

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:A4:8E:36:E4
          inet6 addr: fe80::210:a4ff:fe8e:36e4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:57860 (56.5 KiB)  TX bytes:57860 (56.5 KiB)

$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth2      Failed to read scan data : No data available

eth1      Failed to read scan data : No data available
```

---

### Post by kaamos on 2006-01-27
At least for me, pcmicia devices don't get detected if they are not connected at boot time. Check if this helps with lspci

---

### Post by ssalman on 2006-01-27
[quote=kaamos]At least for me, pcmicia devices don't get detected if they are not connected at boot time. Check if this helps with lspci[/quote]

rebooted with the card being plugged, same result ! 

I'm guessing it's reading the cad in one of the below lines??

```
0000:00:08.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
0000:00:08.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
```

---

### Post by ssalman on 2006-01-28
Any one?? ;)

---

