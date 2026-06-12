---
title: "Fujitsu11.10 | Siemens Amilo Pro v3515 wireless problem"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by crhodes on 2011-12-19
Hello all, i just installed Ubuntu 11.10 on the Fujitsu Siemens laptop stated above and i am having problems with the wireless i have tried the driver with Ndiswrapper and no luck, i have looked around for other problems with 11.10 and the Broadcom adapter seemed to be a problem, but i dont think this laptop uses that adapter

any help would be greatly appreciated, thanks

---

### Post by praseodym on 2011-12-19
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
You dont need ndiswrapper for Broadcom-wireless cards, so you should uninstall it via:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Is there a recommended driver in "additional drivers" for your card? If yes, activate it via cable connection afterwards.

---

### Post by crhodes on 2011-12-19
I have inputted the code and uninstalled Ndiswrapper, also i have tried additional drivers numerous times and no drivers appear, here is the output from the lines of code:

Code:
```
administrator@ubuntu:~$ lspci -nnk | grep -iA2 net
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: via-rhine
administrator@ubuntu:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
via                    45249  0 
drm                   192194  1 via
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
joydev                 17393  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
snd                    55902  13   snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_viapro             12969  0 
video                  18908  0 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
via_rhine              27413  0 
pata_via               13398  0 
sata_via               13534  1 
administrator@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

administrator@ubuntu:~$ rfkill list
```

It might be good to note that this laptop uses a button to turn the wireless on and off, i seen some other threads with this noted, thanks

---

### Post by praseodym on 2011-12-19
There is no wireless card listed with "lspci". Was it the complete output? Did you check the BIOS if it can be activated there?

---

### Post by crhodes on 2011-12-19
I ran 'lspci' again and here is the output,

```
administrator@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)

```

I am quite sure this laptop has built-in wireless as the specifications state it has Atheros/ Broadcom 802.11 Wirless LAN, I also checked the BIOS and there is nothing stating me to enable the wireless

---

### Post by praseodym on 2011-12-19
Maybe its a PCMCIA or internal USB?

```
lsusb
pccardctl info
```
please

---

### Post by crhodes on 2011-12-19
Not too sure about that, not getting much output from the commands,

```
administrator@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
administrator@ubuntu:~$ pccardctl info

```

pccardctl info doesn't seem to be giving any information back

---

### Post by praseodym on 2011-12-19
Looks like the card is not recognized. Maybe broken or not in the right place (slot)?!

---

### Post by crhodes on 2011-12-19
I'm really not too sure now, strange really, maybe the laptop doesn't have built-in wireless after all, just seems strange because fujitsu have WLAN drivers for this laptop on their site, plus the laptop has a wireless-on/off button, thank you for you help anyway

---

### Post by praseodym on 2011-12-19
Try this module:

```
sudo modprobe -v fsam7400 radio=1
```
Check:
```
lspci -nnk
rfkill list
iwconfig
```

---

### Post by crhodes on 2011-12-20
Sorry for the late reply, i typed the code in and received this back

