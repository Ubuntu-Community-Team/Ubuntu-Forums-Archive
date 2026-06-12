---
title: "Aironet 350 not being recognized"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by thesupremeg33k on 2006-06-03
I inherited an older Thinkpad from work (Thinkpad 600E) and am trying to get my Aironet 350 working under Dapper.  I did the server install and used a script (its been a long day, cant remember the name) to install Xfce as the window manager.  Everything is working fine except I can't get it to detect my card -- it doesn't show up at all in an ifconfig -a.  I noticed this before -- with a 2.4.x kernel it would show the card (but not get an IP via DHCP) so I upgraded to a 2.6 kernel (figured it may help) and it stopped showing up.

Anybody have any suggestions?  I'm at a bit of a loss as to how to proceed.

---

### Post by Skye on 2006-06-03
Is the computer seeing it at all?  Run ```
lsmod
``` and see if you can find an entry for the card.

EDIT: Edited for stupid grammar mistakes.

---

### Post by thesupremeg33k on 2006-06-05
```
Module                  Size  Used by
nvram                  10760  1 
uinput                 10496  1 
apm                    23408  1 
ppdev                  10628  0 
cpufreq_userspace       7328  0 
cpufreq_stats           7488  0 
freq_table              5792  1 cpufreq_stats
cpufreq_powersave       2816  0 
cpufreq_ondemand        8616  0 
cpufreq_conservative     9960  0 
ipv6                  287584  20 
dm_mod                 63512  1 
md_mod                 76756  0 
af_packet              25864  2 
lp                     13220  0 
tsdev                   8896  0 
8139too                29696  0 
mii                     7040  1 8139too
pcmcia                 42556  0 
irtty_sir              10240  0 
sir_dev                21692  1 irtty_sir
nsc_ircc               25920  0 
parport_pc             38724  1 
irda                  219196  3 irtty_sir,sir_dev,nsc_ircc
analog                 13728  0 
crc_ccitt               3200  1 irda
ns558                   6660  0 
parport                39624  3 ppdev,lp,parport_pc
floppy                 65252  0 
i2c_piix4              10000  0 
i2c_core               23296  1 i2c_piix4
pcspkr                  3204  0 
snd_cs46xx             91336  0 
gameport               17160  4 analog,ns558,snd_cs46xx
snd_rawmidi            27296  1 snd_cs46xx
snd_seq_device         10124  1 snd_rawmidi
snd_ac97_codec        100512  1 snd_cs46xx
snd_ac97_bus            3328  1 snd_ac97_codec
snd_pcm_oss            56992  0 
snd_mixer_oss          21248  1 snd_pcm_oss
snd_pcm                96516  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27140  1 snd_pcm
psmouse                40836  0 
serio_raw               8580  0 
snd                    59748  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         12296  2 snd_cs46xx,snd_pcm
intel_agp              25628  1 
agpgart                37580  1 intel_agp
yenta_socket           30988  3 
rsrc_nonstatic         15488  1 yenta_socket
pcmcia_core            45332  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 50144  0 
pci_hotplug            30652  1 shpchp
evdev                  11136  2 
ext3                  147848  1 
jbd                    62996  1 ext3
ide_generic             2432  0 
uhci_hcd               35984  0 
usbcore               137732  2 uhci_hcd
ide_cd                 36740  0 
cdrom                  42272  1 ide_cd
ide_disk               19968  3 
piix                   12420  1 
generic                 5892  0 
processor              27080  0 
capability              5896  0 
commoncap               8192  1 capability
vga16fb                14856  1 
vgastate               11136  1 vga16fb
fbcon                  44448  71 
tileblit                3712  1 fbcon
font                    9216  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3200  1 bitblit
```

---

### Post by Skye on 2006-06-05
I'm sorry, I was half asleep when I wrote that.  The command you should run is ```
lspci -v
```

---

### Post by thesupremeg33k on 2006-06-05
lspci -v gives me...

```

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at 40000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 1.0

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 168
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=176
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: 70000000-dfffffff
	Prefetchable memory behind bridge: e0000000-f7ffffff

