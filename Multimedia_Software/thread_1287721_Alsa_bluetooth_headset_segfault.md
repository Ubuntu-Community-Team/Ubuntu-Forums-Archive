---
title: "Alsa bluetooth headset segfault"
date: 2009-10-10
forum: Multimedia Software
---

### Post by jasmine55 on 2009-10-10
hi,

I am trying to setup my plantronics 510 bluetooth headset with alsa.

The problem is, that after 2-3 seconds of playing sound successfully I get a segmentation fault:


[250665.940090] hci_scodata_packet: hci0 SCO packet for unknown connection handle 50
[250702.342282] aplay[7774]: segfault at 2b39ade0 ip b7c1cadb sp bf8069b0 error 4 in libasound_module_rate_speexrate.so[b7c1a000+3000]
[250703.585046] btusb_isoc_complete: hci0 corrupted SCO packet
[250703.585064] btusb_isoc_complete: hci0 corrupted SCO packet
[250703.585096] hci_scodata_packet: hci0 SCO packet for unknown connection handle 46
[250703.585102] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585108] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585113] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585118] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585124] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585129] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585134] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585140] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585145] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250703.585151] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[250705.136230] aplay[7786]: segfault at 2b87fde0 ip b7ce6adb sp bffd3170 error 4 in libasound_module_rate_speexrate.so[b7ce4000+3000]
[250708.029540] aplay[7798]: segfault at 2a556de0 ip b7c84adb sp bfe6f010 error 4 in libasound_module_rate_speexrate.so[b7c82000+3000]
[250708.076056] hci_scodata_packet: hci0 SCO packet for unknown connection handle 51
[250713.452766] aplay[7810]: segfault at 2a34cde0 ip b7b75adb sp bfa60400 error 4 in libasound_module_rate_speexrate.so[b7b73000+3000]
[250713.493062] hci_scodata_packet: hci0 SCO packet for unknown connection handle 52
[250713.493073] hci_scodata_packet: hci0 SCO packet for unknown connection handle 52
[250713.493079] hci_scodata_packet: hci0 SCO packet for unknown connection handle 52

that's my alsa configuration:

```




pcm.rc {
         type rate
         slave.pcm bluetooth2
         slave.rate 8000
 }

pcm.bluetooth2 {
        type route
        slave.pcm bluetooth
        slave.channels 1
        ttable.0.0 1
        ttable.1.0 1
}

pcm.bluetooth {
        type bluetooth
        #device "XX:XX:XX:XX:XX:XX" #optional, connects to specific device instead the default one
        profile "auto"             #optional, supported profiles are: auto, hifi and voice
}



```I am using blueman with bluez from the blueman ppa.

another question: if i reverse the order of the rate and route plugin, I hear absolutely nothing - what is the reason for that?

has someone an idea?

thank you :)

---

### Post by Neill_R on 2012-05-05
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 


I have a similar problem. I have a Nexus Talknano bluetooth headset. It works fine with my Nokia 6300 phone and works in part with my computer. It works, in that I can use the microphone with Skype and hear via the sound card. However if i select the talknano for sound output nothing is heard. However I can control the slider showing the output volume by using the Talknano volume control buttons 

UBUNTU 12.04 on an ASROCK G31M-S motherboard.


When i get connect the talknano the following appears in seconds 

[COLOR=Red]ANY IDEAS PLEASE?[/COLOR]

Are the default settings in /etc/bluetooth/audio.conf correct?

lost to know what to look at next where is alsa config stored?

log viewer shows 

May  5 23:40:41 freds bluetoothd[879]: /org/bluez/879/hci0/dev_80_4C_04_00_1C_B2/fd14: fd(32) ready
May  5 23:40:41 freds rtkit-daemon[1517]: Successfully made thread 4279 of process 2532 (n/a) owned by '1000' RT at priority 5.
May  5 23:40:41 freds rtkit-daemon[1517]: Supervising 4 threads of 1 processes of 1 users.
May  5 23:40:46 freds bluetoothd[879]: Audio connection got disconnected
May  5 23:40:46 freds kernel: [ 6298.553042] Bluetooth: hci0 SCO packet for unknown connection handle 1
May  5 23:40:46 freds kernel: [ 6298.553053] Bluetooth: hci0 SCO packet for unknown connection handle 1
May  5 23:40:46 freds kernel: [ 6298.553059] Bluetooth: hci0 SCO packet for unknown connection handle 1



[COLOR=Red]details that might be of interest[/COLOR]

administrator@freds:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
administrator@freds:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 005: ID 0af0:6971 Option Globetrotter HSDPA Modem
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 007: ID 041e:406c Creative Technology, Ltd Live! Cam Sync [VF0520]
administrator@freds:~$ 


administrator@freds:~$ lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

administrator@freds:~$ sudo lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASRock Incorporation Device 3662
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fea78000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
administrator@freds:~$

administrator@freds:~$ sudo aplay -l
[sudo] password for administrator: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
administrator@freds:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/3.2.0-24-generic-pae/kernel/sound/firewire/snd-firewire-speakers.ko

administrator@freds:~$ sudo arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
administrator@freds:~$

---

