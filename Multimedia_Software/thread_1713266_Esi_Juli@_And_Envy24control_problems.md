---
title: "Esi Juli@ And Envy24control problems"
date: 2011-03-23
forum: Multimedia Software
---

### Post by darkMarko on 2011-03-23
Hi guys.
I just got a new Esi Juli@ soundcard and it works flawlessly on Ubuntu Studio 64 bit.The problem is i cant get Envy24control to start.
It reports an error saying No ICE1712 cards found.I have searched for a solution but it seems nobody had this problem with Juli@.I assume ALSA doesn't detect the card properly and sends a negative signal to Envy24control like it does on some other cards based on that same chip.
Any help would be appreciated.

---

### Post by cchhrriiss121212 on 2011-03-24
Envy24control is for ICE1712 only, your card is ICE1724. You can use alsamixer to control the settings.

---

### Post by darkMarko on 2011-03-24
Thanx for the reply.
I have installed alsamixergui from synaptic but it doesent detect my card..it shows that my card is pulse audio..and there are no settings to change that so i downloaded Gnome ALSA Mixer.He does find the card but the only settings available are master volume and gain.Not very useful really since the normal sound mixer provided those already.
Is there any app that provides the same functionality as the windows one that came with the card?

---

### Post by cchhrriiss121212 on 2011-03-24
Try using alsamixer via the terminal - just type it in and press enter, use arrow keys to adjust. 
> Is there any app that provides the same functionality as the windows one that came with the card?
I don't know, what functionality are you talking about?

See this thread for more tips on sample rates an such:
[http://www.head-fi.org/forum/thread/274363/esi-juli-with-alsa-linux](http://www.head-fi.org/forum/thread/274363/esi-juli-with-alsa-linux)

---

### Post by darkMarko on 2011-03-24
Ok i have tried it in a terminal but it still only allows me to control master volume and master gain.
And by other functionality i meant separate gain controls for inputs and outputs the realtime monitoring control,sample rate control and most importantly sound routing.

---

### Post by cchhrriiss121212 on 2011-03-24
On the thread I linked to you can see that alsamixer should be doing all that. What do you see when you type in aplay -l && lspci -v?

---

### Post by darkMarko on 2011-03-24
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Juli [ESI Juli@], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at fe00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fd00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0000000-f01fffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at fc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=16]
	I/O ports at f400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: medium devsel, IRQ 7
	Memory at fdffd000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at f200 [size=8]
	I/O ports at f100 [size=4]
	I/O ports at f000 [size=8]
	I/O ports at ef00 [size=4]
	I/O ports at ee00 [size=16]
	I/O ports at ed00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series] (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device 21f3
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdcc0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at ae00 [size=256]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
	Subsystem: Giga-byte Technology Device aa60
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fdcfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at df00 [size=8]
	I/O ports at de00 [size=4]
	I/O ports at dd00 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at db00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at ce00 [size=256]
	Memory at fddff000 (64-bit, prefetchable) [size=4K]
	Memory at fddf8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:04.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
	Subsystem: Device 3031:4553
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at bf00 [size=32]
	I/O ports at be00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ICE1724
	Kernel modules: snd-ice1724

Even tho i disabled the ATI sound on my graphics card under ubuntu he still finds it.I also disabled the integrated audio in BIOS.Juli@ should be the only one.

---

### Post by cchhrriiss121212 on 2011-03-24
That is the problem, when you open alsamixer it will select the default card controls, in this case it is the ATI HDMI device. Press f6 in alsamixer to select the juli@ and you should see the right controls.

You should be able to set the default audio device using pulse audio. If you want to remove the ATI audio, try blacklisting the snd-hda-intel module:
```
sudo gedit /etc/modprobe.d/blacklist
```
Then type "blacklist snd-hda-intel", save and reboot. Then the juli@ will be the only card and therefore default.

---

### Post by darkMarko on 2011-03-24
Ok i blacklisted ATI thanx a lot for that..he was getting on my nerves.
In alsamixer i did select Juli@ even before he was disabled..now alsamixer detects Juli@ as default but still offers no control except master volume and gain.I mean all controls are there but none work in the console.In the Gnome Alsa Mixer GUI they are grayed out and Alsamixergui still shows PulseAudio as my card..it allows me to change just the master volume and nothing else.I read through the link u sent me but they all had sample rate problems and playback problems..i don't.I just want a capable mixer for the card.

---

### Post by cchhrriiss121212 on 2011-03-24
Have you been running anything with sudo or as root?

This could be a pulse problem. Do you get any options to control levels via pavucontrol?

---

### Post by darkMarko on 2011-03-24
Tried running it as sudo now..same results...either it does nothing or its grayed out...Pavucontrol seems to be good i can change its settings and it monitors the signal level.Still far away from the windows controler's functionality tho...

---

### Post by cchhrriiss121212 on 2011-03-24
Please do not run things as sudo, I asked to make sure you haven't done so already, I should have made that clear before as it can cause issues like this.

So regarding pavucontrol, does it have more features than alsamixer? Which ones are absent that you would like?
> Still far away from the windows controler's functionality tho...
I would not hold your breath for that. The things you have listed should be do-able, but something like sound-routing is more complex and, depending on exactly what you want to do, involves beyond the GUI setup.

---

### Post by darkMarko on 2011-03-24
The 1 function i would like to have is the ability to record stereo mix or what you hear..however you want to call it.Juli@ doesn't have a separate recording channel for that but in windows you could route the audio from any source to any source with the card's mixer making it possible to record anything in any DAW or audio editor.Thats all i actually really need.
I tried recording but JACK has too many...problems so to say..so i gave up on recording in Ubuntu.

---

### Post by cchhrriiss121212 on 2011-03-24
You should be able to do that if you follow this:
[http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html](http://www.ubuntugeek.com/how-to-recording-internal-audio-in-ubuntu.html)

---

### Post by darkMarko on 2011-03-24
Works perfectly.
Thanx alot man.

---

