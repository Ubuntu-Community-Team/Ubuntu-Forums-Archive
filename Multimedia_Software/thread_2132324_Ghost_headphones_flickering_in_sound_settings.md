---
title: "Ghost headphones flickering in sound settings"
date: 2013-04-04
forum: Multimedia Software
---

### Post by dikkjo on 2013-04-04
Hi everyone,

i'm having the strangest problem, in my sound settings i see "Headphones - Builtin audio" appearing and disappearing continuously.
The problem is that the flickering is not only visual, but it mute anything i'm playing for a split second every one second.

I have absolutely no headphones connected, not even via bluetooth. The only way i've found to make it stop is actually connecting headphones!

I can't understand if i'm having an hardware problem, or if it's something wrong in my config.
I have an Intel HDA from Realtek and i've recently switched to 2.0 speaker , instead of the 2.1 i had before. 
If i check alsamixer during the flickering, I see that the channels for 5.1 are being muted/unmuted, despite my mode being set to "Analog stereo output".

I think i can live with the headphones always connected, but i'd like to know why ;)
Has anyone encountered this kind of issues?

Cheers

---

### Post by gordintoronto on 2013-04-04
Sounds like a hardware problem, within the headphone jack. Wouldn't hurt to describe your computer.

---

### Post by Assasin_Asha on 2013-10-10
I know this thread is several months old, but I encountered the exact same issue and I have a somewhat workaround. I decided to post it here, because this happened to be the first and one of the only posts in Google search results.
Basically, it seems that certain... I think it's volume, but it might be tones as well... prompt the momentary activation of Built-in Headphones or something on those Realtek integrated sound cards, which mutes the volume for an instant.
It seems that lowering the overall system volume down, at the least tones down the flickering by a significant amount. This of course requires sound system with decent volume boost, but it is a way of dealing with that flickering. I lowered my own to about 30% and I don't experience this anymore... for now...
Hope this helps anyone out there!

---

### Post by TQLeaman on 2013-11-01
I can confirm the same problem after upgrading to 13:10 and running Ubuntu Gnome version.

On the top bar the speaker icon every few seconds changes to the headphone icon and back again. Inserting headphones switches the icon properly and the problem goes away until to remove the headphones. The effect on sound output for me is either a momentary "drop out" of sound or a momentary increase in output volume. This is NOT a hardware problem, as the machine was not exhibiting this on either the vanilla and Gnome versions of Ubuntu 12.04.

I read mention of this being a "Realtek" problem. (HardInfo reports my audio as an Intel 82801Ji Audio Controller but the board is a Gigabyte X58-USB3, which on their spec site mentions a Realtek ALC892 in the audio section).

I have included the Machine Spec (from HardInfo) below including the PCI devices which hopefully provides somebody somewhere with some insight. Interestingly, HardInfo suggests that I have two audio controllers but that is not the case, it is an NVidia GTX 460 graphics card, which has no physical audio outputs presented and is therefore probably a red herring but I mention it just in case.

Using the mixer I can see two Output entries:
Digital Output (S/PDIF) - Built in Audio
Analogue Output - Built in Audio

I am using the Analogue Output. Turning the Digital output off / on makes no difference to the problem.

If anyone wants to dig some more and requires further info, testing then just let me know.

All the best,

TQ

---

- Computer -
Processor: 8x Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
Memory: 24689MB (1461MB used)
Operating System: Ubuntu 13.10
Date/Time: Fri 01 Nov 2013 11:10:39 GMT

-Display-
Resolution: 3840x1080 pixels
OpenGL Renderer: Unknown
X11 Vendor: The X.Org Foundation

-Multimedia-
Audio Adapter: HDA-Intel - HDA Intel
Audio Adapter: HDA-Intel - HDA NVidia

-Input Devices-
 Power Button
 Power Button
 Logitech HID compliant keyboard
 Logitech HID compliant keyboard
 Logitech USB Receiver
 Logitech USB Receiver
 HDA Intel Front Headphone
 HDA Intel Line Out Side
 HDA Intel Line Out CLFE
 HDA Intel Line Out Surround
 HDA Intel Line Out Front
 HDA Intel Line
 HDA Intel Rear Mic
 HDA Intel Front Mic
 HDA NVidia HDMI/DP,pcm: 9=
 HDA NVidia HDMI/DP,pcm: 8=
 HDA NVidia HDMI/DP,pcm: 7=
 HDA NVidia HDMI/DP,pcm: 3=

-SCSI Disks-
ATA OCZ-AGILITY3
Optiarc DVD RW AD-7260S
WD 15EADS External
ATA ST2000DM001-9YN1
ATA ST2000DM001-9YN1
ATA ST2000DM001-9YN1
ATA ST2000DM001-9YN1
HitachiG ST
HitachiG ST

