---
title: "Severly stuttering playback and double image"
date: 2009-06-16
forum: Mythbuntu
---

### Post by Mattaus on 2009-06-16
Hi all,

I've just installed MythTV for the very first time on the following hardware:

ASUS M4A78-VM Motherboard (ATI 3200 Integrated Graphics)
AMD Athlon X2 4800+
2GB of DDR2 RAM
Leadtek 2000H RevJ
1x 160GB SATAII HDD
1x 1TB SATAII HDD

Now I have scanned in the channels as required and have managed to start the front end fine. However when I watch live TV the playback is not only at about 1 frame per second, but its also split into 2 screens. Imagine 2 player Golden Eye on the old N64 if you will - it splits the screen horizontally, but displays exactly the same image in both.

For the stuttering playback I figure its a buffer related issue but I'm not entirely sure, and for the split screen I have no idea. I looked through all the options but could not see anything dealing with it.

It may be worth noting that audio playback is fine.

Any suggestions?

Sorry if it is a common problem - I have looked but could not find much.

Cheers.

---

### Post by AlecJ on 2009-06-16
The problem is the video chip drivers, you need to search out the proper ATI binary, or fit a new card with known working drivers.

---

### Post by AboveTheLogic on 2009-06-16
I have the split screen issue with one of my frontends, and it's an ATI too.

I did enable proprietary drivers, but that's about as far as I could get. It only occurs with some channels, and seems to work fine playing other media like SD videos that I already had. Also, it locks up when pausing, do you have that, Mattaus?

---

### Post by Mattaus on 2009-06-16
I installed the latest drivers from the AMD website - is this what you mean? It runs XBMC without a single hitch - no lockup at all and as smooth as my old machine that used nVidia graphics.

Actually scratch that - my machine has locked up at random intervals over the past couple of days (but not when pausing, it is totally random) but when I say locked up I mean no picture nothing. I had to pull the power to get anything back at all. Last night the machine was running for the entire time I was working on it without any problems.

Even though I can afford it, I would rather try find the proper binaries for my current graphics, than install a new card. But if I do it will be nVidia I guess.

EDIT: Just read about the 9.6 Driver release for ATI cards under Linux. Might give them a whirl tonight and see what that does

---

### Post by AboveTheLogic on 2009-06-16
well, in the mythbuntu control center there is a place to install the AMD proprietary drivers, I'm not sure how yours is setup...

---

### Post by Mattaus on 2009-06-16
> **AboveTheLogic said:**
> well, in the mythbuntu control center there is a place to install the AMD proprietary drivers, I'm not sure how yours is setup...

I'm not running Mythbuntu - I'm only running MythTV under Ubuntu.

The penny has sort of just dropped...am I in the wrong place to be asking for help on this issue lol?

Actually could you be talking about proprietry hardware drivers? Under System > Administrator > Hardware (or something like that) I have the option to install some ATI drivers. I might try this AFTER I try the 9.6 Drivers.

Also, are both the split screen AND the stuttering playback driver related? That's the impression I'm getting.

---

### Post by AboveTheLogic on 2009-06-16
Yeah there is a proprietary drivers application buried in those menus somewhere, its the same thing.

I think your stuttering playback is related to the video problem, but maybe its not.

I don't think there is anything wrong with you posting in this section with your setup, its all pretty much the same thing. Mythbuntu just has a few more features.

---

### Post by Mattaus on 2009-06-16
Coolies. I have a few potential solutions to try but if I get desperate I may just fork out for a 8400GS or something basic and switch to nVidia (as they seem to be better for this sort of stuff).

Nice and cheap and will probably work better.

---

### Post by AboveTheLogic on 2009-06-16
don't give up!

what's your lspci -v output for the video device?

---

### Post by Mattaus on 2009-06-16
> **AboveTheLogic said:**
> don't give up!

what's your lspci -v output for the video device?

I haven't given up yet lol....just saying if I get truly stuck that's what I'll go for. Unfortunately been in Aus I'm at work right now and will be for the next 5 hours :(

I am in the process of learning about SSH and VNC so in the future I will be able to check from work :p

As soon as I get home I will let you know what the output is.

---

### Post by AboveTheLogic on 2009-06-16
I was just going to suggest SSH :)

