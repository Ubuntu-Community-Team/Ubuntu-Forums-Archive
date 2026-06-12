---
title: "No sound since upgrade to Natty 11.04"
date: 2011-07-12
forum: Multimedia Software
---

### Post by robbennett75 on 2011-07-12
Hi all,
I've got the "dummy output" showing in the sound preferences dialogue, but can't really figure out where to go next.

I've got:
```
rob@claret:~$ sudo aplay -l
[sudo] password for rob: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```and 

```
rob@claret:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
    Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: cc000000-cdffffff
    Prefetchable memory behind bridge: ce000000-dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at cbef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: 80800000-809fffff
    Prefetchable memory behind bridge: 0000000080a00000-0000000080bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: 80c00000-80dfffff
    Prefetchable memory behind bridge: 0000000080e00000-0000000080ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 7880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 7c00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 8000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 8080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at cbeffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: cbf00000-cbffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 8c00 [size=8]
    I/O ports at 8880 [size=4]
    I/O ports at 8800 [size=8]
    I/O ports at 8480 [size=4]
    I/O ports at 8400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: medium devsel, IRQ 10
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. P5GD1-VW Mainboard
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at cbffe000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 9880 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46) (prog-if 10 [OHCI])
    Subsystem: Allied Telesis, Inc IEEE 1394 4port DCST 1394-3+1B
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at cbfff800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at 9c00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

06:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8343
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at cdf00000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidia-173, nvidia-current, nouveau, nvidiafb

06:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8343
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at cdffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Most of the problems I've found in the archive are about reinstalling alsa, which I've done several times, so I really hope someone can point me in the right direction.

many thanks,
Rob, 
Southampton, UK

---

### Post by BicyclerBoy on 2011-07-12
With 11.04 I don't think you need to update alsa to get HDMI audio to work.

Are you trying to get HDMI audio to work ?
Or are you trying to use normal mobo sound working ?

search forums for nvidia hmdi audio

---

### Post by robbennett75 on 2011-07-13
Hi,
No, I'm not wanting HDMI audio, just regular inboard sound like I had in the previous versions of Ubuntu.

As I understand it I'm close because the aplay -l command shows my sound card, but I'm stumped about where to go next.

Rob

---

### Post by pedrotokarski on 2011-07-13
same problem here, was working nice yesterday, after kernel upgrade today, it's not. any clues?

---

### Post by lidex on 2011-07-14
Aplay looks fine so I would suspect pulse audio. Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
[I] Ignore any 'No such file or directory' errors[/I

---

### Post by selcho on 2011-07-15
Hi,
I was having the same problem. Tried all the above suggestions without success. Compared the lsmod output for 2.6.38-8-generic and 2.6.38-10 generic kernels and found that snd-hda-intel and snd-hda-codec-realtek were not being loaded. 
From working 2.6.38-8-generic install:

[HTML]$ lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 82fe
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

$ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC1200

$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

options snd-hda-intel model=ALC1200
#options snd-hda-intel model=auto index=-0[/HTML]Edited /etc/alsa-base.conf using the "model=ALC1200" information in place of "model=auto" and sound is now working.

Sound Preferences no longer lists the Analogue Surround 7.1 Output selection but Analogue Surround 5.1 Output preferable to silence.

There must be a code re-write solution to this but hope this helps in the meantime.

---

### Post by robbennett75 on 2011-07-15
lidex, thanks but it's made no difference. 

I also tried adding 

[PHP]options snd-hda-intel model=auto index=-0[/PHP]to the end of my /etc/modprobe.d/alsa-base.conf but also made no difference.

Does this lsmod outout tell us something?  I notice the used by "0" output against snd_hda_intel

```

rob@claret:~$ lsmod
Module                  Size  Used by
autofs4                27918  1 
vesafb                 13449  1 
ip6table_filter        12711  0 
ip6_tables             22545  1 ip6table_filter
binfmt_misc            13213  1 
ipt_MASQUERADE         12663  3 
iptable_nat            12977  1 
nf_nat                 24827  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19024  4 iptable_nat,nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           69744  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             12512  2 
md4                    12523  0 
xt_CHECKSUM            12493  1 
iptable_mangle         12615  1 
xt_tcpudp              12531  5 
iptable_filter         12706  1 
ip_tables              18125  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21907  11 ip6table_filter,ip6_tables,ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_CHECKSUM,iptable_mangle,xt_tcpudp,iptable_filter,ip_tables
bridge                 75021  0 
stp                    12811  1 bridge
snd_hda_codec_hdmi     27535  4 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nfsd                  252397  11 
exportfs               12870  1 nfsd
snd_rawmidi            25269  1 snd_seq_midi
nfs                   282952  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lockd                  74292  2 nfsd,nfs
fscache                50364  1 nfs
nfs_acl                12771  2 nfsd,nfs
auth_rpcgss            39173  2 nfsd,nfs
nls_utf8               12493  2 
cifs                  247650  3 
sunrpc                199096  19 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
parport_pc             32111  1 
serio_raw              12990  0 
nvidia              10675438  72 
snd                    55295  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
w83627ehf              24000  0 
hwmon_vid              12658  1 w83627ehf
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
firewire_ohci          31504  0 
floppy                 60032  0 
firewire_core          56138  1 firewire_ohci
e100                   40108  0 
crc_itu_t              12627  1 firewire_core


