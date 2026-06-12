---
title: "Audio hardware detected but no sound?? Hardy, 2.6 2.6.24-19-generic"
date: 2008-06-29
forum: Multimedia Software
---

### Post by darkblane on 2008-06-29
Hello everyone, this is my first post so be kind ;)

I have just installed Hardy on an Asus X53s laptop (mb ver F3SR) and everything has installed perfectly, really happy except no audio :(

The audio hardware is detected, 'alsamixer' shows the hardware as Realtek ALC660-VD.

Below is the terminal output for 'aplay -l' and 'lspci'.
No matter how many different combinations of vol control prefs I choose or altering the devices in 'sound preferences' I get no sound. nothing.
Movies and mp3 play without error, just no audio.

Any ideas? I'm completely stumped and desperate to get rid of Vista of this machine but can't live without audio. All suggestions and advice will be greatly appreciated.

rgds, Karl.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
darkblane@darkblane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by lukjad on 2008-06-29
On thing that came to mind was something similar happened to me. Go check what type of kernel you have. I had both the generic kernel installed and a server kernel and I couldn't get the sound to work at all. When I figured it out I just deleted that kernel (in Synaptic) and the generic kernel took over. Sound was back. This may not be your problem and PLEASE don't try uninstalling a kernel without guidance or a lot of research.
Hope this helps.

---

### Post by lukjad on 2008-06-29
Also try unplugging and replugging everything, sometimes that works. Also remember that Hardy seems to have difficulty playing movies and movie clips. This could just be another manifestation of it. If you can, download TEENpup and burn the ISO to a CD. Then go ahead and do a full shutdown. When you boot up your PC next boot off that CD and try to play some music or a movie. If it works we'll know that it is a software problem and not a hardware problem. (BTW I only suggested TEENpup because I know it and use it a lot.)

---

### Post by darkblane on 2008-06-30
Hi lukjad007, thanks for the reply and the suggestions.

The machine is a laptop and audio is working perfectly in Vista/XP so I know this is a software issue. The server kernel sources were not installed so I'm no closer to finding the cause at the moment.
I suspect I'll have to wait until the next kernel release to have another crack at getting audio working :(

Once again, thanks for your suggestions and time.

Regards,

Karl.

---

### Post by lukjad on 2008-06-30
You're welcome. If I think of anything I'll PM you and post it on this thread.

---

### Post by markbuntu on 2008-06-30
Can you play anything in rythmbox?
cd?
Internet radio?

If not, try this, go to System/Preferences/Sound and change the settings from autodetect to alsa. Also, right click on the little speaker in your panel and open the volume control. In the top it will say:

Volume Control: something something

What does it say?

---

### Post by darkblane on 2008-07-01
In "Sound Preferences" I have the following options:

For 'Sound Events', 'Music and Movies' and 'Audio Conferencing'

Autodetect
Si3054 Modem
ALC861VD Analog
AlSA - Advanced Linux Sound Architecture
OOS - Open Sound System
PulseAudio Sound Server

For 'Audio Conferencing > Sound capture' I have;

Si3054 Modem
ALC861VD Analog
AlSA - Advanced Linux Sound Architecture
OOS - Open Sound System
PulseAudio Sound Server
Test Sound
Silence

For 'Default Mixer Tracks' under 'Device' I have

HDA Intel (ALSA mixer) > Mixer,PCM,Front,Front Mic,Front Mic Boost,Line-In,CD,Microphone,Mic Boost,PC Speaker,Capture,Digital
Realtek ALC660-VD (OOS Mixer) > Volume,Speaker,Line-in,Microphone,CD,PCM-2,In-gain
Playback: ALSA PCM on Front:0 (ALC681VD Analog) via DMA (PulseAudio Mixer) > Master
Capture: Monitor Source of ALSA PCM on front:0 (ALC681VD Analog) via DMA (PulseAudio Mixer) > Master
Capture: ALSA PCM on front:0 (ALC681VD Analog) via DMA (PulseAudio Mixer) > Master

The volume conrol preferences give me the options to select any of the above Default Mixer Track's Devices and outputs/inputs.

Every combination of each I have tried results in no sound whatsoever. All applications appear to be playing sound, it just can't be heard.

I really can't understand what's going wrong here :(
The laptop is;

Asus X53Sseries
DUO T5450
15.4" WXGA
HD-DVD
802.11a/b/g
160GB HD
2B RAM
ATI Mobility Radeon HD 24000 ; VRAM:128MB

Any ideas?????

```
darkblane@darkblane-laptop:~$ sudo lshw -C multimedia
[sudo] password for darkblane: 
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

```
darkblane@darkblane-laptop:~$ sudo lshw -C multimedia
[sudo] password for darkblane: 
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

```
darkblane@darkblane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
darkblane@darkblane-laptop:~$ 
```

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                                                                                          &#9474;
&#9474; Chip: Realtek ALC660-VD                                                                                                                  &#9474;
&#9474; View: [Playback] Capture  All                                                                                                            &#9474;
&#9474; Item: Master [dB gain=-31.00]                                                                                                            &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;                &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;  &#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;                          &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;      &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;      &#9500;&#9472;&#9472;&#9508;       &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;OO&#9474;      &#9474;MM&#9474;                 &#9474;OO&#9474;      &#9474;MM&#9474;                &#9474;MM&#9474;       &#9474;OO&#9474;      &#9474;MM&#9474;                 &#9474;OO&#9474;      &#9474;MM&#9474;      &#9474;MM&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                 &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                 &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;      52                57<>57     73<>75     0<>0      0<>0     55<>55     74<>74     0<>0      0<>0      74<>74                         &#9474;
&#9474;  < Master > Headphon    PCM       Front    Front Mi  Front Mi    Line        CD       Mic     Mic Boos   PC Speak  Caller I  Off-hook    &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9474;                                                                                                                                          &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```

---

### Post by markbuntu on 2008-07-01
Somewhere in these forums there is a thread about adding a line in modules or something to get intel sound to work on certain laptops but it appear that you may have that module loaded already. Anyway it would not hurt to hunt one of those down and check it out.

By appears to be playing does that mean you can see the bars move in the Pulse Audio Volume Meter?

---

### Post by darkblane on 2008-07-03
Hi markbuntu, I finally solved it 10 minutes ago. I found this thread, [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959) and followed the guidelines there.
I edited /etc/modprode.d/asla-base and told it the model of laptop was a "lenovo" (this had worked for a few others) and on reboot it was all working. Well pleased. Now I'm going to try and get my Amd64 working on Ubuntu with an e-mu0404 next, it's going to take more work than this did but I'm sure I'll get it working.

Thanks for your help and suggestions and also to everyone who's contributed across many similar threads that led me to having working audio. Much appreciated.

Karl ;)

---

