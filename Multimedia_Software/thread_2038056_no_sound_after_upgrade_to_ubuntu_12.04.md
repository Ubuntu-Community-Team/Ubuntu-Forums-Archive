---
title: "no sound after upgrade to ubuntu 12.04"
date: 2012-08-05
forum: Multimedia Software
---

### Post by redsprite on 2012-08-05
hey everyone,
 
I recently upgraded to ubuntu 12.04 but  just after updating  grub i lost sound so
i have tried theese 2 links :

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)

without result 

 Accordingly  to second link i found that the 
/etc/asound.conf was empty then i paste this code
----     code  -------
 pcm.!default { 
[LIST]
[*]type plug slave.pcm { 
[LIST]
[*]type hw card 0 device 1
[/LIST]
}
[/LIST]
}
--------------------------------------------
 where i have the crad and device numbres  ( card 0 device 1 )from this comand : aplay-l 
 
but without result.


My  ALSA information is located at [http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf](http://www.alsa-project.org/db/?f=09dcab500ad7ce35734659ea1779dc09209d35cf)


and here is the full terminal output for this command : 



"cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound"


terminal output :


H/W path               Device     Class       Description
=========================================================
                                  system      Desktop Computer
/0                                bus         945GCM-S2L
/0/0                              memory      128KiB BIOS
/0/4                              processor   Intel(R) Pentium(R) 4 CPU 3.00GHz
/0/4/8                            memory      16KiB L1 cache
/0/4/9                            memory      1MiB L2 cache
/0/4/1.1                          processor   Logical CPU
/0/4/1.2                          processor   Logical CPU
/0/17                             memory      3GiB System Memory
/0/17/0                           memory      2GiB DIMM 667 MHz (1,5 ns)
/0/17/1                           memory      1GiB DIMM 667 MHz (1,5 ns)
/0/100                            bridge      82945G/GZ/P/PL Memory Controller Hub
/0/100/2                          display     82945G/GZ Integrated Graphics Controller
/0/100/1b                         multimedia  N10/ICH 7 Family High Definition Audio Controller
/0/100/1c                         bridge      N10/ICH 7 Family PCI Express Port 1
/0/100/1c.1                       bridge      N10/ICH 7 Family PCI Express Port 2
/0/100/1c.1/0          eth0       network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                         bus         N10/ICH 7 Family USB UHCI Controller #1
/0/100/1d.1                       bus         N10/ICH 7 Family USB UHCI Controller #2
/0/100/1d.2                       bus         N10/ICH 7 Family USB UHCI Controller #3
/0/100/1d.3                       bus         N10/ICH 7 Family USB UHCI Controller #4
/0/100/1d.7                       bus         N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e                         bridge      82801 PCI Bridge
/0/100/1f                         bridge      82801GB/GR (ICH7 Family) LPC Interface Bridge
/0/100/1f.2            scsi0      storage     N10/ICH7 Family SATA Controller [IDE mode]
/0/100/1f.2/0.0.0      /dev/sda   disk        164GB Hitachi HDS72161
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      98GiB Extended partition
/0/100/1f.2/0.0.0/1/5  /dev/sda5  volume      52GiB HPFS/NTFS partition
/0/100/1f.2/0.0.0/1/6  /dev/sda6  volume      45GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      2863MiB Linux swap volume
/0/100/1f.2/0.0.0/3    /dev/sda3  volume      52GiB EXT3 volume
/0/100/1f.3                       bus         N10/ICH 7 Family SMBus Controller
/0/1                   scsi2      storage     
/0/1/0.0.0             /dev/sdb   disk        4004MB SCSI Disk
/0/1/0.0.0/1           /dev/sdb1  volume      3818MiB Windows FAT volume
total 0
crw-rw---T+  1 root audio 116, 33 août   5 23:28 timer
crw-rw---T+  1 root audio 116,  1 août   5 23:28 seq
crw-rw---T+  1 root audio 116,  2 août   5 23:28 pcmC0D2c
crw-rw---T+  1 root audio 116,  6 août   5 23:28 hwC0D2
crw-rw---T+  1 root audio 116,  7 août   5 23:28 controlC0
drwxr-xr-x   2 root root       60 août   5 23:28 by-path
drwxr-xr-x   3 root root      220 août   5 23:28 .
crw-rw---T+  1 root audio 116,  4 août   6 00:16 pcmC0D0p
crw-rw---T+  1 root audio 116,  5 août   6 00:16 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 août   6 00:16 pcmC0D1p
drwxr-xr-x  16 root root     4280 août   6 00:18 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  sssf       3197 F.... pulseaudio
/dev/snd/pcmC0D1p:   sssf       3197 F...m pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [c00f4c70] f4c70
[    0.211679] ACPI: No dock devices found.
[    0.211712] HEST: Table not found.
[    0.342219] pnp: PnP ACPI: found 15 devices
[    0.396278] audit: initializing netlink socket (disabled)
[    0.396341] type=2000 audit(1344209244.392:1): initialized
[    0.551806] ERST: Table is not found!
[    0.916899] isapnp: No Plug & Play device found
[    1.283502] Fixed MDIO Bus: probed
[    1.284078] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.300262] hub 1-0:1.0: USB hub found
[    1.300822] hub 2-0:1.0: USB hub found
[    1.301291] hub 3-0:1.0: USB hub found
[    1.301769] hub 4-0:1.0: USB hub found
[    1.302271] hub 5-0:1.0: USB hub found
[    1.328229] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   48.750267] lp: driver loaded but no devices found
[   48.964335] leds_ss4200: no LED devices found
[   49.134686] type=1400 audit(1344205694.301:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=597 comm="apparmor_parser"
[   49.137697] type=1400 audit(1344205694.305:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=597 comm="apparmor_parser"
[   49.139072] type=1400 audit(1344205694.305:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=597 comm="apparmor_parser"
[   50.051667] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   50.051763] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   50.051812] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   50.138538] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   50.155202] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   50.155396] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   50.161843] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   50.164791] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   64.949377] type=1400 audit(1344205710.117:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1321 comm="apparmor_parser"
[   64.950367] type=1400 audit(1344205710.117:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1321 comm="apparmor_parser"
[   64.951582] type=1400 audit(1344205710.117:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1321 comm="apparmor_parser"
[   64.957701] type=1400 audit(1344205710.125:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1320 comm="apparmor_parser"
[   64.984754] type=1400 audit(1344205710.153:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1322 comm="apparmor_parser"
[   65.002998] type=1400 audit(1344205710.169:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox/firefox{,*[^s][^h]}" pid=1323 comm="apparmor_parser"
[   65.010902] type=1400 audit(1344205710.177:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1322 comm="apparmor_parser"
[   65.012146] type=1400 audit(1344205710.181:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox/firefox{,*[^s][^h]}//browser_java" pid=1323 comm="apparmor_parser"
[   65.014493] type=1400 audit(1344205710.181:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1322 comm="apparmor_parser"
[   65.017056] type=1400 audit(1344205710.185:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk" pid=1323 comm="apparmor_parser"
[   65.418985] apm: BIOS not found.
[   77.205110] vboxdrv: Found 2 processor cores.
[   77.269497] vboxpci: IOMMU not found (not registered)
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 12/27/2007
        Serial services are supported (int 14h)
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: 945GCM-S2L
    Serial Number:  
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: 945GCM-S2L
    Serial Number:  
    Manufacturer: Gigabyte Technology Co., Ltd.
    Serial Number:  
    Manufacturer: Intel
    Serial Number:  
    Port Type: Serial Port 16450 Compatible
    Port Type: Serial Port 16450 Compatible
    Manufacturer: None
    Serial Number: None
    Manufacturer: None
    Serial Number: None
snd_seq_dummy          12686  0 
snd_hda_codec_realtek    63371  1 
snd_hda_intel          32364  5 
snd_hda_codec         111551  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
usb_storage            39646  1 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:43 memory:d11c0000-d11c3fff

Any help is much appreciated!

---

### Post by redsprite on 2012-08-05
now sound works like a charme on kernel 3.0.0-16 but still didn't work on kernel 3.2.0-29

---