```

thanks for any suggestions.

Rob

---

### Post by myyk on 2011-07-15
I don't mean to sound like a retard but mine was muted when it loaded, just unmuted and wala sound.

---

### Post by selcho on 2011-07-15
Hi Rob,

Have you tried editing the /etc/modprobe.d/alsa-base.conf  using card number ALC880 (information supplied in  your first post).

options snd-hda-intel model=ALC880

and delete

options snd-hda-intel model=auto index=-0

My lsmod shows snd_hda_intel is used by 1 when sound is working.

Hope this helps

Malc

---

### Post by lidex on 2011-07-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by selcho on 2011-07-16
Hi lidex,

[http://www.alsa-project.org/db/?f=e219d57944a4b21750d0f885a9b234acdbcb2f94](http://www.alsa-project.org/db/?f=e219d57944a4b21750d0f885a9b234acdbcb2f94)

My sound seems to be working normally after editing /etc/alsa-base.conf except that I no longer have an eight channel speaker selection. Front speakers out no longer available.

Does this upload shed any light on that?

Thanks,
Malc

---

### Post by lidex on 2011-07-16
> **selcho said:**
> Hi lidex,

[http://www.alsa-project.org/db/?f=e219d57944a4b21750d0f885a9b234acdbcb2f94](http://www.alsa-project.org/db/?f=e219d57944a4b21750d0f885a9b234acdbcb2f94)

My sound seems to be working normally after editing /etc/alsa-base.conf except that I no longer have an eight channel speaker selection. Front speakers out no longer available.

Does this upload shed any light on that?

Thanks,
Malc
For one thing there is no model ALC1200. What is the make/model of this computer?

---

### Post by selcho on 2011-07-17
Hi lidex,

Many thanks for quick reply.

PC is home assembled from procured parts.

Motherboard is ASUS P5Q with following Intel Audio Controller.

$ lspci -v | less

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. Device 82fe
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

The ALC1200 model information comes from:

~$cat /proc/asound/card0/codec* | grep Codec
Codec Realtek ALC1200

The sound wouldn't work at all after update to 2.6.38-10-gerneric kernel.

[FONT=monospace]By using this model number in /etc/modprobe.b/alsa-base.conf I was able to get the sound to work[FONT=Verdana] semmingly well except for lost 8 channel selection.

The computer has no sound problems with the 2.6.28-8-generic kernel.

Thanks 
Malc
[/FONT][/FONT]

---

### Post by selcho on 2011-07-17
HI lidex,

Re-checked all settings booting into both kernels and confirm that cat /proc/asound/card0/codec* | grep Codec always returns the ALC1200 number. 

Unchecked options snd-hda-intel model=auto index=-0 line in /etc/modprobe.d/alsa-base.conf and ran again - no sound. 

As a last resort I modified this line to read 
options snd-hda-intel model=auto
without index=-0 and what do you know - everything is fixed - Analogue Surround 7.1 appears in Sound Preferences and 8 channels restored.

What does index=-0 cause to happen when loading audio?

Thanks

Malc

---

### Post by robbennett75 on 2011-07-17
Hi lidex,

[http://www.alsa-project.org/db/?f=72cdbe131c9d85470d5179bb8b7c694f21af878f](http://www.alsa-project.org/db/?f=72cdbe131c9d85470d5179bb8b7c694f21af878f)

I also tried adding the line to alsa-base.conf as suggested by selcho, but made no difference.

cheers,

Rob

---

### Post by lidex on 2011-07-17
> **robbennett75 said:**
> Hi lidex,

[http://www.alsa-project.org/db/?f=72cdbe131c9d85470d5179bb8b7c694f21af878f](http://www.alsa-project.org/db/?f=72cdbe131c9d85470d5179bb8b7c694f21af878f)

I also tried adding the line to alsa-base.conf as suggested by selcho, but made no difference.

cheers,

Rob

Once again a non-existent model. What is the make/model and/or motherboard info?

---

### Post by selcho on 2011-07-17
Hi,

Finally got a code line addition for /etc/modprobe.d/alsa-base.conf that satisfies both 2.6.38-8-generic and 2.6.38-10-generic kernels.

options snd-hda-intel model=auto index=0 gives Analogue Sound 7.1 Output - sound works properly.

The only difference after update was the 2.6 .38-10-generic kernel will not load the correct modules with the additional dash (-) as in 
options snd-hda-intel model=auto index=-0

Hopes this helps anyone else with similar hardware and ubuntu 11.04 64bit.

Rgds

Malc.

---

### Post by lidex on 2011-07-17
That's an invalid number anyway.
 You can use 0, or you can use positive or negative integers: -1, -2, 1, 2 etc. I have no idea where you came up with that -0

---

### Post by robbennett75 on 2011-07-18
> **lidex said:**
> Once again a non-existent model. What is the make/model and/or motherboard info?
It does exist!  I'm sat next to it.  The systemboard is ASUS P5GD1-VM
Rob

---

### Post by selcho on 2011-07-18
Hi lidex,

Thanks for reply.

The options snd-hda-intel model=auto index=-0 was created in the /etc/modprobe.d/alsa-base.conf file during a clean install of 64bit version of ubuntu 11.04 with kernel 2.6.38-8 generic and the sound system was working perfectly with it. After update to kernel 2.6.38-10-generic the sound had disappeared and it took a while to figure out that this was causing the problem in my case.  If as you say model number ALC1200 is unknown to alsa, that probably explains the quirk. Anyway it is working fine now.

Regards,

Malc

---

### Post by lidex on 2011-07-18
> **robbennett75 said:**
> It does exist!  I'm sat next to it.  The systemboard is ASUS P5GD1-VM
Rob

Referencing the model selection in alsa-base.conf.
Yours:
```
snd-hda-intel: model=ALC880
```
ALC880 options from alsa documentation:
```
ALC880
======
  3stack	3-jack in back and a headphone out
  3stack-digout	3-jack in back, a HP out and a SPDIF out
  5stack	5-jack in back, 2-jack in front
  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
  6stack	6-jack in back, 2-jack in front
  6stack-digout	6-jack with a SPDIF out
  w810		3-jack
  z71v		3-jack (HP shared SPDIF)
  asus		3-jack (ASUS Mobo)
  asus-w1v	ASUS W1V
  asus-dig	ASUS with SPDIF out
  asus-dig2	ASUS with SPDIF out (using GPIO2)
  uniwill	3-jack
  fujitsu	Fujitsu Laptops (Pi1536)
  F1734		2-jack
  lg		LG laptop (m1 express dual)
  lg-lw		LG LW20/LW25 laptop
  tcl		TCL S700
  clevo		Clevo laptops (m520G, m665n)
  medion	Medion Rim 2150
  test		for testing/debugging purpose, almost all controls can be
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)
```
I don't see it.

---

### Post by robbennett75 on 2011-07-18
Agree that it doesn't appear to be there.   Would it be "asus" ?

Rob

---

### Post by lidex on 2011-07-18
> **robbennett75 said:**
> Agree that it doesn't appear to be there.   Would it be "asus" ?

Rob

I'd give it a try then 6stack and auto

---

### Post by robbennett75 on 2011-07-19
I've edited /etc/modprobe.d/alsa-base.conf and amended the final line to read

options snd-hda-intel model=asus
and
options snd-hda-intel model=6stack
and
options snd-hda-intel model=auto

each time with a reboot, but my audio output remains 'dummy output'.

Rob

---

### Post by lidex on 2011-07-22
> **robbennett75 said:**
> I've edited /etc/modprobe.d/alsa-base.conf and amended the final line to read

options snd-hda-intel model=asus
and
options snd-hda-intel model=6stack
and
options snd-hda-intel model=auto

each time with a reboot, but my audio output remains 'dummy output'.

Rob

Please post an updated alsa-info.txt

---

### Post by robbennett75 on 2011-07-27
Updated:
[http://www.alsa-project.org/db/?f=cf303eb4603a21336ef65acb10c4bc60786addfb](http://www.alsa-project.org/db/?f=cf303eb4603a21336ef65acb10c4bc60786addfb)

many thanks,
Rob

---

### Post by lkjoel on 2011-07-27
It might only be a pulseaudio problem.
Try Sound Troubleshooting in my signature.

---

### Post by robbennett75 on 2011-07-27
Hi lkjoel,

```