0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
	Subsystem: IBM: Unknown device 00eb
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50102000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-11fff000 (prefetchable)
	Memory window 1: 12000000-13fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
	Subsystem: IBM: Unknown device 00eb
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at 50101000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 14000000-15fff000 (prefetchable)
	Memory window 1: 16000000-17fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
	Subsystem: IBM CS4610 SoundFusion Audio Accelerator
	Flags: medium devsel, IRQ 11
	Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
	Memory at 50000000 (32-bit, non-prefetchable) [size=1M]

0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 48
	I/O ports at fcf0 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 48, IRQ 11
	I/O ports at 8400 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
	Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20) (prog-if 00 [VGA])
	Subsystem: IBM ThinkPad 570
	Flags: bus master, medium devsel, latency 128, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=16M]
	Memory at 70000000 (32-bit, non-prefetchable) [size=4M]
	Memory at 70400000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [dc] Power Management version 1

0000:02:00.0 Ethernet controller: D-Link System Inc DFE-690TXD CardBus PC Card (rev 10)
	Subsystem: D-Link System Inc: Unknown device 1395
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1000 [size=256]
	Memory at 12000000 (32-bit, non-prefetchable) [size=512]
	Capabilities: [50] Power Management version 2



```

---

### Post by Skye on 2006-06-05
Hrm.  According to that output, there's no aironet card in your computer, but there is a wired D-Link PCMCIA card.  Was the Aironet card in the computer when you ran that command, or were you using a D-Link PCMCIA wired ethernet card for internet?

If the wireless card WAS plugged in, your laptop isn't recognizing that it's there, which is probably why you can't get it to work.

So, if that was lspci -v without the wireless card in, plug it in, get the output, and paste it in here.  

Also, in either case, return the output of ```
cardctl ident
```

---

### Post by thesupremeg33k on 2006-06-05
The AIronet was most definately in when I was running that.  I also have a wired card (interesting how the Best Buy card shows up as a D-Link...I wonder..;) ) in there.  Anyways, here's what cardctl ident shows...

```

Socket 0:
  product info: "BestBuy", "DX-E201"
  manfid: 0x0000, 0x024c
  function: 6 (network)
Socket 1:
  no product info available


```

The D-Link card is in socket 0 and if I switch positions, the computer reports the updated assignments correctly (so its not a bad slot).

---

### Post by Skye on 2006-06-05
That's very interesting-  the computer isn't seeing the Aironet card at all.  This brings up the question, do you know for a fact that the card itself works?

Assuming that you do, there's only one other thing I can think of to get this working, because I had to do it with my computer to get my PCMCIA bus working.

First things first- lets make a backup of your grub menu.lst, considering that it's important and we'll be editing it.
```
sudo cp /boot/grub/menu.lst ~/Desktop
```
This copies your current settings to your Desktop so that if something breaks, you'll be able to fix it.
Next thing we're going to do is open up the original file for editing:
```
sudo gedit /boot/grub/menu.lst
```
Once that's open, look for the part that says something like this (what it says for you may be slightly different):
[quote=file]## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5[/quote]
On the very next line, there's something that says **#defoptions=**. At the end of that line, add a space, and then the command **pci=assign-busses**. So, when all is said and done, your line should look something (but not necessarily exactly) like this:

**# defoptions=quiet splash pci=assign-busses**

Finally, update grub so that it sees the new settings:
```
sudo update-grub
```

Reboot, and see if the card works now.

NOTE: Should this break your working wired ethernet card with no gain to your wireless card, all you need to do to undo it is reverse the commands above:
```
sudo cp ~/Desktop/menu.lst /boot/grub
sudo update-grub
``` and then reboot, and things should be back to as they were.  Good Luck!

---

### Post by thesupremeg33k on 2006-06-05
No luck with that :(  Anybody else have ideas?

The card does work in other laptops (Windows) and worked with 2.4.x kernels

---

