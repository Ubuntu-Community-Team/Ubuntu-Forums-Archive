---
title: "Ralink RT3090: Network disabled"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by mercedesbenzformula1 on 2010-12-24
](*,) AHHHHHHHHHHHHH!!!!
I have made many billions upon billions of attempts to make my integrated network card on my HP Pavilion p6620f work but every single one has failed!

sudo lspci returns: 
```

02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Lite-On Communications Inc Device 6632
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-80-63-96-9d-65-1c
	Kernel driver in use: rt2800pci
	Kernel modules: rt2860sta, rt2800pci

```

sudo lshw -c net returns: 
```

*-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:96:63:80
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list 

```

iwconfig wlan0 returns:
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Any help would be immensely, prodigally appreciated. Thanks. :D , ](*,)

---

### Post by dineshs on 2010-12-24
Can you try postcount 7 [here]("http://ubuntuforums.org/showthread.php?t=1650507")

---

### Post by mercedesbenzformula1 on 2010-12-24
thank you for your response dineshs.

I have already checked to see if my wireless is enabled and wireless in terminal and "WirelessEnabled=true" was returned in gedit. I also tried lsmod but can't figure out how to use it. Every time I try to use it all I get is: ```
Usage: lsmod
```

---

### Post by dineshs on 2010-12-24
Have you tried post #3 [here]("http://ubuntuforums.org/showthread.php?t=1505217")
(use [COLOR="Blue"]sudo[/COLOR] before commands)
or post #7 [here]("http://ubuntuforums.org/showthread.php?p=9631393#post9631393")

---

### Post by maurolust on 2011-10-03
Hello, I have the same issue, but no solution so far has worked. I run ubuntu 10.4LTS and lspci gives
```
 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe. 
```

NetworkManager.state starts as:
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

After running ```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```

NetworkManager updates to the same state, and nothing changes. My card is still dead, as iwconfig would put it:
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Searching further on the state of my wireless card i get
```

~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe50ffff

```

I am using Markus Tisofts PPA for the RT3090 driver ([https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090))

I have also tried wlan0 up, with no results.
```

~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

I have also tried see what rfkill would tell me, but I get no messages, nothing, just plain silence.

---

### Post by praseodym on 2011-10-03
Hi,

create that file again:

```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Insert

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```
save and reboot. Please show after that:

```
lsmod
rfkill list
iwconfig
sudo iwlist scan
```

---

### Post by maurolust on 2011-10-03
Thanks for your attention.
Done the editing (even though NetworkManagement was already exactly as you described).

Here is the response to your commands.
fasten your seatbelt:

```

lsmod
Module                  Size  Used by
rfcomm                 40425  4 
binfmt_misc             7960  1 
sco                     9649  2 
bridge                 53184  0 
stp                     2171  1 bridge
ppdev                   6375  0 
bnep                   11884  2 
l2cap                  34839  16 rfcomm,bnep
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_idt      61546  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  1 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
joydev                 11104  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  325095  3 
drm_kms_helper         30742  1 i915
uvcvideo               62883  0 
snd                    71283  15 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               6700  0 
drm                   200288  4 i915,drm_kms_helper
videodev               40550  1 uvcvideo
soundcore               8052  1 snd
jme                    31557  0 
psmouse                65040  0 
sdhci                  17960  1 sdhci_pci
jmb38x_ms               8643  0 
btusb                  13097  2 
v4l1_compat            15495  2 uvcvideo,videodev
memstick               10121  1 jmb38x_ms
intel_agp              29319  2 i915
i2c_algo_bit            6024  1 i915
mii                     5237  1 jme
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    11892  1 videodev
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
led_class               3764  1 sdhci
serio_raw               4918  0 
cfg80211              148341  0 
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  4 
```



```
~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```


```
iwconfig
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```


```
:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```

By the way, my wireless is working fine on Windows 7.

---

### Post by praseodym on 2011-10-03
I dont know this PPA, delete the file and reinstall the kernel:

