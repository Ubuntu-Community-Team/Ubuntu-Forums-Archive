---
title: "Built in wireless card not working"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by sssSami on 2012-05-19
I have an 6 year old Inspiron 1300, and the built in wireless card doesn't seem to work(at all).
It has worked in earlier versions of Ubuntu after installing the driver in the "Additional drivers"(or whatever it's called in english). It doesn't show up there now...

I assume it's somehow been turned off, disconnected or somehow destroyed or damaged. How can I check that? Is it possibille to fix it by myself trough the Terminal or physically?

Right now I use a blue Gigabyte USB wireless thing.


lspci -vvnn | grep 14e4```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

```Can't see the above code return anything about wireless...

---

### Post by sssSami on 2012-05-20
Bump :\

I have the drivers.
I've tried both the native linux driver and ndiswrapper. Nothing seems to work.

---

### Post by praseodym on 2012-05-20
Please show the outputs of
> lspci -nnk
iwconfig
rfkill list
lsmod

---

### Post by sssSami on 2012-05-21
lspci -nnk
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
    Subsystem: Dell Device [1028:01c9]
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: ata_piix
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01c9]
    Kernel driver in use: b44
    Kernel modules: b44


```iwconfig
```
lo        no wireless extensions.

ham0      no wireless extensions.

eth0      no wireless extensions.


```rfkill list
*(nothing)*

lsmod
```
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252189  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               22528  1 
arc4                   12473  0 
joydev                 17393  0 
rt2800usb              22300  0 
rt2800lib              53264  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              20061  1 rt2800usb
rt2x00lib              48858  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436455  3 rt2800lib,rt2x00usb,rt2x00lib
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
dell_laptop            13671  0 
cfg80211              178679  2 rt2x00lib,mac80211
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                87213  0 
snd_timer              28931  2 snd_pcm,snd_seq
serio_raw              13027  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  18 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
mac_hid                13077  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
i915                  414568  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
b44                    31412  0 
ssb                    50691  1 b44
i2c_algo_bit           13199  1 i915
video                  19068  1 i915

```

---

### Post by TBABill on 2012-05-21
Your active driver is RT2800USB. Can you run 'lsusb' in a terminal without quotes and provide that output? Looks like a Realtek device according to the output of lsmod.

---

### Post by sssSami on 2012-05-21
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0461:4d22 Primax Electronics, Ltd 


```
lol, I always forget to plug the USB wireless back in when I'm done in the Terminal :-\"

---

### Post by TBABill on 2012-05-21
Looks like Ubuntu is not even seeing the device plugged in. Was it plugged in when you ran lsusb?

---

### Post by sssSami on 2012-05-21
> **TBABill said:**
> Looks like Ubuntu is not even seeing the device plugged in. Was it plugged in when you ran lsusb?
No. I assumed you were trying to troubleshoot the internal wireless

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 008: ID 1044:800d Chu Yuen Enterprise Co., Ltd GN-WB32L 802.11n USB WLAN Card**
Bus 004 Device 003: ID 0461:4d22 Primax Electronics, Ltd 

```The USB wireless device is from gigabyte, according to the label. And yes, that works, but that wasn't the problem, that's just a workaround. The USB device isn't even mine.

---

### Post by praseodym on 2012-05-21
See here:
[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=1044%3A800d#post-4365112](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wird-nicht-erkannt-komme-nicht-/?highlight=1044%3A800d#post-4365112)
Its a Ralink rt3070sta chipset. Install the rt5370sta driver
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/42/20/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir /etc/Wireless
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo service network-manager stop
sudo modprobe -rfv rt2800pci
sudo service network-manager start 
```
replug the stick. Please show
```
uname -a
```
DKMS should build the driver automatically after a kernel upgrade, obviously, this doesnt work right now

---

### Post by sssSami on 2012-05-21
Replug? I tought I were going to be independent on the USB device...
```
Linux *(deleted this)*-ME051 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux

```

---

### Post by praseodym on 2012-05-21
Ah, sorry, looks like an internal USB?! Install the package '''linux-headers-generic''' (metapackage for autom. updates) and reboot

---

### Post by sssSami on 2012-05-22
Bump
EDIT: sorry, didn't see your post.

sudo apt-get install linux-headers-generic, I assume?
linux-headers-generic is already newest version, it says.

[IMG]http://jpg.artige.no/store/5/5057.jpg[/IMG]

---

### Post by sssSami on 2012-05-23
I simply bumt the thread, since it's not solved.
Altough, I haven't rebooted since I installed updates last time.
I think I saw something about kernel there(64 bits:confused:).

I'll also add that I've tried to boot the 10.04 LTS Live CD (normal ubuntu) for another purpose, and the wireless didn't work there either.

EDIT: The wireless card wasn't connected preperly. Same with one of the RAM sticks.
Altough, the wireless is *still* not working.


lspci -vvnn | grep 14e4
```
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

---

### Post by sssSami on 2012-05-23
**Bump** *yet again*:-k

Kinda annoying when it obviously can find the wireless card but refuse to use it.
Did one of the things I was asked to put into the terminal blacklist that driver?

---

### Post by praseodym on 2012-05-23
There is the device. It works with the native "b43" Broadcom driver. But you need the firmware for it:

> sudo apt-get install b43-fwcutter
reboot.

---

### Post by sssSami on 2012-05-23
But then what? Wish I had God's phone number, then I'd ask for the wireless to magically work.

---

### Post by sssSami on 2012-05-23
I guess a fresh install would do.
The current is messed up. Doesn't even take wired connections - only the USB wireless device works...

---

