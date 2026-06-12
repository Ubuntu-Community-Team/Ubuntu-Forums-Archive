---
title: "snd_hda_intel no sound"
date: 2008-05-22
forum: Multimedia Software
---

### Post by laleshii on 2008-05-22
```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
05:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

the audio card is installed properly or so I think. I tried building the modules with module-assistant but I get the same result. Volume is maximum on all channels.

---

### Post by Zorael on 2008-05-22
There are two levels to this; no sound, and weird sound.

The prime suspect when not getting *any* sound is having important channels muted. You may have several multiplicative channels that all affect output. For instance; I have a Master, a PCM *and* a Front channel. If I put them all at 50%, the end volume is Master*PCM*Front = 0.5*0.5*0.5 = _12.5_%. So I always keep Front and PCM at 100%, and use Master to manage the output. Obviously, if even one is at 0%, I get 0% volume.

Open up '**alsamixer**' in a terminal and make sure everything checks out. If you're using Pulseaudio, which is the default in Ubuntu 8.04 and later (but not in Kubuntu, for instance), make that '**alsamixer _-Dhw_**' instead.

If you're having issues with the card not reacting when you connect headphones, see if there are *options* in your soundmixer. Some cards have options like Headphone Jack Detection, which you'd need to activate to get that behavior.

Failing all that, you may be able to solve it by specifying a *model* for your sound chipset. This is more the case of when you're getting sound but only from one speaker, the soundcard not detecting when you're connecting headphones (with no option to toggle this available), crackling sound or static, volume oddities, etc.

Basically, drivers aren't per-soundcard model but rather *per-chipset*. Furthermore, even though two different soundcards may be based on the same model of chipsets, they can have *quirks* caused by other factors involved in its making. Perhaps all Brand**X** cards based on Chipset**A** have a slightly different revision of that chipset than Brand**Y**'s cards do, so their drivers' code need to differ slightly. Even though your computer senses it's based on ChipsetA, it doesn't know if it has Brand**X**'s or Brand**Y**'s quirks, and you can end up with weird stuff when what it defaults to isn't right for *your* card. While it might very well be what another user with a Brand**Z** card, also based on ChipsetA, needs.

A more concrete example would be channels; perhaps ChipsetA technically supports having up to 5 channels (two front, two back, center), but the default cheapo ChipsetA cards only support two (left, right). You bought an expensive ChipsetA card, however, and you want all your 5 channels. But the driver only gives you the default two unless explicitly told your card supports more. You get the idea.

At this point you may want to consider manually upgrading ALSA. [There is a neat script for this](http://ubuntuforums.org/showthread.php?p=6589810) written by soundcheck. Newer versions just may be able to detect which quirks are needed automagically. If that doesn't help or if you don't want to, then read on.


Enter this command to find out which chipset your card is based on.
```
$ aplay -l
```
It'll say something like:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: **_ALC883_** Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #
```
...where the **ALC883** part is the chipset name, and what you want to find out. Find the entry for that chipset in the below list, and note the available *models*.

[INDENT]**Note:** This list is available for offline reading in **/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz**. The contents of it also differ between versions of ALSA.

