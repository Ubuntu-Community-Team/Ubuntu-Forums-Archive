---
title: "No 'enable wireless' option since upgrade to 12.10"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by The_Cougar_Kid on 2012-10-23
I have a DELL Desktop that has been dual boot with VISTA for some years.  I originally installed 9.04, but I have upgraded over the years and recently to 12.10.  I have NEVER had any wireless connection problems on this particular machine - until now!  The machine uses a Broadcom Corporation BCM4318.  I can connect by cable - but this PC is located about 15 metres from the router (it's a VERY LONG but very inconvenient cable!) but I really need to get the wireless connection working again.  On the network menu there is no option to 'enable wireless' so no wireless networks are listed.  If I look at 'edit connections' then the wireless connection is all present and correct.  I have checked in the package manager that all the required networking components are installed.  I have seen reference to trying 'additional drivers' from the 'Settings' options - but I don't get an 'additional drivers' option.  Where next?  Thanks for any help

---

### Post by westie457 on 2012-10-23
What does ```
rfkill list all
``` tell us please

---

### Post by The_Cougar_Kid on 2012-10-23
> **westie457 said:**
> What does ```
rfkill list all
``` tell us please

Nothing at all - it just returned straight to the prompt...

---

### Post by westie457 on 2012-10-23
Not quite what was expected however not a problem as this tells us something.

Which driver are you using. Please post the output of ```
lsmod
```

Thank you

---

### Post by The_Cougar_Kid on 2012-10-24
As requested - thanks for your help

Module                  Size  Used by
dm_crypt               22402  0 
parport_pc             31968  0 
ppdev                  12817  0 
rfcomm                 37276  0 
bnep                   17707  2 
bluetooth             183228  10 rfcomm,bnep
binfmt_misc            17260  1 
coretemp               13168  0 
dcdbas                 14054  0 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
gspca_spca561          14033  0 
gspca_main             27626  1 gspca_spca561
videodev               95841  1 gspca_main
microcode              18209  0 
snd_seq_midi           13132  0 
psmouse                84843  0 
snd_rawmidi            25382  1 snd_seq_midi
serio_raw              13031  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
usblp                  17751  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                16925  0 
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
radeon                820703  3 
floppy                 55444  0 
ttm                    75534  1 radeon
e1000e                174645  0 
drm_kms_helper         45271  1 radeon
drm                   230463  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13197  1 radeon

---

### Post by The_Cougar_Kid on 2012-10-24
Does this help at all?  Under 'network' it only mentions my wired connection.  See the attachment

---

### Post by The_Cougar_Kid on 2012-10-24
sorry - it wouldn't accept the attachment in html format.  This is the salient bit

d:network
                description: Ethernet interface              product: 82562V-2 10/100 Network Connection              vendor: Intel Corporation              physical id: 19
              bus info: pci@0000:00:19.0
              logical name: eth0
              version: 02              serial: 00:1e:c9:71:80:61              size: 100Mbit/s              capacity: 100Mbit/s              width: 32 bits              clock: 33MHz              capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation               configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.1-2


 latency=0 multicast=yes port=twisted pair speed=100Mbit/s              resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)

---

### Post by westie457 on 2012-10-24
At the moment you have no wireless driver installed that I can see.

Please post the output of ```
lspci -vnn
``` 

or ```
lshw -C network
```
Could you put this between [code]
paste here

[ /code] tags. Clicking the # at the top of the message pane will generate the tags for you.

Thank you

---

