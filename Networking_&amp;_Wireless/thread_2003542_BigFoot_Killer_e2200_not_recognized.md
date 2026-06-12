---
title: "BigFoot Killer e2200 not recognized"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by xmsauer on 2012-06-14
Hi All, I'm having trouble get my ethernet connection working on my MSI GT60 laptop. There is a Bigfoot Killer e2200 gaming LAN inside.

```

$ lspci -vnn
...
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. Device [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:10bc]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f7300000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at d000 [size=128]
    Capabilities: <access denied>
....

``````
maxa@max-msi ~ $ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 13
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f7300000-f733ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:0b:f0:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=18.168.6.1 ip=192.168.1.227 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f7200000-f7201fff

``````

maxa@max-msi ~ $ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
bbswitch               13396  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
ext2                   73795  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
arc4                   12529  2 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
dm_multipath           23230  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlwifi               328352  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
psmouse                87603  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13211  0 
i915                  468651  3 
drm_kms_helper         46978  1 i915
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  4 i915,drm_kms_helper
rts_pstor             445196  0 
soundcore              15091  1 snd
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
mxm_wmi                12979  0 
wmi                    19256  1 mxm_wmi
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash

```Did anyone managed to get this working? Thanks a lot.

---

### Post by chili555 on 2012-06-14
I've searched and searched and the answer is not yet; but you might be first! Are you dual-booting with Windows? Is the Windows driver in the directory C:\Program Files\Bigfoot Networks\Killer Network Manager\ or similar? If we could see the .inf file, it might help us. If it is available, please paste it here and give us the link in your reply. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

For the benefit of the searchers, I already tried to download the 256 Mb (!!) driver from MSI and extract it by wine, unshield, cabextract, unzip and unrar. No luck so far.

---

### Post by xmsauer on 2012-06-14
Thanks for the reply! Unfortunately, my laptop is linux-only, but one of my colleagues has dual-boot. We will provide the .inf file.

---

### Post by xxyy013 on 2012-06-14
Same problem here, also an msi GT60.
I still have a dual boot installation so I can provide the inf file.

