---
title: "Desperately trying to get wireless working on a Lenovo G780"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by _asc_ on 2012-11-04
Hello,

I'm desperately trying to get wireless lan working on a Lenovo G780. When I boot the Live-DVD, I can activate the proprietary Broadcom driver without a problem and wireless is working perfectly. But when I try to activate the driver on the Ubuntu installation, the radio button jumps back to the "Not in use" setting without any error message and wireless is not working. I have also found some threads in the forum where people said that they got wireless working but I did not get any answers when I asked how they did it.

lsmod |grep wl gives me nothing and modprobe wl returns:

```
FATAL: Module wl not found.
```

I'm struggling with this issue for a few days now and I have run out of ideas.

Here is some additional information:
Operating System: Ubuntu 12.10 64 Bit (I have also tried the 32Bit version, but had the same issue)

**sudo lshw -c network**
```
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d3900000-d393ffff ioport:2000(size=128)
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d3800000-d3803fff
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 08:ed:b9:a3:da:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-17-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```

**lspci -vvv**
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 08)
	Subsystem: Lenovo Device 3979
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at d3900000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at 2000 [size=128]
	Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Broadcom Corporation Device 0587
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at d3800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma

```

**ifconfig**
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14304 (14.3 KB)  TX bytes:14304 (14.3 KB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:a3:da:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Bucky Ball on 2012-11-04
Have you done an update with a cable? Do that and try again if not. 

You have both b43-fwcutter and firmware-b43-installer installed? Check in Synaptics or Software Centre.

I have never seen this driver before. Maybe a new innovation in 12.10:
```

driver=brcmsmac
```PS: Stick with the 64 bit. 12.10 has only been out a couple of weeks so expect breakages. I'm presuming 12.04 LTS was fine? If you still have that installed see what driver that is using.

---

### Post by uclugLee on 2012-11-04
When you booted from the live cd and was able to connect to wireless, then start the install process.  On the screen where you are asked where you want to install, at the bottom of that screen there are two check boxes.  One asks if you want to download updates while installing, the other asks if you want to install third party software.  Did you select the box to download updates while installing?  I have found that using that option installs my wireless, LAN and video drivers while installing the OS.

---

### Post by Hadaka on 2012-11-04
Hi, please post the output of..

```
rfkill list all 
```

```
lspci -nn | grep 0280 
```

thanks

---

### Post by _asc_ on 2012-11-04
Hello,

thank you both for your answers. The problem is, that ethernet is not working as well. In fact the threads, I mentioned, in my first post where people said that they got wireless running were all about getting ethernet to work and there have not been solutions yet.

Nevertheless, since I had wireless access during install, I checked both checkboxes to install updates and third party software. So I should have all updates (I did a fresh install this morning).

The notebook is new, so I have not tried Ubuntu 12.04.

Checking in Software Center I could see that both b43-fwcutter and firmware-b43-installer are not installed. I have another notebook with Ubuntu 12.10 so I could download packages and copy them over if necessary.

---

### Post by Hadaka on 2012-11-04
Hi, sending you a zip file and instructions for loading from another
machine is no problem, but first we need to verify exactly which
broadcom driver you need for your card, there are several.

```
lspci -nnk | grep -iA5 net 
```

this will also show what module you currently have loaded.

thanks

---

### Post by _asc_ on 2012-11-04
rfkill list all:
```
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
```

lspci -nn |grep 0280:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

---

### Post by _asc_ on 2012-11-04
lspci -nnk |grep -iA5 net:
```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 08)
	Subsystem: Lenovo Device [17aa:3979]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma
