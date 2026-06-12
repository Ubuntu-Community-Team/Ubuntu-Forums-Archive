---
title: "updated to 11.10 not wireless"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by angryfox on 2012-06-28
a few days ago i updated my system to ubuntu 11.10 and my wireless card wont work anymore. please help!
im using a dell latitude d620

angryfox@MrSmith:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:ecffc000-ecffffff

---

### Post by josephmills on 2012-06-28
can we see a 
```
lspci -nn | grep 14e4 
```
and also 
```
lsmod
```
and 
```
rfkill list all 
```

---

### Post by angryfox on 2012-06-28
angryfox@MrSmith:~$ angryfox@MrSmith:~$ sudo lshw -C network
angryfox@MrSmith:~$: command not found
angryfox@MrSmith:~$   *-network UNCLAIMED     
*-network: command not found
angryfox@MrSmith:~$        description: Network controller
description:: command not found
angryfox@MrSmith:~$        product: BCM4311 802.11b/g WLAN
product:: command not found
angryfox@MrSmith:~$        vendor: Broadcom Corporation
vendor:: command not found
angryfox@MrSmith:~$        physical id: 0
physical: command not found
angryfox@MrSmith:~$        bus info: pci@0000:0c:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
angryfox@MrSmith:~$        version: 01
version:: command not found
angryfox@MrSmith:~$        width: 32 bits
width:: command not found
angryfox@MrSmith:~$        clock: 33MHz
No command 'clock:' found, did you mean:
 Command 'clock' from package 'xview-clients' (universe)
clock:: command not found
angryfox@MrSmith:~$        capabilities: pm msi pciexpress bus_master cap_list
capabilities:: command not found
angryfox@MrSmith:~$        configuration: latency=0
configuration:: command not found
angryfox@MrSmith:~$        resources: memory:ecffc000-ecffffff
resources:: command not found

and 


angryfox@MrSmith:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
nvidia              10390874  34 
snd_hda_intel          28358  2 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio         100930  1 
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
joydev                 17393  0 
snd                    55902  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
video                  19069  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
wmi                    18744  1 dell_wmi
psmouse                73673  0 
serio_raw              12990  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0 

and

0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by josephmills on 2012-06-28
can we see what I asked for plz 
```
lspci -nn | grep 14e4
```

---

### Post by angryfox on 2012-06-28
angryfox@MrSmith:~$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by josephmills on 2012-06-28
> **angryfox said:**
> angryfox@MrSmith:~$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Thanks 

do this 
```
sudo apt-get install b43-fwcutter 
```
then 
```
sudo apt-get install firmware-b43-installer 
 
```
then 
```
sudo modprobe b43 
```
then 
```
rfkill unblock all 
```
do you have wireless ?
If not post 
```
rfkill list all 
```
and 
```
lsmod
```
and 
```
dmesg | grep b43 
```

thanks

---

### Post by angryfox on 2012-06-28
nope still not working

angryfox@MrSmith:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
and

angryfox@MrSmith:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
b43                   318816  0 
ssb                    50682  1 b43
mac80211              393421  1 b43
cfg80211              172427  2 b43,mac80211
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
nvidia              10390874  34 
snd_hda_intel          28358  4 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_usb_audio         100930  2 
snd_pcm                80435  5 snd_hda_intel,snd_hda_codec,snd_usb_audio
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        24558  1 snd_usb_audio
snd_seq_midi           13132  0 
uvcvideo               67271  1 
videodev               85626  2 uvcvideo
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
joydev                 17393  0 
snd                    55902  21 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
video                  19069  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
wmi                    18744  1 dell_wmi
psmouse                73673  0 
serio_raw              12990  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0 

and last

angryfox@MrSmith:~$ dmesg | grep b43
[ 3763.616625] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 3763.616645] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[ 3763.749535] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 3763.912099] Registered led device: b43-phy0::tx
[ 3763.912192] Registered led device: b43-phy0::rx
[ 3763.912292] Registered led device: b43-phy0::radio

---

