---
title: "alsamixer (headphone)"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by jwalters on 2008-04-15
using the new Heron........no volume from headphones........checked alsamixer and although it shows the square sitting to the right of 'master' there is no way to control the volume up or down....??

master seems to work fine as do all the others........headphones shows green (not off)

I reinstalled alsa to no avail as it is the same as before...........??

---

### Post by gleble on 2008-04-15
Have a look at this
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) 
If that's not how you reinstalled Alsa then try it. My headphone jack was knackered. It did wonders

---

### Post by warp99 on 2008-04-15
> **jwalters said:**
> using the new Heron........no volume from headphones........checked alsamixer and although it shows the square sitting to the right of 'master' there is no way to control the volume up or down....??

master seems to work fine as do all the others........headphones shows green (not off)

I reinstalled alsa to no avail as it is the same as before...........??

It may be your sound card or module has a "quirk" and needs adjustment. Some of the specifications for sound cards are not followed by the manufactures so a little tweak is needed. So do the following

```
lspci -v
```
and
```
lsmod |grep snd
```
and post the results. On the 'lspci -v' command you only have to post the results for the multimedia controller that's listed. If your not sure just post the entire output of 'lspci -v'.

---

### Post by jwalters on 2008-04-15
the second part of your code I couldn't get to open....duuuh just what exactly is the character followed by grep? I tried L...I tried I.....grep to no avail......

I also believe the problem I have is affecting the whole sound system as well as the headphones....thanks

---

### Post by warp99 on 2008-04-15
> **jwalters said:**
> the second part of your code I couldn't get to open....duuuh just what exactly is the character followed by grep? I tried L...I tried I.....grep to no avail......

I also believe the problem I have is affecting the whole sound system as well as the headphones....thanks

Well then do the following:
```
sudo apt-get install grep
```
then run the command again. Your output should look like this:
```
lsmod |grep snd
snd_hda_intel          14424  0
snd_hda_codec         191776  1 snd_hda_intel
snd_pcm                52936  2 snd_hda_intel,snd_hda_codec
snd_timer              15300  1 snd_pcm
snd                    32964  4 snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
soundcore               3744  1 snd
snd_page_alloc          6472  2 snd_hda_intel,snd_pcm

```
but may be different for your soundcard.

---

### Post by jwalters on 2008-04-15
I can't run the code till I can understand what the character is before the GREB.......what is it?

It looks like an I , but it extends a bit farther and when I try  Igreb

it returns one word.....lsmod........that's it. ??

---

### Post by warp99 on 2008-04-15
> **jwalters said:**
> I can't run the code till I can understand what the character is before the GREB.......what is it?

It looks like an I , but it extends a bit farther and when I try  Igreb

it returns one word.....lsmod........that's it. ??
That's the pipe character. Look at the key just above your enter button. It's the character above the backslash.

---

### Post by jwalters on 2008-04-15
jwalters@jwalters-desktop:~$ sudo lspci -v
[sudo] password for jwalters: 
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [dc] HyperTransport: MSI Mapping

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Dell Unknown device 020e
	Flags: 66MHz, fast devsel, IRQ 7
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Dell Unknown device 020e
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: fde00000-fdefffff
	Capabilities: [b8] Subsystem: Dell Unknown device 020e
	Capabilities: [8c] HyperTransport: MSI Mapping

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f028:020e
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 221
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/3 Enable+
	Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Capabilities: [40] Subsystem: Dell Unknown device 020e
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Capabilities: [40] Subsystem: Dell Unknown device 020e
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] #0f [0010]

01:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem
	Subsystem: Conexant Unknown device 200f
	Flags: bus master, medium devsel, latency 32, IRQ 7
	Memory at fd9f0000 (32-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=8]
	Capabilities: [40] Power Management version 2

jwalters@jwalters-desktop:~$ sudo lsmod |grep snd
snd_hda_intel         344600  2 
Here it is ...thank you. On my keyboard the line above the slash is broken in the middle. I would never had found it on my own :-) 

snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

---

### Post by warp99 on 2008-04-15
Now we're getting somewhere. I need one more piece of information, the chipset. So run 'alsamixer' at the prompt and just below 'Card:' in the right hand corner it says 'Chip:' What chipset does it say?

BTW this seems to be a problem since there is another thread with the same sound card and the same problem of no sound:

[http://ubuntuforums.org/showthread.php?t=755338](http://ubuntuforums.org/showthread.php?t=755338)

I'm also trying to help this person, so your not alone on this one.

---

### Post by jwalters on 2008-04-15
chip..........Realtek ALC 888.............

---

### Post by warp99 on 2008-04-16
The reason that you microphone may not be working is that ALSA could be using a minimal configuration, therefore not including the microphone input:

[http://hg.alsa-project.org/alsa-kernel/raw-file/5082de4abb26/Documentation/ALSA-Configuration.txt](http://hg.alsa-project.org/alsa-kernel/raw-file/5082de4abb26/Documentation/ALSA-Configuration.txt)

> (except)

Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)
    power_save	- Automatic power-saving timtout (in second, 0 =
		disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
		(default = on)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

The list of models for the ACL888 is as follows:
> 

	  Model name	Description
	  ----------    -----------

         ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  acer-aspire	Acer Aspire 9810
	  medion	Medion Laptops
	  medion-md2	Medion MD2
	  targa-dig	Targa/MSI
	  targa-2ch-dig	Targs/MSI with 2-channel
	  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
	  lenovo-101e	Lenovo 101E
	  lenovo-nb0763	Lenovo NB0763
	  lenovo-ms7195-dig Lenovo MS7195
	  haier-w66	Haier W66
	  6stack-hp	HP machines with 6stack (Nettle boards)
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  auto		auto-config reading BIOS (default)

So you would need to add the model to your options list like this:

First open the options file for editing:
```
sudo gedit /etc/modprobe.d/options
```

then add to the bottom of the file an option to choose the model you have. Let's give an example:

I have a motherboard with 6 jack and an SPDIF port. Looking at the list I see the model '6stack-dig' is what I'm looking for, so I add this line to the file:

```
options snd-hda-intel index=0 model=6stack-dig
```

I save the file then issue a 'sudo reboot'. 

Your model may be different, so replace '6stack-dig' with the one you have. If something happens just change the model or remove the line from the options file completely to reverse any changes.

---

### Post by Yellow Pasque on 2008-04-16
Try these scripts to build ALSA 1.0.16 in addition to configuring alsa-base:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by jwalters on 2008-04-20
nothing seemed to work for me so I reinstalled heron..........applied the extra codecs etc. and now everything works fine............love Heron..........thanks guys!

---

