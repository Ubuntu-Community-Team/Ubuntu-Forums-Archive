---
title: "Guess what... no wireless!!"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by cespinal on 2011-05-22
Hi all! 

Just installed kubuntu 11.04... everything working beautifully except wireless... 

I guess this an easy one to solve. Seems that I need to blacklist one of the drivers although I dont know how to do that. 

lspci gives me the output: ```
06:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

```


rfkill list all gives me this output: ```
0: brcmwl-0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
1: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no

```

and lshw -C network gives me this: ```
 *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 5c:ac:4c:70:c3:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0200000-d0203fff
```

As said, blacklisting the wrong drivers should help (I guess).... 

Any hints? 
Cheers!

---

### Post by cespinal on 2011-05-22
bump

---

### Post by josephmills on 2011-05-22
> **cespinal said:**
> 

rfkill list all gives me this output: ```
0: brcmwl-0: Wireless LAN
       [b] Soft blocked: yes
        Hard blocked: yes
1: acer-wireless: Wireless LAN
        Soft blocked: yes[/b]
        Hard blocked: no

```

and lshw -C network gives me this: ```
 *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 5c:ac:4c:70:c3:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
     
Any hints? 
Cheers!

you wireless switch is turned off what kinda computer is this ? also try [code]rfkill unblock all 
``` after you play with the switch then could you show us ```
rfkill list all 
``````
lsmod
``````
dmesg | egrep wl|b43|wlan
``` thanks

---

### Post by cespinal on 2011-05-22
hi there...thanks for replying... 

rfkill unblock all did not seem to do anything.... 

here are the rest of the outputs: 

```
rfkill list all
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

```
lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
vesafb                 13761  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211_crypt_tkip    17387  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2739144  416 
uvcvideo               72195  0 
wl                   2568244  0 
acer_wmi               23771  0 
videodev               82052  1 uvcvideo
sparse_keymap          13898  1 acer_wmi
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
edac_core              53845  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
sp5100_tco             13744  0 
soundcore              12680  1 snd
k10temp                13119  0 
edac_mce_amd           23464  0 
serio_raw              13166  0 
i2c_piix4              13303  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
tg3                   141750  0 
video                  19438  0 
pata_atiixp            13165  0 
```

```
dmesg | egrep wl|b43|wlan
b43: command not found
```

My model is an Acer Aspire 7751G with AMD processors and an ATI card. Im running the 64 bit version of Kubuntu...

---

### Post by josephmills on 2011-05-23
```
sudo apt-get install bcmwl-kernel-source 
``` do you have it? 
then ```
sudo apt-get install broadcom-sta-source 
``` do you have this one? 
then 
```
sudo apt-get install broadcom-sta-common 
``` do you have this one ?
then 
```
sudo apt-get install firmware-b43-installer 
``` do you have this 
please post back also you want to mke it so there is nothing blocking in rfkill so try 
```
rfkill unblock wifi 
``` then ```
rfkill unblock wlan 
``` then let us see ```
rfkill list all 
``` we want it to say that there is npothing blocking it

---

### Post by cespinal on 2011-05-23
Hi there!, 

Had all of them except broadcom-sta-source. 
Then ran all the commands you suggested. Here is the output: 

```
cae@cae-Aspire:~$ rfkill list all                                                                              
0: acer-wireless: Wireless LAN                                                                                 
        Soft blocked: yes                                                                                      
        Hard blocked: no                                                                                       
1: brcmwl-0: Wireless LAN                                                                                      
        Soft blocked: no                                                                                       
        Hard blocked: no 
```

I must say that before running the commands, the wifi LED was orange (typical). After running all of them, the wifi LED became off... 

thank you very much for taking the time to help me with this...I'm hoping we can solve it... KDE feels so good :)

---

### Post by josephmills on 2011-05-23
could we see a ```
lspci -nn
``` I think I know what might be going on here but I need to see that first we will get this down we are getting real close

---

### Post by cespinal on 2011-05-23
haha! great to see we are getting close ;) 

here is the output: 


cae@cae-Aspire:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]
02:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

---

### Post by josephmills on 2011-05-23
> **cespinal said:**
> haha! great to see we are getting close ;) 

here is the output: 


cae@cae-Aspire:~$ lspci -nn

06:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n** [14e4:4357] **(rev 01)

that is not what I thought that I would see but ok please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)
you need the b43sta then we will have to do some blacklisting some stuff also could we see a ```
lsusb
```thanks again tell me us if you get any errors

---

### Post by flash63 on 2011-05-23
Hello,
acer_wmi need a option to activate Wireless
```
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```
Restart

Check
```
rfkill list
iwlist chan
sudo iwlist scan
```

---

### Post by cespinal on 2011-05-23
Hi guys!, thanks for all the info... 
Just had to dash to the office. Will get back to that this afternoon and let you know...

---

### Post by cespinal on 2011-05-23
> **flash63 said:**
> Hello,
acer_wmi need a option to activate Wireless
```
echo "options acer_wmi wireless=1" | sudo tee /etc/modprobe.d/acer_wmi.conf
```
Restart

Check
```
rfkill list
iwlist chan
sudo iwlist scan
```

ITS ALIVE!!!!! EEEEEETS AAAAAALIIIIIVE!!!!!!!

Seems to work, although the wifi led is still orange... strange.. will do a reboot and see if it stays...

EDIT: works great!... marking thread as solved... Thank you so much

---

