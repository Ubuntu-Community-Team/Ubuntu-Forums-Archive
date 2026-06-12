---
title: "Intermittent connection problem"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by raysa on 2012-07-13
My connection to the internet seems to be playing up - but not always. When it is troublesome some (but not all) web pages will not load or take ages, the email client will grind to a halt and general connectivity becomes very unreliable.
The router seems to be OK - another computer connected at the same time and accessing the same web pages soars along with no trouble.
At first I thought it was the ethernet connection so I changed the cable and still had the trouble, then I plugged in a USB wireless adaptor but the problem remains.
I fired up Windows (which I normally never use), and although it was considerably better it still played up with occasional webpages hanging.
I'm running xubuntu 12.04 on an Acer X1930 computer.
What should I check, and how?
Thanks.

---

### Post by Kirk Schnable on 2012-07-13
Since you're having problems under Windows as well, it sounds to me like this could be a hardware problem.

Nevertheless, let's take a look at your kernel version and the hardware you're running.  Please supply us with the output of:

```
uname -r
```

```
lspci
```

Kirk

---

### Post by raysa on 2012-07-13
Thanks Kirk. I'm actually having doubts about whether the problem is also in Windows. It seems the website I used to test it was having some problems itself (spotted on another copmputer). I've booted back into Windows and tried several sites and they seem OK. Mind you, this problem has always been intermittent, so it's hard to be certain.

Back in ubuntu I now can't get connected at all! So I've copied the outputs you requested from the troubled desktop and am posting them from another computer:

ray@ray-desktop:~$ uname -r
3.2.0-26-generic
ray@ray-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
ray@ray-desktop:~$ 

Thanks, Ray

---

### Post by Cheesehead on 2012-07-13
There are three options. See which ones you can rule out:

1) Hardware or something elso on your system. Kirk Schnable is all over the hardware angle. If connectivity slows, what about the rest of your system? Can you still launch the calculator? Open a terminal and try the command  [FONT="Courier New"]top[/FONT]  to see what's consuming the most resources. Does the terminal take unusally long to open? Does top take a long time to start? Does top show very high CPU/MEM usage?

2) Local LAN congestion. Many LAN activity monitors are in the Ubuntu repositories. Personally, I use EtherApe. When connectivity slows, fire up the monitor - what's consuming all the bandwidth? Which machines is it running to/from? The answer should be pretty clear.

3) Upstream ISP congestion. If you have ruled out the other two, then this is likely your problem. Not much you can do about it except complain to them or look into a different provider.

---

### Post by raysa on 2012-07-13
Thanks. I think I can rule out No.3 because other computers using the same router & ISP have no probs. Does that also cover No.2?
As for hardware & resources, I haven't notice any probs with any other aspects of performance - applications load quickly and everything seems to motor along nicely. If I look at CPU usage in Task Manager it doesn't seem unduly stretched whan big apps launch - never goes beyond about 30-50%.

Ray

---

### Post by raysa on 2012-07-14
I've gone into Windows a couple of more times and the problem does seem to exist there too. Not so severe - hanging up less often and for shorter periods, but definitely not as it should be.

So, with the router and ISP side tested with other computers and found to be working fine, am I left with the conclusion that it's a hardware problem in the desktop?

As the rest of the computer performance seems to be fine, does this narrow it down further? How can I test such things?

Thanks, Ray

---

### Post by Kirk Schnable on 2012-07-14
You may want to try using a different network card.  You can pick them up pretty cheaply if you don't have one laying around.

That is going to be the simplest answer in the long-run.  If you find out that there's a problem with your network card, there's not a whole lot you can do about that other than replace it.

Kirk

---

### Post by raysa on 2012-07-15
Thanks Kirk. Forgive my ignorance, but a couple of questions:

The computer doesn't have a separate network card - I assume this function is carried out within the motherboard circuitry. If I fit a separate network card, will it take over that function?

When the problem occurs, the computer doesn't connect with either an ethernet cable or with a usb wireless adaptor - does this suggest where the problem is? (I'm not sure of the difference between network cards and adaptors, but I assume the fault lies somewhere before the ethernet/wireless choice). Does a separate network card do stuff before this stage?

Thanks, Ray

---

