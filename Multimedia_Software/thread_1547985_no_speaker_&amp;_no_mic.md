---
title: "no speaker &amp; no mic"
date: 2010-08-07
forum: Multimedia Software
---

### Post by ohme on 2010-08-07
headphones do produce sound, however.
I have this problem since ever (all the way from 32b ubuntu 6 up to my 64b Lucid Lynx 10.04, kernel 2.6.32-24). I use a lg laptop, model p1, encoder is alc883, soundcard intel-hda, 5.1ch... 

fixed the user groups, set everything on alsamixer to be reasonable (Master - max, headphones-on, speaker -max, pcm - max, front - max, front mic - max, front mic boost- min, line-max, mic-max, mic-boost-min, spdif -on, spdif def. pcm - on, beep - max,caller id-max, off-hook - max), connector in the volume tool set to analog speaker, I tried many of the models in alsa-base.conf's last line (options snd-hda-intel=...). if I had an easy option to brute-force (without having to restart), I would have tried them all.

ideas anyone?

---

### Post by zimac on 2010-08-09
i fixed my no mic problem by installing "linux-backports-modules-alsa-lucid-generic"

---

### Post by ohme on 2010-08-10
thanks. no change, though.

---

### Post by bilkay on 2010-08-10
Having the same problem: Sound over headphones but not speakers.

Here's the relevant output from lspci -v:

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 1484
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```From alsamixer:

```
 Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Intel G45 DEVCTG                               F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -0.75, -0.75]                 Esc: Exit               &#9474;
&#9474;

```The CREATIVE webcam microphone works if selected from panel "Sound preferences," but the internal mic doesn't work at all.

---

### Post by ohme on 2010-09-02
bump

---

### Post by lidex on 2010-09-03
> **ohme said:**
> bump

Can you remove alsa-backports, reboot, and run this command please.
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by ohme on 2010-09-04
thanks for answering!
here's the link:
[http://www.alsa-project.org/db/?f=23194ed96539ecd2222b527be1711d52ab480fbe](http://www.alsa-project.org/db/?f=23194ed96539ecd2222b527be1711d52ab480fbe)

---

### Post by lidex on 2010-09-05
Whatever it is that you added to alsa-base.conf, please remove it and reboot. Now post the output of these commands:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by ohme on 2010-09-05
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: RKYWSF27
	Release Date: 01/25/2007
	Address: 0xE4AF0
	Runtime Size: 111888 bytes
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported


# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: LG Electronics
	Product Name: ROCKY
	Version: Not Applicable
	Serial Number: Not Applicable

Handle 0x0008, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Disabled
	Description: HD-Audio

---

### Post by lidex on 2010-09-05
If you are able to update your bios, please do so.
Also post an updated alsa-info text.

---

### Post by ohme on 2010-09-05
unfortunately LG doesn't publish official updates for my bios, and did not reply to a few requests by me over the years. there is some unofficial stuff over the net, but I'm not sure it is a good idea to use it.

anyway, the new alsa-info is in:
[http://www.alsa-project.org/db/?f=2937d92c762b81a53599baba5aba162ad1b89435](http://www.alsa-project.org/db/?f=2937d92c762b81a53599baba5aba162ad1b89435)


thanks again.

---

### Post by lidex on 2010-09-05
Gotcha.
Go into your bios setup and make sure your onboard HD audio is enabled:
> Type: Sound
Status: Disabled
Description: HD-Audio 
Following step is an alsa upgrade. Use the link in my sig

---

### Post by ohme on 2010-09-05
no such option (or anything that seems relevant) in the bios. but I don't think that this is really the point, since the sound card does work - only the speakers and the mic fail.

---

### Post by lidex on 2010-09-06
Did you try the alsa upgrade?

---

### Post by ohme on 2010-09-06
yes. didn't change anything.

---

### Post by lidex on 2010-09-06
What are the onboard options in bios?

---

### Post by ohme on 2010-09-07
Hi,
As I said, no relevant entry in the bios. here's my entire bios menu:

Main:
    System time & date ...
    Pri. Master       [cd-rom]
    Sec. Master       [120GB SATA]
Advanced:
    Legacy USB support [enabled]
    Boot time diagnostic screen [enabled]
    Core multi-processing [enabled]
    virtualization technology [enabled]
    SATA controller mode [enabled]
        AHCI configuration [enabled]
    CPU deeper sleep [supported]
    Battery charge stop percentage [standard]
    Battery fast charge [disabled]
    fan mode control [on]
         Silent mode in AC [normal]
         Silent mode in DC [normal]
    Fn key setup [5 sec.]
    Wake on lan [disabled]
    PXE/Remote boot OPROM [disabled]
    PCIE device wake up [enabled]
    SIO control:
         Serial port A: [auto]
         Parallel port [enabled]
         mode [ECP]
         Base I/O address [378]
         Interrupt [IRQ 5]
         DMA channel [DMA 1]
Security:
    some password options....
Boot:
    Boot priority order...
Exit:
    Exit with/without save, load defaults....

---

### Post by ohme on 2011-08-06
bump

---