This post focuses on Intel HDA cards. If you _don't_ have one such but you're experiencing the same-ish issues, open up that **ALSA-Configuration.txt.gz** file and see if your chipset is listed there. The rest of the post should apply regardless.[/INDENT]
```
  Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    [Multiple options for each card instance]
    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = use LPIB, 2 = POSBUF)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
    bdl_pos_adj	- Specifies the DMA IRQ timing delay in samples.
		Passing -1 will make the driver to choose the appropriate
		value based on the controller chip.
    
    [Single (global) options]
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)
    power_save	- Automatic power-saving timtout (in second, 0 =
		disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
		(default = on)

    This module supports multiple cards and autoprobe.
    
    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  6stack	6-jack in back, 2-jack in front
	  6stack-digout	6-jack with a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)
	  asus		3-jack (ASUS Mobo)
	  asus-w1v	ASUS W1V
	  asus-dig	ASUS with SPDIF out
	  asus-dig2	ASUS with SPDIF out (using GPIO2)
	  uniwill	3-jack
	  fujitsu	Fujitsu Laptops (Pi1536)
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  medion	Medion Rim 2150
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC260
	  hp		HP machines
	  hp-3013	HP machines (3013-variant)
	  fujitsu	Fujitsu S7020
	  acer		Acer TravelMate
	  will		Will laptops (PB V7900)
	  replacer	Replacer 672V
	  basic		fixed pin assignment (old default model)
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  hp-bpc-d7000	HP BPC D7000
	  hp-tc-t5735	HP Thin Client T5735
	  hp-rp5700	HP RP5700
	  benq		Benq ED8
	  benq-t31	Benq T31
	  hippo		Hippo (ATI) with jack detection, Sony UX-90s
	  hippo_1	Hippo (Benq) with jack detection
	  sony-assamd	Sony ASSAMD
	  ultra		Samsung Q1 Ultra Vista model
	  lenovo-3000	Lenovo 3000 y410
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC267/268
	  quanta-il1	Quanta IL1 mini-notebook
	  3stack	3-stack model
	  toshiba	Toshiba A205
	  acer		Acer laptops
	  dell		Dell OEM laptops (Vostro 1200)
	  zepto		Zepto laptops
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC269
	  basic		Basic preset

	ALC662/663
	  3stack-dig	3-stack (2-channel) with SPDIF
	  3stack-6ch	 3-stack (6-channel)
	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
	  6stack-dig	 6-stack with SPDIF
	  lenovo-101e	 Lenovo laptop
	  eeepc-p701	ASUS Eeepc P701
	  eeepc-ep20	ASUS Eeepc EP20
	  m51va		ASUS M51VA
	  g71v		ASUS G71V
	  h13		ASUS H13
	  g50v		ASUS G50V
	  auto		auto-config reading BIOS (default)

	ALC882/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  arima		Arima W820Di1
	  targa		Targa T8, MSI-1049 T8
	  asus-a7j	ASUS A7J
	  asus-a7m	ASUS A7M
	  macpro	MacPro support
	  mbp3		Macbook Pro rev3
	  imac24	iMac 24'' with jack detection
	  w2jc		ASUS W2JC
	  auto		auto-config reading BIOS (default)

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
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  clevo-m720	Clevo M720 laptop series
	  fujitsu-pi2515 Fujitsu AMILO Pi2515
	  auto		auto-config reading BIOS (default)

	ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  toshiba	Toshiba laptop support
	  asus		Asus laptop support
	  asus-laptop	ASUS F2/F3 laptops
	  auto		auto-config reading BIOS (default)

	ALC861VD/660VD
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF OUT
	  6stack-dig	6-jack with SPDIF OUT
	  3stack-660	3-jack (for ALC660VD)
	  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
	  lenovo	Lenovo 3000 C200
	  dallas	Dallas laptops
	  hp		HP TX1000
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1882
	  3stack	3-stack mode (default)
	  6stack	6-stack mode

	AD1884A / AD1883 / AD1984A / AD1984B
	  desktop	3-stack desktop (default)
	  laptop	laptop with HP jack sensing
	  mobile	mobile devices with HP jack sensing
	  thinkpad	Lenovo Thinkpad X300

	AD1884
	  N/A

	AD1981
	  basic		3-jack (default)
	  hp		HP nx6320
	  thinkpad	Lenovo Thinkpad T60/X60/Z60
	  toshiba	Toshiba U205

	AD1983
	  N/A

	AD1984
	  basic		default configuration
	  thinkpad	Lenovo Thinkpad T61/X61
	  dell		Dell T3400

	AD1986A
	  6stack	6-jack, separate surrounds (default)
	  3stack	3-stack, shared surrounds
	  laptop	2-channel only (FSC V2060, Samsung M50)
	  laptop-eapd	2-channel with EAPD (Samsung R65, ASUS A6J)
	  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
	  ultra		2-channel with EAPD (Samsung Ultra tablet PC)

	AD1988/AD1988B/AD1989A/AD1989B
	  6stack	6-jack
	  6stack-dig	ditto with SPDIF
	  3stack	3-jack
	  3stack-dig	ditto with SPDIF
	  laptop	3-jack with hp-jack automute
	  laptop-dig	ditto with SPDIF
	  auto		auto-config reading BIOS (default)
	
	Conexant 5045
	  laptop-hpsense    Laptop with HP sense (old model laptop)
	  laptop-micsense   Laptop with Mic sense (old model fujitsu)
	  laptop-hpmicsense Laptop with HP and Mic senses
	  benq		Benq R55E
	  test		for testing/debugging purpose, almost all controls
			can be adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y

	Conexant 5047
	  laptop	Basic Laptop config 
	  laptop-hp	Laptop config for some HP models (subdevice 30A5)
	  laptop-eapd	Laptop config with EAPD support
	  test		for testing/debugging purpose, almost all controls
			can be adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y

	Conexant 5051
	  laptop	Basic Laptop config (default)
	  hp		HP Spartan laptop

	STAC9200
	  ref		Reference board
	  dell-d21	Dell (unknown)
	  dell-d22	Dell (unknown)
	  dell-d23	Dell (unknown)
	  dell-m21	Dell Inspiron 630m, Dell Inspiron 640m
	  dell-m22	Dell Latitude D620, Dell Latitude D820
	  dell-m23	Dell XPS M1710, Dell Precision M90
	  dell-m24	Dell Latitude 120L
	  dell-m25	Dell Inspiron E1505n
	  dell-m26	Dell Inspiron 1501
	  dell-m27	Dell Inspiron E1705/9400
	  gateway	Gateway laptops with EAPD control
	  panasonic	Panasonic CF-74

	STAC9205/9254
	  ref		Reference board
	  dell-m42	Dell (unknown)
	  dell-m43	Dell Precision
	  dell-m44	Dell Inspiron

	STAC9220/9221
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF
	  intel-mac-v1	Intel Mac Type 1
	  intel-mac-v2	Intel Mac Type 2
	  intel-mac-v3	Intel Mac Type 3
	  intel-mac-v4	Intel Mac Type 4
	  intel-mac-v5	Intel Mac Type 5
	  macmini	Intel Mac Mini (equivalent with type 3)
	  macbook	Intel Mac Book (eq. type 5)
	  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
	  macbook-pro	Intel Mac Book Pro 2nd generation (eq. type 3)
	  imac-intel	Intel iMac (eq. type 2)
	  imac-intel-20	Intel iMac (newer version) (eq. type 3)
	  dell-d81	Dell (unknown)
	  dell-d82	Dell (unknown)
	  dell-m81	Dell (unknown)
	  dell-m82	Dell XPS M1210

	STAC9202/9250/9251
	  ref		Reference board, base config
	  m2-2		Some Gateway MX series laptops
	  m6		Some Gateway NX series laptops
	  pa6		Gateway NX860 series

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup

	STAC92HD71B*
	  ref		Reference board
	  dell-m4-1	Dell desktops
	  dell-m4-2	Dell desktops

	STAC92HD73*
	  ref		Reference board
	  dell-m6	Dell desktops

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    power_save and power_save_controller options are for power-saving
    mode.  See powersave.txt for details.

    Note 2: If you get click noises on output, try the module option
	    position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
	    register value without FIFO size correction as the current
	    DMA pointer.  position_fix=2 will make the driver to use
	    the position buffer instead of reading SD_LPIB register.
	    (Usually SD_LPLIB register is more accurate than the
	    position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    MORE NOTES ON "azx_get_response timeout" PROBLEMS:
    On some hardwares, you may need to add a proper probe_mask option
    to avoid the "azx_get_response timeout" problem above, instead.
    This occurs when the access to non-existing or non-working codec slot
    (likely a modem one) causes a stall of the communication via HD-audio
    bus.  You can see which codec slots are probed by enabling
    CONFIG_SND_DEBUG_VERBOSE, or simply from the file name of the codec
    proc files.  Then limit the slots to probe by probe_mask option.
    For example, probe_mask=1 means to probe only the first slot, and
    probe_mask=4 means only the third slot.

    The power-management is supported.
```
Open **/etc/modprobe.d/alsa-base.conf** up in a text editor with superuser permissions, such as by running '**gksu gedit /etc/modprobe.d/alsa-base.conf**' in a run box (Alt+F2), or '**kdesudo kate /etc/modprobe.d/alsa-base.conf**' if running Kubuntu. Then add a line to the bottom of that file as below, replacing *<model>* with a model that was listed as available to your chipset.
```
options snd-hda-intel model=*<model>*
```
As my example of '**aplay -l**' showed earlier, I have a soundcard with an **ALC883** chipset. As such, on my *Acer* laptop I made it '**model=*acer***', since the name of that model was something of an obvious giveaway.

