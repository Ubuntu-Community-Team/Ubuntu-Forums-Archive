---
title: "Issues with two sound cards"
date: 2008-07-10
forum: Multimedia Software
---

### Post by SoftTaco on 2008-07-10
I Have two sound cards, an onboard realtek and a pci Soundblaser live. The problem is ubuntu cant decide which to use. First off it gives them names i cant understand. Then when set the one i want in Sound Preferences (by trail and error) some programs still use the other card

Also i have a 5.1 system hooked up to the soundblaser but cant figure out how to turn that on ubuntu wants to use only one channel it seems

---

### Post by Arthur Archnix on 2008-07-10
Ubuntu has a sound preferences setting you can use. Look in your system preferences or admin menu for "sound". Find the default device. Have you tried setting this with the soundcard you want to use? Some trial and error may be required. Also, take a look at the sound playback options. It's possible you can set it up here as well.

Update: I realize you've done some of this already. Perhaps you can write down the names of the cards that Ubuntu reports and include it in your reply along with the output of lspci -v.

Lastly, and this is a bit more advanced, but if you don't want to use one soundcard at all, say onboard, you can likely disable it in your bios. In which case, Ubuntu will just use your other soundcard. 

Failing that, /etc/modprobe.d/alsa-base is the file that contains a lot of the information use by your soundcard. If the options above fail to resolve it for you, post the content of that file back here along with the output of lspci -v and perhaps others or myself can give more info.

---

### Post by SoftTaco on 2008-07-10
[IMG]http://img149.imageshack.us/img149/2320/screenshotsoundpreferenly6.png[/IMG]
I opened the dropdown so you can see the options i have.

the different CA106 options select different channels of my 5.1
i have them all set so that the test produces a tone in the center channel. But like i was saying some programs dont seem to care.
Specifically mplayer and firefox flash video still output to the other card.

id rather not disable the card, ideally i want to use it for a headset/mic setup for ventrillo and skype.

Also thanks for helping sorry if i dont make sense in some places but i am a bit sickly right now

lspci -v output:
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: b0000000-cfffffff
	Prefetchable memory behind bridge: d2100000-d21fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e300 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e100 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e200 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at d2000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: d0000000-d1ffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 8212
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e400 [size=256]
	I/O ports at e500 [size=64]
	Memory at d2001000 (32-bit, non-prefetchable) [size=512]
	Memory at d2002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 5201
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=8]
	I/O ports at e900 [size=4]
	I/O ports at ea00 [size=8]
	I/O ports at eb00 [size=4]
	I/O ports at ec00 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 3102
	Flags: medium devsel, IRQ 11
	I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at c000 [size=128]
	[virtual] Expansion ROM at d2100000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at d000 [size=32]
	Capabilities: <access denied>

02:02.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: ATI Technologies Inc ATI TV Wonder Pro
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Biostar Microtech Int'l Corp P4TSV Onboard LAN (RTL8100B)
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at d100 [size=256]
	Memory at d1010000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at d1000000 [disabled] [size=64K]
	Capabilities: <access denied>

```

---

### Post by Arthur Archnix on 2008-07-10
That's ok. Here's what I'd do. I'd go into my bios and try to disable onboard. Then come back and see it mplayer and flash work.

I know this isn't your ideal setup, but it would be good to know for you and me that it's possible to use these apps with your preferred device.

While still disabled, see if your skype and ventrillo work as well.

I say this quickly because I'm off to bed, and while you're waiting for a better answer from others or myself you can do this useful troubleshooting as well as have decent, if not ideal, sound playback.

Also, if you run into problems (for example, you disable onboard but flash still doesn't work) then we don't waste time trying to fix the wrong thing.

Best,

---

### Post by SoftTaco on 2008-07-10
Ok well disabling the sound card via the bios appears to have fixed all the sound issues but it is still just playing out of one channel.

Running
```
speaker-test -Dplug:surround51 -c6 -l1 -twav[A

```
Returns the error
```
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

```
but i have no app running that is using it.

---

### Post by SoftTaco on 2008-07-11
Think i got it now

Just reconfigured alsa"
```
sudo aptitude install build-essential module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```

---

### Post by Arthur Archnix on 2008-07-11
Can we get a status update?

At the moment do you have onboard disabled, but your other soundcard playing all the sound properly and using all the 5 channels?

If so, then what's the next step. You want to enable your on-board sound card in order to run audio input for both skype & ventrillo?

If that's the case, while your onboard is still disabled you should take another shot of the devices available under your sound preferences. That way, when you re-enable it you'll be able to tell them apart.

It also occurs to me that you may be running pulse-audio, in which case, sound preferences probably isn't controlling your audio at all. Or if so, is doing it very badly. Perhaps you ought to look at installing a pulse sound configuration gui? On debian these packages are called paman, paprefs. Do you have similar packages and are they installed?

---

