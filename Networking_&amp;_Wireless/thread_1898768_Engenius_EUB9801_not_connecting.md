---
title: "Engenius EUB9801 not connecting"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by brec on 2011-12-22
Ubuntu 11.04

This is a USB wireless adapter

I otbtained and built the rt3572 driver [per these instructions]("https://help.ubuntu.com/community/WifiDocs/Device/Engenius%20EUB9801%20Natty%2011.04").  The system talks to the device:  it shows my two SSIDs (one 2.4GHz, one 5GHz) in the panel menu but after I chose one and supply the WPA2 password it doesn't connect to the LAN.  The wireless icon in the panel continues animating as if it's looking for a network; ifconfig hangs; software which requires a network connection, such as Chromium Browser, doesn't start.  There's a disconnect choice in the menu underneath the SSID, but choosing it does nothing.

---

### Post by praseodym on 2011-12-22
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | egrep 'rt3|rt2'
```

---

### Post by kurt18947 on 2011-12-22
Here's a link:
[http://ubuntuforums.org/showthread.php?t=1659230&highlight=engenius](http://ubuntuforums.org/showthread.php?t=1659230&highlight=engenius)
It doesn't sound like the most Linux-friendly adapter out there.

---

### Post by brec on 2011-12-22
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | egrep 'rt3|rt2'
```

Oboy!  The doctor is IN!  Thanks for looking...

```

~$ lspci -nnk | grep -iA2 net
0d:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
	Kernel driver in use: r8169
--
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:7640]
	Kernel driver in use: r8169
~$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c31c Logitech, Inc. 
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1740:9801 Senao [COLOR="RoyalBlue"]### <--- Engenius USB Adapter[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  3 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2786212  307 
soundcore              12680  1 snd
rt3572sta             653760  1 [COLOR="RoyalBlue"]### <-- the driver[/COLOR]
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73535  0 
edac_core              53845  0 
sp5100_tco             13744  0 
edac_mce_amd           23464  0 
k10temp                13119  0 
i2c_piix4              13303  0 
serio_raw              13166  0 
joydev                 17606  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
pata_jmicron           12747  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13165  0 
r8169                  48022  0 
xhci_hcd               77643  0 
ahci                   25951  3 
libahci                26642  1 ahci
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: C0:C1:C0:A2:03:94   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ sudo iwlist scan
[sudo] password for brec: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: B0:E7:54:DC:C6:F9
                    Protocol:802.11b/g
                    ESSID:"2WIRE954"     [COLOR="RoyalBlue"]### <-- neighbor's SSID[/COLOR]
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/100  Signal level=-81 dBm  Noise level=-76 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: C0:C1:C0:A2:03:93
                    Protocol:802.11b/g/n
                    ESSID:"brecWFII"   [COLOR="RoyalBlue"]### <-- my 2.4GHz SSID[/COLOR]
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-78 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700103AE4BE2606DC387A22C22845A1BEA63C103C000103
          Cell 03 - Address: C0:C1:C0:A2:03:94
                    Protocol:802.11a/n
                    ESSID:"brecWFII5"    [COLOR="RoyalBlue"]### <-------- my 5GHz SSID[/COLOR]
                    Mode:Managed
                    Frequency:5.745 GHz (Channel 149)
                    Quality=47/100  Signal level=-71 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700103AE4BE2606DC387A22C22845A1BEA63C103C000103

~$ rfkill list
~$ dmesg | egrep 'rt3|rt2'
[    5.744701] rtusb init rt2870 --->
[    5.749111] usbcore: registered new interface driver rt2870
[   12.445453] <==== rt28xx_init, Status=0
[   13.806464] <==== rt28xx_init, Status=0
[   20.745099] IP: [<ffffffffa014bb6b>] CntlOidRTBssidProc+0x7b/0x570 [rt3572sta]
[   20.745123] Modules linked in: binfmt_misc parport_pc ppdev vesafb snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fglrx(P) soundcore rt3572sta snd_page_alloc psmouse edac_core sp5100_tco edac_mce_amd k10temp i2c_piix4 serio_raw joydev lp parport usbhid hid firewire_ohci pata_jmicron firewire_core crc_itu_t pata_atiixp r8169 xhci_hcd ahci libahci
[   20.745149] RIP: 0010:[<ffffffffa014bb6b>]  [<ffffffffa014bb6b>] CntlOidRTBssidProc+0x7b/0x570 [rt3572sta]
[   20.745224]  [<ffffffffa016a153>] ? RTUSBWriteMACRegister+0x43/0x60 [rt3572sta]
[   20.745233]  [<ffffffffa016aa17>] ? RTUSBWriteBBPRegister+0xb7/0x100 [rt3572sta]
[   20.745243]  [<ffffffffa014c125>] CntlIdleProc+0xc5/0x190 [rt3572sta]
[   20.745253]  [<ffffffffa014ef38>] MlmeCntlMachinePerformAction+0xe8/0x290 [rt3572sta]
[   20.745260]  [<ffffffffa0110471>] ? MlmeDequeue+0x61/0x80 [rt3572sta]
[   20.745267]  [<ffffffffa011167f>] MlmeHandler+0x18f/0x2c0 [rt3572sta]
[   20.745278]  [<ffffffffa0173770>] ? MlmeThread+0x0/0xb0 [rt3572sta]
[   20.745285]  [<ffffffffa0173800>] MlmeThread+0x90/0xb0 [rt3572sta]
[   20.745317] RIP  [<ffffffffa014bb6b>] CntlOidRTBssidProc+0x7b/0x570 [rt3572sta]
~$ 

```