If you are using windows at work, I highly recommend tunnelier as your SSH client--- if you have the rights on your machine to install it... otherwise putty portable is the way to go. You can port forward to port 5900 through SSH so you only need to forward port 22 with your router. Don't forget about dynamic DNS if you have a dynamic IP...

---

### Post by Mattaus on 2009-06-16
:lolflag:

This is a whole new world of hurt for me...see this thread:

[http://ubuntuforums.org/showthread.php?t=1187765](http://ubuntuforums.org/showthread.php?t=1187765)

Basically I am looking into it, and have a how to printed out ready to go for tonight. I'm fine with everything except basic network setup at home. I am living at my gf's house at the moment (as her folks are on holiday in Canada for 5 weeks) and as such I'm going to have to scramble around for the password to their router to enable the port forwarding. 

I hate networking...I really do. And it ain;t helping that the HTPC is wireless. I don't even have a static IP address for it yet (its still 10.1.1.3 or something. Does that sound right?) Feel free to post in that other thread if you want to lend a hand there as well :D

I think maybe I should try and solve one problem at a time instead of my current "all at once" methodology. 

Nah bugger it this is more fun.

---

### Post by Mattaus on 2009-06-17
Right, because I'm an idiot and did not read through the entire instructions for installing shepherd before I did it last night, I basically got nothing else done because I didn't want to reboot the machine at any point.

Also I could not find the user name or password for my GF's families router and did not want to reset it because it's not really mine to mess with. Her dad was in the army and hides stuff **really** well...

So I spent the night cooking dinner, watching bad Aussie reality shows and My Name is Earl. *sigh*

Sorry off topic.

Anyway - here is the output of lspci -v:

> 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f8c00000-f8dfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8e00000-f8efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=8]
	I/O ports at b000 [size=4]
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=16]
	Memory at f8bffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f8bfe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at f8bfd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f8bff800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8bfc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8bfb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at f8bff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 837b
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at f8bf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	Memory behind bridge: f8f00000-fbffffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82ef
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at f8bfa000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 2300
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at f8df0000 (32-bit, non-prefetchable) [size=64K]
	Memory at f8c00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ASUSTeK Computer Inc. Device 82f1
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f8de8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8385
	Flags: bus master, fast devsel, latency 0, IRQ 2301
	I/O ports at e800 [size=256]
	Memory at f8eff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at f8ec0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: LeadTek Research Inc. Device 6f2b
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

03:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: LeadTek Research Inc. Device 6f2b
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

03:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: LeadTek Research Inc. Device 6f2b
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

03:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Netgear Device 5e00
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at f8ff0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k



I guess all you care about is the GFX part but as I don;t know too much I just included it all.

Like I said I have not had a chance to try the new 9.6 Drivers or the ones under hardware settings yet.

EDIT: How do I insert text with scroll bars so it does not take up so much space!?

---

### Post by AboveTheLogic on 2009-06-17
> **Mattaus said:**
> EDIT: How do I insert text with scroll bars so it does not take up so much space!?

use the [ code ] tags

i think this is the relevant part...

```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
Subsystem: ASUSTeK Computer Inc. Device 82f1
Flags: bus master, fast devsel, latency 0, IRQ 2300
Memory at d0000000 (32-bit, prefetchable) [size=256M]
I/O ports at d000 [size=256]
Memory at f8df0000 (32-bit, non-prefetchable) [size=64K]
Memory at f8c00000 (32-bit, non-prefetchable) [size=1M]
Capabilities: <access denied>
Kernel driver in use: fglrx_pci
Kernel modules: fglrx
```

How about this:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

---