### Post by josephmills on 2012-06-28
reboot the computer if still no wireless try to disable networing and re-enable it under the panel. try
```
sudo rmmod dell_wmi
```
then post here the output of 
```
dmesg
```

---

### Post by angryfox on 2012-06-28
[    0.310959] pnp: PnP ACPI: found 14 devices
[    0.310961] ACPI: ACPI bus type pnp unregistered
[    0.310966] PnPBIOS: Disabled by ACPI PNP
[    0.347573] PCI: max bus depth: 2 pci_try_num: 3
[    0.347648] pci 0000:00:1e.0: BAR 15: assigned [mem 0xc0000000-0xc3ffffff pref]
[    0.347652] pci 0000:00:1e.0: BAR 14: assigned [mem 0xc4000000-0xc9ffffff]
[    0.347657] pci 0000:00:1e.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.347662] pci 0000:00:1c.2: BAR 15: assigned [mem 0xca000000-0xca1fffff 64bit pref]
[    0.347666] pci 0000:00:1c.2: BAR 13: assigned [io  0x3000-0x3fff]
[    0.347671] pci 0000:00:1c.1: BAR 15: assigned [mem 0xca200000-0xca3fffff 64bit pref]
[    0.347675] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.347679] pci 0000:00:1c.0: BAR 14: assigned [mem 0xca400000-0xca5fffff]
[    0.347683] pci 0000:00:1c.0: BAR 15: assigned [mem 0xca600000-0xca7fffff 64bit pref]
[    0.347687] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.347692] pci 0000:01:00.0: BAR 6: assigned [mem 0xef000000-0xef01ffff pref]
[    0.347696] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.347698] pci 0000:00:01.0:   bridge window [io  disabled]
[    0.347704] pci 0000:00:01.0:   bridge window [mem 0xed000000-0xefefffff]
[    0.347708] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.347715] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.347719] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.347727] pci 0000:00:1c.0:   bridge window [mem 0xca400000-0xca5fffff]
[    0.347733] pci 0000:00:1c.0:   bridge window [mem 0xca600000-0xca7fffff 64bit pref]
[    0.347742] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.347746] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.347754] pci 0000:00:1c.1:   bridge window [mem 0xecf00000-0xecffffff]
[    0.347760] pci 0000:00:1c.1:   bridge window [mem 0xca200000-0xca3fffff 64bit pref]
[    0.347769] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.347773] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.347781] pci 0000:00:1c.2:   bridge window [mem 0xece00000-0xecefffff]
[    0.347787] pci 0000:00:1c.2:   bridge window [mem 0xca000000-0xca1fffff 64bit pref]
[    0.347797] pci 0000:03:01.0: BAR 15: assigned [mem 0xc0000000-0xc3ffffff pref]
[    0.347801] pci 0000:03:01.0: BAR 16: assigned [mem 0xc4000000-0xc7ffffff]
[    0.347804] pci 0000:03:01.0: BAR 0: assigned [mem 0xc8000000-0xc8000fff]
[    0.347811] pci 0000:03:01.0: BAR 0: set to [mem 0xc8000000-0xc8000fff] (PCI address [0xc8000000-0xc8000fff])
[    0.347815] pci 0000:03:01.0: BAR 13: assigned [io  0x2000-0x20ff]
[    0.347818] pci 0000:03:01.0: BAR 14: assigned [io  0x2400-0x24ff]
[    0.347821] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.347824] pci 0000:03:01.0:   bridge window [io  0x2000-0x20ff]
[    0.347830] pci 0000:03:01.0:   bridge window [io  0x2400-0x24ff]
[    0.347836] pci 0000:03:01.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[    0.347843] pci 0000:03:01.0:   bridge window [mem 0xc4000000-0xc7ffffff]
[    0.347849] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.347854] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.347861] pci 0000:00:1e.0:   bridge window [mem 0xc4000000-0xc9ffffff]
[    0.347867] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xc3ffffff pref]
[    0.347899] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.347905] pci 0000:00:01.0: setting latency timer to 64
[    0.347914] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.347920] pci 0000:00:1c.0: setting latency timer to 64
[    0.347932] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.347938] pci 0000:00:1c.1: setting latency timer to 64
[    0.347951] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.347957] pci 0000:00:1c.2: setting latency timer to 64
[    0.347967] pci 0000:00:1e.0: setting latency timer to 64
[    0.347977] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.347983] pci 0000:03:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.347992] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.348017] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.348020] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.348023] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.348026] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xefffffff]
[    0.348029] pci_bus 0000:00: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.348032] pci_bus 0000:00: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.348035] pci_bus 0000:00: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.348038] pci_bus 0000:00: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.348041] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.348045] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xffafffff]
[    0.348048] pci_bus 0000:01: resource 1 [mem 0xed000000-0xefefffff]
[    0.348051] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.348054] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.348057] pci_bus 0000:0b: resource 1 [mem 0xca400000-0xca5fffff]
[    0.348060] pci_bus 0000:0b: resource 2 [mem 0xca600000-0xca7fffff 64bit pref]
[    0.348063] pci_bus 0000:0c: resource 0 [io  0x4000-0x4fff]
[    0.348066] pci_bus 0000:0c: resource 1 [mem 0xecf00000-0xecffffff]
[    0.348069] pci_bus 0000:0c: resource 2 [mem 0xca200000-0xca3fffff 64bit pref]
[    0.348073] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.348076] pci_bus 0000:09: resource 1 [mem 0xece00000-0xecefffff]
[    0.348079] pci_bus 0000:09: resource 2 [mem 0xca000000-0xca1fffff 64bit pref]
[    0.348083] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.348086] pci_bus 0000:03: resource 1 [mem 0xc4000000-0xc9ffffff]
[    0.348089] pci_bus 0000:03: resource 2 [mem 0xc0000000-0xc3ffffff pref]
[    0.348092] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.348095] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.348098] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.348101] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.348104] pci_bus 0000:03: resource 8 [mem 0xc0000000-0xefffffff]
[    0.348107] pci_bus 0000:03: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.348110] pci_bus 0000:03: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.348113] pci_bus 0000:03: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.348116] pci_bus 0000:03: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.348119] pci_bus 0000:03: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.348122] pci_bus 0000:03: resource 14 [mem 0xfee10000-0xffafffff]
[    0.348125] pci_bus 0000:04: resource 0 [io  0x2000-0x20ff]
[    0.348128] pci_bus 0000:04: resource 1 [io  0x2400-0x24ff]
[    0.348131] pci_bus 0000:04: resource 2 [mem 0xc0000000-0xc3ffffff pref]
[    0.348134] pci_bus 0000:04: resource 3 [mem 0xc4000000-0xc7ffffff]
[    0.348191] NET: Registered protocol family 2
[    0.348279] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.348582] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.349100] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.349363] TCP: Hash tables configured (established 131072 bind 65536)
[    0.349366] TCP reno registered
[    0.349369] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.349379] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.349487] NET: Registered protocol family 1
[    0.349546] pci 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.349570] pci 0000:00:1d.0: PCI INT A disabled
[    0.349583] pci 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.349606] pci 0000:00:1d.1: PCI INT B disabled
[    0.349620] pci 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.349643] pci 0000:00:1d.2: PCI INT C disabled
[    0.349657] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.349679] pci 0000:00:1d.3: PCI INT D disabled
[    0.349691] pci 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.349728] pci 0000:00:1d.7: PCI INT A disabled
[    0.349759] pci 0000:01:00.0: Boot video device
[    0.349776] PCI: CLS 64 bytes, default 64
[    0.349784] Simple Boot Flag at 0x79 set to 0x1
[    0.350226] audit: initializing netlink socket (disabled)
[    0.350238] type=2000 audit(1340887882.344:1): initialized
[    0.382629] highmem bounce pool size: 64 pages
[    0.382636] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.396750] VFS: Disk quotas dquot_6.5.2
[    0.396841] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.397685] fuse init (API version 7.16)
[    0.397804] msgmni has been set to 1656
[    0.398215] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.398248] io scheduler noop registered
[    0.398251] io scheduler deadline registered
[    0.398268] io scheduler cfq registered (default)
[    0.398410] pcieport 0000:00:01.0: setting latency timer to 64
[    0.398453] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.398513] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.398573] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.398664] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.398724] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.398813] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.398873] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.398988] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.399018] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.399087] intel_idle: MWAIT substates: 0x22220
[    0.399089] intel_idle: does not run on family 6 model 15
[    0.399592] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.400052] ACPI: AC Adapter [AC] (on-line)
[    0.400145] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.400542] ACPI: Lid Switch [LID]
[    0.400595] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.400601] ACPI: Power Button [PBTN]
[    0.400650] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.400654] ACPI: Sleep Button [SBTN]
[    0.400706] ACPI: acpi_idle registered with cpuidle
[    0.424588] thermal LNXTHERM:00: registered as thermal_zone0
[    0.424592] ACPI: Thermal Zone [THM] (63 C)
[    0.424615] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.424665] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.424697] ERST: Table is not found!
[    0.424788] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.445405] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.460463] isapnp: Scanning for PnP cards...
[    0.462897] ACPI: Battery Slot [BAT1] (battery absent)
[    0.470344] ACPI: Battery Slot [BAT0] (battery present)
[    0.611184] Freeing initrd memory: 13324k freed
[    0.816867] isapnp: No Plug & Play device found
[    0.842485] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.842841] Linux agpgart interface v0.103
[    0.844629] brd: module loaded
[    0.845385] loop: module loaded
[    0.845568] ata_piix 0000:00:1f.2: version 2.13
[    0.845588] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.845595] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.845647] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.846057] scsi0 : ata_piix
[    0.846178] scsi1 : ata_piix
[    0.847651] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.847654] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.848135] Fixed MDIO Bus: probed
[    0.848166] PPP generic driver version 2.4.2
[    0.848218] tun: Universal TUN/TAP device driver, 1.6
[    0.848221] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.848321] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.848341] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.848357] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.848362] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.848409] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.848435] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.848449] ehci_hcd 0000:00:1d.7: debug port 1
[    0.852352] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.852372] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[    0.868026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.868179] hub 1-0:1.0: USB hub found
[    0.868184] hub 1-0:1.0: 8 ports detected
[    0.868290] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.868306] uhci_hcd: USB Universal Host Controller Interface driver
[    0.868332] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.868341] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.868345] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.868391] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.868423] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.868572] hub 2-0:1.0: USB hub found
[    0.868578] hub 2-0:1.0: 2 ports detected
[    0.868658] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.868667] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.868672] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.868712] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.868754] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.868900] hub 3-0:1.0: USB hub found
[    0.868905] hub 3-0:1.0: 2 ports detected
[    0.868985] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.868994] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.868998] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.869038] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.869080] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.869227] hub 4-0:1.0: USB hub found
[    0.869231] hub 4-0:1.0: 2 ports detected
[    0.869310] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.869319] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.869323] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.869371] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.869413] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.869561] hub 5-0:1.0: USB hub found
[    0.869566] hub 5-0:1.0: 2 ports detected
[    0.869717] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.872755] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.872763] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.872898] mousedev: PS/2 mouse device common for all mice
[    0.873081] rtc_cmos 00:06: RTC can wake from S4
[    0.873212] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.873254] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.873362] device-mapper: uevent: version 1.0.3
[    0.873473] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.873513] EISA: Probing bus 0 at eisa.0
[    0.873515] EISA: Cannot allocate resource for mainboard
[    0.873518] Cannot allocate resource for EISA slot 1
[    0.873520] Cannot allocate resource for EISA slot 2
[    0.873523] Cannot allocate resource for EISA slot 3
[    0.873525] Cannot allocate resource for EISA slot 4
[    0.873527] Cannot allocate resource for EISA slot 5
[    0.873530] Cannot allocate resource for EISA slot 6
[    0.873532] Cannot allocate resource for EISA slot 7
[    0.873534] Cannot allocate resource for EISA slot 8
[    0.873537] EISA: Detected 0 cards.
[    0.873548] cpufreq-nforce2: No nForce2 chipset.
[    0.873626] cpuidle: using governor ladder
[    0.873751] cpuidle: using governor menu
[    0.873753] EFI Variables Facility v0.08 2004-May-17
[    0.874132] TCP cubic registered
[    0.874301] NET: Registered protocol family 10
[    0.875093] NET: Registered protocol family 17
[    0.875112] Registering the dns_resolver key type
[    0.875148] Using IPI No-Shortcut mode
[    0.875246] PM: Hibernation image not present or could not be loaded.
[    0.875260] registered taskstats version 1
[    0.881609] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.890094]   Magic number: 0:715:886
[    0.890207] rtc_cmos 00:06: setting system clock to 2012-06-28 12:51:23 UTC (1340887883)
[    0.890963] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.890965] EDD information not available.
[    1.008459] ata2.00: ATAPI: _NEC DVD+/-RW ND-6650A, 102C, max UDMA/33
[    1.008845] ata1.00: ATA-8: TOSHIBA MK8052GSX, LV011D, max UDMA/100
[    1.008848] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.016489] ata1.00: configured for UDMA/100
[    1.016664] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8052GS LV01 PQ: 0 ANSI: 5
[    1.016821] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.016856] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.016886] sd 0:0:0:0: [sda] Write Protect is off
[    1.016890] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.016926] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.024478] ata2.00: configured for UDMA/33
[    1.027482] scsi 1:0:0:0: CD-ROM            _NEC     DVD+-RW ND-6650A 102C PQ: 0 ANSI: 5
[    1.028993] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.028997] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.029106] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.029166] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.079886]  sda: sda1 sda2 < sda5 >
[    1.080370] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.080449] Freeing unused kernel memory: 696k freed
[    1.080731] Write protecting the kernel text: 5348k
[    1.080799] Write protecting the kernel read-only data: 2196k
[    1.101109] udevd[87]: starting version 173
[    1.174226] tg3.c:v3.119 (May 18, 2011)
[    1.174248] tg3 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.174261] tg3 0000:09:00.0: setting latency timer to 64
[    1.200811] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:1c:23:00:8a:48
[    1.200817] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.200821] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.200824] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.348075] usb 1-7: new high speed USB device number 4 using ehci_hcd
[    1.473260] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.804047] usb 2-2: new full speed USB device number 2 using uhci_hcd
[    1.954524] hub 2-2:1.0: USB hub found
[    1.956486] hub 2-2:1.0: 4 ports detected
[    2.200046] usb 3-2: new low speed USB device number 2 using uhci_hcd
[    2.461486] usb 2-2.3: new full speed USB device number 3 using uhci_hcd
[    2.591555] hub 2-2.3:1.0: USB hub found
[    2.593482] hub 2-2.3:1.0: 3 ports detected
[    2.673486] usb 2-2.4: new full speed USB device number 4 using uhci_hcd
[    2.917493] usb 2-2.3.2: new full speed USB device number 5 using uhci_hcd
[   17.921760] udevd[316]: starting version 173
[   17.979109] lp: driver loaded but no devices found
[   18.011820] Adding 3229028k swap on /dev/sda5.  Priority:-1 extents:1 across:3229028k 
[   18.062746] nvidia: module license 'NVIDIA' taints kernel.
[   18.062751] Disabling lock debugging due to kernel taint
[   18.080198] intel_rng: FWH not detected
[   18.102436] leds_ss4200: no LED devices found
[   19.167937] wmi: Mapper loaded
[   19.195540] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:21/LNXVIDEO:00/input/input4
[   19.195817] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   19.195975] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   19.445351] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.445363] nvidia 0000:01:00.0: setting latency timer to 64
[   19.445369] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.455547] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01c2]
[   19.455576] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   19.455717] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
[   19.457327] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[   19.457493] generic-usb 0003:045E:0047.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2/input0
[   19.457528] usbcore: registered new interface driver usbhid
[   19.457530] usbhid: USB HID core driver
[   19.458441] Linux video capture interface: v2.00
[   19.459221] uvcvideo: Found UVC 1.00 device A4 TECH USB2.0 PC Camera J (0ac8:c40a)
[   19.471400] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.486919] type=1400 audit(1340909502.092:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=557 comm="apparmor_parser"
[   19.487390] type=1400 audit(1340909502.092:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=557 comm="apparmor_parser"
[   19.487697] type=1400 audit(1340909502.092:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=557 comm="apparmor_parser"
[   19.489120] Bluetooth: Core ver 2.16
[   19.489188] NET: Registered protocol family 31
[   19.489190] Bluetooth: HCI device and connection manager initialized
[   19.489193] Bluetooth: HCI socket layer initialized
[   19.489196] Bluetooth: L2CAP socket layer initialized
[   19.489383] input: A4 TECH USB2.0 PC Camera J as /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/input/input6
[   19.489566] usbcore: registered new interface driver uvcvideo
[   19.489569] USB Video Class driver (v1.1.0)
[   19.493376] Bluetooth: SCO socket layer initialized
[   19.494086] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   19.503241] usbcore: registered new interface driver btusb
[   19.584890] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 18
[   19.584896] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[   19.584901] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   19.585085] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[   19.585089] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: excluding 0x2000-0x20ff 0x2400-0x24ff
[   19.617107] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.622248] 
[   19.622255] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xc4000000-0xc9ffffff]
[   19.622261] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc4000000-0xc9ffffff: excluding 0xc4000000-0xc81fffff
[   19.622277] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xc0000000-0xc3ffffff pref]
[   19.622281] pcmcia_socket pcmcia_socket0: cs: memory probe 0xc0000000-0xc3ffffff: excluding 0xc0000000-0xc3ffffff
[   19.684936] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.685007] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   19.685043] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.699809] usbcore: registered new interface driver snd-usb-audio
[   19.734715] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   19.780755] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.780947] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.805243] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   19.807349] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   19.809533] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.810305] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc80-0xcbf
[   19.810940] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   19.811015] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   19.811087] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   19.811683] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.956404] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input10
[   19.976388] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input11
[   20.035697] type=1400 audit(1340909502.640:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=835 comm="apparmor_parser"
[   20.046565] type=1400 audit(1340909502.652:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=834 comm="apparmor_parser"
[   20.046886] type=1400 audit(1340909502.652:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=836 comm="apparmor_parser"
[   20.048347] type=1400 audit(1340909502.656:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=836 comm="apparmor_parser"
[   20.048654] type=1400 audit(1340909502.656:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=836 comm="apparmor_parser"
[   20.068415] type=1400 audit(1340909502.676:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=840 comm="apparmor_parser"
[   20.072591] type=1400 audit(1340909502.680:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=840 comm="apparmor_parser"
[   20.254502] init: failsafe main process (763) killed by TERM signal
[   20.257175] init: apport pre-start process (897) terminated with status 1
[   20.299601] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   20.299605] vesafb: scrolling: redraw
[   20.299609] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   20.301508] vesafb: framebuffer at 0xd0000000, mapped to 0xf9c00000, using 3072k, total 3072k
[   20.301599] fbcon: VESA VGA (fb0) is primary device
[   20.301707] Console: switching to colour frame buffer device 128x48
[   20.301736] fb0: VESA VGA frame buffer device
[   20.305405] init: apport post-stop process (940) terminated with status 1
[   20.356662] ppdev: user-space parallel port driver
[   20.405653] init: gdm main process (980) killed by TERM signal
[   21.112945] Bluetooth: RFCOMM TTY layer initialized
[   21.112951] Bluetooth: RFCOMM socket layer initialized
[   21.112953] Bluetooth: RFCOMM ver 1.11
[   21.141839] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.141843] Bluetooth: BNEP filters: protocol multicast
[   23.426149] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   23.641535] init: plymouth-stop pre-start process (1267) terminated with status 1
[   25.543092] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.019178] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   26.064425] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.210998] tg3 0000:09:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   29.211003] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   29.211192] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.580448] tg3 0000:09:00.0: PME# enabled
[   34.580481] tg3 0000:09:00.0: wake-up capability enabled by ACPI
[   34.616113] tg3 0000:09:00.0: BAR 0: set to [mem 0xecef0000-0xecefffff 64bit] (PCI address [0xecef0000-0xecefffff])
[   34.616212] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   34.649234] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.192078] tg3 0000:09:00.0: BAR 0: set to [mem 0xecef0000-0xecefffff 64bit] (PCI address [0xecef0000-0xecefffff])
[   35.192168] tg3 0000:09:00.0: irq 45 for MSI/MSI-X
[   35.224916] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   37.239307] audit_printk_skb: 30 callbacks suppressed
[   37.239311] type=1400 audit(1340909519.844:22): apparmor="DENIED" operation="open" parent=1675 profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=1725 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   37.683825] tg3 0000:09:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   37.683830] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   37.684046] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   45.224050] CE: hpet increased min_delta_ns to 20113 nsec
[   48.304013] eth0: no IPv6 routers present