-PCI Devices-
Host bridge		: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
PCI bridge		: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13) (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13) (prog-if 00 [Normal decode])
PIC		: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13) (prog-if 20 [IO(X)-APIC])
PIC		: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13) (prog-if 00 [8259])
PIC		: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers (rev 13) (prog-if 20 [IO(X)-APIC])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
Audio device		: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
PCI bridge		: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
PCI bridge		: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 (prog-if 00 [Normal decode])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
USB controller		: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
PCI bridge		: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
ISA bridge		: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
RAID bus controller		: Intel Corporation 82801 SATA Controller [RAID mode]
SMBus		: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
USB controller		: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
VGA compatible controller		: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1) (prog-if 00 [VGA controller])
Audio device		: NVIDIA Corporation GF104 High Definition Audio Controller (rev a1)
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
Host bridge		: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
Host bridge		: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

---

---

### Post by cancerkid09 on 2013-11-09
I believe this has something to do with the non open source nvidia drivers, are you using 319? 
I to am having this exact issue, I didnt have this problem before enabling nvidia 319 driver. I had scratchy audio due to it switching constantly between headphones and speakers. I fixed this with > sudo alsa force-reload now i only get the flashing strobe light of an icon in shell. 
I tried switching back to the open source driver but it has not fixed my problem. "Headphones - Built-in Audio" still flashes on every high note as if to a certain frequecy.
I can to confirm this is not a hardware problem, my guess would be a nvidia kernel module that is conflicting with HDA.

Specs: 
Intel Core 2 Quad Q8300 (LGA 775)
Intel DG41BI motherboard
Intel HDA
Geforce 210 (running 304)

PCI Devices:
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Audio
Audio Adapter: HDA-Intel - HDA Intel
Audio Adapter: HDA-Intel - HDA NVidia

---

### Post by TQLeaman on 2013-11-26
Sorry guys, I feel terribly rude for not responding sooner but I just realised I missed replying to this one.

Yes I am using the 319-updates version.

Since the flickering on the tray was just as annoying as the sound, I ended up plugging my speakers into the headphone socket, which at least makes the problem go away and my speakers, in turn provide a separate headphone jack.

I guess we will be waiting for a fix...

TQ

---

### Post by Purri on 2014-01-16
> **TQLeaman said:**
> Sorry guys, I feel terribly rude for not  responding sooner but I just realised I missed replying to this one.

Yes I am using the 319-updates version.

Since the flickering on the tray was just as annoying as the sound, I  ended up plugging my speakers into the headphone socket, which at least  makes the problem go away and my speakers, in turn provide a separate  headphone jack.

I guess we will be waiting for a fix...

TQ

I also have the same issue, while using a nvidia 319 driver.
I have a similar solution to TQLeaman's.
 I found that using my c/sub jack instead of line out -jack reduces the sound flickering greatly while using speakers.

---

### Post by colin13 on 2014-01-18
I also have the same issue, i have realtek and nvidia.  Has anyone found a solution?  This is very hard to find anything about.

---

### Post by NrNice on 2014-01-26
Hi,

I have the same issue:
In "Volume control", "Input device", when I choose "Line In", it change back after 2-3 s to "Front Microphone".
When I play audio I have gliches every seconds

Spec
Motherboard 970 Extreme4
vendor: ASRock
AMD FX8120 Eight-Core Processor
NVIDIA GF119 [GeForce GT 520] driver nvidia-319 ver 319.32-0ubuntu7 (recommended)
Audio device SBx00 Azalia (Intel HDA) 

I need to use Line input and have a good quality sound.

Did you find a fix.

---

### Post by Alkin_Nasuf on 2014-03-26
Hi,

I am experiencing the same issue with Gigabyte H87N-WIFI and i5 4670. Graphics is Radeon HD 5750 with open-source drivers. Ended up using c/sub jack instead as suggested. I believe it is a driver issue -- same audio chip. How we can report this as a bug? I mean what information needs collecting?

Cheers

---

### Post by nicolai.kraus on 2014-09-06
I have solved this issue by just plugging in another cable (not connected to headphone or speaker) into the headphone plug. Works perfectly for me! I also have the Gigabyte H87N-WIFI as the poster above.

---

### Post by xv1700 on 2014-11-04
Same problem here. I tried Nicolai's headphone jack trick and it's fixed it for me ... except I have to plug it in and then remove it again or I can't get any sound out at all, it's like they are somehow the same device.

---

### Post by green69 on 2014-11-10
Same problem here using NVIDIA driver version 331.38.

Fortunately the extra-jack plugin solution seems to work.

Cheers

---