```
sudo apt-get remove --purge rt3090
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) build-essential dkms
```
Reboot and check:
```
uname -a
lspci -nnk | grep -iA2 Ralink
lsmod
iwconfig
sudo iwlist scan
dmesg | egrep 'rt2|rt3'
```

---

### Post by maurolust on 2011-10-03
Thank you, Praseodym. Looks like I should be starting to worry.

Before I proceed:
Reinstall the kernell sounds like something that suggests a full backup of my data. Is there any other caveat? I just like to know what I'm doing, that's why I switched to Linux. ;)

For what I understand, this will just reinstall the same kernell version I'm currently using, not updating to a new one, am I wrong? For what I've read recently, this whole problem is something that affects many fresh installs. Will reinstalation of the kernell bring me back to square one and make my system work as it did before I suspended it and lost the wireless? 
Sorry for taking your time with these questions.

---

### Post by praseodym on 2011-10-03
> **maurolust said:**
> Thank you, Praseodym. Looks like I should be starting to worry.

Before I proceed:
Reinstall the kernell sounds like something that suggests a full backup of my data. Is there any other caveat? I just like to know what I'm doing, that's why I switched to Linux. ;)

No, the reinstallation just cleans up to "default" settings. Maybe there are some remains of whatever, no worries about that.
> 
For what I understand, this will just reinstall the same kernell version I'm currently using, not updating to a new one, am I wrong? For what I've read recently, this whole problem is something that affects many fresh installs. Will reinstalation of the kernell bring me back to square one and make my system work as it did before I suspended it and lost the wireless? 
Sorry for taking your time with these questions.

Right, it reinstalls the current kernel, that is in use to square one. For a (possible) kernel-update, run the update-manager or by hand:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
For this device normally the modules rt2860sta and rt3090sta are part of the linux kernel. Reboot after that and check as described.

---

### Post by maurolust on 2011-10-03
No problems.

lsmod
```
Module                  Size  Used by
rfcomm                 40425  4 
binfmt_misc             7960  1 
sco                     9649  2 
bridge                 53184  0 
stp                     2171  1 bridge
ppdev                   6375  0 
bnep                   11884  2 
l2cap                  34839  16 rfcomm,bnep
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_idt      61546  1 
snd_hda_intel          25805  1 
snd_hda_codec          85759  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
vga16fb                12757  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
vgastate                9857  1 vga16fb
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  15 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62883  0 
soundcore               8052  1 snd
joydev                 11104  0 
btusb                  13097  2 
videodev               40550  1 uvcvideo
bluetooth              58685  9 rfcomm,sco,bnep,l2cap,btusb
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
jmb38x_ms               8643  0 
v4l1_compat            15495  2 uvcvideo,videodev
sdhci_pci               6700  0 
jme                    31557  0 
sdhci                  17960  1 sdhci_pci
memstick               10121  1 jmb38x_ms
v4l2_compat_ioctl32    11892  1 videodev
led_class               3764  1 sdhci
psmouse                65040  0 
mii                     5237  1 jme
i915                  325095  3 
intel_agp              29319  2 i915
drm_kms_helper         30742  1 i915
drm                   200288  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
serio_raw               4918  0 
cfg80211              148341  0 
video                  20623  1 i915
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  3 
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```



sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


dmesg | egrep 'rt2|rt3'
```
[    9.812196] rt3090sta: disagrees about version of symbol module_layout
[   10.250200] rt3090sta: disagrees about version of symbol module_layout
```

Doesn't look like much has changed. Is that a surprise?

---

### Post by maurolust on 2011-10-03
You didn't ask, but 

