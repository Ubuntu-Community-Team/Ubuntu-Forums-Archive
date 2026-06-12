---
title: "Cannot see D-Link DIR-615"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by CrawlingKSnake on 2011-05-22
Hey guys,

I've just installed ubuntu 11.04 on my dell inspiron mini 10; dual-booting it with Windows 7.

I've looked at a couple of other threads about problems with the wireless card in the netbook and about problems with the wireless router. However, this problem doesn't seem to be the same; the netbook can see other wireless networks, just not mine, and other people seemed to be able to access their wireless network for a short period of time before they stopped being able to access it.

I can't see the wireless network on the D-link DIR-615 at all in ubuntu, though it still works in windows 7. 

I've tried reinstalling the broadcom STA drivers as per this [link ]("http://www.ubuntumini.com/")and reinstalling but this hasn't made any difference.

What things should I consider trying in order to resolve this?

Thanks for any help!

Ps. As a side note, my other ubuntu laptop (a toshiba equium A100) cannot see this network either, but has no problem connecting to other, although oddly it couldn't detect it in windows either before I put in a new harddrive and installed ubuntu on it.

---

### Post by josephmills on 2011-05-22
> **CrawlingKSnake said:**
> Hey guys,

I've just installed ubuntu 11.04 on my dell inspiron mini 10; dual-booting it with Windows 7.

I've looked at a couple of other threads about problems with the wireless card in the netbook and about problems with the wireless router. However, this problem doesn't seem to be the same; the netbook can see other wireless networks, just not mine, and other people seemed to be able to access their wireless network for a short period of time before they stopped being able to access it.

I can't see the wireless network on the D-link DIR-615 at all in ubuntu, though it still works in windows 7. 

I've tried reinstalling the broadcom STA drivers as per this [link ]("http://www.ubuntumini.com/")and reinstalling but this hasn't made any difference.

What things should I consider trying in order to resolve this?

Thanks for any help!

Ps. As a side note, my other ubuntu laptop (a toshiba equium A100) cannot see this network either, but has no problem connecting to other, although oddly it couldn't detect it in windows either before I put in a new harddrive and installed ubuntu on it.


Hi there could you open your terminal and type in ```
lspci -nn
``` and ```
rfkill list all 
``` then paste here also are you on the machine (dell) with internet?

---

### Post by CrawlingKSnake on 2011-05-22
Ok, here's the output

 > hamer@hamer-Inspiron-1011:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
hamer@hamer-Inspiron-1011:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
hamer@hamer-Inspiron-1011:~$ 
Yeah I'm on the dell atm using a wired connection. I've got other computers I can access the internet through though.

Thanks

---

### Post by josephmills on 2011-05-22
how about a ```
lsmod 
``` and ```
dmesg | grep rt
``` thanks

---

### Post by CrawlingKSnake on 2011-05-22
Here's the output for that:

> hamer@hamer-Inspiron-1011:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
lib80211_crypt_tkip    17203  0 
snd_seq_midi_event     14475  1 snd_seq_midi
usbhid                 41704  0 
wl                   2642531  0 
dell_laptop            13515  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
compal_laptop          19283  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
hid                    77084  1 usbhid
dcdbas                 14054  1 dell_laptop
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
videodev               75143  1 uvcvideo
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
video                  18951  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ath_pci               183044  0 
wlan                  224640  1 ath_pci
ath_hal               398701  1 ath_pci
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
r8169                  42534  0 
hamer@hamer-Inspiron-1011:~$ dmesg | grep rt
[    0.000000] Movable zone start PFN for each node
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] virtual kernel memory layout:
[    0.008215] mce: CPU supports 5 MCE banks
[    0.201346] ACPI: (supports S0 S3 S4 S5)
[    0.292601] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.296698] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.296888] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.297079] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.297269] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.298113] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.298791] pci 0000:00:1f.2: PME# supported from D3hot
[    0.299912] pci 0000:03:00.0: supports D1 D2
[    0.299922] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.300945] pci 0000:04:00.0: supports D1 D2
[    0.300953] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.461927] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.462031] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.462218] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.462305] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.462466] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.462551] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.562494] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.928634] Linux agpgart interface v0.103
[    0.928803] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    0.928980] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.929165] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.929411] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.092609] ehci_hcd 0000:00:1d.7: debug port 1
[    1.096516] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.112035] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.112351] hub 1-0:1.0: 8 ports detected
[    1.113287] hub 2-0:1.0: 2 ports detected
[    1.114030] hub 3-0:1.0: 2 ports detected
[    1.116483] hub 4-0:1.0: 2 ports detected
[    1.117248] hub 5-0:1.0: 2 ports detected
[    1.142200] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.142220] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.144077] rtc_cmos 00:08: RTC can wake from S4
[    1.144244] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.144291] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.149329] Using IPI No-Shortcut mode
[    1.150572] rtc_cmos 00:08: setting system clock to 2011-05-22 22:45:16 UTC (1306104316)
[    1.306454] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.420611] <30>udev[66]: starting version 167
[    1.972208] USB Mass Storage support registered.
[   14.265463] <30>udev[281]: starting version 167
[   18.001216] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.001226] [drm] Driver supports precise vblank timestamp query.
[   18.081442] [drm] initialized overlay support
[   19.183994] ppdev: user-space parallel port driver
[ 3848.438926] UDP: short packet: From 187.175.192.32:4988 121/77 to 192.168.0.103:19141
[ 3938.444868] UDP: short packet: From 187.175.192.32:4988 122/89 to 192.168.0.103:19141


