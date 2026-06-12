---
title: "Sabertooth 990FX Sound Problems in Ubuntu"
date: 2013-02-19
forum: Multimedia Software
---

### Post by Alvinator9000 on 2013-02-19
I have an issue where sound will not play through the onboard audio ports in the motherboard from Ubuntu.

Config:
Asus Sabertooth 990FX (Rev 1.0)
Logitech wireless headphones (H800) running perfectly fine through USB interface.
Sound system is plugged into the motherboard front speaker output.
I had Win7 installed for quite some time and audio worked fine until near the end (so it may just be that the board is croaked) and so I switched to UbuntuStudio.
I am running UbuntuStudio 12.10 on it.  I cannot recall if I ever had sound out the motherboard on Ubuntu.

Sounds work perfect through the headphones (but obvs not when I route the sound to the onboard using the PulseAudio Volume Control)

Also I should mention I have two ATI graphics cards each with HDMI on them which I don't use the HDMI stuff on them (and have no way of testing HDMI either).


I have tried multiple troubleshooting tutorials, (namely the two mentioned on the op of this thread: [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240) ) to no avail.


I will try and see if I can run sounds through a live USB and see if that will do anything, and then I'll get back to you.

In the meantime though if there's any specific info you want me to run, please ask for it, thanks

---

### Post by Alvinator9000 on 2013-02-19
Reserved, for answer :)

---

### Post by Alvinator9000 on 2013-02-19
Okay so it doesn't work in the Live USB, I tried first WITH the logitech also plugged in, then without, so it doesn't work either way unfortunately

---

### Post by gordintoronto on 2013-02-19
> **Alvinator9000 said:**
> Sounds work perfect through the headphones (but obvs not when I route the sound to the onboard using the PulseAudio Volume Control) ...


I don't understand what you are trying to say. Does sound work at all?

---

### Post by Alvinator9000 on 2013-02-19
> **gordintoronto said:**
> I don't understand what you are trying to say. Does sound work at all?

It works through the headphones, but only whence I route it to the headphones, (like it should), problem is when I route it to my onboard sound card nothing happens at all.  Like in PulseAudio Volume Control I can see the blue bar dancing like music is supposedly going out but its not, and any tests seem to come up alright but with no sound whatsoever.  

Sound works in Windows through the onboard and through the headphones.
Sound does NOT work in Ubuntu-Studio 12.10 through the onboard but works on the headphones.  I'm wondering if its a chipset driver I am missing from the kernel (I'm only a month-old Ubuntu convert) as this board is pretty new still.

Thanks again for any help in advance!!!

PS I won't be home until Thursday afternoon so I'm sorry in advance for my apparent absence regarding the matter in question, please be patient with me.):P

---

### Post by Yellow Pasque on 2013-02-20
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by gordintoronto on 2013-02-20
Here's why I'm confused: headphones are not an alternative to the onboard sound device. I assume you could plug the headphones into the green jack at the back of the computer and hear sound, if you selected the right settings in Sound Settings. I assume you could plug the headphones into the headphone jack on the front of the computer, if your settings are correct and the motherboard was properly installed in the case.

Do you have some other sound device? What do you see in Sound Settings? (I don't use Studio, so I'm not sure what tabs are available: perhaps "hardware," "input" and "output.")

Wouldn't hurt to copy/paste the output from two terminal commands:
lspci
lsusb

---

### Post by Yellow Pasque on 2013-02-20
> **gordintoronto said:**
> Here's why I'm confused: headphones are not an alternative to the onboard sound device.

In this case, the user is referring to separate USB headphones, which is its own USB sound device and independent of onboard sound.

---

### Post by Alvinator9000 on 2013-02-21
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Thank you, here is the link to the info requested: [http://www.alsa-project.org/db/?f=7cb1a83b6cb80746db876265b2d655de0646be85](http://www.alsa-project.org/db/?f=7cb1a83b6cb80746db876265b2d655de0646be85)


> Here's why I'm confused: headphones are not an alternative to the onboard sound device.
In this case, the user is referring to separate USB headphones, which is its own USB sound device and independent of onboard sound.

Absolutely correct, the USB headphones are a separate audio card which encodes it wirelessly to the headphones.


>  What do you see in Sound Settings? (I don't use Studio, so I'm not sure what tabs are available: perhaps "hardware," "input" and "output.")

I see "Playback", "Recording", "Output Devices", Input Devices", and "Configuration", some of which have slightly overlapping functionality but are laid out nicely.


> Wouldn't hurt to copy/paste the output from two terminal commands:
lspci
lsusb

Here's all that:

alvin@Desktop-Ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port E)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port F)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (PCI express gpp port H)
00:0b.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (NB-SB link)
00:0d.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RD890 PCI to PCI bridge (external gfx1 port B)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
02:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5430 Series]
05:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
06:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450/6350]
06:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
07:05.0 RAID bus controller: Silicon Image, Inc. SiI 0649 Ultra ATA/100 PCI to ATA Host Controller (rev 02)
07:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
alvin@Desktop-Ubuntu:~$ lsusb
Bus 002 Device 003: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 004 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 005 Device 002: ID 04e7:0020 Elo TouchSystems Touchscreen Interface (2700)
Bus 007 Device 002: ID 046d:0a29 Logitech, Inc. 
Bus 008 Device 002: ID 06a3:8012 Saitek PLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
alvin@Desktop-Ubuntu:~$ 


