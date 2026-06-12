---
title: "Lenovo G570 - Ralink RT3090 Wireless 802.11n not working"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by dc10 on 2012-05-31
Hi,

I have a Lenovo G570 machine.
Wireless work properly from within windows.
From Ubuntu, it used to work but today suddenly it didn't work.

I'll paste some things that could be useful:

```

uname -a:
Linux ubuntu 3.0.0-20-generic #34-Ubuntu SMP Tue May 1 17:24:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
 
lspci -nn:
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series] [1002:68e4]
07:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
08:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

lsmod:
Module                  Size  Used by
rfcomm                 47946  8 
bnep                   18436  2 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62190  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33390  4 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
snd_hwdep              13668  1 snd_hda_codec
fglrx                2928969  0 
rt2x00pci              14578  1 rt2800pci
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00lib              54461  3 rt2800pci,rt2800lib,rt2x00pci
i915                  575554  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72711  0 
mac80211              462046  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29991  2 snd_pcm,snd_seq
drm_kms_helper         42558  1 i915
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   236290  3 i915,drm_kms_helper
videodev               93004  1 uvcvideo
btusb                  18600  2 
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 rt2x00lib,mac80211
bluetooth             166150  23 rfcomm,bnep,btusb
v4l2_compat_ioctl32    17083  1 videodev
soundcore              12680  1 snd
ideapad_laptop         13871  0 
psmouse                73882  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
eeprom_93cx6           12725  1 rt2800pci
serio_raw              13166  0 
mei                    41480  0 
video                  19597  1 i915
sparse_keymap          13890  1 ideapad_laptop
usbhid                 47198  0 
hid                    95463  1 usbhid
atl1c                  41681  0 
ahci                   26002  1 
libahci                26861  1 ahci
 
nm-tool:

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unmanaged
  Default:           no
  HW Address:        DC:0E:A1:61:1C:DA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unmanaged
  Default:           no
  HW Address:        60:D8:19:24:47:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


 
rfkill list all:
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
 
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:61:1c:da  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 60:d8:19:24:47:52  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Anny suggestion would really be appreciated.

Thanks!

---

### Post by dc10 on 2012-05-31
Forgot to mention that the output of lshw -C network shows wlan0 as unmanaged.

---

### Post by dc10 on 2012-06-01
Any suggestion/help?

Thanks! :)

---

### Post by praseodym on 2012-06-01
Anything seems "on". Please show
```
iwconfig
dmesg | grep rt2
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
route -n
```
Any chance for a cable connection? If yes, try this driver:

[http://forum.ubuntuusers.de/post/2666022/](http://forum.ubuntuusers.de/post/2666022/)
rt2800pci needs to be unloaded

---

### Post by dc10 on 2012-06-02
```

iwconfig:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
 
dmesg | grep rt2
[   40.326290] rt2800pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   40.326321] rt2800pci 0000:08:00.0: setting latency timer to 64
[   40.371478] Registered led device: rt2800pci-phy0::radio
[   40.371494] Registered led device: rt2800pci-phy0::assoc
[   40.371507] Registered led device: rt2800pci-phy0::quality
 
cat /etc/resolv.conf
# Generated by NetworkManager
 
iwlist chan
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
 
sudo iwlist scan
 
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

No chance for wired connection.
Thanks for your support

---

### Post by praseodym on 2012-06-02
Edit the wireless connection in the NM->IPv4 settings->Change to "Automatic (DHCP), addresses only" and add

```
8.8.8.8, 8.8.4.4
```
as DNS-servers. Restart the NW. Any button/switches/keys/key combinations to turn the power on?

> ```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]0 dBm[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by dc10 on 2012-06-02
I've tried configuring the Network Manager as you said but continues not working. Tried to switch off/on the wireless button but nothing.

---

### Post by praseodym on 2012-06-02
Any key combination like Fn+F2 or sth.?

Check:

1.) BIOS in "Config -> Network -> Wireless LAN ..." if it is activated

2.) Activating the button via windows (if dualboot)

3.) Hardware-Reset:

[LIST]
[*] Shutdown and shut off

[*] take out battery and current cable

[*] Hold the "On"-button for at least 30 seconds

[*] Battery and/or current cable in
[/LIST]
4.) BIOS default settings
[LIST]
[*]Reboot and press F1 (should be) to enter BIOS

[*] F9 for default settings

[*] F10 to save&exit

[*] if the logo appears, press the button to shutdown

[*] Turn on again
[/LIST]

---

### Post by dc10 on 2012-06-02
> **praseodym said:**
> Any key combination like Fn+F2 or sth.?

Check:

1.) BIOS in "Config -> Network -> Wireless LAN ..." if it is activated

2.) Activating the button via windows (if dualboot)

3.) Hardware-Reset:

[LIST]
[*] Shutdown and shut off

[*] take out battery and current cable

[*] Hold the "On"-button for at least 30 seconds

[*] Battery and/or current cable in
[/LIST]
4.) BIOS default settings
[LIST]
[*]Reboot and press F1 (should be) to enter BIOS

[*] F9 for default settings

[*] F10 to save&exit

[*] if the logo appears, press the button to shutdown

[*] Turn on again
[/LIST]

Nothing of this worked.

Yes, I have dualboot together with windows. Inside windows wireless works properly.

I've entered again on ubuntu, and some more things were blocked again doinng a rfkill list all:

```

$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        DC:0E:A1:61:1C:DA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        60:D8:19:24:47:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
$ lspci -nn | egrep "Ethernet|Network"
07:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
08:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]

$ sudo lshw -C network
[sudo] password for alex: 
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:61:1c:da
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:e0500000-e053ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 60:d8:19:24:47:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.0.0-20-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:e0400000-e040ffff

```

---

### Post by praseodym on 2012-06-03
Now it shows "soft block". Try

> sudo rfkill unblock all

---

### Post by dc10 on 2012-06-03
When I entered Ubuntu again all soft/hard things were already unblocked. Anyway I executed a sudo rfkill unblock all but without any positive effect :(

---

### Post by praseodym on 2012-06-03
Check, if Windows deactivates the card. Some buttons only work at boot-up!

---

### Post by dc10 on 2012-06-03
I don't think windows deactivate the card because I'm writing this from within windows.

---

### Post by praseodym on 2012-06-03
I mean, if Windows shuts off the card during the shutdown.

---

### Post by dc10 on 2012-06-03
Mmmm no. If I boot Windows, then restart/shutdown and then boot on Ubuntu the led indicator for wireless card continues being ON.

---

### Post by dc10 on 2012-06-04
Any other suggestions would be appreciated.

Thanks

---

