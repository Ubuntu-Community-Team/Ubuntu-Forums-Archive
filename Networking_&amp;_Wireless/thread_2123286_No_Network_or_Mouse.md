---
title: "No Network or Mouse"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by coreymcdonald855 on 2013-03-07
Hey, all. following a fresh install of 12.04, I've lost wired network support and my USB mouse is neither visible nor responsive. This is day four and the issue is increasingly frustrating. Looking forward to your advice.

AsRock 75 Pro 3
Intel I5 3.1 GHz quad
Radeon HD 7870 Ghz Edition

---

### Post by gordintoronto on 2013-03-07
Tell us about your computer? If possible, open Terminal, enter these commands:
lspci
lsusb
If possible, copy/paste the results here.

64-bit Ubuntu 12.04.2?

Perhaps you can do those things from your LiveDVD or LiveUSB?

---

### Post by coreymcdonald855 on 2013-03-07
I tried reinstalling to see if that would fix it, no change. Back on the "Try Ubuntu." Is that the same as Live? It's x64, though. As far as system specs, they are as follows:

AsRock Z75 Pro 3
Intel I5 3.1 GHz Quad
Radeon HD 7870 GHz Edition

Also, I cannot seem to access the terminal in whatever mode I am currently running Ubuntu. Let me know if you need any other info, I would be happy to provide. Thank you for the prompt response.

---

### Post by gordintoronto on 2013-03-08
In "Try Ubuntu" (which is Live DVD or Live USB -- which?) press the Windows key and type terminal. Then you can enter the commands.

---

### Post by coreymcdonald855 on 2013-03-08
I'm home on spring break, I will post results as soon as I get back in town. Thank you for the instructions.

---

### Post by varunendra on 2013-03-08
*Thread moved to **Networking & Wireless**.*

---

### Post by coreymcdonald855 on 2013-03-18
lspci brought back: 
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 6818
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
03:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


lsusb brought back:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 154b:0062 PNY 
Bus 002 Device 007: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse

LiveUSB, to answer that question.

---

### Post by varunendra on 2013-03-18
> **coreymcdonald855 said:**
> I've lost wired network support and my USB mouse is neither visible nor responsive.
What did you mean by mouse not visible? At system level, it IS visible at least -
> **coreymcdonald855 said:**
> 
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. **RTL8111/8168B** PCI Express Gigabit Ethernet controller (rev 06)
...
Bus 002 Device 007: ID 1bcf:0007 **Sunplus Innovation Technology Inc. Optical Mouse**

As for the network card, the above chip is supported by native r8169 driver.

Please post outputs of -
```
lspci -nnk | grep -iA2 net
usb-devices | grep -A6 -B2 0007
lsmod
dmesg | grep 816
```

---

### Post by coreymcdonald855 on 2013-03-18
Please keep in mind that I am running Ubuntu LiveUSB. The issues described only occur when booting from the installed Ubuntu 12.04. As for the mouse, I meant the cursor isn't visible. The mouse is not responsive (e.g. moving it won't wake the monitor).

```
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: **[COLOR="#000080"]r8169[/COLOR]**
```