And thanks again everyone for your help its very much appreciated :D

---

### Post by gordintoronto on 2013-02-21
OK, now I get it, you have a Logitech USB sound card which talks to wireless earphones, and that combination works when selected? And you have speakers (?) connected to the onboard sound (front or back?) which you did not get working?

I actually wanted you to tell us what appeared under each of the Sound Settings tabs. I assume there are four output devices, and the onboard is this one:
Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)

Under "output", you might see a drop-down list labelled "connectors." This plays a vital role in selecting the output you want, and there might be several options. On my computer, I select "analog output".

---

### Post by Alvinator9000 on 2013-02-21
> **gordintoronto said:**
> OK, now I get it, you have a Logitech USB sound card which talks to wireless earphones, and that combination works when selected? And you have speakers (?) connected to the onboard sound (front or back?) which you did not get working?

Absolutely correct. And yes speakers all work too and are connected to the back (I do not have front ports on this case, thus am only using the rear).


> I actually wanted you to tell us what appeared under each of the Sound Settings tabs. I assume there are four output devices, and the onboard is this one:
Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)

PLAYBACK
- System Sounds
- Google Chrome (when playing music, youtube, etc)
I can select between showing "All Streams", "Applications", and "Virtual Streams".

RECORDING
"No application is currently recording audio"
Again I can select between the "All Streams", "Applications", and "Virtual Streams".

OUTPUT DEVICES
- Logitech Wireless Headset Analog Stereo (two channels locked proportionally with each other, not set as default device)
Port(s): Analog Output
- Built-in Audio Analog Surround 7.1 (8 ch locked pptnly, set as default)
Port (s): Analog Output

Options to show "All Output Devices", "Hardware Output Devices" and "Virtual Output Devices"

INPUT DEVICES
- Logitech Wireless Headset Analog Mono (1ch)
Port: Microphone
- Built-in Audio Analog Stereo
Port: "Front Microphone" "Rear Microphone" "Line-in"

Options to show "All input devices" "All Except Monitors" "Hardware Input Devices" "Virtual Input Devices" and "Monitors", most of the time just "All Except monitors" is selected.

CONFIGURATION
Cedar HDMI Audio [Radeon HD 5400/6300 Series]
Profile: Off

Cedar HDMI Auhio [Radeon HD 5400/6300 Series]
Profile: Off

Built-in Audio
Profile: Analog Surround 7.1 Output + Analog Stereo Input
More Profiles (And yes I have tried them all):
- Analog Stereo Duplex
- Analog Stereo Output
- Digital Stereo (HDMI) Output + Analog Stereo Input
- Digital Stereo (HDMI) Output
- Analog Surround 5.1 Output + Analog Stereo Input
- Analog Surround 4.1 Output + Analog Stereo Input
- Analog Surround 5.1 Output
- Analog Surround 4.1 Output
- Analog Surround 7.1 Output + Analog Stereo Input
- Analog Surround 5.0 Output + Analog Stereo Input
- Analog Surround 4.0 Output + Analog Stereo Input
- Analog Surround 7.1 Output
- Analog Surround 5.0 Output
- Analog Surround 4.0 Output
- Analog Stereo Input
- Off

Logitech Wireless Headset
Profile: Analog Stereo Output + Analog Mono Input
(More just include an output, or off)


> Under "output", you might see a drop-down list labelled "connectors." This plays a vital role in selecting the output you want, and there might be several options. On my computer, I select "analog output".

I see that in the "Playback" Tab, I see Chrome there (for example) and I can select which device its audio stream is playing through (hence why I can test it on the headphones)
So, close to what you are asking for, my chrome is set to "Built-in Audio Analog Surround 7.1" but I can also choose "Logitech Wireless Headset"


...and yes before anyone asks I have checked over every mute option the "Volume Control" gives, all the sliders are all at 100%, 


I think that should help a bit, I listed everything I could from the volume control, thanks again :)

---

### Post by Alvinator9000 on 2013-05-24
Bump :)

...And some more info...
Onto Ubuntu 13.04 now, clean install, UbuntuStudio again.

I have the onboard (motherboard) sound card not functioning.
I have now a SB Live! EMU10k1 sound card plugged in internally (PCIe?) fully works
And I have a generic China brand USB sound card also fully works
And I have the Logitech H800 USB Headphones also (which show up as a sound card). fully works

...All function fine EXCEPT the onboard, and I would REALLY like to get 7.1 running as purchasing a house is more important to me than buying a good card to do what my already existing hardware should be capable of.

And to clarify, none of the live CDs worked with it, but Windows did work with it when it was installed, but there is a possibility it stopped working, currently I don't have an extra hdd to reinstall Win7 onto atm so I cannot test this.  IF it did indeed stop working while in Windows well then I should just RMA the board, but I think its something to do with software so I'll go that route first, plus the last two times I've RMA'd these boards its taken over a month for the whole process and I can't seem to part with it for that long.

---