### Post by Kirk Schnable on 2012-07-15
> **raysa said:**
> Thanks Kirk. Forgive my ignorance, but a couple of questions:

No problem, that's what we're here for!

> **raysa said:**
> The computer doesn't have a separate network card - I assume this function is carried out within the motherboard circuitry. If I fit a separate network card, will it take over that function?

Correct.  Similar to the way many boards have integrated graphics, and you can go buy an expensive graphics card to take over the graphics functions.  You can also have additional network cards, and use them PLUS the one on your board.

> **raysa said:**
> When the problem occurs, the computer doesn't connect with either an ethernet cable or with a usb wireless adaptor - does this suggest where the problem is? (I'm not sure of the difference between network cards and adaptors, but I assume the fault lies somewhere before the ethernet/wireless choice). Does a separate network card do stuff before this stage?

Oh, I wasn't aware that this was the case.  A new network card may not help you with your problem in this case.

Now it's starting to sound like a software problem to me again.  The network manager software is what, as you put it, "decides" which interface to use.  This has nothing to do with your hardware.

Does the problem only occur when both interfaces are plugged in?  Does the wired network work great as long as the USB WiFi card isn't plugged in?

Kirk

---

### Post by raysa on 2012-07-15
No, at first I only had the wired connection, and when that played up and didn't get solved with a new cable, I plugged in the usb wireless adaptor. That worked fine for several days, then that started playing up too.
Now the problem occurs whether its just cable, just wireless (cable removed) or both connected.

With both connected, when the web connection was lost I tried going into the network manager and switching from wired to wireless and back, but it wouldn't connect with either, and then the manager's scanning stopped recognising the router at all until I rebooted - but still no connection.

Ray

New bit of info in case it's helpful ... when you first mentioned that it looked like a hardware problem I mentioned the problem over in the hardware forum and it was suggested that I run iwevent from a terminal.

I've done this again today, and for most of the time I just got "Scan request completed", but something new has been output - at exactly the time the connection was lost:

19:11:20.582913 wlan0 Scan request completed
19:13:20.582906 wlan0 Scan request completed
19:13:21.142957 wlan0 New Access Point/Cell address:Not-Associated
19:13:21.954946 wlan0 Scan request completed
19:13:21.986490 wlan0 Association Response IEs:010882848B962430486C32040C1218602D1A0C181AFFFF 00000100000000002C0101000000000000000000003D160B08 1500000000000000000000000000000
19:13:21.986584 wlan0 New Access Point/Cell address:00:23:4D:11:F9:59
19:15:20.583211 wlan0 Scan request completed
19:17:20.582918 wlan0 Scan request completed
19:19:20.586914 wlan0 Scan request completed

One more thing to mention: the network manager (and indeed all other software) is configured just the same on the troublesome computer as it is on the spare one that is having no trouble at all (which I'm using now because the desktop won't connect again).

Thanks, Ray

---

### Post by Kirk Schnable on 2012-07-15
Can you give me the output of:
```
lspci -v
```

As I'd like to see what driver you're using.  I wonder if this might be a driver conflict.

Kirk

---

### Post by raysa on 2012-07-15
Thanks Kirk.  Here it is:

ray@ray-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fe429000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 8000
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at fe400000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe428000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at f080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at fe427000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at fe420000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe426000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
	I/O ports at f0d0 [size=8]
	I/O ports at f0c0 [size=4]
	I/O ports at f0b0 [size=8]
	I/O ports at f0a0 [size=4]
	I/O ports at f060 [size=32]
	Memory at fe425000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Acer Incorporated [ALI] Device 0492
	Flags: medium devsel, IRQ 11
	Memory at fe424000 (64-bit, non-prefetchable) [size=256]
	I/O ports at f040 [size=32]
	Kernel modules: i2c-i801

ray@ray-desktop:~$ 

Ray

---

### Post by Kirk Schnable on 2012-07-15
Alright, now can you give me:

```
modinfo e1000e
```

Kirk

---