```
ubuntu@ubuntu:~$ usb-devices | grep -A6 -B2 0007
T:  Bus=02 Lev=02 Prnt=02 Port=07 Cnt=02 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1bcf ProdID=0007 Rev=01.12
S:  Product=USB Optical Wheel Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=60mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=**[COLOR="#000080"]usbhid[/COLOR]**
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
```

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23126  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
snd_hda_intel          34117  5 
coretemp               13642  0 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
kvm_intel             137888  0 
snd_seq_midi           13325  0 
kvm                   422160  1 kvm_intel
snd_rawmidi            30750  1 snd_seq_midi
snd_hwdep              17765  1 snd_hda_codec
snd_seq_midi_event     14900  1 snd_seq_midi
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
ghash_clmulni_intel    13221  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   18240  2 
aesni_intel            51134  0 
mei                    41410  0 
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
rfcomm                 47562  0 
aes_x86_64             17256  1 aesni_intel
lpc_ich                17145  0 
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
joydev                 17694  0 
bluetooth             211812  10 bnep,rfcomm
parport_pc             32867  0 
microcode              23030  0 
serio_raw              13216  0 
mac_hid                13254  0 
ppdev                  17114  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
dm_multipath           23306  0 
scsi_dh                14589  1 dm_multipath
ext2                   73799  1 
squashfs               36801  1 
overlayfs              28353  1 
nls_iso8859_1          12714  1 
nls_utf8               12558  0 
isofs                  40307  0 
dm_raid45              78156  0 
xor                    17153  1 dm_raid45
dm_mirror              22204  0 
dm_region_hash         20962  1 dm_mirror
dm_log                 18565  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 781017  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
uas                    18073  0 
usb_storage            49288  1 
radeon                912794  2 
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
video                  19598  0 
drm                   290344  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13565  1 radeon
r8169                  62766  0 
```

```
ubuntu@ubuntu:~$ dmesg | grep 816
[    2.617700] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    2.706797]  [<ffffffff816a8324>] kernel_thread_helper+0x4/0x10
[    2.706801]  [<ffffffff816a8320>] ? gs_change+0x13/0x13
[    3.207461] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.207608] r8169 0000:05:00.0: irq 45 for MSI/MSI-X
[    3.207734] r8169 0000:05:00.0: eth0: RTL8168evl/8111evl at 0xffffc90001776000, bc:5f:f4:67:d6:05, XID 0c900800 IRQ 45
[    3.207736] r8169 0000:05:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   42.790042] r8169 0000:05:00.0: eth0: link down
[   42.790064] r8169 0000:05:00.0: eth0: link down
[   44.974838] r8169 0000:05:00.0: **eth0: [COLOR="#000080"]link up[/COLOR]**
```

Thank you for the assistance.

---

### Post by varunendra on 2013-03-18
First off, please use code tags for posting terminal codes (follow the example link in my sig. to see how). It preserves formatting and makes it more readable.

About the problem, guess you need to post the outputs from the installed system instead. As highlighted in your above post, both network and mouse are normal in the live session, so that doesn't give any hints to the problem in the installed system.

If the keyboard works, you can use **Ctrl+Alt+T** to open terminal, then you can run the commands and redirect them to a file on your desktop for easy copy-paste later.

Precisely (after opening terminal)-
```
cd ~/Desktop
lspci -nnk | grep -iA2 net > info.txt
usb-devices | grep -A6 -B2 0007 >> info.txt
lsmod >> info.txt
dmesg | grep 816 >> info.txt
```
This will create a file "info.txt" on your desktop and put all the outputs in it.

You can then connect a usb thumb drive and copy the file to it for posting here. From the same terminal (being in 'Desktop' directory) -
```
cp info.txt /media/**usb**
```
where '**usb**' would be the name by which your thumb drive appears in nautilus (the file browser).

---

### Post by coreymcdonald855 on 2013-03-20
I am not seeing the link you mentioned. I will post results as soon as I figure that out.

---

### Post by coreymcdonald855 on 2013-03-21
I'm not seeing the example link in your sig.

---

### Post by varunendra on 2013-03-21
> **coreymcdonald855 said:**
> I'm not seeing the example link in your sig.

Ah, don't sweat it.. :) It's a good thing to do but not necessary. Let's just focus on your problem.

Did you succeed in creating and copying the report file using just keyboard? Please attach it here for us to see.


By the way, here is the link you were so worried about :D : [[COLOR="#000080"]_Code Tags example_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=12368389")

---

### Post by coreymcdonald855 on 2013-03-21
```

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1bcf ProdID=0007 Rev=01.12
S:  Product=USB Optical Wheel Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=60mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
Module                  Size  Used by
[    0.332839] pci 0000:05:00.0: >[10ec:8168] type 00 class 0x020000
[    0.358164] NET: Registered protocol family 2
[    0.418169] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.420613]  [<ffffffff8168b024>] kernel_thread_helper+0x4/0x10
[    0.420616]  [<ffffffff8168b020>] ? gs_change+0x13/0x13
[   15.571602] init: bluetooth main process (816) terminated with status 1
[  266.758169] sr 3:0:0:0: >[sr0]  
[  266.763816] sr 3:0:0:0: >[sr0] CDB: 

```

---

### Post by varunendra on 2013-03-21
Was that really all of the output ?? Then I see some serious errors here -
> **coreymcdonald855 said:**
> ```

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
**[COLOR="#FF0000"](---- no kernel driver line here, means no driver loaded ----)[/COLOR]**
```

Same for mouse -
> ```
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=**[COLOR="#FF0000"](none)[/COLOR]**
```

lsmod is totally blank. Its impossible that no drivers loaded, but at least it indicates a seriously broken system -
> ```
Module                  Size  Used by
[COLOR="#FF0000"]?????????????????????[/COLOR]
```


So if that is really the complete output from the system, you seem to be a victim of a corrupt installation or upgrade. Two thing you may try, but let's try your luck before I suggest them. Enter these commands in terminal -
```
sudo modprobe r8169
sudo modprobe usbhid
```
The first one is supposed to make your ethernet work, the second one is for mouse. Although I'm almost certain they'll fail with some error. If they do fail, here are your two options to try -

[INDENT]**1)** When the system is booting (at the purple screen), press and hold 'Shift' key. You should get the GRUB boot menu (on some systems, it is 'Esc' key instead of 'Shift'). Can you see an option to boot into an older kernel there ? Try the older one if you have the option and post back here for further instructions.

**2)** If you don't have the option of an older kernel, it means your installation is somehow broken. Check the source ISO that you downloaded to install. To check its integrity : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If it is intact, check your installation media (cd/usb that you used to install). It can be checked by pressing 'any' key when it is booting (again, the purple screen as shown here : [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)) , then selecting the "Check disk for defects" option.[/INDENT]

Another option with very thin chance of recovery is to try the recovery mode from grub menu (first option above) then choose '**dpkg (fix broken packages)**' option in the recovery menu. But as I said, chances of recovery are very slim from what I can gather from the above outputs.

Please note that if the ISO happens to be corrupt (md5sum doesn't match), and you need to download it again, I'd recommend to download via torrent. It ensures the integrity of the downloaded data. Official links for torrents : [www.ubuntu.com/download/desktop/alternative-downloads](www.ubuntu.com/download/desktop/alternative-downloads)

Let us know how it goes.

**PS:**
Oh and glad that you figured out the code tags :)

---

### Post by coreymcdonald855 on 2013-03-22
I did the MD5SUM before installation, everything was good. I will try the other methods shortly. Thank you for your quick reply.

---

### Post by coreymcdonald855 on 2013-03-22
Well... MD5SUM matched, no dpkh (fix broken packages) option, no option for an older kernel... checked the disk, 1 error. It won't tell me what the error is, though. Completely lost.

---

### Post by varunendra on 2013-03-22
> **coreymcdonald855 said:**
> Well... MD5SUM matched, no dpkh (fix broken packages) option, no option for an older kernel... checked the disk, 1 error. It won't tell me what the error is, though. Completely lost.

If your system can boot from usb, I'd suggest to create a live usb instead of cd. USB installation is fast and won't cost you another cd. Besides, the error may also be a result of an old, weak optical drive, in which case the error may repeat itself even with a newer cd.

In any case, re-installation seems to be the only reasonable choice.

---

### Post by coreymcdonald855 on 2013-03-24
I created a live USB and that is what current install is from. I will overwrite the current live USB and reinstall. Guess I may be using W7, after all. Sad day.

---

### Post by varunendra on 2013-03-24
> **coreymcdonald855 said:**
> I created a live USB and that is what current install is from. I will overwrite the current live USB and reinstall. Guess I may be using W7, after all. Sad day.
Sad indeed.
Let's hope it gets all good with a fresh one. :|

---

### Post by coreymcdonald855 on 2013-03-26
Well, it turns out the hard drive was bad. I tried to install W8 on the old drive, no dice. Since I already bought it and can't return, I bought a new hard drive to put W8 on. Installed and working great. Didn't try Ubuntu on new drive, but that's the only thing that wasn't replaced when I built this rig. Weird stuff... anyway, thank you for the assistance. I will try Linux again in the future.

---