Note that **acer** was one of the available **ALC883** models! Which chipset you have takes priority of any hint you may find in the model names. If you have an **ASUS ImaginaryModel 9999** laptop with an **ALC883** chipset, you'll quickly notice that there are no **asus** models available for that chipset. "*But, there's an **asus** available in **ALC[COLOR="Red"]861[/COLOR]**; I'll use that instead!*", you may think, and you'll eventually only solve your issues by pure luck and chance.

In my case, after that it worked; sound from both speakers and headphone jack detection. Refer to the list entries for your chipset to see which models are available to you. Obviously, if one strikes you as immediately suspicious (Acer and **acer**, Dell and **dell**, number of jacks, SPDIF or no SPDIF, etc), that could just be the one, **if available in your chipset's list**. Try one, then do a complete system restart to see if it worked.


[INDENT]**Note:** The following *may* be possible if you don't want to reboot (who does?). Omit the 'pulseaudio' lines if you're not using that. You're not if you're running Kubuntu.
```
$ pulseaudio -k
$ sudo service alsa-utils stop
$ sudo modprobe -r snd_hda_intel
$ sudo modprobe snd-hda-intel
$ sudo service alsa-utils start
$ pulseaudio -D
```
All in one line, for your copy/paste pleasure:
**pulseaudio -k && sudo service alsa-utils stop && sudo modprobe -r snd_hda_intel && sudo modprobe snd-hda-intel && sudo service alsa-utils start && pulseaudio -D**[/INDENT]