### Post by The_Cougar_Kid on 2012-10-24
[Code}
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
    Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ff00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at fe00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at fd00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at fb00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at fa00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at f900 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fdffd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdc00000-fdcfffff
    Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801IR (ICH9R) LPC Interface Controller [8086:2916] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 IDE interface [0101]: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] [8086:2920] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f800 [size=8]
    I/O ports at f700 [size=4]
    I/O ports at f600 [size=8]
    I/O ports at f500 [size=4]
    I/O ports at f400 [size=16]
    I/O ports at f300 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: medium devsel, IRQ 11
    Memory at fdffc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] [8086:2926] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Dell Inspiron 530 [1028:020d]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f100 [size=8]
    I/O ports at f000 [size=4]
    I/O ports at ef00 [size=8]
    I/O ports at ee00 [size=4]
    I/O ports at ed00 [size=16]
    I/O ports at ec00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV610 video device [Radeon HD 2400 PRO] [1002:94c3] (prog-if 00 [VGA controller])
    Subsystem: Dell Radeon HD 2400 Pro [1028:0302]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at ce00 [size=256]
    [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

02:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at fdcfe000 (32-bit, non-prefetchable) [size=8K]
    Kernel modules: ssb
[/code]

---

### Post by The_Cougar_Kid on 2012-10-24
```

WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
alaric@UPSTAIRS2U:~$ sudo lshw -C network
[sudo] password for alaric: 
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:71:80:61
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.1-2 ip=192.168.1.82 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:ff00(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0
       resources: memory:fdcfe000-fdcfffff
alaric@UPSTAIRS2U:~$ 

```

---

### Post by westie457 on 2012-10-24
Okay we are getting there. Not sure if you have installed the Broadcom STA Driver. As stated in a previous post I cannot see any drivers listed.

Here is what I would like you to do.

```
sudo apt-get remove bcmwl-kernel-source
```
If the system requires a reboot do not, it can wait a few minutes until we have finished. Warning - in some cases rebooting now can remove the wired capability as well.

Next is ```
sudo apt-get install linux-firmware-nonfree
```
After this has installed wait for about 2 minutes and check if there is any wireless networks available. If none show up then two more terminal commands```
sudo rmmod ssl

sudo modprobe b43
```

any joy now?

Thank you

---

### Post by The_Cougar_Kid on 2012-10-25
Well it took about four minutes rather than 2, but, hey, IT WORKS!!!!  It auto-connected to my own wireless router and also shows other available networks too!

---

### Post by The_Cougar_Kid on 2012-10-25
Thanks very much indeed for your help and all your patience!!!

---

### Post by moroccan92 on 2012-10-25
[The_Cougar_Kid]("http://ubuntuforums.org/member.php?u=930526")
it's woork for you ?? 
please , try to restart your computer , and see if he find always the wireless connection

---

### Post by westie457 on 2012-10-25
@ The_Cougar_Kid

Using 'Thread Tools' near the top of the page could you mark this as 'Solved' please.

@ moroccan92

Could you give more details of the problems you are having please. Either in a  new thread or on this one.

Thank you.

---

### Post by moroccan92 on 2012-10-25
@westie457

[http://ubuntuforums.org/showpost.php?p=12316294&postcount=11](http://ubuntuforums.org/showpost.php?p=12316294&postcount=11)
i try this post from you , and it's work for me 
but when i restart my computer , i don't find my wireless connection 
i don't understand that
this is my thread 
[http://ubuntuforums.org/showthread.php?t=2076079](http://ubuntuforums.org/showthread.php?t=2076079)

---

### Post by The_Cougar_Kid on 2012-10-25
Oh dear - morrocan92 appears to be correct.  When I restarted, the wireless connection did not restart.  But when I tried
sudo modprobe b43it immediately re-appeared again....  So it looks as though I may need to run this command each time I reboot...

---

### Post by wildmanne39 on 2012-10-25
Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by The_Cougar_Kid on 2012-10-26
Thank you.  That really does seem to have solved the problem  After I rebooted the wireless connection connected automatically

---

### Post by kingcobra4545 on 2013-02-25
@westie457 : U are a genius, it did not work for me either , till i executed the below command.The command before this fetched 'no modules installed msg', but after i hit this command , the wifi works like a charm.It actually worked fine when I installed ubuntu 12.10 , I updated the system , it downloaded some 251mb, then it restarted but after tat , wifi is gone.
sudo modprobe b43

---