rob@claret:~$ aplay -l
aplay: device_list:240: no soundcards found...

```Where should I go next?

Rob

---

### Post by lkjoel on 2011-07-27
Could you give me the output of:
```
lspci -v | grep "Multimedia"
```

---

### Post by robbennett75 on 2011-07-27
```

rob@claret:~$ lspci -v | grep "Multimedia"
rob@claret:~$ 

```However, I also note that 

```

rob@claret:~$ sudo aplay -l
[sudo] password for rob: 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Rob

---

### Post by lkjoel on 2011-07-27
This looks like a permissions issue.
Type this into a Terminal window:
```
sudo usermod -aG audio `whoami`

```

---

### Post by robbennett75 on 2011-07-27
```

rob@claret:~$ sudo usermod -aG audio `whoami`
rob@claret:~$ 

```

---

### Post by lkjoel on 2011-07-27
> **robbennett75 said:**
> ```

rob@claret:~$ sudo usermod -aG audio `whoami`
rob@claret:~$ 

```
Now reboot your computer

---

### Post by robbennett75 on 2011-07-27
> **lkjoel said:**
> Now reboot your computer

Thank you!  Thank you!  Thank you!  It's worked!  I've got sound again!

cheers,
Rob  :P

---

### Post by lkjoel on 2011-07-27
> **robbennett75 said:**
> Thank you!  Thank you!  Thank you!  It's worked!  I've got sound again!

cheers,
Rob  :P
No problem! Glad that it is fixed now!

---

