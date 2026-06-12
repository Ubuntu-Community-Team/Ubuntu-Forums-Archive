---
title: "HP ENVY dv7 enable wifi lan"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by cico.sail on 2013-04-03
Hi
I have a new notebook where I can't enable the wifi card.
The command by keyboard not works so I try to use the command line.
If I type
```
lshw -C network
```
I see that my card is named "ra0"
Then I type 
```
ifconfig ra0 up
```
and
```
iwlist ra0 scan
```
so I see my wifi net
but if I see in the GUI tool bar wifi it's always disabled.
If I type the commands
```
rfkill unblock all
rfkill list
```
I have
```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```
Is there a way to disable the hard block?

---

### Post by jackyboy633 on 2013-04-03
Hi there,

Please could you open a terminal and post the output of the following commands:
```
lsmod
```
```
lspci
```
This is to see what driver module you have installed, and this will help me fix your problem. :)

---

### Post by cico.sail on 2013-04-04
Hi jackyboy633

```
:~$ lsmod
Module                  Size  Used by
des_generic            21416  0 
md4                    12596  0 
vmnet                  55801  13 
vsock                  52876  0 
vmci                   91680  1 vsock
vmmon                  76138  0 
bnep                   18141  2 
rfcomm                 42652  0 
bluetooth             205000  10 bnep,rfcomm
compat                 14950  3 bnep,rfcomm,bluetooth
parport_pc             32689  0 
ppdev                  17074  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_idt      70210  1 
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
nls_utf8               12558  7 
cifs                  313935  12 
fscache                61094  1 cifs
nouveau               896008  1 
ttm                    83596  1 nouveau
joydev                 17458  0 
mxm_wmi                13022  1 nouveau
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
coretemp               13401  0 
kvm_intel             132760  0 
kvm                   414071  1 kvm_intel
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
mei                    40691  0 
microcode              22804  0 
snd_seq_midi_event     14900  1 snd_seq_midi
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                95595  0 
serio_raw              13216  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtsx_pci_ms            13012  0 
soundcore              15048  1 snd
i915                  520615  3 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
drm_kms_helper         49113  2 nouveau,i915
memstick               16555  1 rtsx_pci_ms
lpc_ich                17062  0 
drm                   288721  7 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13414  2 nouveau,i915
rt3290sta            1174375  0 
video                  19391  2 nouveau,i915
hp_accel               25977  0 
wmi                    19071  3 nouveau,mxm_wmi,hp_wmi
lis3lv02d              19830  1 hp_accel
input_polldev          13897  1 lis3lv02d
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
rtsx_pci_sdmmc         17476  0 
r8169                  61651  0 
ahci                   25721  3 
libahci                31192  1 ahci
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
rtsx_pci               28325  2 rtsx_pci_ms,rtsx_pci_sdmmc

```
And
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de3 (rev a1)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
0a:00.0 Network controller: Ralink corp. Device 3290
0a:00.1 Bluetooth: Ralink corp. Device 3298
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```
I should add that I installed the driver Ralink RT3290 using the instructions on the post
[http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290]("http://askubuntu.com/questions/229195/wireless-driver-how-to-load-manufacturers-sta-file-ralink-3290")
Regards

---

### Post by cico.sail on 2013-04-15
Up
No more suggestions?
After the installation of the driver Ralink RT3290 the problem is not solved.
To turn on the wifi char from keyboard I have to take a precise time of the boot between the boot SO selection and Ubuntu start.
However if I suceed, when the chart works the system crash to a black screen and message like:
```
Kernel panic - not syncing: Fatal exception in interupt
```

---

### Post by Bucky Ball on 2013-04-15
*Thread moved to **Networking & Wireless***

Actually, post the result of the first command you used:
```

sudo lshw -C network
```

That will give the driver, if any, in use and other relevant information. lspci doesn't yeild much info.

---

### Post by cico.sail on 2013-04-15
Hi Bucky, thanks for your attention.
To prevent crash the chart is currently disabled.
```
:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:74510000-7451ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 07
       serial: a0:b3:cc:4d:db:63
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=172.16.3.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:74404000-74404fff memory:74400000-74403fff

```

---

### Post by cico.sail on 2013-04-22
Up

---