```

---

### Post by Hadaka on 2012-11-04
dang !..you have the oh so fun unsupported broadcom card.
BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]
let me dig around, i have the file you need for this...

---

### Post by Hadaka on 2012-11-04
ok, ERROR on my part,I had this confused with another card.sorry.
you need the sta driver with a couple items blacklisted.

lets see what you currently have loaded

```
lsmod
```

thanks

---

### Post by _asc_ on 2012-11-04
lsmod:
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
uas                    17844  0 
usb_storage            48838  1 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_conexant    57842  1 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
arc4                   12529  2 
aes_x86_64             17208  1 aesni_intel
brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
brcmutil               14755  1 brcmsmac
cfg80211              206566  2 brcmsmac,mac80211
cordic                 12535  1 brcmsmac
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
rts5139               356158  0 
microcode              22803  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
psmouse                95552  0 
serio_raw              13215  0 
joydev                 17457  0 
bcma                   35656  1 brcmsmac
mei                    40690  0 
i915                  520519  3 
nouveau               895609  0 
ttm                    83595  1 nouveau
drm_kms_helper         46784  2 i915,nouveau
drm                   275528  6 i915,nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  2 i915,nouveau
mxm_wmi                12979  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
video                  19335  2 i915,nouveau
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_microsoft          12798  0 
usbhid                 46947  0 
hid                   100366  2 hid_microsoft,usbhid

```

---

### Post by Hadaka on 2012-11-04
@ Buckyball .... [14e4:27]


[https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

---

### Post by Hadaka on 2012-11-04
try this..

```
sudo echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

```
sudo echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

---

### Post by Hadaka on 2012-11-04
then activate the brcmsmac

```
sudo modprobe brcmsmac 
```

*if it connects.

```
sudo echo 'brcmsmac' >> /etc/modules 
```

---

### Post by _asc_ on 2012-11-04
Unfortunately, it still does not connect. I have also tried to reboot after blacklisting (and then, ofcourse, executed "sudo modprobe brcmsmac" again).

The current output of lsmod is now:
```

Module                  Size  Used by
nls_iso8859_1          12713  1 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  12 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_conexant    57842  1 
joydev                 17457  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
arc4                   12529  2 
brcmsmac              531848  0 
mac80211              539908  1 brcmsmac
brcmutil               14755  1 brcmsmac
cfg80211              206566  2 brcmsmac,mac80211
cordic                 12535  1 brcmsmac
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_rawmidi            30512  1 snd_seq_midi
nouveau               895609  0 
snd_seq_midi_event     14899  1 snd_seq_midi
rts5139               356158  0 
psmouse                95552  0 
btusb                  18334  0 
microcode              22803  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
bluetooth             209199  22 bnep,rfcomm,btusb
serio_raw              13215  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    83595  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
i915                  520519  3 
bcma                   35656  1 brcmsmac
lpc_ich                17061  0 
drm_kms_helper         46784  2 nouveau,i915
drm                   275528  6 nouveau,ttm,i915,drm_kms_helper
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13413  2 nouveau,i915
mei                    40690  0 
mac_hid                13205  0 
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
video                  19335  2 nouveau,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
uas                    17844  0 
usb_storage            48838  1 

```

---

### Post by Hadaka on 2012-11-04
ok, lets make sure the sta driver package is actually loaded.

```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
 
```

you will need to issue the blacklist commands again

and the modprobe command

---

### Post by Hadaka on 2012-11-04
forgot..you have no internet..let me look for the zip'd file to send you

---

### Post by chili555 on 2012-11-04
> Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]]FWIW, I believe STA (bcmwl-kernel-source) is correct for this device, not b43 and not brcmsmac.

Now we return you to your regularly scheduled gurus.

---

