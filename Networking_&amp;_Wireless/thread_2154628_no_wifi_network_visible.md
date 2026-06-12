---
title: "no wifi network visible"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by manngaurav on 2013-06-15
Hey guys, I think this is the most repeated issue but i have searched all such threads and no one of them have same problem as me :(
So i was using a live usb on UBUNTU 13.04 64BIT on my laptop acer aspire 4752,BCM43227 , it worked well and the wifi was working very correctly , after 10-15 minutes the system froze/hanged only the arrow was moving and nothing else so i pressed the power button and shut down forcibly.

Now the problem my wifi is enabled but it doesn't show any networks , before restarting it showed 12 networks , please help. 
I know some of you may argue that because maybe there are no networks,but i have checked using  my desktop pc that there are 10 networks available with more than 50% strength


please someone help me this post has got 64 views and no replies :'( , should i add something else that maybe of use..?

---

### Post by praseodym on 2013-06-16
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lspci -nnk | grep -iA2 VGA
iwconfig
lsmod
sudo iwlist scan
```
Does LAN work?

---

### Post by manngaurav on 2013-06-16
ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
    Subsystem: Foxconn International, Inc. Device [105b:e040]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0500]
    Kernel driver in use: tg3
03:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0500]
    Kernel driver in use: sdhci-pci

ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:0506]
    Kernel driver in use: i915

ubuntu@ubuntu:~$ iwconfig

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

ubuntu@ubuntu:~$ lsmod

Module                  Size  Used by
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl
dm_crypt               22820  0 
ath3k                  12918  0 
btusb                  22474  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  6 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
joydev                 17377  0 
coretemp               13355  0 
uvcvideo               80847  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm_intel             132891  0 
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
kvm                   443165  1 kvm_intel
acer_wmi               32467  0 
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
parport_pc             28152  0 
sparse_keymap          13890  1 acer_wmi
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
serio_raw              13215  0 
dm_multipath           22843  0 
mac_hid                13205  0 
ppdev                  17073  0 
snd                    68876  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
bnep                   18036  2 
lpc_ich                17061  0 
mei                    41158  0 
lp                     17759  0 
scsi_dh                14843  1 dm_multipath
soundcore              12680  1 snd
rfcomm                 42641  12 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
squashfs               36522  1 
overlayfs              28003  1 
nls_iso8859_1          12713  1 
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
usb_storage            57204  1 
wmi                    19070  1 acer_wmi
sdhci_pci              18590  0 
sdhci                  32522  1 sdhci_pci
i915                  600351  3 
tg3                   153796  0 
ptp                    18621  1 tg3
pps_core               14080  1 ptp
ahci                   25731  1 
libahci                31364  1 ahci
video                  19390  2 i915,acer_wmi
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper

ubuntu@ubuntu:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : Invalid argument

lo        Interface doesn't support scanning.


YES LAN IS WORKING

---

### Post by manngaurav on 2013-06-16
I THINK the above output is hard to understand so , here is the link to   (screenshots and ouptut as .pdf and .odt , i dont know how to make it more readable)   [https://drive.google.com/folderview?id=0B7HkyEpc4XxdQnhSWnl0TE9KWU0&usp=sharing](https://drive.google.com/folderview?id=0B7HkyEpc4XxdQnhSWnl0TE9KWU0&usp=sharing) . Thank you very much for your help , please help me solve it thank you once again

---

### Post by ahallubuntu on 2013-06-16
~

---

### Post by Hadaka on 2013-06-16
Hi, give this a try..
copy and paste..
```
 
echo blacklist acer_wmi | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then do..
```
sudo modprobe -rfv wl
sudo modprobe -v wl
```
boot 
thanks.

---

### Post by manngaurav on 2013-06-16
@ahallubuntu    i dont know why is that wl driver is  showing up but here  i think the driver is correct[ATTACH=CONFIG]243870[/ATTACH][ATTACH=CONFIG]243871[/ATTACH]

---

### Post by manngaurav on 2013-06-16
@ahallubuntu  this was the output of all those instruction i dont know if they were completed correctly or not please check , because i still dont have any networks


   	 	 	 	   ubuntu@ubuntu:~$  sudo apt-get --reinstall install bcmwl-kernel-source  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following package was automatically installed and is no longer required:  
   linux-image-generic  
 Use 'apt-get autoremove' to remove it.  
 0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 104 not upgraded.  
 Need to get 0 B/1,346 kB of archives.  
 After this operation, 0 B of additional disk space will be used.  
 (Reading database ... 162424 files and directories currently installed.)  
 Preparing to replace bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6 (using .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...  
 Removing all DKMS Modules  
 Done.  
 Unpacking replacement bcmwl-kernel-source ...  
 Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...  
 Loading new bcmwl-6.20.155.1+bdcom DKMS files...  
 Building only for 3.8.0-19-generic  
 Building for architecture x86_64  
 Building initial module for 3.8.0-19-generic  
 Done.  
 

 wl:  
 Running module version sanity check.  
  - Original module  
    - No original module exists within this kernel  
  - Installation  
    - Installing to /lib/modules/3.8.0-19-generic/updates/dkms/  
 

 depmod....  
 

 DKMS: install completed.  
 update-initramfs is disabled since running on read-only media  
  
ubuntu@ubuntu:~$ sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
ubuntu@ubuntu:~$ sudo modprobe wl

---

### Post by manngaurav on 2013-06-16
> **Hadaka said:**
> Hi, give this a try..
copy and paste..
```
 
echo blacklist acer_wmi | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then do..
```
sudo modprobe -rfv wl
sudo modprobe -v wl
```
boot 
thanks.  
 here's the ouptut of you commands

ubuntu@ubuntu:~$ echo blacklist acer_wmi | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist acer_wmi
ubuntu@ubuntu:~$ sudo modprobe -rfv wl
rmmod wl
rmmod cfg80211
ubuntu@ubuntu:~$ sudo modprobe -v wl
insmod /lib/modules/3.8.0-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko

STILL UNSOLVED

---

### Post by manngaurav on 2013-06-16
i rebooted and nothing happens , perhaps because i am using live usb everything gets deleted on reboot..?  after every time i restart i have to go to system>softwaresand apps>enable multiverse and then under additional drivers the broadcom sta driver then only i can get the enable wifi option in network manager

---

### Post by manngaurav on 2013-06-17
i request the forum moderator to delete this thread i have solved the problem myself after waiting for 2 days, left me with a bad taste anyways thankyou for all those who tried to help

---

### Post by matt_symes on 2013-06-17
Hi

> **manngaurav said:**
> i request the forum moderator to delete this thread i have solved the problem myself after waiting for 2 days, left me with a bad taste anyways thankyou for all those who tried to help

Instead of having the thread deleted, do you fancy posting your solution in this thread so that others can benefit from it ?

Kind regards

---