### Post by raysa on 2012-07-15
ray@ray-desktop:~$ modinfo e1000e
filename:       /lib/modules/3.2.0-26-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        1.5.1-k
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     14805D4156B766DD3F4208D
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-26-generic SMP mod_unload modversions 
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           WriteProtectNVM:Write-protect NVM [WARNING: disabling this can lead to corrupted NVM] (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
ray@ray-desktop:~$

---

### Post by Kirk Schnable on 2012-07-15
It does look like there may be a newer version of e1000e available:
[http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.0.0.1/](http://sourceforge.net/projects/e1000/files/e1000e%20stable/2.0.0.1/)

Although I usually find Intel drivers to be fairly reliable and I've never seen something like this with any of my e1000e cards.

Can you give me:
```
lsmod
```

So I can see if any modules look out of place...

Kirk

---

### Post by raysa on 2012-07-15
Thanks for your time, Kirk. I'd really like to crack this.

ray@ray-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
arc4                   12529  2 
rtl8192cu             103297  0 
rtl8192c_common        75767  1 rtl8192cu
rtlwifi               111202  1 rtl8192cu
snd_hda_intel          33773  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              205544  2 rtlwifi,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
serio_raw              13211  0 
mac_hid                13253  0 
i915                  468737  2 
wmi                    19256  0 
snd                    78855  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
usb_storage            49198  3 ums_realtek
uas                    18180  0 
e1000e                156693  0 
ray@ray-desktop:~$

---

### Post by Kirk Schnable on 2012-07-15
Everything looks okay to my eye.  Would you feel comfortable compiling and trying the latest stable e1000e version I pointed out in the previous post?

Kirk

---

### Post by raysa on 2012-07-16
Sorry about delayed response - time difference between us means staggered bed-times!

I'd be happy try the new e1000e, but I'd need clear instructions - not done compiling before.

One other thing I've noticed: Occasionally (but not always - nothing is consistent about this fault) re-booting the router will restore connection - even though the router was working perfectly for two other computers connected to it.

If the problem is to do with the computer recognising (or suddenly losing recognition of) the router, I wondered about changing some of the settings in the network manager's "Edit connections" area instead of leaving them on auto, but it asks for information I don't understand or know where to find.

But anyway, if e1000e is worth a try, can you help me with the compiling?

Thanks, Ray

One more thing just in case it's relevant - the computers that work fine with the router are 32-bit, whereas the one with the problems is 64-bit.

Ray

---

### Post by Kirk Schnable on 2012-07-16
I don't think the architecture of the OS should have anything to do with this.  But if you try using an i386 version of the Live CD, your computer would be (for all intents and purposes) downgraded to 32-bit while it's running in that live session. 

You should be able to figure out the e1000e install process from this guide.  I think the only thing you might not know is what to put in for "KERNEL VERSION".   Put in the output of the command: "uname -r".

[http://www.intel.com/support/network/sb/CS-032514.htm](http://www.intel.com/support/network/sb/CS-032514.htm)

If you need more assistance with it, let us know.

Kirk

---

### Post by raysa on 2012-07-16
Thanks Kirk. I'm trying with this, but don't seem to have got it right.

If I try the rpm build instruction, I get a message "rpm: -tb: unknown option" and nothing happens.

If I try the numbered instructions below that (are these instead of or as well as the rpm thing?), all seems OK until I move to the extracted folder and its src sub-folder as instructed, but then the "# make install" doesn't do anything.

Ray

Ah ... some progress, but not success yet.

I decided (rightly or wrongly) that the rpm thing was not the way, so I tried the numbered instructions again - but this time leaving the "#" off the "make install" (doh!).
It did stuff, and now I can see the .ko file just where it says it should be.

But instruction 5 has me stumped. I followed it carefully but it gave a message that the file is already there.

I've rebooted but the computer still won't connect on either wireless or wired.

I've just done that modinfo thing again, and it shows the driver as version 2.0.0.1-NAPI, so it looks like I installed it.

But alas the computer is still seldom connecting properly. 

Ray

The new driver doesn't appear to have made any difference - still got the same connection problems.

In Windows I can nearly always connect but web-loading etc is erratic and slow. Worse in Ubuntu, with long periods of no connection at all.

The computer and the router are clearly not talking to each other well (often not at all in Ubuntu), although the router continues to work perfectly with other machines.

What next?  

(also asking this over in the hardware forum in case the conclusion is that it's a hardware issue).

Ray

---