Start playing something, connect/disconnect headphones, etc. If the model was not appropriate for your card, you may even have introduced issues you didn't have before, *so give it a good and thorough testing*. Open up a mixer (**alsamixer**, **gnome-alsamixer**, **kmix**, etc) and pay special attention to muted channels (as always) and *options*. Some chipset models have options such as Headphone Jack Detection, and if your original problem was that your speakers kept on blaring even though you had headphones plugged in, you could have just "**unlocked**" that setting, and you'd just need to realize it's there, find it, and enable it.

If it didn't work, change it to something else from that list and give it another go.


**Failing THAT too**, your best bet would be to replace ALSA with [OSS 4](http://en.wikipedia.org/wiki/Open_Sound_System). It is now licensed under the GPL, so if you place great weight on freedom then you're no longer barred by it being binary only. It's not old and deprecated either, contrary to common misconception; the old OSS3 included in the kernel, however, is. That is essentially a development snapshot from 10 years ago, and OSS has been (commercially) developed ever since.

Unlike the Linux-specific ALSA, it's a portable architecture, "available in 11 major Unix-like operating systems"[SIZE="1"][[1]](http://en.wikipedia.org/wiki/Open_Sound_System)[/SIZE]. As such, an application written to use OSS can be recompiled to work with Solaris and BSD-based systems, whereas ALSA is still Advanced ***Linux*** Sound Architecture.

There's a guide [here](http://ubuntuforums.org/showthread.php?t=780961) on how to install it, and an interesting developer journal entry on the subject [here](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html). Oh, and an older blog post by the maintainer of OSS [here](http://4front-tech.com/hannublog/?p=5), though written before it was licensed under the GPL.

Do note, OSS does not (at the time of writing) work with Pulseaudio.

---

### Post by RamenBooko on 2008-07-30
Thanks, I had:

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

This is on a Dell E520, and adding the model=dell-3stack, then restarting alsa-utils and changing the master volum withing alsamixer fixed it.

Thanks a lot!

---

### Post by Tair on 2008-09-12
Thanks, Zorael! It works for me as well! I have Lenovo 3000 N200. As output for "aplay -l" I had:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I've replaced <model> with "lenovo", so:
```

options snd-hda-intel model=lenovo

```
have restarted my computer, and yahoo now I have sound!

---

### Post by dwp0980 on 2008-10-05
Hi,

I have a Sony Vaio AR61E which I'm loving under Ubuntu Intrepid (after some teething problems).

However, I'm still having some issues with the sound. I've searched high and low, and it would appear the alsa-base option is vaio-ar.  With this option, and also with 'auto' it works fine through the internal speakers, but the headphone socket doesn't seem to work and also I cannot get sound through the HDMI out.  I've tried all sorts of different combinations.

Any help gratefully received.  Output of _aplay -l_ below

```
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

---

### Post by markbuntu on 2008-10-05
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

There are more links and stuff here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by andresmh on 2008-12-24
What settings do I use if my card is not exactly listed but it's close? This is what aplay -l returns:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Zorael on 2008-12-24
> **andresmh said:**
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Experiment with what's available in the AD198**1**, AD198**4**, AD198**6A** and AD198**8** sections, I'd say. If anything strikes you as immediately matching, try that first.

---

### Post by Zorael on 2008-12-24
Updated (copy/pasted) the model list from the documentation of the current Intrepid version of alsa-base (1.0.17.dfsg-2ubuntu1). Also reworded some bits, added to others, and did a bit of cleanup.

---

### Post by Athena1 on 2009-01-23
Hii....

When I tested my laptop got below info...

card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ATI SB/HDMI is not listed ... what should i do?? Can anyone please help me fix this????

---

### Post by kesar on 2009-02-17
I have intel D945gccr mobo with realtek alc883 onboard audio. But I am not able to hear any sound.
the commands gave following results:

user1@user1-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Set [SSS USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0










user1@user1-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)












lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device d605
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at a3100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by jeremyjjbrown on 2009-04-04
Thanks Zorael,

That worked great. Seams my hardware was just improperly detected.

---

### Post by brianho on 2010-06-29
Hi im new to Ubuntu and Im not getting sounds from my speakers but i do get sound from my headphone jack
I own a Toshiba satellite U205-S5021

$ aplay -l 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0003
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at ffd80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at cff8 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at ffd40000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Toshiba America Info Systems Device 0003
    Flags: bus master, fast devsel, latency 0
    Memory at ffc80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at ffd3c000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: ffa00000-ffafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at cf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at cf60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at cf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at cf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffd3bc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: ff900000-ff9fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at afa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation Device 1040
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at ffaff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at ff9ff000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at bf40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 168, IRQ 21
    Memory at ff900000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
    Memory window 0: 40000000-43fff000 (prefetchable)
    Memory window 1: 44000000-47fff000
    I/O window 0: 0000b000-0000b0ff
    I/O window 1: 0000b400-0000b4ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at ff9fe800 (32-bit, non-prefetchable) [size=2K]
    Memory at ff9f8000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at ff9fd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at ff9fe700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci


i've already tried adding : toshiba , thinkpad , basic and hp      to the line
options snd-hda-intel model=<model>

with no luck
Any help please?
thank you

---