This is just after a reboot, when the systray menu shows brecWFII5 connected, but the menu's wireless-signal icon is still animated as if it's searching.  After I issued the terminal commands and composed this message, all the SSIDs were shown as disconnected.  I chose brecWFII5 from the menu and the icon changed from up-down arrows (reflecting the ethernet connection) to the animated wireless one.

---

### Post by praseodym on 2011-12-22
Check the file /etc/Wireless/RT2870STA/RT2870STA.dat. Adjust the SSID there "11n-AP"
> ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT3572STA"
and the wireless key to yours.

Did you update/install the package **linux-firmware**?

Why using 2 different NWs? Do you want to connect randomly with different clients with different wireless devices of different capabilities concerning 2,4 and 5 GHz region? Or do you want to just connect randomly to one of those with one client?

---

### Post by brec on 2011-12-22
> **praseodym said:**
> Check the file /etc/Wireless/RT2870STA/RT2870STA.dat. Adjust the SSID there "11n-AP"

...

and the wireless key to yours.


The only SSID in the file is
SSID=brecWFII

> 
Did you update/install the package **linux-firmware**?


synaptic says it is installed.

> 
Why using 2 different NWs? Do you want to connect randomly with different clients with different wireless devices of different capabilities concerning 2,4 and 5 GHz region? Or do you want to just connect randomly to one of those with one client?

I recently upgraded my router and wireless access point from single to dual band to get the better range of the 5GHz band for new clients.  Some of the existing clients are single- (2.4GHz) band only.  I had a 2.4GHz USB adapter that was working on this client, but alas I seemed to have fried it by absent-mindedly inserting it into a SATA connector next to a USB connector.  I replaced it with the Engenius device in order to use 5GHz.

This morning after powering up the system with the USB adapter inserted it didn't let me in via ssh (my usual way of interfacing), Chromium Browser didn't start, and iwconfig hung.  I restarted without the Engenius device.

---

### Post by praseodym on 2011-12-22
On Ubuntu clients you can add the MAC-address of the router and therefore the coresponding "Cell" _additionally_ to the ESSID in the field "**BSSID**" of the network-manager applet.

> ```
          Cell 02 - Address: [COLOR="Red"]C0:C1:C0:A2:03:[COLOR="Cyan"]93[/COLOR][/COLOR] [COLOR="Lime"]<< different![/COLOR]
                    Protocol:802.11[COLOR="Cyan"]b/g/n[/COLOR]
                    ESSID:"brecWFII"   ### <-- my 2.4GHz SSID
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/100  Signal level=-83 dBm  Noise level=-78 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700103AE4BE2606DC387A22C22845A1BEA63C103C000103
          Cell 03 - Address: [COLOR="Red"]C0:C1:C0:A2:03:[COLOR="Cyan"]94[/COLOR][/COLOR] [COLOR="Lime"]<< different![/COLOR]
                    Protocol:802.11[COLOR="Cyan"]a/n[/COLOR]
```
Additionally Cell 03 only shows a+n mode, while cell 02 shows b+g+n!

---

### Post by brec on 2011-12-22
> **praseodym said:**
> On Ubuntu clients you can add the MAC-address of the router and therefore the coresponding "Cell" _additionally_ to the ESSID in the field "**BSSID**" of the network-manager applet.

In the applet I deleted the brecWFII (Cell 02) connection and entered the brecWFII5 (Cell 03) MAC address in the BSSID field.  After restart it still doesn't connect.

> 
Additionally Cell 03 only shows a+n mode, while cell 02 shows b+g+n!

802.11 b/g are 2.4GHz only.  802.11a is 5GHz only.

---

### Post by praseodym on 2011-12-22
Why not creating two profiles?

---

### Post by brec on 2011-12-22
> **praseodym said:**
> Why not creating two profiles?

The applet wouldn't let me edit the 5GHz profile to put in the BSSID -- it was all greyed-out -- until I deleted the other one.

I just ordered another 2.4GHz-only USB adapter to replace the one I fried (AirLink101 AWLL5088 Wireless N 150 Ultra Mini USB Adapter, $13.06 at Amazon).  It worked out of the box.  If I don't get a solution for the Engenius one I'll just go back to the AirLink101.

---

### Post by praseodym on 2011-12-22
Tried to start the applet from terminal:

```
gksu nm-connection-editor
```
for editing the 5 GHz profile?

---

### Post by brec on 2011-12-22
> **praseodym said:**
> Tried to start the applet from terminal:

```
gksu nm-connection-editor
```
for editing the 5 GHz profile?

No, I did it locally with a mouse.

---