---

### Post by angryfox on 2012-06-28
Still wont turn on. led indicator is still off only the bluetooth one is on

---

### Post by josephmills on 2012-06-28
> **angryfox said:**
> Still wont turn on. led indicator is still off only the bluetooth one is on

ok lets see 
```
rfkill list all 
```
and also 
```
lsmod
```

seems like the driver is not there on boot O_o

---

### Post by angryfox on 2012-06-28
angryfox@MrSmith:/var/cache/apt/archives$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

and

angryfox@MrSmith:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
sparse_keymap          13658  0 
snd_usb_audio         100930  2 
snd_hda_intel          28358  4 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
pcmcia                 39822  0 
snd_pcm                80435  5 snd_usb_audio,snd_hda_intel,snd_hda_codec
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               67271  1 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27428  0 
videodev               85626  2 uvcvideo
psmouse                73673  0 
usbhid                 41905  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
hid                    77367  1 usbhid
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18367  1 yenta_socket
nvidia              10390874  34 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19069  0 
wmi                    18744  0 
snd                    55902  21 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0

---

### Post by josephmills on 2012-06-28
> **angryfox said:**
> angryfox@MrSmith:/var/cache/apt/archives$ ```
rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
and
```

angryfox@MrSmith:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
sparse_keymap          13658  0 
snd_usb_audio         100930  2 
snd_hda_intel          28358  4 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
pcmcia                 39822  0 
snd_pcm                80435  5 snd_usb_audio,snd_hda_intel,snd_hda_codec
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24558  1 snd_usb_audio
btusb                  18160  2 
bluetooth             148869  23 bnep,rfcomm,btusb
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
uvcvideo               67271  1 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27428  0 
videodev               85626  2 uvcvideo
psmouse                73673  0 
usbhid                 41905  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
hid                    77367  1 usbhid
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_rsrc            18367  1 yenta_socket
nvidia              10390874  34 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19069  0 
wmi                    18744  0 
snd                    55902  21 snd_hda_codec_idt,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   132972  0
```


Ok the driver is not loading on start up we have to fix this. 

please open terminal and enter in 
```
gksudo gedit /etc/modules 
```
Enter your password and you should get a file that looks like this 
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```



We need to add one line at the end called [COLOR="Red"][SIZE="4"]b43[/SIZE][/COLOR]

Like this 
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
b43

```


then [COLOR="Red"]PROOF READ[/COLOR]
then save and close gedit then go back to the terminal.

enter in
```
sudo modprobe b43
```

then if you have wireless great if not enter in 

```
sudo modprobe dell_wmi
```

Now you should have wireless if not. 

reboot then post 
```
dmesg | grep b43
```

Thanks (and you are almost there)

---

### Post by angryfox on 2012-06-28
Yaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaah! it works! thanks your the best!

---

### Post by josephmills on 2012-06-28
Glade to see that !!  You also rocked it too :D Great Job could you mark this as solved please and thanks.

---