Thanks

---

### Post by josephmills on 2011-05-22
all right try this please open up synaptic and type in bcm onto the search bar then remove everything that comes up then shut down the computer and then restart then open synaptic package manager and type in bcm and install the broadcom-sta-source and the broadcom-sta-common the firmware-b43-lpphy-installer and the bcmwl-kernel-source then reboot the computer and post ```
lsmod | grep wl
``` and ```
dmesg | grep wl
``` thanks

---

### Post by CrawlingKSnake on 2011-05-22
Alright then.

I don't know if it's relevant or not but after installing the packages in synaptic I received an error message that said:

> An error occured

The following details are provided:

E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1 

The terminal output read:

> 
hamer@hamer-Inspiron-1011:~$ lsmod | grep wl
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
wlan                  224640  1 ath_pci
hamer@hamer-Inspiron-1011:~$ dmesg | grep wl
[   17.316235] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.264561] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.264586] wl 0000:03:00.0: setting latency timer to 64



Cheers

---

### Post by josephmills on 2011-05-22
install the firmware-b43-lpphy-installer  and reboot anything?

---

### Post by CrawlingKSnake on 2011-05-22
No error message this time.

This output in the terminal:

> hamer@hamer-Inspiron-1011:~$ lsmod | grep wl
wl                   2642531  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
wlan                  224640  1 ath_pci
hamer@hamer-Inspiron-1011:~$ dmesg | grep wl
[   17.863400] wl: module license 'MIXED/Proprietary' taints kernel.
[   18.686947] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.686973] wl 0000:03:00.0: setting latency timer to 64
hamer@hamer-Inspiron-1011:~$ 
The netbook can still see the same routers as before and still doesn't pick up the D-link.

Thanks

---

### Post by josephmills on 2011-05-22
hardline reset the d-link router anything? try ```
sudo rmmod -f dell-laptop

``` 
then post ```
rfkill list all
```

---

### Post by CrawlingKSnake on 2011-05-22
I can't get at the router to reset it until tomorrow, unfortunately people already sleeping in that room.

I entered the commands into the console anywho and got this:

> hamer@hamer-Inspiron-1011:~$ sudo rmmod -f dell-laptop
[sudo] password for hamer: 
ERROR: Removing 'dell_laptop': No such file or directory
hamer@hamer-Inspiron-1011:~$ rfkill list all
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
hamer@hamer-Inspiron-1011:~$ 


Thanks for all your help so far, I'm going to have to sleep now for a bit though. I'll reset the router and enter the commands in the terminal again and post the results in the morning tomorrow.

Thanks again! 

I'm really hoping that ubuntu will detect the wifi in the end, running windows on this netbook is a really horribly slow and breaky experience!

---

### Post by CrawlingKSnake on 2011-05-23
Ok then.

Reset the router and can now access the internet wirelessly through the dlink both the dell netbook and the toshiba laptop that I mentioned as a side note.

The internet connection failed after a couple of moments but turning off the modem and the router brought it back. However this happens quite a lot anyway and I'm forever resetting them in this way.

I'll follow the instructions to change the SSID of the router, add some security etc. and continue to use the wireless connection throughout the day and report back whether it still works.

Many many thanks!

---