### Post by clayton on 2009-06-17
Is your output going to an HDTV? I have a Neuros Link ([http://www.neurostechnology.com/]("http://www.neurostechnology.com/")) which comes with an Asus M3A78-EM board (HD 3200 graphics). I had the the double screen issue, too, and was able to defeat it by going to the on-screen menu (M), and going two up-arrows to video scan rate, and changing from auto detect to progressive (my tv is set to 720p). I haven't found a way to keep the 720p setting persistent; mythtv always goes back to the auto-detect mode. Also, pausing the screen turned it into a single image, which helped in navigating the on screen menu.

---

### Post by Mattaus on 2009-06-17
Hmm. It appears that the video card is having issues with any video. Last night I left the machine running while I slept. Basically it ran for nearly 12hours straight without issue. It was however on the desktop and all it was displaying was a terminal. 

2 hours a go my GF rung me to say she was watching some movies and it froze up. Twice. The first time was after about 10mins, the second time it lasted about an hour. Both times she was in MP.

Like I said I have not had a chance to try new drivers yet. I will try mess with the scan rate and see what that does, and then if I still have no luck I will try the drivers.

If all else fails then I'm switching to nVidia :( I really don't want to spend hours and hours debugging this. I have bigger fish to fry.

---

### Post by Mattaus on 2009-06-18
Clayton,

I was looking around for a way to possibly make the video scan method stay as default when I stumbled across other posts (in other forums as well) regarding the doubling of images in MythTV using ATI hardware.

Now obviously I cannot test any of this atm as I am at work, but it does seem legit as it solved pretty much every one elses problems.

The issue seems to stem from a deinterlacer called "bobdeint" which causes double imaging on ATI cards.

One way to permamently deselect this type of deinterlacing is to change your playback profile. See:

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

I **know** my playback profile is CPU++ at the momement (as I remember looking at it and thinking "WTF is that?") and what would you know bobdeint is the default deinterlacer for that profile.

So what I'm going to try tonight is any of the other profiles. If it fixes it I will then create a custom profile best suited for my hardware.

If you try this anytime over the next few hours I'd love to hear what the results are...

Still doesn't explain the crashing in XBMC though :(

---

### Post by AboveTheLogic on 2009-06-18
switching cards would definetely be the easiest, I've had good luck with the nvidia card on my master backend

---

### Post by tduffy83 on 2009-06-18
Switching playback profiles to "normal" fixed this issue with me.  Make sure you are using the latest binaries from ATI's website.  There used to be an unofficial wiki that had full instructions, but it appears the link is broken.  

The link is: [http://wiki.cchtml.com/](http://wiki.cchtml.com/)

Maybe it will be back up in time.

One thing to note is that by changing your profile to normal this will disable deinterlacing which can be annoying for interlaced source material like 1080i or 480i.  I wouldn't really call this a solution but more of a workaround.  I'd upgrade to nvidia as apparently their drivers work much better.  The only reason I haven't bought an nvidia card for this machine is because it's really only my master backend and I do not watch tv on it.

---

### Post by Mattaus on 2009-06-18
Hmm...changing to normal fixed the dual screen problem but the playback is still stuttering badly. I guess I will try the drivers now and root around in MythTVs settings to see what I can find.

EDIT: Sorry for the noobness but when you say "binaries from ATI's website" do you mean the drivers downloaded through the support and drivers link? As that's what I have although I haven't had a chance to install 9.6 yet.

---

### Post by AboveTheLogic on 2009-06-18
normal playback mode fixed my problem too :)

---

### Post by Mattaus on 2009-06-18
I've decided I'm switching to nVidia regardless. Less hassle and my MythTV EPG problems are annoying me atm :p

---

### Post by clayton on 2009-06-18
Mattaus,

I switched from cpu+ to Normal and problem gone. Thanks for the feedback!

---

### Post by Mattaus on 2009-06-18
> **clayton said:**
> Mattaus,

I switched from cpu+ to Normal and problem gone. Thanks for the feedback!

Glad to be of some help! Feel like I'm taking and not giving enough back lol.

---

### Post by Mattaus on 2009-06-19
Right...I solved **all** all my problems this morning by purchasing a nVidia 8400GS for AU$39. Cheap as chips, playback is perfect.

Its a bit of a kick in the nuts as I am an ATI fan (I always go for the underdog) but I'm not complaining thats for sure.

Thanks everyone for helping out!

---