```

administrator@ubuntu:~$ sudo modprobe -v fsam7400 radio=1
WARNING: All config files need .conf: /etc/modprobe.d/amilo_special_keys.modprobe, it will be ignored in a future release.
administrator@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364]
    Subsystem: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364]
    Kernel driver in use: agpgart-via
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:1364]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:2364]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:3364]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:4364]
00:00.5 PIC [0800]: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller [1106:5364]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device [1106:6364]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:7364]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
    Kernel modules: shpchp
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:a364] (rev 80)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT8237A SATA 2-Port Controller [1106:0591] (rev 80)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: sata_via
    Kernel modules: sata_via
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: pata_via
    Kernel modules: pata_via
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: uhci_hcd
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: uhci_hcd
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: uhci_hcd
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: uhci_hcd
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: ehci_hcd
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237A PCI to ISA Bridge [1106:3337]
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel modules: i2c-viapro
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller [1106:287e]
    Subsystem: VIA Technologies, Inc. Device [1106:337e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine
00:13.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
    Kernel modules: shpchp
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] [1106:3371] (rev 01)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel modules: viafb
04:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

I did find a Belkin wireless receiver, and this seems to be working at the moment, the laptop may not have built-in wireless, although this receiver is working okay, thank you for the hel p

---

### Post by praseodym on 2011-12-20
> ```
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine
```
Right, only LAN is shown, but maybe its an internal USB or PCMCIA card?!

```
pccardctl info
lsusb
```
please

---

### Post by nipper77 on 2012-02-24
Any news on this yet? Having the same problem and can't get it resolved. Not exactly unix savy either.

---

### Post by praseodym on 2012-02-24
The module is obsolete in 11.10, try the other one:

```
sudo modprobe -rfv fsam7400
sudo modprobe -v wistron_btns 
```
If it only works until reboot, make it permanent:
```
echo "wistron_btns" | sudo tee -a /etc/modules 
```

---

### Post by nipper77 on 2012-02-25
> **praseodym said:**
> The module is obsolete in 11.10, try the other one:

```
sudo modprobe -rfv fsam7400
sudo modprobe -v wistron_btns 
```
If it only works until reboot, make it permanent:
```
echo "wistron_btns" | sudo tee -a /etc/modules 
```

Ok thanks I'll give it a go. All I need to do is type those commands into terminal right?

---

### Post by praseodym on 2012-02-25
Right. C/P also works there

---

### Post by nipper77 on 2012-02-27
> **praseodym said:**
> The module is obsolete in 11.10, try the other one:

```
sudo modprobe -rfv fsam7400
sudo modprobe -v wistron_btns 
```
If it only works until reboot, make it permanent:
```
echo "wistron_btns" | sudo tee -a /etc/modules 
```

No joy I'm getting :

FATAL: Module fsam7400 not found.

followed by

insmod /lib/modules/3.0.0-12-generic/kernel/drivers/input/misc/wistron_btns.ko
FATAL: Error insterting wistron_btns (/lib/modules/3.0.0-12-generic/kernel/drivers/input/misc/wistron_btns.ko: No such device

Any other suggestions?

---

### Post by praseodym on 2012-02-27
Please show the outputs of #12

---

### Post by nipper77 on 2012-02-28
> **praseodym said:**
> Please show the outputs of #12

Ok a truly bizarre occurrence this morning. Found an old belkin wireless adapter and plugged it in to get things going in the meantime. Sure enough two wireless adapters turn up under my network settings, the belkin one and the internal one. So for some strange reason it seems to be working now off the internal wireless, don't ask me how or why because nothing has changed on the laptop as far as I know since the last post.

The only thing is that I'm currently running it off LiveCD and each time I loaded it up off the CD there was a driver update icon in the top right, up to now I'd been updating that. This time I didn't and the wireless worked straight off. Here's hoping it stays that way.

---

### Post by nipper77 on 2012-02-28
And it would seem I spoke to soon. Wireless was working perfectly for a few hours then I switched off the machine, when I turned it on again there was no sign of the wireless adapter so I restarted again. This time the adapter showed up but as 'device not ready' and that's its current status. I can see it but can't turn it on which I suppose is an improvement from recent weeks but not from this morning when it was somehow working perfectly.

---

### Post by praseodym on 2012-02-28
What kind of stick is that? Please show:

```
lsusb
lsmod
iwconfig
```with plugged stick

---

### Post by nipper77 on 2012-04-17
> **praseodym said:**
> What kind of stick is that? Please show:

```
lsusb
lsmod
iwconfig
```with plugged stick

Ok I haven't posted on this for a while, kind of gave up on it for a bit after trying a few suggested solutions none of which worked and I've been quite busy getting a few projects completed. However I thought I'd come back to it as I've noticed something very strange. If I don't boot the laptop into Ubuntu for weeks on end, then the first time that I subsequently do wireless is somehow available....BUT...if I then reboot Ubuntu the inbuilt wireless adapter becomes unavailable again. So essentially if I leave Ubuntu alone for a few weeks then boot into it I have a fully functioning wireless adapter until I reboot the OS when it subsequently becomes unavailable again. Thought that was very strange.

---

### Post by nipper77 on 2012-04-17
right so I've just rebooted there and at this point still have my inbuilt wireless adapter functioning. This did also happen about 6 weeks ago and it failed on the third reboot so I'll see what happens later but for now it is again working.

---

### Post by nipper77 on 2012-04-18
And on the third reboot it finally failed and now I have no wireless again. Furthermore, the USB adapter I had been using to get web access is now giving me the same error - wireless is disabled by hardware switch - this hadn't ever happened previously.

---

