---
title: "Intel 3945 wifi not working 11.04"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by raiden82 on 2011-09-16
Hi, just got a laptop with the Intel 3945ABG card and Ubuntu (or any linux distro) doesn't see it at all, not finding a lot of help since this card is "supposed" to work, can't even find drivers..
If i wasn't dreaming first time i tried the connection was working but reinstalled and never worked again.

here's lspci:

[HTML]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 10)
05:01.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:01.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:01.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:01.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
[/HTML]have to mention that i don't have any other mean to connect to internet other than my desktop pc on wifi as well.

Thanks

---

### Post by praseodym on 2011-09-16
Have a look in your BIOS settings if wireless is turned off.

---

### Post by raiden82 on 2011-09-16
Hi, thanks for the reply, in the bios there's no option regarding wlan, i've tried to change other options with no luck, and the laptop has buttons for it that do nothing..

---

### Post by wildmanne39 on 2011-09-16
Hi, please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
lsusb
```
```
sudo pccardctl ident
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by raiden82 on 2011-09-16
[HTML]cat /etc/lsb-release; uname -a


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux raiden 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux[/HTML]

[HTML] sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:1b:24:8c:4e:17
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:da000000-da003fff ioport:3000(size=256) memory:d4000000-d401ffff[/HTML]

[HTML]lspci -nn | grep -e 0280 -e 0200

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 10)[/HTML]
[HTML]
lsusb

Bus 005 Device 002: ID 062a:0252 Creative Labs 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0204:1976 Chipsbank Microelectronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/HTML]
[HTML]
sudo pccardctl ident

Socket 0:
  no product info available[/HTML]

[HTML]iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
[/HTML]

[HTML]lsmod

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  1 
uas                    17676  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
binfmt_misc            13213  1 
snd_hda_intel          24140  2 
pcmcia                 39671  0 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  450944  3 
usbhid                 41704  0 
hid                    77084  1 usbhid
snd_timer              28659  2 snd_pcm,snd_seq
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
tifm_7xx1              12898  0 
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
tifm_core              15040  1 tifm_7xx1
drm                   180037  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
sky2                   49172  0 [/HTML]

1 command is missing but doesn't return anything, thanks

---

### Post by wildmanne39 on 2011-09-16
Hi, alright the card does not show up at all so I recommend if this is a desktop that you open it up and put the card in a different slot or reseat the card.

Other wise the card may be dead.
Thank you

---

### Post by raiden82 on 2011-09-16
was working when using the live cd, then i installed it and i stopped, it's a laptop..and works under windows or fedora live cd

---

### Post by wildmanne39 on 2011-09-16
Hi, that is strange try this command and post the results and I will do some research.
```
lspci -nn
```
I can tell you that no drivers are loaded for it but it should still be able to be seen.
Thank you

---

### Post by raiden82 on 2011-09-16
here:

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
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
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 10)
05:01.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
05:01.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
05:01.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
05:01.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

---

### Post by wildmanne39 on 2011-09-16
Hi, unplug your wired connection then run this command please:
```
sudo modprobe iwl3945
```
then give it a minute to see if the card comes a live. If so we will need to make it permanent.
Thank you

---

### Post by raiden82 on 2011-09-16
Hi, just changed in the bios this option: Preboot Environment from disabled to enabled
and now it works, that's strange plus i'm sure i've tried before...well thanks for the help anyway!

---

### Post by wildmanne39 on 2011-09-16
Hi, I had thought about the bios but I knew you had already tried that.

Would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by raiden82 on 2011-09-16
Didn't really know about that option, it worked just once, after reboot it's gone again sigh..

---

### Post by wildmanne39 on 2011-09-16
Hi, is that with the command I posted? or just the bios change? It may be that you need to replace your battery if you are losing bios settings.
Thank you

---

### Post by raiden82 on 2011-09-16
Hi, the bios keeps the settings it's just strange, the command before returns nothing.

---

### Post by wildmanne39 on 2011-09-16
Hi, is this the command you are talking about?
```
sudo modprobe iwl3945
```
if so it will not return anything it will just turn your wireless on hopefully but we will have to make it permanent because when you restart your computer it will be gone.

Is this command working for you? do we need to make it permanent?

Also remember you need to unplug your wired connection before you run it.
Thank you

---

### Post by raiden82 on 2011-09-16
Yes that command and changes nothing, i don't have a wired connection, only a desktop with wireless.
It still shows in the network manager that i've connected before, the only thing i can think of is some power issues where the card doesn't get enough? bah

---

### Post by chili555 on 2011-09-17
> **raiden82 said:**
> Hi, just changed in the bios this option: Preboot Environment from disabled to enabled
and now it works, that's strange plus i'm sure i've tried before...well thanks for the help anyway!When you go back into the BIOS, is it again shown as disabled, even though you changed it and saved your changes? In other words:

1. Boot computer, enter BIOS, change Preboot Environment from disabled to enabled. Be sure to save changes, often F10 in BIOS.

2. Load Ubuntu and wireless works.

3. Shut down and sip a cup of tea.

4. Boot to Ubuntu. Does wireless work?

5. If not, reboot to BIOS; what does Preboot Environment say?

---

### Post by raiden82 on 2011-09-17
Thanks Chili, yes the bios saves the settings as they stay the same after reboot, i think it's just some hardware issue with the card as it works randomly, once i even got the wireless option in the bios, so i guess it switches on/off by itself, today i tried to install windowze to see if it's the same and yes, no wifi. sigh..
Think that i just got the laptop for the wifi as i needed for work.
I have a 3g dongle around which works as wifi as well, going to try if that works, Huawei E160 any idea?
thanks

---

### Post by bkratz on 2011-09-17
Here is a thread about the E160

[http://ubuntuforums.org/showthread.php?t=1748447&page=2](http://ubuntuforums.org/showthread.php?t=1748447&page=2)

---

### Post by SeijiSensei on 2011-09-17
Even if it's a laptop, you should be able to open a door on the bottom of the device to gain access to the Intel card. I recommend taking it out and re-seating it in the slot before giving up.

---

### Post by raiden82 on 2011-09-17
Hi, i've tried that as well and nothing, thanks for the help anyways!

---

### Post by wildmanne39 on 2011-09-17
Hi, I am sorry to hear that it is a hardware issue but that is what I suspected but it through me by working sometimes.

---

### Post by raiden82 on 2011-09-17
I didn't give up! i possibly found the issue, the wifi switch doesn't work or it's not installed properly as after few tries it blinked on and connected! but just that one time, is there any command to force it on/off?

---

### Post by wildmanne39 on 2011-09-17
Hi, it is possible, what brand of laptop is this? I am thinking a dell.
Thank you

---

### Post by raiden82 on 2011-09-17
It's an advent

---

### Post by wildmanne39 on 2011-09-17
Hi, I do not see any modules loaded in your lsmod information that can be unloaded to turn it on.

Run this command again and post the results hopefully it will show something this time.
```
rfkill list all
```   
Thank you

---

### Post by raiden82 on 2011-09-21
Sry, i've been away, i took the chance to run the updates when the wifi was working and now seems to connect nicely every time i restart.

Thanks a lot for the help.

---

### Post by wildmanne39 on 2011-09-21
Hi, your welcome! I an glad it is working.

---

