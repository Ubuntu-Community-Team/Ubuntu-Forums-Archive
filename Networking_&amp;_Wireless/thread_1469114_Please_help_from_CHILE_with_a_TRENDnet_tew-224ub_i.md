---
title: "Please help from CHILE with a TRENDnet tew-224ub in Lucid Lynx on acer aspire 4220"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by bichopro on 2010-05-01
Hi, first: apologize my bad english

I can't connect my usb external wireless card.
when i plug nothing happens and i can't see on network manager.

On karmic i found this solution:

> So one can run gksudo gedit /etc/modprobe.d/blacklist.conf and add the line blacklist at76c50x_usb to the file, run sudo depmod -aeq to get it working again.

But on lucid lynx nothing happens.

i try  this:

> sudo apt-get install atmel-firmware

After a reboot y see my usb card but can't connect to my wifi router (wep protocol) i remove and reinstall the linux-firmware.

I have a internal wireless card atheros and its working with no problem, but i need the usb card because the distance of the wifi router its so long.

I plug my usb card and this is the result:

acer aspire 4220, TRENDnet tew-224ub wireless card on Lucid Lynx.

lspci
> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

lsusb
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 07b8:b000 D-Link Corp. BWU613
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig
> eth0      Link encap:Ethernet  direcciónHW 00:1b:24:c7:d0:ce  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:27 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:35753 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:35753 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:9341012 (9.3 MB)  TX bytes:9341012 (9.3 MB)

wlan0     Link encap:Ethernet  direcciónHW 00:1d:d9:6a:a6:f8  
          Direc. inet:192.168.1.4  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21d:d9ff:fe6a:a6f8/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:6024 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5306 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:4708131 (4.7 MB)  TX bytes:882583 (882.5 KB)

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"enrique"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:02:CF:59:6F:BF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod
> Module                  Size  Used by
dm_crypt               11331  0 
snd_hda_codec_realtek   203168  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
arc4                    1153  2 
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121792  0 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
acer_wmi               13861  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               9932176  45 
sdhci_pci               5470  0 
cfg80211              126485  3 ath5k,mac80211,ath
sdhci                  15462  1 sdhci_pci
ricoh_mmc               2923  0 
psmouse                63245  0 
serio_raw               3978  0 
k8temp                  3024  0 
led_class               2864  3 ath5k,acer_wmi,sdhci
agpgart                31724  1 nvidia
i2c_nforce2             5199  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ieee1394               81181  1 ohci1394
vga16fb                11385  1 
vgastate                8961  1 vga16fb
forcedeth              49556  0 
ahci                   32008  5 
video                  17375  0 
output                  1871  1 video

sudo lshw -C network
> *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:c7:d0:ce
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f4488000-f4488fff ioport:30f8(size=8) memory:f4489c00-f4489cff memory:f4489800-f448980f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:d9:6a:a6:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.4 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f4000000-f400ffff

Thank for your time

---

### Post by bichopro on 2010-05-02
bump

---

### Post by bichopro on 2010-05-04
bump

---

### Post by bichopro on 2010-05-07
bump

---

### Post by twola on 2010-07-18
Assuming you are using Karmic:
Open a terminal session (Applications->Accessories->Terminal)
Type  	Code:
 	sudo gedit /etc/modprobe.d/blacklist.conf 
This will ask for your password, and open a text editor
Add a line  	Code:
 	blacklist rt2800usb 
Save the file & reboot.

---

