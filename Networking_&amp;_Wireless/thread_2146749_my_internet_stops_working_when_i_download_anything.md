---
title: "my internet stops working when i download anything"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by rlcbm on 2013-05-19
i am using netgear n300 with ndsi wrapper so it will work but when i download anything it crashes my internet but the contection bar says its conected ```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
07:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)



``` ```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
07:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
rlcbm@rlcbm-CM6630-CM6730-CM6830:~$ clear


rlcbm@rlcbm-CM6630-CM6730-CM6830:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  2 
snd_hda_codec_hdmi     31423  1 
ndiswrapper           192647  0 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
parport_pc             31968  0 
ppdev                  12817  0 
coretemp               13168  0 
kvm_intel             126745  0 
kvm                   357806  1 kvm_intel
aesni_intel            17938  0 
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
snd_hda_codec_realtek    63356  1 
eeepc_wmi              12949  0 
asus_wmi               19320  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_intel          32515  5 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
video                  18847  0 
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
wmi                    18590  1 asus_wmi
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17161  0 
mac_hid                13037  0 
usblp                  17751  0 
radeon                820703  2 
microcode              18209  0 
psmouse                84843  0 
ttm                    75534  1 radeon
lpc_ich                16925  0 
drm_kms_helper         45271  1 radeon
serio_raw              13031  0 
drm                   230463  4 radeon,ttm,drm_kms_helper
soundcore              14599  1 snd
lp                     13299  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13197  1 radeon
parport                40753  3 parport_pc,ppdev,lp
mei                    35796  0 
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
ums_realtek            17669  0 
uas                    17556  0 
usb_storage            39350  3 ums_realtek
r8169                  55976  0 

``` and it stops working when i use youtube

---

### Post by rlcbm on 2013-05-19
bump i really need help its the only os i have

---

### Post by matt_symes on 2013-05-19
Thread move to the **networking and wireless** sub-forum.

Please leave 24 hours between bumping threads. This is an international forum and people can arrive at any time of the day (or night).

If someone sees your post and can help, they will usually post.

---

### Post by rlcbm on 2013-05-19
sry

---

### Post by wildmanne39 on 2013-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by rlcbm on 2013-05-19
oh i used quote not code did not know about that

---

### Post by wildmanne39 on 2013-05-19
No problem enjoy the forum.

---

### Post by rlcbm on 2013-05-20
bump

---

### Post by rlcbm on 2013-05-21
bump again aw

---

### Post by grahammechanical on 2013-05-21
I do not understand what is happening on your computer. What do you mean when you say "it crashes my internet." Do you mean that when you are browsing the web/internet and you use Software Centre to download an application then the browser looses the connection to your Internet Service Provider?

This happens to me and it also happens when I try to browse the web at the same time as running a system update. It is not possible to download large amounts of data and browse the web at the same time because the connection to the ISP does not have enough bandwidth to do these two things at once.

It is different if I am using a web browser to download a file. But even so the download will slow down if I keep switching to new web sites. This is to be expected.

If something different is happening to you, then please explain more clearly. What computer do you have? Are you connecting to the router by wireless or by ethernet cable? What wireless adapter does the computer have.

Regards.

---

### Post by rlcbm on 2013-05-21
> **grahammechanical said:**
> I do not understand what is happening on your computer. What do you mean when you say "it crashes my internet." Do you mean that when you are browsing the web/internet and you use Software Centre to download an application then the browser looses the connection to your Internet Service Provider?

This happens to me and it also happens when I try to browse the web at the same time as running a system update. It is not possible to download large amounts of data and browse the web at the same time because the connection to the ISP does not have enough bandwidth to do these two things at once.

It is different if I am using a web browser to download a file. But even so the download will slow down if I keep switching to new web sites. This is to be expected.

If something different is happening to you, then please explain more clearly. What computer do you have? Are you connecting to the router by wireless or by ethernet cable? What wireless adapter does the computer have.

Regards.
oh it works on windows so i know its not the isp and i have Verizon and i think yes to first question and ty for replying its on op but its netgear wna3100(v1) and thats a usb for internet the computer is a asus computer

---

### Post by rlcbm on 2013-05-22
bump

---

### Post by setheb on 2013-05-22
I had a similiar problem with a Bluetooth adapter I bought years ago. It worked fine on Windows, but not on Ubuntu.

Have you read the datasheet for your USB network adapter?
[http://www.netgear.com/images/WNA3100_DS_15June1018-5775.pdf](http://www.netgear.com/images/WNA3100_DS_15June1018-5775.pdf)

The WNA3100 does not support Linux.

Did you notice the driver download is 22MB? Hardware manufacturers have been doing this ever since the "soft" modem. They skimp on hardware components by offloading as much work as possible on to the driver.

 What's happening is the wireless signal is fluxuating when your "Internet crashes." It probably wants to offload more data more quickly. The linux module dosen't recognize or support the new condition or its parameters. As the device expects to communicate with the Windows driver, they're both confused. Crash.

Don't hold your breath waiting for the module to support your device, it could take years... if the condition is even widely adopted.

Wired Gigabit owns, BTW. Get yourself a long cord!

---

### Post by rlcbm on 2013-05-23
do i get a wired gigabit is that a receaver because i have a router

---

### Post by setheb on 2013-06-02
> **rlcbm said:**
> do i get a wired gigabit is that a receaver because i have a routerI added "Wired Gigabit owns" to my post because you noted earlier that your PC has a Gigabit-capable Ethernet controller:> **rlcbm said:**
> ```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```It stands to reason that if you're working with wireless at N speeds, the router already operates its Ethernet segment at Gigabit speeds. Speeds that can only be achieved with a cord. Simply put: nothing beats a cord. It may be ugly, in the way, inconvienient and everything else -- but when it comes to time-sensitive data like gaming, video streaming and large file downloads -- those extra few milliseconds shaved from transmission time really polish off its lack of wireless interference.

Even if it's quite a distance from the router to your Ubuntu rig: a 100-foot CAT6 Ethernet cable is available in the $20-$30 range on Amazon.com.

---