NetworkManager.state is still
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```

Thank you for lending me your time knowledge and willpower.

---

### Post by praseodym on 2011-10-03
Try to load the module by hand:

```
sudo modprobe -v rt3090sta
sudo depmod -a
sudo service network-manager restart
```
Check:

```
grep rt2 /etc/modprobe.d/*
grep rt3 /etc/modprobe.d/*
iwconfig
dmesg | egrep 'rt2|rt3'
lsmod
route -n
```

---

### Post by maurolust on 2011-10-03
> **praseodym said:**
> Try to load the module by hand:

```
sudo modprobe -v rt3090sta
sudo depmod -a
sudo service network-manager restart
```


All I got from "sudo modprobe" was this:
```

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
insmod /lib/modules/2.6.32-34-generic/updates/dkms/rt3090sta.ko 
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-34-generic/updates/dkms/rt3090sta.ko): Invalid module format

```

---

### Post by praseodym on 2011-10-03
Check:

```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by maurolust on 2011-10-03
RT3090 is not there. 
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by praseodym on 2011-10-03
Are there 2 files, one with and one without ".conf"? If there is only one file without .conf then rename it:

```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
```
If there are 2 files that are identical, remove the one without .conf
```
sudo rm /etc/modprobe.d/blacklist
```
Try the other module:

```
sudo modprobe -v rt2860sta
sudo depmod -a
```

---

### Post by maurolust on 2011-10-04
> **praseodym said:**
> Are there 2 files, one with and one without ".conf"? 
Yes there are. The one without conf contains just the line
```
blacklist rt2800pci
```

The other one is that long blacklist I've posted.

---

### Post by orny on 2011-10-04
Yesterday I upgraded from 2.6.32-33-generic to -34 and my rt3090 stopped working after reboot. It appears that I experience the same problem as described in this thread, i.e. cannot load the driver:
~$ sudo  modprobe -v rt3090sta
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
insmod /lib/modules/2.6.32-34-generic/updates/dkms/rt3090sta.ko 
FATAL: Error inserting rt3090sta (/lib/modules/2.6.32-34-generic/updates/dkms/rt3090sta.ko): Invalid module format

Will appreciate help.

---

### Post by praseodym on 2011-10-04
@maurolust:

rename the file to:

```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist-rt2800pci.conf
```
Then load the driver:

```
sudo modprobe -v rt2860sta
sudo depmod -a
```

@orny: Try rt2860sta, too.

---

### Post by orny on 2011-10-04
> **praseodym said:**
> @maurolust:

Then load the driver:

```
sudo modprobe -v rt2860sta
sudo depmod -a
```@orny: Try rt2860sta, too.

The driver loads, but it does not help, wifi does not work.

---

### Post by praseodym on 2011-10-04
Please show:

```
rfkill list
iwconfig
dmesg | egrep 'rt2|rt3'
lsmod
route -n
```

---

### Post by orny on 2011-10-04
> **praseodym said:**
> Please show:

```
rfkill list
iwconfig
dmesg | egrep 'rt2|rt3'
lsmod
route -n
```

Here is:

```

user@user-desktop:~$ sudo rfkill list
[sudo] password for user: 

user@user-desktop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

user@user-desktop:~$ sudo dmesg|egrep 'rt2|rt3'
[   16.477178] rt3090sta: disagrees about version of symbol module_layout

user@user-desktop:~$ sudo lsmod
Module                  Size  Used by
joydev                  8740  0 
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  5 
snd_pcm_oss            35308  0 
ppdev                   5259  0 
snd_mixer_oss          13746  2 snd_pcm_oss
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm                70694  3 snd_hda_intel,snd_pcm_oss,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               57406  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               34425  1 uvcvideo
cfg80211              126112  0 
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54244  20 snd_hda_codec_realtek,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
fglrx                2092908  29 
soundcore               6620  2 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  1 fglrx
serio_raw               3978  0 
i2c_piix4               8335  0 
k8temp                  3152  0 
ndiswrapper           184677  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
video                  17375  0 
vgastate                8961  1 vga16fb
output                  1871  1 video
pata_atiixp             3148  0 
usb_storage            39841  0 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32360  2 
user@user-desktop:~$  sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

### Post by praseodym on 2011-10-04
You need to uninstall ndiswrapper completely first:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then try it again.

---

### Post by orny on 2011-10-04
Thank you for your effort but wifi still does not work.

---

### Post by praseodym on 2011-10-04
Please show the outputs of #22 again

---

### Post by maurolust on 2011-10-04
Same thing. I also checked the other blacklist files to look for something blocking rt3090. Is it possible that some other blacklisted driver might be affecting it? I'll keep following.

Also, from what we saw so far, is that an issue with this version of the kernell? 

Thank you for the help.

For others with the same issue: this is a common issue in notebooks from "Microboard" brand (brazilian). if you can read portuguese, [this how-to](http://www.tecnoloide.com.br/site/2011/03/09/faca-a-placa-sem-fio-do-seu-notebook-microboard-funcionar/#comments) may work for some people, but it didn't do magic for me. The funny thing is that this same computer model also is shipped with their Debian-based installation (I've never seen it, but I assume it works). 


I have had the same problem before and thought I had solved it using the rt3090 driver I downloaded from [markus-tisoft]("https://launchpad.net/~markus-tisoft/+archive/rt3090"), but it came back like the Phoenix. I guess it's the very same driver anyway.

---

### Post by orny on 2011-10-05
> **praseodym said:**
> Please show the outputs of #22 again

```

user@user-desktop:~$ rfkill list

user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

user@user-desktop:~$ sudo dmesg|egrep 'rt2|rt3'
[   18.023298] rt3090sta: disagrees about version of symbol module_layout
user@user-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
joydev                  8740  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22069  5 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            35308  0 
snd_hwdep               5412  1 snd_hda_codec
snd_mixer_oss          13746  2 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2092908  29 
snd                    54244  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_hwdep,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               57406  0 
agpgart                31724  1 fglrx
psmouse                63677  0 
soundcore               6620  2 snd
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
i2c_piix4               8335  0 
k8temp                  3152  0 
cfg80211              126112  0 
ndiswrapper           184677  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usb_storage            39841  0 
pata_atiixp             3148  0 
r8169                  34140  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
ahci                   32360  2 
mii                     4381  1 r8169
video                  17375  0 
output                  1871  1 video

user@user-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
user@user-desktop:~$ 

```

---

### Post by praseodym on 2011-10-05
Ndiswrapper is still there, try it again, modified with:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
[COLOR="Red"]sudo rm /etc/modprobe.d/ndiswrapper[/COLOR]
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
[COLOR="Red"]sudo update-initramfs -u -k all[/COLOR]
```
Reboot, and #22 again

---

### Post by orny on 2011-10-05
> **praseodym said:**
> Ndiswrapper is still there, try it again, modified with:

It appears that it was already gone:

[CODE]user@user-desktop:~$ sudo modprobe -rf ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
user@user-desktop:~$ sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
Package ndisgtk is not installed, so not removed
The following packages were automatically installed and are no longer required:
  texlive-base libbeagle1 lmodern texlive-common luatex python-utidylib
  python-gtkmozembed libtidy-0.99-0 texlive-latex-base-doc texlive-binaries
  python-feedparser python-boto python-rsvg texlive-latex-base
  python-evolution texlive-luatex texlive-latex3 python-chardet
  texlive-doc-base librsync1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory
user@user-desktop:~$ sudo rm /etc/modprobe.d/ndiswrapper
user@user-desktop:~$ sudo rm -r /etc/ndiswrapper/* 
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory
user@user-desktop:~$ sudo depmod -a
user@user-desktop:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.32-34-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
Cannot find /lib/modules/2.6.32-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.32-21-generic
user@user-desktop:~$ 


Now I reboot, will write soon.

---

### Post by orny on 2011-10-05
```

user@user-desktop:~$ rfkill list
user@user-desktop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

user@user-desktop:~$ dmesg|egrep 'rt2|rt3'
[   17.299606] rt3090sta: disagrees about version of symbol module_layout
[   17.303478] rt3090sta: disagrees about version of symbol module_layout
user@user-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_realtek   203408  1 
ppdev                   5259  0 
snd_hda_intel          22069  5 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  2 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8740  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2092908  29 
uvcvideo               57406  0 
snd                    54244  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  1 fglrx
psmouse                63677  0 
videodev               34425  1 uvcvideo
soundcore               6620  2 snd
v4l1_compat            13251  2 uvcvideo,videodev
k8temp                  3152  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126112  0 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
usb_storage            39841  0 
pata_atiixp             3148  0 
r8169                  34140  0 
vgastate                8961  1 vga16fb
ahci                   32360  2 
mii                     4381  1 r8169
video                  17375  0 
output                  1871  1 video
user@user-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
user@user-desktop:~$ sudo modprobe -v rt2860sta[sudo] password for user: 
insmod /lib/modules/2.6.32-34-generic/kernel/drivers/staging/rt2860/rt2860sta.ko 
user@user-desktop:~$ sudo depmod -a
user@user-desktop:~$ sudo service network-manager restart
network-manager start/running, process 1458
user@user-desktop:~$ 

```

Wireless is still dead.

---

### Post by praseodym on 2011-10-05
> update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-32-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
Imho you should clean up the old kernels. Be sure you have booted into 2.6.32-3[COLOR="Red"]4[/COLOR] by typing

```
uname -a
```
and clean up all the other stuff with following [COLOR="Red"]one-liner[/COLOR] (copy/paste :!: ):

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

From here:

[http://linuxundich.de/de/ubuntu/alte-kernel-inkl-header-mit-nur-einem-befehl-entfernen/](http://linuxundich.de/de/ubuntu/alte-kernel-inkl-header-mit-nur-einem-befehl-entfernen/)

---

### Post by praseodym on 2011-10-05
Try it with module rt2800pci:

```
sudo modprobe -rf rt2860sta
sudo modprobe -v rt2800pci
sudo depmod -a
```

---

### Post by orny on 2011-10-05
I guess it is a kind o risky operation. Should I backup data before I proceed? Perhaps it will be safer to downgrade to ...33 kernel version (rt3090 worked smoothly with it)? Does it make sense?

---

### Post by orny on 2011-10-05
> **orny said:**
> I guess it is a kind of risky operation. Should I backup data before I proceed? Perhaps it will be safer to downgrade to ...33 kernel version (rt3090 worked smoothly with it)? Does it make sense?
"risky operation" - I meant #32

---

### Post by praseodym on 2011-10-05
You can also uninstall older kernel and kernel-header-versions by hand via synaptic, no problem (I used this way before without problems). If it worked with kernel 2.6.32-33 you can use the tool **startupmanager** to boot into -33 by default.

---

### Post by orny on 2011-10-05
Bingo! It started. As an option of last resort I opened synaptic and searched it for "ralink". It showed several items and rt3090.dkms as "installed", I made reinstall and reboot, and wifi is on. Sorry for nagging, perhaps I should start from the simplest thing. I was in a bit of panic because i really need this notebook with wireless net working.

---

### Post by maurolust on 2011-10-05
I decided to try a Kubuntu 11.04 liveCD I had laying around to see if things work different fron there. I can`t get wifi access but iwconfig shows something very different. I`ll run Ubuntu live to see if I get the same result.
```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"engstosa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:60:4A:26   
          Bit Rate=40.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0

```

---

### Post by maurolust on 2011-10-05
It also works fine if I boot from a Ubuntu 11 live USB. Is that useful information? I can`t find my ubuntu 10 live CD...

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"engstosa"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:60:4A:26   
          Bit Rate=27 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:33   Missed beacon:0

```

We already reinstalled rt3090.dkms, but I think I`ll try that once again.

---

### Post by maurolust on 2011-10-05
Yes, it did work. Something must have scared the gremlins. Thank you, praseodym. I hope you learned as much from it as I did.:popcorn:

---