### Post by Hadaka on 2012-11-04
Thanks chilli555, glad you are here, i cannot locate my sta zip file.
i was going by this guide for [14e4:4727]
[https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

any help you can provide, please feel free to do so,like..the sta driver zip
file or anything else to get this working.

thanks.

---

### Post by chili555 on 2012-11-04
> **Hadaka said:**
> Thanks chilli555, glad you are here, i cannot locate my sta zip file.
i was going by this guide for [14e4:4727]
[https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/BroadcomSTA%28Wireless%29)

any help you can provide, please feel free to do so,like..the sta driver zip
file or anything else to get this working.

thanks.If it worked on the live DVD but not when he installed it, that's where I'd look. Please see attached. I think he can right-click it and install it from the DVD.

---

### Post by _asc_ on 2012-11-04
bcmwl-kernel-source_5 has a dependency on dkms, so I executed the following commands:

```
sudo dpkg --install dkms_2.2.0.3-1.1ubuntu1_all.deb
sudo dpkg --install bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
```

The dkms installation went fine, but for bcmwl-kernel-source, I got:

```
(Reading database ... 145497 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb) ...
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
```

B43 and wl are still blacklisted. Do I have to remove them from the blacklist? If it is not "brcmsmac", is there an other module I have to load?

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12713  1 
uas                    17844  0 
usb_storage            48838  1 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 46619  12 
bnep                   18140  2 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_conexant    57842  1 
joydev                 17457  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
microcode              22803  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rts5139               356158  0 
snd_seq_midi           13324  0 
psmouse                95552  0 
snd_rawmidi            30512  1 snd_seq_midi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
nouveau               895609  0 
btusb                  18334  0 
bluetooth             209199  22 rfcomm,bnep,btusb
serio_raw              13215  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    83595  1 nouveau
mei                    40690  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  520519  3 
drm_kms_helper         46784  2 nouveau,i915
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
mxm_wmi                12979  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
drm                   275528  6 nouveau,ttm,i915,drm_kms_helper
i2c_algo_bit           13413  2 nouveau,i915
ideapad_laptop         18086  0 
sparse_keymap          13890  1 ideapad_laptop
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mac_hid                13205  0 
video                  19335  2 nouveau,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp


```

---

### Post by Hadaka on 2012-11-04
Hi, you will need to..

```
gedit /etc/modprobe.d/blacklist.conf
```

go to the bottom of the file and remove the blacklist items you added.

then reload the driver.

*you MAY have to end up blacklisting brcmsmac as well.

after you unblackist the 2 items
```
sudo modprobe wl 
```

wl is needed for the sta driver.

---

### Post by chili555 on 2012-11-04
The installation of bcmwl-kernel-source blacklists brcmsmac and b43 automagically. Remove the blacklist for wl. Then do:```
sudo modprobe wl
```Any errors or warnings? Any wireless connection?

---

### Post by _asc_ on 2012-11-04
sudo modprobe wl gives me:

```
FATAL: Module wl not found.
```

---

### Post by rsavage on 2012-11-04
You need the header package for your current kernel to build wl. Please see [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access)

---

### Post by chili555 on 2012-11-04
> Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.I think this is our problem. I think that the linux-headers-generic package and its dependencies are somewhere on the live DVD. Insert the DVD, open Ubuntu Software Center select Edit > Software sources and enable the DVD as a source. Then see if you can find and install linux-headers-generic. Then find bcmwl-kernel-source and see if you can reinstall it. Then try:```
sudo modprobe wl
```

---

### Post by rsavage on 2012-11-04
> 
I think that the linux-headers-generic package and its dependencies are somewhere on the live DVD

I think they are installed on the liveCD/liveUSB environment, but are not available as packages like bcmwl-kernel-source.

---

### Post by _asc_ on 2012-11-04
Success :)

I found the linux-headers-generic package in the Software Center, but the install button was grayed out, although I activated the DVD as source. In in end, I downloaded the packages with my working Ubuntu installation. As soon as I reinstalled the bcmwl-kernel-source module, the wl module was loaded and wireless access worked perfectly. So, to help others that might have the same issue, I want to summarize the solution. It seems that the following statements solved the problem:

```
sudo dpkg --install dkms_2.2.0.3-1.1ubuntu1_all.deb
sudo dpkg --install linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb
sudo dpkg --install linux-headers-generic_3.5.0.17.19_amd64.deb
sudo dpkg --install bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
```


Thank's to all of you who helped me with this issue! You are great!

---

### Post by flash63 on 2012-11-05
Hello,
same problems here with a Lenovo G580 (solved).

[http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097](http://forum.ubuntuusers.de/topic/lan-wlan-probleme-mit-lenovo-g580/2/#post-4987097)

For Ethernet you need the attached Driver-Package for the new alx module. Only for Ubuntu 12.04! 

Don't install directly any pakage from Compat-Wireless or any Backport-Modules from the repositories! The Modules of the lib80211 Subsystem will be replaced an the Broadcom-Module (wl) becomes unuseable.

---

