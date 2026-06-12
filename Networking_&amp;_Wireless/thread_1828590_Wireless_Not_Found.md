---
title: "Wireless Not Found"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by Somniac on 2011-08-19
Salutations.

I've decided to make the complete switch from Windows XP to Ubuntu: Codename Narwhal.

My main hang-up at the moment is getting online through the demonstration. I'm booting to a CD, as the external hard drive cannot be booted from on this, ahem, less than new desktop of mine.

This is my first time using Ubuntu. The installation checks off up to the Online part - what I'm looking for is a step by step in an easy to digest manner.

I have my MAC address, SSID, and Workgroup at the ready. However, I find I'm not able to get the hardware picked up (Zyxel) to begin this all.

Hope I'm making sense. Any suggestions on how to get this bad boy online pre-installation?

---

### Post by Somniac on 2011-08-19
Still no luck. Tried using the Zyxel driver for my M-302 (XP-compatible), but it completely farked that instance of Ubuntu.

Currently I still have Windows XP on this computer, and am just booting from the Ubuntu disk.

I also noticed none of my hardware comes up when I try to look it up on Ubuntu. My computer is six years old - what's my best bet for Ubuntu compatibility?

Any help would be immensely appreciated, and if there's any information I'm missing that's making this more difficult to answer than need be, I'm more than happy to grab more.

---

### Post by nm_geo on 2011-08-19
Please open a terminal and copy and paste the following commands in the terminal.  Then copy the results to the thread.

```
lspci -nn 
```

```
sudo lshw -C network
```

```
lsmod
```

Those will give enough information to start the process.

---

### Post by Somniac on 2011-08-23
> **nm_geo said:**
> ...

Hey Geo.

Thanks for your help, and sorry for the delay.

I got the following:

> ubuntu@ubuntu:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:04.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:05.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:06.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:0a.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0376] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0374] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0378] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR5513 802.11abg Wireless NIC [168c:0020] (rev 01)
01:08.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
01:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
07:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [GeForce 8800 GTS] [10de:0193] (rev a2)
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
sudo lshw -C network
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5513 802.11abg Wireless NIC
       vendor: Atheros Communications Inc.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: memory:effc0000-effdffff
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo lshw -C network
SCSI          

Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
binfmt_misc            13213  1 
snd_ctxfi              85192  2 
snd_pcm                80244  1 snd_ctxfi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  10 snd_ctxfi,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17322  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_ctxfi,snd_pcm
asus_atk0110           17664  0 
wacom                  41292  0 
nv_tco                 13331  0 
psmouse                73312  0 
k8temp                 12872  0 
serio_raw              12990  0 
i2c_nforce2            12906  0 
squashfs               35973  1 
aufs                  159344  4086 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
nouveau               621970  2 
usbhid                 41704  0 
ttm                    65184  1 nouveau
firewire_ohci          31504  0 
drm_kms_helper         40745  1 nouveau
hid                    77084  1 usbhid
usb_storage            43946  1 
uas                    17676  0 
floppy                 60032  0 
drm                   180037  4 nouveau,ttm,drm_kms_helper
firewire_core          56138  1 firewire_ohci
i2c_algo_bit           13184  1 nouveau
crc_itu_t              12627  1 firewire_core
video                  18951  1 nouveau
pata_amd               13762  0 
sata_nv                23176  0 
ubuntu@ubuntu:~$ 


---

### Post by praseodym on 2011-08-23
Normally the module ath5k got the product and vendor IDs of this card. Here on my PC:
```
modinfo ath5k | grep 0020
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d000[COLOR="Red"]0020[/COLOR]7sv*sd*bc*sc*i*
```
Try:

```
sudo modprobe -v ath5k
sudo depmod -a
sudo update-initramfs -u
```
The driver ath5k doesnt work well with all cards, if necessary it can be replaced with the ath_pci, which has to be self compiled.


[http://madwifi-project.org/](http://madwifi-project.org/)

You may try different versions of the driver package, see [here]("http://forum.ubuntuusers.de/topic/problem-mit-pci-karte-netgear-wg311t/#post-2728016"), its from the german forum, but the installation procedures are self-explaining.

---

### Post by lkjoel on 2011-08-23
Could you run the Network Info script (in my signature), and attach the generated file (NETWORK-INFO.txt.gz)?

---