I think it's this one: C:\Program Files\Qualcomm Atheros\Killer Network Manager\e22w7x64\e22w7x64.inf
[http://paste.ubuntu.com/1040895/](http://paste.ubuntu.com/1040895/)

There is also another one, less important I think: C:\Program Files\Qualcomm Atheros\Killer Network Manager\bflwf\bflwf.inf
[http://paste.ubuntu.com/1040925/](http://paste.ubuntu.com/1040925/)

hope this can help to find out.

---

### Post by chili555 on 2012-06-14
I'm going to document what I've found and propose a solution. As in all things at the bleeding edge, there are no guarantees that this will work or work well. I believe, however, that trying something beats trying nothing.

From the .inf file you pasted:> [Killer.NTamd64]
; DisplayName           Section                DeviceID
; -----------           -------                --------
%BFTN.L1F%  =           L1F.ndi,               PCI\VEN_[COLOR="Red"]1969[/COLOR]&DEV_[COLOR="Red"]E091[/COLOR] 				    ; e2201/e2205^^^ There is your device pci.id. Now further along:> ;-----------------------------------------------------------------------------
; [COLOR="Red"]L1C[/COLOR]  specific
;
[L1C.reg]
HKR, Ndi, HelpText,, %HelpText%
HKR, Ndi, Service,    0, "Ke2200"
; use ndis5 as the upper bound because NT supports it
HKR, Ndi\Interfaces, UpperRange, 0, "ndis5"
HKR, Ndi\Interfaces, LowerRange, 0, "ethernet"As it happens, there is an Atheros ethernet driver called *atl1c*. Some more research: [http://comments.gmane.org/gmane.linux.kernel/1205207](http://comments.gmane.org/gmane.linux.kernel/1205207)> This driver supports the Atheros [COLOR="Red"]L1C/L1D/L1F[/COLOR] gigabit ethernet
+	  adapter. 
+
+	  To compile this driver as a module, choose M here.  The module
+	  will be called [COLOR="Red"]atl1c[/COLOR].Let's see if we have any luck forcing the existing atl1c to recognize and drive your device. Please open a terminal and do:```
sudo su
modprobe atl1c
echo 1969 e091 > /sys/bus/pci/drivers/atl1c/new_id
ifconfig
exit
```Any improvement?

If not, here is our next prospect: [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

---

### Post by xxyy013 on 2012-06-15
Thanks for all the information.
Unfortunately the ethernet device isn't working yet.

I tried forcing the existing atl1c to recognize and drive the device, doing:
```

sudo -i
modprobe atl1c
echo 1969 e091 > /sys/bus/pci/drivers/atl1c/new_id
ifconfig
exit

```

Without success, the output of ifconfig is still showing only lo and wlan0.

Next I tried th e instructions on: [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)
I had problems using [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2)
And so I tried [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2)
This I could install, but the replacing alx couldn't recognize the device either.

Are there some more things to try?

---

### Post by chili555 on 2012-06-15
> **xxyy013 said:**
> Thanks for all the information.
Unfortunately the ethernet device isn't working yet.

I tried forcing the existing atl1c to recognize and drive the device, doing:
```

sudo -i
modprobe atl1c
echo 1969 e091 > /sys/bus/pci/drivers/atl1c/new_id
ifconfig
exit

```

Without success, the output of ifconfig is still showing only lo and wlan0.Are there any interesting messages here?```
dmesg | grep atl1c
```> 

Next I tried th e instructions on: [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)
I had problems using [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2)
And so I tried [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-05-10-p.tar.bz2)
This I could install, but the replacing alx couldn't recognize the device either.

Are there some more things to try?Did you add your device pci.id to the .c files? If not, I wouldn't expect any improvement. As the website says:> To be clear, both atl1c and alx supports these PCI vendor:device IDs:

    1969:1063 - AR8131 Gigabit Ethernet
    1969:1062 - AR8132 Fast Ethernet (10/100 Mbit/s)
    1969:2062 - AR8152 v2.0 Fast Ethernet
    1969:2060 - AR8152 v1.1 Fast Ethernet
    1969:1073 - AR8151 v1.0 Gigabit Ethernet
    1969:1083 - AR8151 v2.0 Gigabit Ethernet

But alx supports these two new chipstes additionally:

    1969:1091 - AR8161
    1969:1090 - AR8162
But your device 1969:e091 isn't listed. We must modify the files before we compile to try.

I am on my way out the door, but I'll work on this a bit later.

---

### Post by xxyy013 on 2012-06-15
> **chili555 said:**
> Are there any interesting messages here?```
dmesg | grep atl1c
```Did you add your device pci.id to the .c files? If not, I wouldn't expect any improvement. As the website says:But your device 1969:e091 isn't listed. We must modify the files before we compile to try.

I am on my way out the door, but I'll work on this a bit later.

thank you, 

dmesg | grep atl1c  -> no output at all.

I did not change any C file. I think there's something I don't completely understand.
Now I am look for a C file to change, but I don't know what to do.

if I look in the compat-wireless-2012-05-10-p/drivers/net/ethernet/atheros/atl1c/ folder I see following files:
  - atl1c_ethtool.c
  - atl1c.h
  - atl1c_hw.c
  - atl1c_hw.h
  - atl1c_main.c
  - Makefile
Should I change (add the pci.id of the ethernet device) one of them?
My best guess is atl1c_hw.h, this file contains:
```

/* hw-ids */
#define PCI_DEVICE_ID_ATTANSIC_L2C      0x1062
#define PCI_DEVICE_ID_ATTANSIC_L1C      0x1063
#define PCI_DEVICE_ID_ATHEROS_L2C_B    0x2060 /* AR8152 v1.1 Fast 10/100 */
#define PCI_DEVICE_ID_ATHEROS_L2C_B2    0x2062 /* AR8152 v2.0 Fast 10/100 */
#define PCI_DEVICE_ID_ATHEROS_L1D    0x1073 /* AR8151 v1.0 Gigabit 1000 */
#define PCI_DEVICE_ID_ATHEROS_L1D_2_0    0x1083 /* AR8151 v2.0 Gigabit 1000 */
#define L2CB_V10            0xc0
#define L2CB_V11            0xc1


```I don't know to add it correctly, assumed this is the file to be changed.
Could it be something like this:
```
#define PCI_DEVICE_ID_ATHEROS_L1C      0xe091
```And is this enough?

---

### Post by chili555 on 2012-06-15
> I don't know to add it correctly, assumed this is the file to be changed.
Could it be something like this:
```
#define PCI_DEVICE_ID_ATHEROS_L1C      0xe091
```

And is this enough?Exactly! You are well on your way to being a driver dawg! *You also need to make the identical change in atl1c_main.c*. I think I'd try to find out a description to add after that part, something like:```
#define PCI_DEVICE_ID_ATHEROS_L1[COLOR="Red"]F[/COLOR]      0xe091 /* AR???? v?.0 Gigabit 1000 */
```You might run:```
sudo lspci -vvv
```If there are any other details, add them in place of my ??s.

Since the Windows .inf file refers to L1F, I suggest you use F in place of C as I highlighted. Then you'll have to recompile:```
sudo su
make clean
make  [COLOR="Red"]<---and if there are no errors[/COLOR]
make install
exit
```As in all things driver dawg, look at the kernel message file:```
dmesg | grep -e alx -e atl1c
```Good luck!

---

### Post by Mahler122 on 2012-06-22
Using the above method, I have made the alx module work with the E2200 and I have created a small patch to do it here: [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332)

---

### Post by xmsauer on 2012-06-25
[http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) works for me also -- marking this as solved. Thank you very much guys!

---

### Post by PadreAdamo on 2013-04-29
> **xmsauer said:**
> [http://ubuntuforums.org/showthread.php?t=2008332](http://ubuntuforums.org/showthread.php?t=2008332) works for me also -- marking this as solved. Thank you very much guys!

I'm sorry to resurrect a old threat. I have a Killer Xeno Pro. Are you folks able to help me with this patch?

---

