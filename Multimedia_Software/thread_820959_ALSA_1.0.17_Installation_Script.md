---
title: "ALSA 1.0.17 Installation Script"
date: 2008-06-06
forum: Multimedia Software
---

### Post by Yellow Pasque on 2008-06-06
soundcheck is now writing and maintaining the ALSA 1.0.18 update script **see: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)**

---

### Post by Yellow Pasque on 2008-06-06
[SIZE="4"]**Configuring alsa-base**[/SIZE]

**To identify your codec:**
```
aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```

Now, open /etc/modprobe.d/alsa-base with the following command:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Modify or add this line with *modelname* = to the appropriate model name from the list below:
```
options snd-hda-intel model=*modelname*
```

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
	  lenovo	Lenovo 3000 C200 & ASUS X20SG, ASUS U1E
	  dallas	Dallas laptops, Toshiba satellite L30-106
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

---

### Post by jocko on 2008-06-07
> **Temüjin said:**
> I would also like to get another alsa-base list going like the one I linked to in my original post. It seems the OP of that thread is no longer active on these forums.

You already have that list in alsa-driver-1.0.17rc1/alsa-kernel/Documentation/ALSA-Configuration.txt in whatever directory your script unpacks the sources.

---

### Post by Yellow Pasque on 2008-06-09
An ASUS X20SG owner has reported that the lenovo modelname worked for him with his Realtek ALC660VD: [http://ubuntuforums.org/showthread.php?p=5137022#post5137022](http://ubuntuforums.org/showthread.php?p=5137022#post5137022)

I added it to the list.

---

### Post by copyrightake on 2008-06-10
Thanks for the script but i'm having some problems.

During the first script it fails during one of the ./configure parts

```
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
now reboot your machine, and run alsa_2
```


I'm using Ubuntu 8.04 64bit and I have tried fixing this problem by installing libasound2-dev and even lib32asound2-dev, is there anything else I can try to get this working?

---

### Post by revol on 2008-06-10
I think there's an error inside alsa_1.sh script. I've modified (not verified yet) this script and uploaded...

---

### Post by freakwillie on 2008-06-11
Hello,

First of all I would like to thank you for the effort. Its being a hard time for me trying to upgrade ALSA. 

I did as you wrote, but when I type 

```
cat /proc/asound/version
```

I still get the following output:

```
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May 29 2008 for kernel 2.6.24-18-generic (SMP).
```

Any suggestions?

:KS[Edit]

The weird thing is that when I look into the alsa mixer it accuses the 1.0.7rc1 version. But, if I press F2 I get the following: 

[IMG]http://img174.imageshack.us/img174/402/screenshotwilliewillielnk6.png[/IMG]

Note that while in the top it says 1.0.7rc1 it still goes 1.0.6 in the blue screen. Why is that?

---

### Post by freakwillie on 2008-06-14
Looks like the alsa-driver isn't upgrading. 

Here's the alsa-info.sh output: [http://pastebin.ca/1047467](http://pastebin.ca/1047467)

---

### Post by Yellow Pasque on 2008-06-17
Updated for ALSA 1.0.17rc2. I added alsa-lib too.

---

### Post by Yellow Pasque on 2008-06-19
Ok, I connected my backup hard disk yesterday and tested this. It works! (I use OSS4 on my main disk.)

---

### Post by freakwillie on 2008-06-20
I've solved my problem. I compiled a new kernel without the alsa module.

---

### Post by Yellow Pasque on 2008-06-23
> Using Toshiba satellite L30-106 with aplay -l:

card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]

Started with no sound whatsoever, then tried:

options snd-hda-intel model=3stack

This got my built in speakers working, however, not the headphones. I tried to unmute the headphones in alsamixer, however, I could not raise the level on this channel - stuck at zero. Eventually I tried (rather speculative as mine is a Toshiba):

options snd-hda-intel model=dallas

This worked, I now have in built speakers and headphones (had to unmute headphones though).

Thanks to jamesetch for the feedback. Keep it coming.

---

### Post by Yellow Pasque on 2008-06-28
Updated for ALSA driver 1.0.17 Release Candidate 3

Updates:

```
Sound Core

    configure: Add GFP_DMA32 check for 2.4 kernels 
    configure: Added page_to_pfn check for older kernels 
    Fix PPC platform detection and mod-deps condition optimization 
    Release v1.0.17rc3 

ALSA Core

    configure: Add GFP_DMA32 check for 2.4 kernels 
    sound: Add upper_32_bits() for older kernels 
    GFP_DMA32 check - change from GFP_DMA to 0 for kernels not supporting GFP_DMA32 flag 
    configure: Added page_to_pfn check for older kernels 
    alsa: add annotations to bitwise type snd_pcm_hw_param_t 
    [ALSA] Revert "alsa: add annotations to bitwise type snd_pcm_hw_param_t" 

PCM Midlevel

    alsa: add annotations to bitwise type snd_pcm_hw_param_t 
    [ALSA] Revert "alsa: add annotations to bitwise type snd_pcm_hw_param_t" 

/soc/codecs/Makefile

    ALSA: ASoC: Add AK4535 driver 

ALSA Version

    ALSA: Release v1.0.17rc3 

AZT3328 driver

    ALSA: PCI168 snd-azt3328: some more fixups 

Asihpi driver

    asihpi: Meter control return peak. 
    asihpi: Disable S24_3LE incompatible with 2^N buffer size. 

CA0106 driver

    ALSA: ca0106 - Add entry for another MSI K8N Diamond MB 

CMI8788 (Oxygen) driver

    sound: oxygen: fix NULL pointer dereference when loading snd-oxygen 

EMU10K1/EMU10K2 driver

    ALSA: emu10k1 - fix possible memory leak in memory allocation routines 
    ALSA: emu10k1 - simplify the last fix 

Emagic Audiowerk 2

    ALSA: aw2 - Fix Oops at initialization 

HDA Codec driver

    ALSA: hda - Fix wrong volumes in AD1988 auto-probe mode 
    ALSA: hda - Fix digital converter proc output 
    ALSA: hda - Added model selection for iMac 24" 
    ALSA: hda - Added SSID for 'Fujitsu Siemens Amilo M1451G' laptop 
    ALSA: hda - Add MacBook 3.1 support 
    ALSA: hda - disable amp override on non-HP machines 

HDA generic driver

    ALSA: hda - Fix digital converter proc output 

SB drivers

    ALSA: sb - Fix wrong assertions 

SoC Codec AK4535

    ALSA: ASoC: Add AK4535 driver 

SoC Codec TLV320AIC3X

    ALSA: ASoC: TLV320AIC3X: Use register modifier widget for mic bias 
    ALSA: ASoC: TLV320AIC3X: Modify only interface related bits in aic3x_set_dai_fmt 
    ALSA: ASoC: TLV320AIC3X: Add support for digital microphone input 

SoC Codec WM8510

    ALSA: ASoC: Replace custom debug macros with pr_ equivalents 

SoC Codec WM8731

    ALSA: ASoC: Replace custom debug macros with pr_ equivalents 

SoC Codec WM8750

    ALSA: ASoC: Replace custom debug macros with pr_ equivalents 

SoC Codec WM8753

    ALSA: ASoC: Replace custom debug macros with pr_ equivalents 

SoC Dynamic Audio Power Management

    ALSA: ASoC: Add support for generic DAPM register modifier widget 

SoC Freescale

    ALSA: Fix register programming in Freescale MPC8610 HPCD sound driver 

SoC Layer

    ALSA: ASoC: fix PM=n build 
    ALSA: ASoC: Add AK4535 driver 

SoC Texas Instruments OMAP

    ALSA: ASoC: Add digital mic configuration to N810 machine driver 

Trident driver

    ALSA: trident - pause s/pdif output 

Utils

    mod-deps: fix PPC (and maybe other) dependencies problem using right brackets in acinclude.m4 
    Fix PPC platform detection and mod-deps condition optimization 

YMFPCI driver

    ALSA: ymfpci - fix initial volume for 44.1kHz output 

Detailed changelog between 1.0.17rc2 and 1.0.17rc3 releases
alsa-driver
Sound Core

    - configure: Add GFP_DMA32 check for 2.4 kernels 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - configure: Added page_to_pfn check for older kernels 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - Fix PPC platform detection and mod-deps condition optimization 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - Release v1.0.17rc3 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

ALSA Core

    - configure: Add GFP_DMA32 check for 2.4 kernels 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - sound: Add upper_32_bits() for older kernels 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    - GFP_DMA32 check - change from GFP_DMA to 0 for kernels not supporting GFP_DMA32 flag 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - configure: Added page_to_pfn check for older kernels 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - alsa: add annotations to bitwise type snd_pcm_hw_param_t 
    Fully half of all alsa sparse warnings are from snd_pcm_hw_param_t degrading 
    to integer type, this goes a long way towards eliminating them. 
    Signed-off-by: Harvey Harrison <harvey.harrison@gmail.com> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - [ALSA] Revert "alsa: add annotations to bitwise type snd_pcm_hw_param_t" 
    This reverts commit 36b34d2437104f323e09d7c6af6451d3c0b9c0cd. 
    From: Al Viro <viro@ZenIV.linux.org.uk> 
    WIW, *all* this stuff is not bitwise at all. For crying out loud, half 
    of these types are routinely used as array indices and loop variables... 
    If anything, we want a different set of allowed operations - subtraction 
    between elements of type (yielding integer), addition/subtraction of 
    integer types not bigger than ours (yielding our type), comparisons, 
    assignments (=, +=, -=, passing to function as argument, return from 
    function, initializers) and second/third arguments in ?:. With 0 *not* 
    being allowed as a constant of such type. 
    It's not bitwise; we may use the same infrastructure in sparse, but it 
    should be a separate class of types (__attribute__((affine))). 
    dma_addr_t is another candidate for the same treatment, but there we'll 
    need helpers for conversions to hw-acceptable form (dma_to_le32(), etc.) 
    and gradual conversion of drivers. 
    ALSA ones and pm mess are absolutely straightforward cases, though. 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

PCM Midlevel

    - alsa: add annotations to bitwise type snd_pcm_hw_param_t 
    Fully half of all alsa sparse warnings are from snd_pcm_hw_param_t degrading 
    to integer type, this goes a long way towards eliminating them. 
    Signed-off-by: Harvey Harrison <harvey.harrison@gmail.com> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - [ALSA] Revert "alsa: add annotations to bitwise type snd_pcm_hw_param_t" 
    This reverts commit 36b34d2437104f323e09d7c6af6451d3c0b9c0cd. 
    From: Al Viro <viro@ZenIV.linux.org.uk> 
    WIW, *all* this stuff is not bitwise at all. For crying out loud, half 
    of these types are routinely used as array indices and loop variables... 
    If anything, we want a different set of allowed operations - subtraction 
    between elements of type (yielding integer), addition/subtraction of 
    integer types not bigger than ours (yielding our type), comparisons, 
    assignments (=, +=, -=, passing to function as argument, return from 
    function, initializers) and second/third arguments in ?:. With 0 *not* 
    being allowed as a constant of such type. 
    It's not bitwise; we may use the same infrastructure in sparse, but it 
    should be a separate class of types (__attribute__((affine))). 
    dma_addr_t is another candidate for the same treatment, but there we'll 
    need helpers for conversions to hw-acceptable form (dma_to_le32(), etc.) 
    and gradual conversion of drivers. 
    ALSA ones and pm mess are absolutely straightforward cases, though. 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

/soc/codecs/Makefile

    - ALSA: ASoC: Add AK4535 driver 
    The AK4535 codec is included in some HP iPAQ systems. 
    This driver was originally written by Richard Purdie and with some bug 
    fixes from Milan Plzik. While out of tree it has also had some 
    mechanical updates for new APIs and current best practices from Liam 
    Girdwood, Graeme Gregory and Mark Brown. 
    Signed-off-by: Richard Purdie <richard@openedhand.com> 
    Signed-off-by: Milan Plzik <milan.plzik@gmail.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Graeme Gregory <gg@opensource.wolfsonmicro.com> 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

ALSA Version

    - ALSA: Release v1.0.17rc3 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

AZT3328 driver

    - ALSA: PCI168 snd-azt3328: some more fixups 
    - fix problem with codec register 0x6a being write-only 
    by adding a software shadow register 
    (caused annoying noise after module loading due to _toggling_ 
    between gameport and audio bits instead of configuring them properly) 
    - rename several "Wave" mixer controls to "PCM", since this is 
    what Wine and several other apps are looking for (IOW, _requiring_) 
    and this is what AC97 specs use as naming, too, 
    thus I'd guess it's what these controls are 
    - cleanup, small optimizations 
    Signed-off-by: Andreas Mohr <andi@lisas.de> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

Asihpi driver

    - asihpi: Meter control return peak. 
    Use Peak meter instead of Rms meter because it is supported by all card 
    families. 
    Minor checkpatch cleanups. 
    Signed-off-by: Eliot Blennerhassett <linux@audioscience.com> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - asihpi: Disable S24_3LE incompatible with 2^N buffer size. 
    Signed-off-by: Eliot Blennerhassett <eblennerhassett@audioscience.com> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

CA0106 driver

    - ALSA: ca0106 - Add entry for another MSI K8N Diamond MB 
    Added an entry for another MSI K8N Diamond mobo with SSID 1102:1009. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

CMI8788 (Oxygen) driver

    - sound: oxygen: fix NULL pointer dereference when loading snd-oxygen 
    Check that model->control_filter is set before trying to call it. 
    Signed-off-by: Clemens Ladisch <clemens@ladisch.de> 

EMU10K1/EMU10K2 driver

    - ALSA: emu10k1 - fix possible memory leak in memory allocation routines 
    The leak was introduced in "[ALSA] emu10k1 - simplify page allocation 
    for synth" commit. 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: emu10k1 - simplify the last fix 
    Clean up the previous commit for fixing memory leaks. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 

Emagic Audiowerk 2

    - ALSA: aw2 - Fix Oops at initialization 
    The irq handler may be called before the proper initialization of hardware. 
    Call snd_aw2_saa7146_setup() before the irq handler registration. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 

HDA Codec driver

    - ALSA: hda - Fix wrong volumes in AD1988 auto-probe mode 
    Don't create mixer volume elements for Headphone and Speaker if they 
    use the same DAC as normal line-outs on AD1988. Otherwise the amp 
    value gets screwed up, e.g. 
    https://bugzilla.novell.com/show_bug.cgi?id=398255 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: hda - Fix digital converter proc output 
    AC_VERB_GET_DIGI_CONVERT_2 isn't actually implemented but reserved. 
    The whole SIC bits are returned from DIGI_CONVERT_1. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: hda - Added model selection for iMac 24" 
    Added the SSID of a known iMac 24" to automatically use 
    ALC885_IMAC24 quirk. 
    Signed-off-by: Travis Place <wishie@wishie.net> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: hda - Added SSID for 'Fujitsu Siemens Amilo M1451G' laptop 
    Add the SSID for the "Fujitsu Siemens Amilo M1451G" laptop to 
    patch_realtek.c , so that it uses ALC880_FUJITSU by default. 
    Signed-off-by: Travis Place <wishie@wishie.net> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: hda - Add MacBook 3.1 support 
    MacBook 3.1 is compatible with model=mbp3. 
    Added the codec SSID 10b6:3600. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: hda - disable amp override on non-HP machines 
    Some machines with Cx5045 seem to have no problem with the volume 
    over 0dB on NID 0x17. Disable amp overrides for other devices but HP. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

HDA generic driver

    - ALSA: hda - Fix digital converter proc output 
    AC_VERB_GET_DIGI_CONVERT_2 isn't actually implemented but reserved. 
    The whole SIC bits are returned from DIGI_CONVERT_1. 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SB drivers

    - ALSA: sb - Fix wrong assertions 
    snd_assert() in save_mixer() and restore_mixer() in sb_mixer.c is 
    just wrong. The debug code wasn't tested at all, obviously... 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 

SoC Codec AK4535

    - ALSA: ASoC: Add AK4535 driver 
    The AK4535 codec is included in some HP iPAQ systems. 
    This driver was originally written by Richard Purdie and with some bug 
    fixes from Milan Plzik. While out of tree it has also had some 
    mechanical updates for new APIs and current best practices from Liam 
    Girdwood, Graeme Gregory and Mark Brown. 
    Signed-off-by: Richard Purdie <richard@openedhand.com> 
    Signed-off-by: Milan Plzik <milan.plzik@gmail.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Graeme Gregory <gg@opensource.wolfsonmicro.com> 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Codec TLV320AIC3X

    - ALSA: ASoC: TLV320AIC3X: Use register modifier widget for mic bias 
    Signed-off-by: Jarkko Nikula <jarkko.nikula@nokia.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: ASoC: TLV320AIC3X: Modify only interface related bits in aic3x_set_dai_fmt 
    Those two serial data interface control register bits have also other 
    functions and they can be set before aic3x_set_dai_fmt is called. 
    Signed-off-by: Jarkko Nikula <jarkko.nikula@nokia.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: ASoC: TLV320AIC3X: Add support for digital microphone input 
    AIC33 and AIC34 codecs in TLV320AIC3x family support digital microphone 
    input. When enabled, the codec ADC takes bitstream input to low-pass 
    filter from GPIO2 instead of its own delta-sigma modulator while providing 
    oversampling clock through GPIO1. 
    Signed-off-by: Jarkko Nikula <jarkko.nikula@nokia.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Codec WM8510

    - ALSA: ASoC: Replace custom debug macros with pr_ equivalents 
    Several ASoC codec drivers use custom macros equivalent to the standard 
    pr_ macros, most of which are not actually used. Replace these custom 
    macros with the standard ones. 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Codec WM8731

    - ALSA: ASoC: Replace custom debug macros with pr_ equivalents 
    Several ASoC codec drivers use custom macros equivalent to the standard 
    pr_ macros, most of which are not actually used. Replace these custom 
    macros with the standard ones. 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Codec WM8750

    - ALSA: ASoC: Replace custom debug macros with pr_ equivalents 
    Several ASoC codec drivers use custom macros equivalent to the standard 
    pr_ macros, most of which are not actually used. Replace these custom 
    macros with the standard ones. 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Codec WM8753

    - ALSA: ASoC: Replace custom debug macros with pr_ equivalents 
    Several ASoC codec drivers use custom macros equivalent to the standard 
    pr_ macros, most of which are not actually used. Replace these custom 
    macros with the standard ones. 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Dynamic Audio Power Management

    - ALSA: ASoC: Add support for generic DAPM register modifier widget 
    This generic register modifier widget is for updating multiple codec 
    register bits at once when the widget changes its power state. 
    Signed-off-by: Jarkko Nikula <jarkko.nikula@nokia.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Freescale

    - ALSA: Fix register programming in Freescale MPC8610 HPCD sound driver 
    Fix the Freescale MPC8610 HPCD sound driver so that it programs the DMACR 
    and PMUXCR registers in the global utilities correctly. 
    Signed-off-by: Timur Tabi <timur@freescale.com> 
    Acked-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Layer

    - ALSA: ASoC: fix PM=n build 
    Fix sound/soc build failure when CONFIG_PM=n: 
    linux-next-20080617/sound/soc/soc-core.c:829: error: 'soc_resume_deferred' undeclared (first use in this function) 
    soc3.out:make[3]: *** [sound/soc/soc-core.o] Error 1 
    Signed-off-by: Randy Dunlap <randy.dunlap@oracle.com> 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - ALSA: ASoC: Add AK4535 driver 
    The AK4535 codec is included in some HP iPAQ systems. 
    This driver was originally written by Richard Purdie and with some bug 
    fixes from Milan Plzik. While out of tree it has also had some 
    mechanical updates for new APIs and current best practices from Liam 
    Girdwood, Graeme Gregory and Mark Brown. 
    Signed-off-by: Richard Purdie <richard@openedhand.com> 
    Signed-off-by: Milan Plzik <milan.plzik@gmail.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Graeme Gregory <gg@opensource.wolfsonmicro.com> 
    Signed-off-by: Mark Brown <broonie@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

SoC Texas Instruments OMAP

    - ALSA: ASoC: Add digital mic configuration to N810 machine driver 
    Signed-off-by: Jarkko Nikula <jarkko.nikula@nokia.com> 
    Signed-off-by: Liam Girdwood <lg@opensource.wolfsonmicro.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

Trident driver

    - ALSA: trident - pause s/pdif output 
    Stop the S/PDIF DMA engine and output when the device is told to pause. 
    It will keep on looping the current buffer contents if this isn't done. 
    Signed-off-by: Pierre Ossman <drzeus@drzeus.cx> 
    Tested-by: Rene Herman <rene.herman@gmail.com> 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

Utils

    - mod-deps: fix PPC (and maybe other) dependencies problem using right brackets in acinclude.m4 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
    - Fix PPC platform detection and mod-deps condition optimization 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 

YMFPCI driver

    - ALSA: ymfpci - fix initial volume for 44.1kHz output 
    YDSXGR_BUF441OUTVOL register isn't initialized properly. This may lead to 
    a silent output at full volume of unchanged "Wave Playback Volume". 
    http://bugzilla.kernel.org/show_bug.cgi?id=10963 
    Signed-off-by: Takashi Iwai <tiwai@suse.de> 
    Signed-off-by: Jaroslav Kysela <perex@perex.cz> 
```

---

### Post by Lonely_@ss on 2008-07-07
Please, help! I'm an Acer Aspire 6920G (laptop) owner. And I have no sound in Ubuntu HH since installation. I've tried A LOT OF SOLUTIONS (such as modifying alsa-base with models "acer, acer-aspire, laptop, auto", installing "kmix" and setting main channel to Surround, building various versions of ALSA manually and with autoscripts), but NOTHING helped me. No sound...All soundtests run without errors, but without sound too.

**aplay -l** returns 
"card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]"

**cat /proc/asound/card0/codec#* | grep Codec** returns
"Codec: Realtek ALC889
 Codec: Generic 11c1 ID 1040" (i consider the second line is modem)

I want to know, does ALSA support my laptop (audio)? 
Anybody here with the same laptop?

P.S.: sorry for my English.

---

### Post by Yellow Pasque on 2008-07-08
Lonely-@ss, click on the OSS4 Howto in my signature (another 6920 owner who got no sound from ALSA confirmed OSS4 works: [http://ubuntuforums.org/showpost.php?p=5131350&postcount=10](http://ubuntuforums.org/showpost.php?p=5131350&postcount=10) )

---

### Post by Lonely_@ss on 2008-07-08
Thanks, Temüjin!!!
I saw that post about OSS4 before, but I failed to install it properly that time. Now it worked! Only one problem - my laptop has Acer TubaBass technology (10watt subwoofer), which seems to be off in Ubuntu :(

PS: Offcourse, I wish to have sound with ALSA, so I'll keep trying, when new version arrives. But now I'm happy, listening The Dillinger Escape Plan :guitar: so thx you once more!

---

### Post by skinnie on 2008-07-08
Here alc268 on Hp DV9575Ep with 
```
options snd-hda-intel model=*auto*
```
It didn't work,the mute button was orange (mutted)
With 
```
options snd-hda-intel model=*hp*
```
it worked.
Although in first situation in the input divison of the mixer I had 2 inputs,what is cool,because I have the laptop mic and I can plug an external mic,and adjust both without switches.
Other thing as said before,when type
```
cat /proc/asound/version
```
it returns:
```
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).

```thanks for the scripts

---

### Post by karhulitos on 2008-07-09
Thank you for the scripts. I also wanted latest alsa hoping I could wake up my subwoofer & spdif on this Acer Aspire 7520G.

After the upgrade I still have alsa 1.0.16 ```
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).
```

Freakwillie told recompiling kernel will help. No way I'm doing that! Is upgrading alsa driver supported or what did I do wrong? The scripts both ran clean.

---

### Post by Nescafi on 2008-07-13
> **karhulitos said:**
> Thank you for the scripts. I also wanted latest alsa hoping I could wake up my subwoofer & spdif on this Acer Aspire 7520G.

After the upgrade I still have alsa 1.0.16 ```
~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).
```

Freakwillie told recompiling kernel will help. No way I'm doing that! Is upgrading alsa driver supported or what did I do wrong? The scripts both ran clean.

Hello, I had the same problem and I solved it !

The reason is that the ko modules are not actually installed in the /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver (check the version of the kernel you use).
I don't know why "make install" didn't work and am not able to fix it.

So i decided to install manually the modules myself. This is how I proceeded.
The driver must be correctly compiled before to do that.
```

# backup old modules (change kernel version matching your system of course)
mkdir ~/alsabackup
cp -r /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver ~/alsabackup

# this is my ugly trick to get the modules tree
mkdir ~/temp
     # go to the directory containing the driver sources you just compiled: 
cd /usr/src/alsa/alsa-driver-1.0.17rc3/
find ./ -name ''*.ko'' > ~/temp/listemodules
tar -cv -T ~/temp/listemodules -f ~/temp/alsa-driver-1.0.17rc3.tar
cd ~/temp
mkdir alsa-driver
cd alsa-driver
tar xvf ../alsa-driver-1.0.17rc3.tar

# à présent j'ai toute l'arborescence des modules dans ~/temp/alsa-driver
# remove all these buggy old modules !
sudo rm -fr /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver
# copy the new modules instead
sudo cp -r ~/temp/alsa-driver /lib/modules/2.6.24-19-generic/ubuntu/sound/
# reste plus qu'à redémarrer carrément le système
sudo reboot

```
This worked for me :)

---

### Post by karhulitos on 2008-07-14
> **Nescafi said:**
> This worked for me :)
Worked for me too, thanks!
Unfortunately I needed to fall back to 1.0.16 as the rc3 didn't bring me IEC958 nor the subwoofer I was hoping to find after upgrade. Also, for some strange reason all apps that had audio output set to "default" stopped working. They worked if I  changed them to "alsa" instead.

Anyways this is good info as I guess I'll be using this when next alsa version comes out. Thanks!

---

### Post by Yellow Pasque on 2008-07-14
Script update for ALSA 1.0.17 final release. Also added a line to decompress alsa-tools package so it can build and added alsa-oss package install.

---

### Post by freakwillie on 2008-07-16
> **Nescafi said:**
> Hello, I had the same problem and I solved it !

The reason is that the ko modules are not actually installed in the /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver (check the version of the kernel you use).
I don't know why "make install" didn't work and am not able to fix it.

So i decided to install manually the modules myself. This is how I proceeded.
The driver must be correctly compiled before to do that.
```

# backup old modules (change kernel version matching your system of course)
mkdir ~/alsabackup
cp -r /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver ~/alsabackup

# this is my ugly trick to get the modules tree
mkdir ~/temp
     # go to the directory containing the driver sources you just compiled: 
cd /usr/src/alsa/alsa-driver-1.0.17rc3/
find ./ -name ''*.ko'' > ~/temp/listemodules
tar -cv -T ~/temp/listemodules -f ~/temp/alsa-driver-1.0.17rc3.tar
mkdir alsa-driver
cd alsa-driver
tar xvf ../alsa-driver-1.0.17rc3.tar

# à présent j'ai toute l'arborescence des modules dans ~/temp/alsa-driver
# remove all these buggy old modules !
sudo rm -fr /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver
# copy the new modules instead
sudo cp -r ~/temp/alsa-driver /lib/modules/2.6.24-19-generic/ubuntu/sound/
# reste plus qu'à redémarrer carrément le système
sudo reboot

```
This worked for me :)

How nice you found a way of upgrading without recompiling the kernel, must try that next time.

---

### Post by isachan on 2008-07-16
Temüjin,
I may be missing something, but where is the latest Script update for ALSA 1.0.17 final release ?

Isao

---

### Post by Yellow Pasque on 2008-07-17
> **isachan said:**
> Temüjin,
I may be missing something, but where is the latest Script update for ALSA 1.0.17 final release ?

Isao
Attached to the first post. This forum allows you to edit attachments (although it resets the download/view count).

---

### Post by Hobo55 on 2008-07-21
>Now, open /etc/modprobe.d/alsa-base with the following command:
>```
gksudo gedit /etc/modprobe.d/alsa-base
```

>Modify or add this line with *modelname* = to the appropriate model >name from the list below:
>```
options snd-hda-intel model=*modelname*
```

This worked for my Asus F3Sr with the sound card ALC660-VD:

snd-hda-intel model=lenovo

Thank you kindly!:popcorn:

---

### Post by taylorg273 on 2008-07-24
I'm running Kubuntu 8.04 on a Lenovo Y410 laptop and this worked for me as well. I specified my model as 'lenovo-3000' in my alsa-base file and now have all my audio devices working except for the internal microphone. Big thanks!

---

### Post by fung on 2008-07-24
taylorg273 posted in another thread: > I successfully upgraded to Alsa 1.0.17 thanks to that thread. I used the scripts from post #1 and the configuration instructions in post #19. I now have all of the audio hardware working except for the internal mic (external mic jack is OK). The headphone jack works and even cuts off the speakers when the headphone plug is inserted.

The scripts will download and install everything needed from Alsa. There is one missing step in the instructions in post #19. The 'alsa-driver' directory needs to be created in your home directory for the remainder of the steps to work. This new driver has a model option for 'lenovo-3000' which is what I am now using in my /etc/modprobe.d/alsa-base.

Also just got the webcam working in Skype - too bad I don't have the mic to go with it.

I tried following the instructions from #19 but I got compile errors trying to "make" alsa-driver..

```
In file included from /home/david/Desktop/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/home/david/Desktop/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: In function &#8216;dapm_pop_time_store&#8217;:
/home/david/Desktop/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function &#8216;strict_strtoul&#8217;
make[3]: *** [/home/david/Desktop/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/david/Desktop/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/david/Desktop/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-20-generic'
make: *** [compile] Error 2

```

any ideas?

---

### Post by Vaphell on 2008-07-25
same here, got around it buy compiling another version - there are plenty available on alsa page.
i used 1.0.16, changed that damn patch_via.c and it compiled, make install and headphone jack is not dead anymore! :D

---

### Post by fung on 2008-07-25
I read somewhere (a quick Google search) that v1.0.17 doesn't compile with my kernel 2.6.24 so I had some time and decided to compile the latest kernel. I'll post the results after it's finished.

---

### Post by mocha on 2008-07-26
I looked this over a few times and did some searching and it seems like these scripts won't work properly.  Hardy changed the location where the alsa drivers are supposed to be installed, and Alsa doesn't install them in the proper place.

The Ubuntu wiki for intel hda says:

```
ubuntu default snd-hda-intel.ko location: /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko 

alsa 1.0.15's installation location: /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko 

so copy /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko to /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko . 

and put the modules/* in alsa's compile directory into /lib/modules/.../kernel/sound, you can use "find" to get their location. snd-hda-intel.ko snd-hwdep.ko snd.ko snd-mixer-oss.ko snd-page-alloc.ko snd-pcm.ko snd-pcm-oss.ko snd-rtctimer.ko snd-seq-device.ko snd-seq.ko snd-seq-midi-event.ko snd-seq-oss.ko snd-timer.ko
```

Another wiki page on the HP 2133 says:

```
The sound drivers install to the wrong place, so next you'll type the following commands. If you're using a different version of the kernel, put that in place of 2.6.24-19-generic: 
cd /lib/modules/2.6.24-19-generic
sudo cp -a kernel/sound/* ubuntu/sound/alsa-driver/
```

Including the OP's method, these are all conflicting methods.  So where are all the driver files supposed to go?  /lib/modules/2.6.22-14-generic/ubuntu/sound/alsa-driver/  or  /lib/modules/2.6.22-14-generic/kernel/sound/

???

---

### Post by Yellow Pasque on 2008-07-26
Yeah, the alsa_2.sh script is a remnant from the Feisty days and needs some work. On Ubuntu Hardy, the correct place for the alsa-driver directory is /lib/modules/`uname -r`/ubuntu/sound

I'm guessing the ..../kernel/sound/ dir is for modules built into the kernel.

---

### Post by mocha on 2008-07-26
> **Temüjin said:**
> Yeah, the alsa_2.sh script is a remnant from the Feisty days and needs some work. On Ubuntu Hardy, the correct place for the alsa-driver directory is /lib/modules/`uname -r`/ubuntu/sound

I'm guessing the ..../kernel/sound/ dir is for modules built into the kernel.

Okay great, well can you update the second script then before too many folks use it and wonder why it doesn't fully work?

---

### Post by Yellow Pasque on 2008-07-26
> **mocha said:**
> Okay great, well can you update the second script then before too many folks use it and wonder why it doesn't fully work?
The problem is that I like to test things myself before using them and I don't use ALSA. The thread and scripts would be better maintained by an actual ALSA user (hint, hint, el bow, el bow).

---

### Post by mocha on 2008-07-26
I'd love to try and install Alsa 1.0.17 because it has a bunch of fixes for the Intel HDA.  Maybe I'll get daring and go for it.  I'll post what I did if it's successful.

---

### Post by fung on 2008-07-26
What exactly does alsa_2.sh do anyway. I see it copies a bunch of stuff around but what does that mean?

---

### Post by Nescafi on 2008-07-26
Sorry I forgot a line in my instructions in the post #19. I edited the post so it is up to date.

---

### Post by msmr on 2008-07-27
...I'll do this in the morning.

also, the 1.0.17 packages aren't up in synpatic, so am I to just install them from source, and just go and try to find the config file and just add the options there?

---

### Post by jalanbuntu on 2008-07-29
> **Nescafi said:**
> Hello, I had the same problem and I solved it !

The reason is that the ko modules are not actually installed in the /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver (check the version of the kernel you use).
I don't know why "make install" didn't work and am not able to fix it.

So i decided to install manually the modules myself. This is how I proceeded.
The driver must be correctly compiled before to do that.
```

# backup old modules (change kernel version matching your system of course)
mkdir ~/alsabackup
cp -r /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver ~/alsabackup

# this is my ugly trick to get the modules tree
mkdir ~/temp
     # go to the directory containing the driver sources you just compiled: 
cd /usr/src/alsa/alsa-driver-1.0.17rc3/
find ./ -name ''*.ko'' > ~/temp/listemodules
tar -cv -T ~/temp/listemodules -f ~/temp/alsa-driver-1.0.17rc3.tar
cd ~/temp
mkdir alsa-driver
cd alsa-driver
tar xvf ../alsa-driver-1.0.17rc3.tar

# à présent j'ai toute l'arborescence des modules dans ~/temp/alsa-driver
# remove all these buggy old modules !
sudo rm -fr /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver
# copy the new modules instead
sudo cp -r ~/temp/alsa-driver /lib/modules/2.6.24-19-generic/ubuntu/sound/
# reste plus qu'à redémarrer carrément le système
sudo reboot

```
This worked for me :)

Thanks... this also worked for me using kernel 2.6.24-20-generic. But the sound comes from both laptop speakers and output jack. But its ok for now.... Finally... fhhiiyuuuuuhhh......

Thanks again :) :guitar:

---

### Post by Yellow Pasque on 2008-07-31
> **mocha said:**
> Okay great, well can you update the second script then before too many folks use it and wonder why it doesn't fully work?
Ok, I've updated the script and moved everything into one script (I'm not sure why the original author used 2 scripts).

---

### Post by Yellow Pasque on 2008-07-31
I tested this on my backup hard disk, which has Ubuntu 8.10 with a 2.26.x kernel. Now that I see the 2.6.24-20-generic /lib/modules is layed out a bit differently, I would like confirmation that this works.

Specifically, cat /proc/asound/version should return 1.0.17

---

### Post by fung on 2008-07-31
> **Temüjin said:**
> Specifically, cat /proc/asound/version should return 1.0.17

my cat /proc/asound/version still returns 1.0.16..

but I didn't delete anything since my last try with your previous script. Should I delete anything before trying the new script? Thanks

---

### Post by Yellow Pasque on 2008-07-31
Ok, I've modified the script to to default to Ubuntu 8.04 (kernel 2.6.24-x) directory structure. I've commented the commands for Ubuntu 8.10 (2.6.26-x) in case anyone needs them because the latest release (Alpha 3) still has ALSA 1.0.16.

Please let me know if there are any issues, especially ALSA reporting itself as an earlier version.

---

### Post by davedave on 2008-07-31
Thank you for the latest script update (alsa-1.0.17.sh), I now have sound on my ASUS M51Va-AS045G. The script alsa_1.sh did not work yesterday.

**lspci | grep Audio**
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

**cat /proc/asound/version** 
> Advanced Linux Sound Architecture Driver Version 1.0.17.
Compiled on Aug  1 2008 for kernel 2.6.24-19-generic (SMP).

---

### Post by fung on 2008-08-01
New script also works for me! thanks a lot.

lspci | grep Audio

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

cat /proc/asound/version 

```
Advanced Linux Sound Architecture Driver Version 1.0.17.
Compiled on Jul 31 2008 for kernel 2.6.24-20-generic (SMP).

```

Lenovo 3000 Y410

Edit:
Almost forgot, headphones work (for lenovo y410)! just make sure to add follow the directions in post 2 and add model=lenovo-3000 to: 
/etc/modprobe.d/alsa-base

---

### Post by itsjareds on 2008-08-01
My sound still doesn't work without headphones in. My sound card is an AD1986 Analog, and none of the models on the list worked :neutral:

I didn't install alsa because it seemed like it was already there..

All of my sound settings are unmuted and at full.

---

### Post by mocha on 2008-08-01
Thanks for the new script.  It makes sense now.  I'll try it later.

---

### Post by fung on 2008-08-01
> **itsjareds said:**
> My sound still doesn't work without headphones in. My sound card is an AD1986 Analog, and none of the models on the list worked :neutral:

I didn't install alsa because it seemed like it was already there..

All of my sound settings are unmuted and at full.

Use the script, it installs the latest version of alsa which may or may not include a new driver for your sound card.

---

### Post by chikletz on 2008-08-01
my laptop lenovo 3000 y410

and I already follow the step in post 1 and post 2,but my headphone still doesn't work..anyone can help me??

sory for my bad english

---

### Post by itsjareds on 2008-08-01
> **fung said:**
> Use the script, it installs the latest version of alsa which may or may not include a new driver for your sound card.

I installed it after I posted that, but I'm not sure it worked. The /etc/modprobe.d/alsa-base file still has the same information in it, even my added stuff. Does that mean it didn't update?

I'm not sure what model my computer is, but its a Lenovo Thinkcentre desktop.

---

### Post by jansaell on 2008-08-01
Just for your information, the sound on a ACER Aspire 8920 needs a small program called hda-verb that sends a command to the sound driver. I dont think it actually did need the new 1.0.17 driver, but I installed that anyway.

Read about it in my blog [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30")

---

### Post by jznomoney on 2008-08-03
I have a msi K9NGM4 V2.  I tried to install alsa in ubuntu.  It said it installed correctly. But when I restart I get no sound at all.  I tried setting it to auto and a couple other various models but it did not work.  My sound is using the nvida hda alc888.  It shows the correct model and everything in the alsamixer but it does not play sounds.  Even the sound panel in the preferences gives me an error when i select alsa as my default audio.  Can anyone help me?

---

### Post by Yellow Pasque on 2008-08-03
jznomoney, follow my OSS4 guide :)

---

### Post by jznomoney on 2008-08-05
i got it to work.  But to get it to work i have to type this in a terminal
sudo alsa force-reload

Everytime i restart the pc i have to type that to.
is there a way to make it do that when loading the os before gnome starts?

---

### Post by Fen_Star on 2008-08-05
> **Temüjin said:**
> but you can configure the script to your sound device using this: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
Please excuse my stupidity, I was able to find my device, but I don't know how to add it to the script.

(it is the C-Media one cm6501)

I tried to compile it without editing the edit but it doesn't seem to have worked. Alsamixer still doesn't work, I get the same funtion snd_ctrl_open failed for default: no such... error.

also, the cat /proc/asound... thing tells me there is no such file or directory.

Edit, never mind I substituted usb-audio for the Intel thing.
Edit: Still the same result...

---

### Post by jansaell on 2008-08-06
Hi there jznomoney.

You should be able to insert into then end of the file /etc/rc.local before the line with ***ext 0*** just as I did with the hda-verb program

---

### Post by cutOff on 2008-08-08
Thanks for the script. It worked like a charm on a 2.6.24-18-generic kernel. My soundcard is:

> 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 009f
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 19
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


Only needed to introduce the following line in /etc/modprobe.d/alsa-base

> options snd-hda-intel model=acer


Thanks again for the script.

---

### Post by silentb on 2008-08-08
There is a *.deb package of ALSA 1.0.17 available at

-> [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

which works great for me. :)

---

### Post by roy1980 on 2008-08-14
Temüjin, you are a genius!

I just bought an Aspire 8920G (with the Ati card), and your instructions worked flawlessly.

This just proves how incredibly helpful the ubuntu community is.

Sir, I salute you. 

Cheers

Roy:guitar:

---

### Post by Jack the R on 2008-08-15
For the Asus R1E the lines - 

options snd-hda-intel model=asus

and 

options snd-hda-intel model=auto

work.

---

### Post by Buster222 on 2008-08-16
I ran the script and after reboot KInfoCenter shows that ALSA 1.0.17 has been installed. However, I do not get sound from the card using Audicity. My machine has a 64-bit AMD and my sound card is a M-Audio Delta 66 rev. E. The built-in sound device is dissabled in BIOS, so the only active card is the Delta 66. The bar graphs in Envey24Control moves accoring to the amplitude of the music, so the card "seems to work", but I still get no sound from the card. 

Two questions:

1) In the script, should I modify the following line?:
./configure --with-cards=hda-intel --prefix=/usr 

2) In /etc/modprobe.d/alsa-base, what should the line 
options snd-hda-intel model=modelname 
read? model=maudio?

Here is the information from KInfoCenter (should it say "emulation code"?):

Sound Driver:3.8.1a-980706 (ALSA v1.0.17) emulation code)
Kernel Linux name 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Config options 0

Installed drivers:
Type 10:ALSA emulation

Card config:
M Audio Delta 66 at 0x8000, irq 17

Audio devices:
0:ICE1712 multi (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

;ixers:
0:ICE1712 - multitrack

---

### Post by Yellow Pasque on 2008-08-16
Change
```
./configure --with-cards=hda-intel --prefix=/usr
```
--->
```
./configure --with-cards=ice1712 --prefix=/usr
```

---

### Post by Buster222 on 2008-08-17
That resulted in 

Installed drivers: 
Type 10: ALSA emulation
Card config: no soundcard 

in KInfoCenter, which is confirmed by Audiacity | Preferences.

---

### Post by Yellow Pasque on 2008-08-18
ALSA version 1.0.18rc1 released today. Script for that version added to initial post.

---

### Post by Buster222 on 2008-08-18
I installed alsa-1.0.18rc1 with the script, after changing the following line to:
./configure --with-cards=ice1712 --prefix=/usr

However, I still have:

Card config:
-- no soundcards --

If I can help with any other debug info for the M-Audio Delta 66 rev E please let me know.

---

### Post by jznomoney on 2008-08-18
I don't think your 1.0.18 works.  I am using ubuntu 8.04.1 with kernel 2.6.24-19-generic and when I load alsa-mixer it says its still 1.0.15.

---

### Post by Yellow Pasque on 2008-08-19
> **jznomoney said:**
> I don't think your 1.0.18 works.  I am using ubuntu 8.04.1 with kernel 2.6.24-19-generic and when I load alsa-mixer it says its still 1.0.15.
Hmm. All I did was change the filename(s). I'll look into it when I have time (just started a full-time job).

---

### Post by jznomoney on 2008-08-19
when i open the version file in the /proc/asound folder it says 1.0.18 but alsa mixer says 1.0.15.  Am I missing something?

---

### Post by mocha on 2008-08-19
> **jznomoney said:**
> when i open the version file in the /proc/asound folder it says 1.0.18 but alsa mixer says 1.0.15.  Am I missing something?

Can you run "whereis alsamixer" and see if there is one located in /usr/bin and /usr/local/bin?  If there are 2, run "which alsamixer" and see if it returns the binary in /usr/local/bin.  If ther is only 1 alsamixer in /usr/bin, run "ls -al /usr/bin/alsamixer" and look at the date of the binary.  Mine is dated 2/27/2008 from the default Alsa in Hardy.

---

### Post by jznomoney on 2008-08-19
it is this 
-rwxr-xr-x 1 root root 39028 2008-02-27 08:22 /usr/bin/alsamixer

---

### Post by mocha on 2008-08-19
> **jznomoney said:**
> it is this 
-rwxr-xr-x 1 root root 39028 2008-02-27 08:22 /usr/bin/alsamixer

That's the same one I have from the default Alsa in Hardy.  Do you have an alsamixer in /usr/local/bin?  What about the source directories that you installed 1.0.17 from.  Can you find an alsamixer binary in there?  Run "./alsamixer" on it if you can find it and check the version number.  Did you remember to "make install" after compiling everthing?

---

### Post by jznomoney on 2008-08-19
there is only one copy of alsamixer in the /usr/bin directory.  And I ran the script that was made here so.

---

### Post by mocha on 2008-08-20
> **jznomoney said:**
> there is only one copy of alsamixer in the /usr/bin directory.  And I ran the script that was made here so.

Right, but what about in the directory(s) that you compiled the new version in?  Isn't there a binary "alsamixer" in there somewhere?  If there isn't, then for whatever reason you didn't compile it, therefore it's no surprise that you still have the 1.0.15 version.

---

### Post by jznomoney on 2008-08-20
ok here is what i have found.  It never compiled alsamixer or anything in the alsa-tools.  In the script for alsa tools it points to ./configure in the root of the folder but there is none.  and when compiling alsa-utils it says this when using make
Making all in include
make[1]: Entering directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/include'
make  all-am
make[2]: Entering directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/include'
make[2]: Leaving directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/include'
make[1]: Leaving directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/include'
Making all in alsactl
make[1]: Entering directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl'
Making all in init
make[2]: Entering directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl/init'
make[2]: Entering directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
init_parse.c:43:18: error: list.h: No such file or directory
init_parse.c:92:26: error: init_sysdeps.c: No such file or directory
init_parse.c:93:31: error: init_utils_string.c: No such file or directory
init_parse.c:94:28: error: init_utils_run.c: No such file or directory
init_parse.c:95:24: error: init_sysfs.c: No such file or directory
init_parse.c: In function ‘apply_format’:
init_parse.c:1069: warning: assignment makes pointer from integer without a cast
init_parse.c:1088: error: ‘sysfs_path’ undeclared (first use in this function)
init_parse.c:1088: error: (Each undeclared identifier is reported only once
init_parse.c:1088: error: for each function it appears in.)
init_parse.c: In function ‘parse_line’:
init_parse.c:1408: warning: assignment makes pointer from integer without a cast
make[2]: *** [init_parse.o] Error 1
make[2]: Leaving directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jznomoney/alsa/buildme/alsa-utils-1.0.18rc2/alsactl'
make: *** [all-recursive] Error 1

---

### Post by jznomoney on 2008-08-20
I have also installed alsa in vmware and when i got to that step got the same error.

---

### Post by Buster222 on 2008-08-20
For me KInfoCenter reports 1.0.17 emulation code after running the 1.0.18-script. And still no sound card.

---

### Post by NooNeedsHelp on 2008-08-25
Yeah im sick of trying to use UBUNTU to make music
The applications posess decent enough functionality (not in the same class as cool edit or cubase) but i am having real dramas with jack to.

I can get sound but there is distortion when i play and record sound. This is not the case when Jack is not running.

I can run audacity without jack but there is a lag which does my head in!

---

### Post by Yellow Pasque on 2008-08-25
> **jznomoney said:**
> I have also installed alsa in vmware and when i got to that step got the same error.
It appears that alsa-utils now uses sysfs, so I've added libsysfs-dev to the packages in the script.

---

### Post by jznomoney on 2008-08-26
still same error

sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.18rc2/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.18rc2/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.18rc2/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.18rc2/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl'
Making all in init
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
init_parse.c:43:18: error: list.h: No such file or directory
init_parse.c:92:26: error: init_sysdeps.c: No such file or directory
init_parse.c:93:31: error: init_utils_string.c: No such file or directory
init_parse.c:94:28: error: init_utils_run.c: No such file or directory
init_parse.c:95:24: error: init_sysfs.c: No such file or directory
init_parse.c: In function ‘apply_format’:
init_parse.c:1069: warning: assignment makes pointer from integer without a cast
init_parse.c:1088: error: ‘sysfs_path’ undeclared (first use in this function)
init_parse.c:1088: error: (Each undeclared identifier is reported only once
init_parse.c:1088: error: for each function it appears in.)
init_parse.c: In function ‘parse_line’:
init_parse.c:1408: warning: assignment makes pointer from integer without a cast
make[2]: *** [init_parse.o] Error 1
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.18rc2/alsactl'
make: *** [all-recursive] Error 1
jznomoney@ubuntu:/usr/src/alsa/alsa-utils-1.0.18rc2$

---

### Post by poet_imp on 2008-08-26
hmmmm. I have installed 1.0.17 on a lenovo T61 with the following specs:

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.
Compiled on Aug 26 2008 for kernel 2.6.24-19-server (SMP).

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1984

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ grep hda-intel /etc/modprobe.d/alsa-base
options snd-hda-intel model=thinkpad


So far I am not getting any improvement in sound. I get sound, and always have. It is just not loud enough and I can not seem to make it louder. I have everything turned on and all the way up in alsamixer. The volume is still very low.

Any thoughts? Anybody get past this?

---

### Post by mocha on 2008-08-27
> **poet_imp said:**
> So far I am not getting any improvement in sound. I get sound, and always have. It is just not loud enough and I can not seem to make it louder. I have everything turned on and all the way up in alsamixer. The volume is still very low.

Any thoughts? Anybody get past this?


I just noticed last night that there is a very well hidden volume boost control hidden away in the pulseaudio manager GUI.  If you open it up and go to the devices tab, there you can select your sinks and sources, and if you click the properties button there is a volume slider that goes up to 480%.  This needs serious investigation for those of us with the low volume issues.  I plan to experiment with it tonight.

---

### Post by hyperair on 2008-08-27
Good grief. You're right. But will it damage notebook speakers if cranked up high?

On a side note:
For those who don't feel like compiling but need the functionality of 1.0.17 anyway, I've uploaded some packages to a PPA, including a modified linux-ubuntu-modules package. However, those using the kernel from hardy-proposed (2.6.24-21-generic) will have to wait until the kernel hits hardy-updates, because Launchpad won't be able to build it (Launchpad doesn't include the hardy-proposed repository).
[https://edge.launchpad.net/~alsa-backports/+archive](https://edge.launchpad.net/~alsa-backports/+archive)

p.s. no packages for Gutsy, unfortunately. If anyone wants to help make Gutsy packages, they're welcome to join the team and upload packages.

---

### Post by mocha on 2008-08-28
Well the volume boost in the pulseaudio manager only clips the output, so I'm not clear what the point of it is going up to 480%.

---

### Post by Yellow Pasque on 2008-08-28
I noticed that ALSA 1.0.17 has made its way to the Debian repo, and subsequently to the intrepid (8.10) repo. I'll occasionally check to see if it makes its way into hardy-backports. It would make life a lot easier.

---

### Post by mustafaSK on 2008-08-28
thankyou so much brother,

i was struggelling from the last week to get sound on my fresh install
everything u have tated above is absolutely correct and working

thanx once again:lolflag:

---

### Post by hyperair on 2008-08-29
> **Temüjin said:**
> I noticed that ALSA 1.0.17 has made its way to the Debian repo, and subsequently to the intrepid (8.10) repo. I'll occasionally check to see if it makes its way into hardy-backports. It would make life a lot easier.

It hasn't made its way to hardy-backports, but if you're impatient, there's always the alsa-backports ppa: [http://launchpad.net/~alsa-backports/+archive](http://launchpad.net/~alsa-backports/+archive)

---

### Post by mocha on 2008-08-30
> **hyperair said:**
> It hasn't made its way to hardy-backports, but if you're impatient, there's always the alsa-backports ppa: [http://launchpad.net/~alsa-backports/+archive](http://launchpad.net/~alsa-backports/+archive)

So your packages only work with 2.6.24-19?  If I install them and then choose to use 2.6.24-21 in grub does that mean my sound will break?

---

### Post by hyperair on 2008-08-30
Unfortunately so. However, I cannot create 2.6.24-21 packages in the PPA, because 2.6.24-21-* is in hardy-proposed, and lum requires dependencies from there. However, I've got a compiled package here, which works well for me. I'll upload it somewhere and post a link soon. Stay tuned. =)

---

### Post by hyperair on 2008-08-30
Okay, here we go: [http://www.mediafire.com/?sharekey=f912df99221d05378c9e7c56ba37815f3b9a215871b73154](http://www.mediafire.com/?sharekey=f912df99221d05378c9e7c56ba37815f3b9a215871b73154)
The above is a link to the mediafire folder I put all the debs in. Pick out the one you need and download it.

---

### Post by The-Sheep on 2008-08-30
I have a strange behaviour with my Gigabyte motherboard, which has a Realtek ALC662 Codec.

I use 2.6.24-19-generic on hardy. With alsa 1.0.16 sound playback works, recording seems to fail. 

With several packages of 1.0.17 (launchpad, the script in this thread, Realtek-sound-package)I get no sound. When the driver is load, I hear a short noise in my headphones, but no app is able to play sound. Alsamixer shows the card, volumelevels are set etc. 

Any ideas?

---

### Post by hyperair on 2008-08-30
I really have not heard much about Realtek ALC662 codecs, but your problem could be more than just ALSA. It could be a PulseAudio problem as well. It's pretty hard to say. By "able to play sound" do you mean it plays but no sound comes out, or it refuses to play at all? If it's the latter, it's probably an issue with PulseAudio. If it's the former, then it's probably an issue with your drivers.

---

### Post by The-Sheep on 2008-08-30
I'll try to find out what the problem is.
Last afternoon I changed from i386 to x86_64 due a new install. alsa-driver was 1.0.16 and pulseaudio worked fine, e.g. audacious, flash etc. worked with it. 

Now, after the 1.0.17 install, everything (pulseaudio, audacious) which tries to access alsa hw0.0, hangs. 

But if I access the default device, sound works, even with multiple streams.

---

### Post by The-Sheep on 2008-08-30
Workaround:
I  commented out the usage of the hal-module and set pulseaudio to use dmix and dsnoop. But I have no idea where alsa configures the dmix/dsnoop, /etc/asound.conf etc. do not exist.

---

### Post by Acutidens on 2008-09-07
I have been fighting with model=something for my Acer laptop with Intel ICH8 Southbridge and Realtek ALC888 Audio Codec. Setting model=acer did not work but model=auto did.

In short, just add this line at the end of /etc/modprobe.d/alsa-base:

```
options snd-hda-intel model=auto
```

---

### Post by hyperair on 2008-09-07
```

options snd-hda-intel model=auto

```
is the default. If you put model=auto, you're basically asking snd-hda-intel to autodetect your soundcard, which is the default, meaning it wouldn't have a difference if you removed that line completely. model=somethingelse is to force snd-hda-intel to behave the way some other model works, because autodetection doesn't figure out what card you're using.

@The-Sheep:
Try figuring out exactly what your default device is:
```

cat /etc/asound.conf ~/.asoundrc*

```
Also, try checking what devices you have:
```

aplay -L

```

---

### Post by pcozzy on 2008-09-08
I can't seem to get back alsa. 
I installed oss 4 to see if i could get better sound. huh.
I followed installation script and reinstalled alsa-base etc and I can't even get aplay to show anything

```
$ aplay -l
aplay: device_list:215: no soundcards found...
```

I tried to cat /proc...

```
$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
```

I am stumped I am trying to find through google haven't found anything relevant. 

any help to the right direction will be appreciated.

by the way the script run fine with no errors.

---

### Post by klss on 2008-09-08
Hi.

Just downloaded the install script from the first post in this thread. It doesn't seem to install the alsa-plugins.

This is probably the issue with the problem reported some posts earlier.

Cheers

---

### Post by angarato on 2008-09-10
Hello,
I updated the Alsa to 1.0.17 and have to report everything works out as smothly as it should.

So thank you very much! :)

---

### Post by DougAlder on 2008-09-10
Please see [http://ubuntuforums.org/showthread.php?t=915867]("http://ubuntuforums.org/showthread.php?t=915867")for the details of the problem I'm having I followed the directions in this thread and updated ALSA to 1.0.17 but it hasn't fixed the problem - I would really appreciate some help.

---

### Post by The-Sheep on 2008-09-12
> **hyperair said:**
> ```



@The-Sheep:
Try figuring out exactly what your default device is:
[code]
cat /etc/asound.conf ~/.asoundrc*

```
Also, try checking what devices you have:
```

aplay -L

```

asound.conf and ~/.asoundrc* do not exist.

```
root@majestix:~# aplay -L
default:CARD=NVidia
    HDA NVidia, ALC662 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC662 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=NVidia,DEV=0
    HDA NVidia
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I don't see any dmix-device there. Hm.

greetings
The Sheep

---

### Post by Yellow Pasque on 2008-09-12
Script modified for ALSA 1.0.18rc3. Also added alsa-plugins.

---

### Post by klss on 2008-09-12
Termüjin.

1.
You got some BUGS at the bottom of the script. You forgot to change out the _rc1

Perhaps a better idea would be to introduce some variables, to avoid this
in the future


2.
alsa-driver see my options

./configure --with-cards=all --with-card-options=all --with-seqencer=yes --prefix=/usr

3. Why don't you install alsa-oss from sources? 

Cheers

---

### Post by Yellow Pasque on 2008-09-12
klss, Thanks for the tips.
1. fixed
2. I was trying to cut down on build time. It seems that most of the people having issues with their sound and using the script have onboard HD audio. I've added the sequencer flag, though I'm not quite sure what it does. What does --with-card-options=all do?
3. Ubuntu has the latest version. The only change from 1.0.15 to 1.0.17 was switching code version systems (hg->git) [http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17#alsa-oss](http://www.alsa-project.org/main/index.php/Changes_v1.0.16_v1.0.17#alsa-oss)

If you (or anyone else) would like to maintain the script, I would love to wash my hands of it, as I don't use ALSA.

---

### Post by klss on 2008-09-15
1.I think compiling all drivers by default would be the better choice.

Not very well experienced people will get lost if they don't run
hda-intel in particular. Since there is no roll-back, the upgrade 
should work flawless. I wouldn't argue about spending an extra minute for compiling useless code.

2. I think it is always better to compile all packages. It doesn't hurt if
you'd take alsa-oss in. I'll do it.

---

### Post by klss on 2008-09-15
Latest update 10/28/2008


Alsa 1.0.18 will now bw handled over here:

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

BTW: KLSS is now soundcheck

THX

---

### Post by Yellow Pasque on 2008-09-18
> Temüjin: Did you check out your results?
No, I have no way of testing the scripts because I use OSS4 and not ALSA. That's why it's now your duty to maintain the scripts :P BTW, you're doing an excellent job!
One suggestion: Intrepid now uses 2.6.27 kernels, so you'll want to restructure that segment of code.

---

### Post by klss on 2008-09-19
Hi.

I just compiled Audacious from sources using the new alsa-dev env..
Same issues as before via ALSA output.

I'd guess that this is an Audacious upwards compability issue, since the basic Alsa services are working fine.

I also tested VLC and Exaile. These are also working fine.

Cheers

---

### Post by diaa on 2008-09-21
This worked for me and it looks like it didn't break anything, I have an intel-hda card which I think is ALC889A

**UPDATE:**
Turns out It wasn't so straight forward, recording got messed up, sound recorded from the default capturing device is highly distorted, when I set it to hw:0,0 it works well

---

### Post by DakoCwerf on 2008-09-21
will work for asus m51vr with model=m51va

---

### Post by klss on 2008-09-22
Hi folks.

I uploaded my newest version of the script. [http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

I applied some major changes:

1. MultiPle ALSA Package support: Now you can choose after starting the script what Alsa Package to install. (Only one script to maintain)
2. Kernel 2.6.27-x (NON-Ubuntu-Kernels) is supported. I tested it with
   2.6.27-rc6-zen1 (ZEN-kernel)
3. I built in some safety, In case the downloads fail the script will stop to avoid an inconsistent/corrupted installation.

Enjoy.

Cheers

---

### Post by shameless on 2008-09-23
Ok, I'm really confused now. Under Gutsy, my sound worked fine on my Asus R1F, but now that I'm running Hardy, it hasn't been working at all. Tried 

```
philip@RINGWORLD-DOCK9:~$ aplay -l
aplay: device_list:205: no soundcards found...

```

Yet when I did lspci, I got 

```

philip@RINGWORLD-DOCK9:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
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
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


```

Suggestions?

---

### Post by klss on 2008-09-24
Perhaps you'd shed some light on what you've done? 

Did you run any of above listed scripts?

---

### Post by ~jonathan~ on 2008-09-25
Im having some trouble with this, I am very new to linux. Like today makes my 4th day with it and the only problem i have come across is having no sound. When i run 
```
aplay -l
```

I get this
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

so I am guessing I need something for a ICH6 and i have no clue what to do from that point. Can someone please help me with this problem, I have done alot of searching to even get me to this point and would greatly appreciate so of your help.

thanks
~jonathan

---

### Post by klss on 2008-09-28
> **~jonathan~ said:**
> Im having some trouble with this, I am very new to linux. Like today makes my 4th day with it and the only problem i have come across is having no sound. When i run 
```
aplay -l
```

I get this
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

so I am guessing I need something for a ICH6 and i have no clue what to do from that point. Can someone please help me with this problem, I have done alot of searching to even get me to this point and would greatly appreciate so of your help.

thanks
~jonathan

Hi there. 

One more time: 
Did you run one of the above scripts? If not - run the script if you don't succeed with below hints. 

Comment: This thread is not the right place for basic trouble shooting.
You'll find 100s of links, of how to setup your ALSA and how to checkout
if your device is supported. Google will be your friend.

However - below at least a hint: 
Open a terminal. An type "alsamixer". Make sure all outputs Master/PCM/CD are unmuted!
Muted channels/slider do show a "MM" at the bottom. Just type "M" to unmute the active slider.

You might also want to try below: 
The best way to test a sound device is using "aplay". 
This a the player which comes with ALSA. If you don't get aplay to work. Nothing will work. 

You need to open a terminal and type:

aplay -Dhw:0,0 -fcd /usr/share/sounds/startup.wav 
or
aplay -Dplughw:0,0 -fcd /usr/share/sounds/startup.wav

Hint: Copy above commands with CTRL-C. Pasting into a terminal works by pushing left and right mouse button a the same time.

aplay to output hw:0,0 will send an untouched  PCM stream - without any mixing or manipulation - to the sound device on channel 0.

Good luck.

---

### Post by avalenc on 2008-09-30
I'm new to this. I did/ran? lspci and it tells me:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

Would the model name be Azalia? Or the number beore it? Or both?

And will updating (?) alsa cause my internal microphone to work? 

And what if I want to connect an external USB mic?

Thank you.
-Adriana

---

### Post by klikklak on 2008-10-02
The script hosed my computer.  This is after testing oss4 for surround (still had speakers misplaced) and after following the guide.  It fails to boot all the way up (bash craps out errors before gdm) and comes up in maintainer mode (init 1).  I'll be doing a new install of intrepid to solve this, but this is **not good. **

---

### Post by Yellow Pasque on 2008-10-02
> **klikklak said:**
> The script hosed my computer.  This is after testing oss4 for surround (still had speakers misplaced) and after following the guide.  It fails to boot all the way up (bash craps out errors before gdm) and comes up in maintainer mode (init 1).  I'll be doing a new install of intrepid to solve this, but this is **not good. **
Did you report the misplaced surround to the OSS/4Front forums? What kind of sound card do you have?

---

### Post by klikklak on 2008-10-02
> **Temüjin said:**
> Did you report the misplaced surround to the OSS/4Front forums? What kind of sound card do you have?

No I didn't as I was looking for a quick fix.  I did find the ttable commands for asoundrc which should do the trick.  My card is nvidia acs883 (acs?  can't remember and I'm posting from school, the number is correct).

---

### Post by Yellow Pasque on 2008-10-02
Suggestions:
Line 17 - fix the spelling of my user name in the script heading or remove it entirely (I don't care for credits)
Line 40 - alsa-lib-1.0.17**a**

---

### Post by klss on 2008-10-02
> **Temüjin said:**
> Suggestions:
Line 17 - fix the spelling of my user name in the script heading or remove it entirely (I don't care for credits)
Line 40 - alsa-lib-1.0.17**a**

Temüjin: Checkout my script. If a download fails because of a non existing package, the script exits out. This avoids a mess-up if the guys at ALSA change packages. 

As I understand the mess-up of klikklak has something to do with the OSS4 hacking and an intrepid install. 

klikklak: What script are you talking about? There are two!

---

### Post by spid3rz on 2008-10-04
I have just ran the newest script on 8.10 Beta and I'm happy to say my sound issues are now fixed.. previous to running the script all my sounds including the system sounds were static noise. 

Thanks :)

---

### Post by hyperair on 2008-10-04
> **spid3rz said:**
> I have just ran the newest script on 8.10 Beta and I'm happy to say my sound issues are now fixed.. previous to running the script all my sounds including the system sounds were static noise. 

Thanks :)

I reckon the static noise was because Pulseaudio chose the pc speaker instead of the standard sound output, in which case you'd need to select the correct device (via pavucontrol) and that's it. No need to go through the whole compilation process.

---

### Post by spid3rz on 2008-10-04
> **hyperair said:**
> I reckon the static noise was because Pulseaudio chose the pc speaker instead of the standard sound output, in which case you'd need to select the correct device (via pavucontrol) and that's it. No need to go through the whole compilation process.

Ah.. well like I said its fixed now but thanks for possibly identifying the real problem.. your solution sounds a lot easier then mine HAHA..

---

### Post by dblade on 2008-10-05
previous OSS install had caused my issue

---

### Post by klss on 2008-10-06
Hi folks.

I just ran the Ubuntu Studio 8.10 Beta upgrade which comes currently with Alsa 1.0.16 and 2.6.26-1-rt kernel.

The script worked fine.

BTW: I built a bit more sophisticated version of the script, where you can choose between
1. download only, 2. installation only, 3. download&installation

This way you don't have to download the whole stuff any time you want
to reinstall due to whatever reason (e.g. kernel upgrade). You can also manipulate your driver if you like)  
It now also routes all output to a logfile under /var/log for troubleshooting purposes and
it stores now the different Alsa versions on the drive, to make e.g. switching between stable and dev easier and faster.

I'll put it up as BETA for now - perhaps there is somebody out there would like to confirm that it is working. 

As usual - feedback and improvement proposals are always welcome.

THX

---

### Post by 2334242342345523542342332 on 2008-10-07
A pity ubuntu forums require registering for fetching attachments..

While I'm here, I used the first script to download both alsa versions which now generates this:


[PHP][   28.415052] Pid: 4246, comm: alsactl Tainted: P        (2.6.24-19-generic #1)
[   28.415054] EIP: 0060:[<f8b154b1>] EFLAGS: 00010286 CPU: 1
[   28.415073] EIP is at snd_hda_spdif_out_switch_put+0x91/0x130 [snd_hda_intel]
[   28.415075] EAX: 00000000 EBX: f75c8800 ECX: f7f74200 EDX: 00000000
[   28.415077] ESI: dfac9600 EDI: 00000001 EBP: 00000002 ESP: dfb19db8
[   28.415079]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[   28.415081] Process alsactl (pid: 4246, ti=dfb18000 task=dfbae5c0 task.ti=dfb18000)
[   28.415083] Stack: 0000070d 00000001 c04194a0 00000001 dfac9780 00029968 00000001 f8b15420
[   28.415088]        f75c8800 dfac9800 dfac994c f8b034da c031c7e2 bfec75d0 df80c1c0 b7fc1000
[   28.415093]        c2b0df80 00000000 dfac99b0 00000004 00000002 00000000 00000000 39434549
[   28.415098] Call Trace:
[   28.415109]  [<f8b15420>] snd_hda_spdif_out_switch_put+0x0/0x130 [snd_hda_intel]
[   28.415132]  [<f8b034da>] snd_ctl_ioctl+0xc6a/0xd40 [snd]
[   28.415142]  [<c031c7e2>] error_code+0x72/0x80
[   28.415167]  [<c0190000>] do_filp_open+0x50/0x60
[   28.415175]  [<f8b02870>] snd_ctl_ioctl+0x0/0xd40 [snd]
[   28.415185]  [<c019dffb>] do_ioctl+0x2b/0x90
[   28.415190]  [<c019e28e>] vfs_ioctl+0x22e/0x2b0
[   28.415193]  [<c01900ce>] do_sys_open+0xbe/0xe0
[   28.415197]  [<c019e366>] sys_ioctl+0x56/0x70
[   28.415201]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[   28.415209]  =======================
[   28.415210] Code: 94 01 00 00 0f b7 6c 24 16 0f b7 d2 0f b6 fa 89 54 24 0c 89 7c 24 04 89 ea c7 04 24 0d 07 00 00 e8 15 e1 ff ff 8b 96 9c 01 00 00 <0f> b7 02 66 85 c0 74 2a 89 d3 90 8d 74 26 00 0f b7 d0 31 c9 89
[   28.415238] EIP: [<f8b154b1>] snd_hda_spdif_out_switch_put+0x91/0x130 [snd_hda_intel] SS:ESP 0068:dfb19db8
[   28.415255] ---[ end trace c0d0b3a620f5ce42 ]---
[/PHP]

2.6.24-19-generic / Kubuntu

I've reinstalled the kernel package and the alsa* packages, no luck. I knew I shouldn't have proposed to help this friend with his ubuntu laptop :(( 

System Information
        Manufacturer: Dell Inc.
        Product Name: Studio 1535
        Version: Not Specified

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

Will try harder

Thanks for the script.

edt:
Seems like there are very few people for who this is happening.
[http://www.kerneloops.org/search.php?search=snd_hda_spdif_out_switch_put&btnG=Function+Search](http://www.kerneloops.org/search.php?search=snd_hda_spdif_out_switch_put&btnG=Function+Search)

---

### Post by klss on 2008-10-08
Hi folks.

I added a a new script to the download post which checks the environment and your setup with focus on Alsa of course.

Perhaps it helps for troubleshooting in general.

Just run it - best while playing back, since it records playback stream parameters - to see what's going on on your machine.

I hope it helps.

Cheers

---

### Post by sdcope on 2008-10-09
I'm running 8.04, ran the script and followed the instructions on post #19.  My Alsa is still showing 1.0.16 when I F2 in the alsamixer, despite the mixer saying I've upgraded to 1.0.18r3.

Still no sound. :(

P.S. Thanks for all the help and script, btw!

P.P.S. Is this caused by still having kernel 2.6.24-19 installed and not -20?  How does on upgrade the kernel in Ubunut?  (I've switched from Slack.)

---

### Post by klss on 2008-10-10
I tried my Alsamixer - "F2" (Didn't know about F2) - THX . Looks OK.

I guess there must have been a problem with the "lib" install in your 
case.

Please run the newest script. Than we/you have a chance to have a look at the log file.

The kernel itself can be an issue, if Alsa is not build as module in the kernel. But this is normally not the case with Ubuntu kernels. 
I ran into it with my ZEN-Kernel in the beginning. 

This issue you encountered is a known weakness of the script (You'll find in in the ToDos I listed inside the script). 
To avoid these kind of inconsistencies I need to check first if "configure" and "make" run without errors before installing the new packages. I need to look it up how to implement it.

THX

---

### Post by Yellow Pasque on 2008-10-15
There is a typo in the 1.04 script (perhaps in the 1.03 as well)
> 
./configure --with-cards=all --with-card-options=all --with-seqencer=yes --with-oss=yes --prefix=/usr

SHOULD BE --with seq**u**encer

---

### Post by klss on 2008-10-16
> **Temüjin said:**
> There is a typo in the 1.04 script (perhaps in the 1.03 as well)


SHOULD BE --with seq**u**encer

1.05 is ready for download. THX ;)


BTW: We should try to rename this thread to 1.0.x, since 1.0.17 is now available with intrepid.

Cheers

---

### Post by klss on 2008-10-16
Hi folks.

I just uploaded revision 1.06.

The older versions (up to 1.05)  could lead to a corrupted status, because if any  of the package compilation/installation failed the system resp. Alsa packages became inconsistent.

I introduced checks about successful execution for every single "configure" and "make". I now run all "configures" and "make" first. 
If these are executed successfully. I run "make install" on all packages in a final step.

I also verified 1.06 on Intrepid with 2.6.27-7-generic kernel.

The script should run pretty save now.

Good luck.

Cheers

---

### Post by sdcope on 2008-10-16
I ran the script again after running an update.  The script seems to have installed the new alsa perfectly.  When I f2 in Alsa mixer it's showing .18rc3..... alas, the sound isn't working, but I think it must be something else, now.

Thanks again!

---

### Post by Jack the R on 2008-10-16
klss the update script is not working for me (specifically the sound works, except over headphones).  I had this working on a previous install with Temujin's instructions which have since been removed.  

[Here's the uxchecker log.](http://www.extinctionlevelevent.com/misc/linux/uxchecker-101608-23.46.log)

The last lines in /etc/modprobe.d are - 

> # Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=asus

Model=Asus worked before.  I can't remember if  options snd-cmipci mpu_port=0x330 fm_port=0x388 was there before but I think it was.

I've tried both 1.0.17 and 1.0.18 RC3.

---

### Post by klss on 2008-10-17
> **Jack the R said:**
> klss the update script is not working for me (specifically the sound works, except over headphones).  I had this working on a previous install with Temujin's instructions which have since been removed.  

[Here's the uxchecker log.](http://www.extinctionlevelevent.com/misc/linux/uxchecker-101608-23.46.log)

The last lines in /etc/modprobe.d are - 



Model=Asus worked before.  I can't remember if  options snd-cmipci mpu_port=0x330 fm_port=0x388 was there before but I think it was.

I've tried both 1.0.17 and 1.0.18 RC3.

Hi.

First of all - the updated script is not supposed to be doing anything else than the initial script, it just compiles the Alsa packages.

The only difference are the default configure options.
on the driver package, which you had to edit manually before. 
Of course you can still do it!

I just added quite some stuff to make it more save and more convenient -
at least from my perspective.

I added also the logfile option to the script, to be able to investigate cases like yours. 

Did you check your installation log under /var/log first? 

You also need to be careful when upgrading to Intrepid it overwrites
the modeprobe.d/alsa-base . After the upgrade you'll have your 
default settings back.

The upgrades done with the script won't touch your modprobe.d/alsa-base

I had a look in your uxchecker-log. There are no index variables set for
both of your cards. I'd expect an index=0 and an index=1 entry!

However, since Intrepid comes with quite some new stuff and it seems
that there are still issues with the kernel (e.g. segfaults on alsactl), we 
need to be careful here.

Since you're not the only one having problems we need to have a look at it.

And if you guys report an issue:

1. Name your Ubuntu revision
2. Kernel revision
3. Alsa revision
4. Upgrade script revision
5. A bit of background what you've done resp. done before 

THX a lot for the feedback.

Cheers

---

### Post by klss on 2008-10-17
IMPORTANT NOTE: 

The uxchecker.sh script logs partly sensitive data such, as user-id,
groups etc. 

I would not recommend to put them up here - at least not the complete log!!!

I just uploaded a new version 1.02, where you can select e.g. full system check or e.g. Alsa only. 
If you choose e.g. Alsa only you won't face any security relevant issues.

THX

---

### Post by Jack the R on 2008-10-17
Thanks for the reply.

I'm on 8.04, 64 bit

The kernel is  2.6.24-19

Alsa should be 1.0.18 RC3. 

Script version is AlsaUpgrade-1.0.x-rev-1.06.sh

> 
Did you check your installation log under /var/log first? 

I wouldn't know what to look for.

> 
I had a look in your uxchecker-log. There are no index variables set for
both of your cards. I'd expect an index=0 and an index=1 entry!

What do I do to set them?

---

### Post by klss on 2008-10-17
Try:

options snd-cmipci index=0 mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=1 model=asus 

and reboot.

The card/driver with index 0 becomes card 0 and the 2nd becomes 
card 1. (This you'll also see in the uxchchecker.log)
card 0 resp. index 0 is usually the default card. It'll be your choice
how to assign the cards. 
It is strongly recommended to assign the index if you run multiple cards.

Logfile-check:
Just check the log file for strange error messages. Disregard warnings. 


Good luck.

---

### Post by Jack the R on 2008-10-18
It liked the new alsa-base lines even less.  Now there is no sound at all. ](*,)

It gives the error message -

> ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
aplay: main:583: audio open error: No such file or directory
 

I ran uxchecker 1.02 with -a - 

[Link](http://www.extinctionlevelevent.com/misc/linux/tablet/uxchecker-1.02-101808-00.05.log)

Is this a strange error message?

> cat: /proc/asound/card0/stream0: No such file or directory

-----------------------------------------------------------------------------
-    playback-stream card 1
-----------------------------------------------------------------------------

cat: /proc/asound/card1/stream0: No such file or directory

-----------------------------------------------------------------------------
-    codec card0
-----------------------------------------------------------------------------

cat: /proc/asound/card0/codec*: No such file or directory

-----------------------------------------------------------------------------

---

### Post by klss on 2008-10-18
OK! The new uxchecker.sh seems to work;)

I guess you ran aplay with the options "-Dplughw:0,0" (You should actually tell us what you've done, causing
this error message)

If you look in the uxchecker.log it says that you just have your 
internal card connected. And it's called "card 1" now, because you assigned index=1 to it. 
Now if you read my earlier post, this means that we're talking about the 2nd card in 
your system. Thus -Dplughw:1,0 would do the trick. 

or do this

options snd-cmipci index=1 mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=asus 

In this case "-Dplughw:0,0" should work.

As far as I understand the cmipci driver is supposed to drive a 2nd soundcard!?!? The system is not recognising it. What happend to this card?

Comment: When I talked about looking for errors, I talked first of all about the log-file generated by the Alsa installation script - and not the uxchecker.sh 


Good luck

---

### Post by Jonno_FTW on 2008-10-18
I ran your scipt and it started working. 
But there is no sound!
```
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alsa-plugins-1.0.18rc3 configure failed 
```

that's what i got at the end of the log file.

---

### Post by klss on 2008-10-18
> **Jonno_FTW said:**
> I ran your scipt and it started working. 
But there is no sound!
```
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alsa-plugins-1.0.18rc3 configure failed 
```

that's what i got at the end of the log file.

No sound! Strange. 
Because the script - the latest version - didn't do anything to your system!
At this stage - where it left the scene according to the log - one of my new features kicked in. If one stage fails the script stops the entire process, without touching anything.

and again I am happy to support until the script runs stabil (it does in my environment) BUT:

if you guys report an issue:

1. Name your Ubuntu revision
2. Kernel revision
3. Alsa revision
4. Upgrade script revision
5. A bit of background what you've done resp. done before 
6. Attach the relevant logs

Hint: 
As you see in the log, the script encountered a problem when configuring the alsa-plugins.
You can go to the target directory /usr/src/Als*/alsa-pl* an run a "./configure --prefix=/usr" manually, just
to see what's going on. If it is working manually just run the script again.


THX

---

### Post by Jonno_FTW on 2008-10-18
Ok
I'm running Hardy 8.04
Kernel is: 2.6.24-21-generic
Alsa version: according to synaptic is 1.0.16
Script version:rev.107

I new at most of this. I just ran the script and waited really.
My sound car is: Realtex ID 663/ HDA intel
The log file is attached.
[ATTACH]88789[/ATTACH]

---

### Post by Jack the R on 2008-10-18
> **klss said:**
> 
I guess you ran aplay with the options "-Dplughw:0,0" (You should actually tell us what you've done, causing
this error message)

Oops.  I think you guessed it.  I copied and pasted from your instructions the line "aplay -Dplughw:0,0 -fcd /usr/share/sounds/question.wav"

> **klss said:**
> 
If you look in the uxchecker.log it says that you just have your 
internal card connected. And it's called "card 1" now, because you assigned index=1 to it. 
Now if you read my earlier post, this means that we're talking about the 2nd card in 
your system. Thus -Dplughw:1,0 would do the trick.

Just tried it - regular audio works, headphones don't work.  Headphones are unmuted in the regular gui mixer.  I ran the alsamixer command and got "  function snd_ctl_open failed for default: No such file or directory
"  I'm not sure what's going on there.  I don't remember manually installing it before, and I don't see it on Synaptic (there's a gui but not alsamixer itself).

> **klss said:**
>  
As far as I understand the cmipci driver is supposed to drive a 2nd soundcard!?!? The system is not recognising it. What happend to this card?

You've got me.  I never added a second sound card and I doubt the tablet pc came with two.

---

### Post by klss on 2008-10-19
> **Jack the R said:**
> Oops.  I think you guessed it.  I copied and pasted from your instructions the line "aplay -Dplughw:0,0 -fcd /usr/share/sounds/question.wav"



Just tried it - regular audio works, headphones don't work.  Headphones are unmuted in the regular gui mixer.  I ran the alsamixer command and got "  function snd_ctl_open failed for default: No such file or directory
"  I'm not sure what's going on there.  I don't remember manually installing it before, and I don't see it on Synaptic (there's a gui but not alsamixer itself).



You've got me.  I never added a second sound card and I doubt the tablet pc came with two.

Obviously we're getting there. ;)

Since you got one card only, it (snd-hda-intel) needs of course index=0 and put a "#" in front of the "option cmi" line .
Change this accordingly in alsa-base.

alsamixer defaults to index 0. Since you don't have index 0 assigned for now - as discussed above -, you'll get an error message. If you want alsamixer to run on your 2nd soundcard (index 1) you start it with "alsamixer -c1"

Since your card is working in general, I'd guess that the driver is not supporting the headphone jack properly. 
You need to google it up.

Anyhow: As far as I see your whole story had nothing to do with the script itself.

Cheers

---

### Post by klss on 2008-10-19
> **Jonno_FTW said:**
> Ok
I'm running Hardy 8.04
Kernel is: 2.6.24-21-generic
Alsa version: according to synaptic is 1.0.16
Script version:rev.107

I new at most of this. I just ran the script and waited really.
My sound car is: Realtex ID 663/ HDA intel
The log file is attached.
[ATTACH]88789[/ATTACH]

1. Could you please try the newest script version in "-f" "full" mode 
   please.
   I've actually never seen that the plugin part failed.  
2. Run also the uxchecker-102.sh, because the Ubuntu package as shown in
   Synaptic will remain 1.0.16. This is the reason why I handed out the
   uxchecker-script.
3. open a new terminal and run "tail -f </var/log/your-logfile>" . this way you'll see what's going on and of course if the script finished up.

I pretty much doubt that the script is causing the trouble. But - you never know.
  
THX

---

### Post by Jack the R on 2008-10-19
I've changed the last lines of the alsa-base file to - 

#options snd-cmipci index=0 mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=asus 

rebooted, same results as before.  Sound from the speakers, no sound from the headphones.  Alsamixer shows the headphones as unmuted, but there is no volume slider.  Just the value 00.  However this is the behavior I saw before, when the headphones were working, so I don't think the value 00 is particularly meaningful.

Aplay won't play a music file, gives the error - 

> ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
aplay: main:583: audio open error: No such device

If I click on the file in Nautilus, Totem Movie Player will play it.  

How can this be a driver issue when the driver was able to play through the headphones before?

---

### Post by klss on 2008-10-20
> **Jack the R said:**
> I've changed the last lines of the alsa-base file to - 

#options snd-cmipci index=0 mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=asus 

rebooted, same results as before.  Sound from the speakers, no sound from the headphones.  Alsamixer shows the headphones as unmuted, but there is no volume slider.  Just the value 00.  However this is the behavior I saw before, when the headphones were working, so I don't think the value 00 is particularly meaningful.

Aplay won't play a music file, gives the error - 



If I click on the file in Nautilus, Totem Movie Player will play it.  

How can this be a driver issue when the driver was able to play through the headphones before?

Hi there.

Of course could this be a driver issue. They change quite some stuff from release to release and most probably don't 
test every single function.

However:

I looked again into your uxchecker-1.02.log.

Issue Codec: it seems that your chosen  model="asus" is not appropriate.

In the log under "Codec" you find ALC660-VD listed for your device.
"Asus" seems to cover ALC660 only.

Within /usr/src/Alsa-1.0.18rc3/alsa-driver-1.0.18rc3/alsa-kernel/Documentation/ALSA-Configuration.txt

you'll find a different model listed for your codec.

Try to change your model=asus in /etc/modprobe.d/alsa-base to  "model=3stack-660" or better "model=3stack-660-digout" 

and reboot. Check your alsamixer again!

If that doesn't help I am running out of ideas,

NOTE: I am doing all this troubleshooting, just because I hope that others learn from it of how to solve their own issues! I do not regard it as part of this thread.

GENERAL: All others reading this should run the same checkup. A soundcard will (should) with all its features functions properly if the correct "model=XXXX" is assigned to your driver. You'll find that out as described above.

Good luck

---

### Post by Jack the R on 2008-10-20
If you're looking at Temujin's list, it is IMO incorrect.  I initially tried the values listed and got the results I'm getting now, sound everywhere but headphones.  The values "auto" and "asus" got the headphones working (BTW, I'm referring to my earlier attempt when I got everything working, not this attempt with your script).

I tried the values "model=3stack-660" and "model=3stack-660-digout," no headphones.

Temujin's instructions were originally in the first post of this thread, right?  Maybe they were in another thread and I've gotten confused.  It'd be nice to find out what driver he linked to, that I had working.

---

### Post by jjustyy on 2008-10-24
> **klss said:**
> 
[QUOTE=Jonno_FTW;5987462]I ran your scipt and it started working. 
But there is no sound!
```
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... configure: error: Package requirements (alsa >= 1.0.11) were not met:

No package 'alsa' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALSA_CFLAGS
and ALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

alsa-plugins-1.0.18rc3 configure failed 
```

that's what i got at the end of the log file.

No sound! Strange. 
Because the script - the latest version - didn't do anything to your system!
At this stage - where it left the scene according to the log - one of my new features kicked in. If one stage fails the script stops the entire process, without touching anything.

...

[/QUOTE]

I've had this error too - I fixed it by installing libasound2-dev

Cheers,
Justin

---

### Post by klss on 2008-10-25
Interesting news - the libasound2-dev issue. 

I had it installed already. That's obviously why I didn't
have any problems here. 

I updated the script 1.09 accordingly (which is available for download). 
I added the libasound2-dev to the package list. It will be installed prior to 
the Alsa upgrade.

I also updated the uxchecker script. I stepped over a nice tool called hwinfo, which 
you'll find in the repository. (uxchecker installs and runs it)

Work in progress. ;)

THX

---

### Post by Jack the R on 2008-10-26
Hmm, no libasound2-dev here.  I'll try the new script tomorrow.

---

### Post by LordOfThePigs on 2008-10-26
Unfortunately, I seem the script fails at compilation every time for me.

When I try to install 1.0.18rc3 I get:
```

Making all in iecset
make[1]: Entering directory `/usr/src/Alsa-1.0.18rc3/alsa-utils-1.0.18rc3/iecset'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
	then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
iecset.c: In function ‘update_iec958_status’:
iecset.c:198: error: ‘IEC958_AES3_CON_FS_22050’ undeclared (first use in this function)
iecset.c:198: error: (Each undeclared identifier is reported only once
iecset.c:198: error: for each function it appears in.)
iecset.c:201: error: ‘IEC958_AES3_CON_FS_24000’ undeclared (first use in this function)
iecset.c:213: error: ‘IEC958_AES3_CON_FS_88200’ undeclared (first use in this function)
iecset.c:216: error: ‘IEC958_AES3_CON_FS_96000’ undeclared (first use in this function)
iecset.c:219: error: ‘IEC958_AES3_CON_FS_176400’ undeclared (first use in this function)
iecset.c:222: error: ‘IEC958_AES3_CON_FS_192000’ undeclared (first use in this function)
iecset.c:225: error: ‘IEC958_AES3_CON_FS_768000’ undeclared (first use in this function)
iecset.c:228: error: ‘IEC958_AES3_CON_FS_NOTID’ undeclared (first use in this function)
make[1]: *** [iecset.o] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.18rc3/alsa-utils-1.0.18rc3/iecset'
make: *** [all-recursive] Error 1
alsa-utils-1.0.18rc3 make failed

```

When I try to install alsa 1.0.17 I get:
```

In file included from /usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: In function ‘dapm_pop_time_store’:
/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function ‘strict_strtoul’
make[3]: *** [/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.17/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [compile] Error 2
alsa-driver-1.0.17 make failed

```

I use Hardy with kernel 2.6.24-21-generic and gcc 4.2.3-1ubuntu3

Any idea what might be wrong?

---

### Post by Jack the R on 2008-10-26
Ran the new script, got libsound2-dev now, same results as before :(

---

### Post by soundcheck on 2008-10-27
> **LordOfThePigs said:**
> Unfortunately, I seem the script fails at compilation every time for me.

When I try to install 1.0.18rc3 I get:
```

Making all in iecset
make[1]: Entering directory `/usr/src/Alsa-1.0.18rc3/alsa-utils-1.0.18rc3/iecset'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
	then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
iecset.c: In function &#8216;update_iec958_status&#8217;:
iecset.c:198: error: &#8216;IEC958_AES3_CON_FS_22050&#8217; undeclared (first use in this function)
iecset.c:198: error: (Each undeclared identifier is reported only once
iecset.c:198: error: for each function it appears in.)
iecset.c:201: error: &#8216;IEC958_AES3_CON_FS_24000&#8217; undeclared (first use in this function)
iecset.c:213: error: &#8216;IEC958_AES3_CON_FS_88200&#8217; undeclared (first use in this function)
iecset.c:216: error: &#8216;IEC958_AES3_CON_FS_96000&#8217; undeclared (first use in this function)
iecset.c:219: error: &#8216;IEC958_AES3_CON_FS_176400&#8217; undeclared (first use in this function)
iecset.c:222: error: &#8216;IEC958_AES3_CON_FS_192000&#8217; undeclared (first use in this function)
iecset.c:225: error: &#8216;IEC958_AES3_CON_FS_768000&#8217; undeclared (first use in this function)
iecset.c:228: error: &#8216;IEC958_AES3_CON_FS_NOTID&#8217; undeclared (first use in this function)
make[1]: *** [iecset.o] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.18rc3/alsa-utils-1.0.18rc3/iecset'
make: *** [all-recursive] Error 1
alsa-utils-1.0.18rc3 make failed

```

When I try to install alsa 1.0.17 I get:
```

In file included from /usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: In function &#8216;dapm_pop_time_store&#8217;:
/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: implicit declaration of function &#8216;strict_strtoul&#8217;
make[3]: *** [/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.17/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.17/alsa-driver-1.0.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [compile] Error 2
alsa-driver-1.0.17 make failed

```

I use Hardy with kernel 2.6.24-21-generic and gcc 4.2.3-1ubuntu3

Any idea what might be wrong?

Hmmh. 

I ran both "./configure" and "make" for both packages manually.

My 1.0.18-rc3 compiles without any problems on 2.6.27-7-general. Unfortunately I do not have an  older kernel available for testing.

Guess what: My make on 1.0.17 driver also failed. 

One thing for sure: This shouldn't have anything to do with the script itself.



Perhaps we shouldn't spent too much effort on resolving these issues. Intrepid will be out soon.
And I also read that very soon 1.0.18 final will be out.

---

### Post by soundcheck on 2008-10-29
Hi folks.

1.0.18-final is out.

Perhaps I manage to get it ready during the next hours.

Cheers

---

### Post by Jack the R on 2008-10-29
I would rather not use Intrepid.  I let Hardy upgrade the kernel, it knocked out the tablet driver, and I was not able to to get the tablet driver working again with the new kernel.  Had to go back to the old kernel, where it worked like a charm.  

I'm rather distrustful of change at this point - one thing gets fixed, another gets broken.

---

### Post by soundcheck on 2008-10-29
> **Jack the R said:**
> I would rather not use Intrepid.  I let Hardy upgrade the kernel, it knocked out the tablet driver, and I was not able to to get the tablet driver working again with the new kernel.  Had to go back to the old kernel, where it worked like a charm.  

I'm rather distrustful of change at this point - one thing gets fixed, another gets broken.


Everybody who is aiming for a stable system, should wait at least some weeks or for the next maintenance realease to let the dust settle.

Installing Alsa manually is a "Hack" (the way how it is done with the script) and should be done by people having some kind of hacker 
attitude. Otherwise it can get very annoying.

Cheers

---

### Post by soundcheck on 2008-10-29
Hi folks.

I started up a new thread called Alsa 1.0.18 Installation Script.

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)



Cheers

BTW: KLSS is now "soundcheck"

---

### Post by Jack the R on 2008-10-31
> **soundcheck said:**
> 
Installing Alsa manually is a "Hack" (the way how it is done with the script) and should be done by people having some kind of hacker 
attitude. Otherwise it can get very annoying.

Cheers

I got it done on the first try with the original instructions. It shouldn't be this much of a problem.  Maybe there's another dependency such as libasound2-dev which the script isn't installing.

---

### Post by sreekanth27 on 2008-11-12
Hello Temüjin,

I tried everything from reinstalling UBUNTU to upgrading RAM to 1.25 gig, to removing pulse to following your steps but to no avail. No sound.

this is the sound card that I have:
sree@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sree@ubuntu:~$ 

the driver version:
sree@ubuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.17.


No sound whatsoever.. 

Do help
Sree

---

### Post by kowic on 2008-11-15
I have no soun after upgrade from 8.04 to 8.10. Trying to solve this problem I got this when I followed the sound troubleshooting guide at [https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation](https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation)
 I have made steps in Alsa driver compilation and Using alsa-source parts


kowic@Strangedevice:/usr/src/modules/alsa-driver$ sudo make install
if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /usr/src/modules/alsa-driver/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.27-7-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/usr/src/modules/alsa-driver/acore'
mkdir -p /lib/modules/2.6.27-7-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.27-7-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make: *** [install-modules] Error 1



Do I have alsa drivers compilaed or is this an error that ruined the process ?


THANKS IN ADVANCE

---

### Post by Yellow Pasque on 2008-11-15
This thread is pretty pointless now that there's an excellent script to build the entire ALSA 1.0.18a suite:
Please use the script that the first post links to (here): [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

I've updated the documentation to point to the correct place.

---

### Post by kowic on 2008-11-15
thanks I am using it right now :D...

---

### Post by nickleus on 2008-12-02
> **Temüjin said:**
> Now, open /etc/modprobe.d/alsa-base with the following command:
```
gksudo gedit /etc/modprobe.d/alsa-base
```Modify or add this line with *modelname* = to the appropriate model name from the list below:
```
options snd-hda-intel model=*modelname*
``````
  Module snd-hda-intel
  --------------------

...
    ALC267/268
      acer        Acer laptops

```
thank you so much. i have been plagued by an annoying clicking sound problem whenever i play anything and all i had to do to fix it was:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add the following line at the bottom of the file:
```
options snd-hda-intel model=*acer*
```

---

### Post by geek#237,598,666 on 2008-12-30
just followed Temujin's post on my acer aspire 4920 running hardy heron and it now works.

ie the sound comes out good and the mic input works.

specifically I added the following line to my modprobe.d

```
options snd-hda-intel model=acer
```

I'm so happy I could skype.  And indeed now the mic is working I can!!!

Thanks Temujin

---

### Post by marquee moon on 2009-01-04
thanks very much, Temujin, this is great! 

Using Ubuntu 8.04 on Toshiba Satellite L30 11D: 

options snd-hda-intel model=dallas

Then un-muted headphones in alsamixer

In four years of using Ubuntu,this is the first time I have ever had speakers and headphones working on this laptop.

---

### Post by himanshuprakash on 2009-02-17
Hi,
I've exactly followed what you d have written out here. I've installed ALSA 1.0.16. I got Applications-->Sounds and Vedio-->Alsaplayer

on clicking neither it opens nor any audio output comes.
any idea whats wrong, I am having Lenovo Y410 Notebook.

Thanks!
Himanshu

> **Temüjin said:**
> [SIZE="4"]**Configuring alsa-base**[/SIZE]

**To identify your codec:**
```
aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```

Now, open /etc/modprobe.d/alsa-base with the following command:
```
gksudo gedit /etc/modprobe.d/alsa-base
```

Modify or add this line with *modelname* = to the appropriate model name from the list below:
```
options snd-hda-intel model=*modelname*
```

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
	  lenovo	Lenovo 3000 C200 & ASUS X20SG, ASUS U1E
	  dallas	Dallas laptops, Toshiba satellite L30-106
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

---

### Post by hyperair on 2009-02-17
@himanshuprakash: I'm also using the Lenovo Y410 notebook. Compiling ALSA from source is only required in Hardy, because the kernel's version (1.0.16) does not have an appropriate driver for this notebook. However, as of Intrepid, sound works out of the box.

---

### Post by dan_s28 on 2009-04-03
Thanks Temujin. Your thread helped me alot. Keep up the good work!

-Dan

---

### Post by jjroper on 2009-04-05
Sorry, I should say that I am also using Jaunt-Jackalope, not Intrepid Ibex anymore.

I am confused.  First, I followed all the instructions and still have no sound.

But, alsa-base does not exist, while alsa-base.config does.  So, I assume that is the file to modify.

Next, when I do the Codec, I get:

james@Jim-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9205
Codec: LSI ID 1040

So, I put the following line in the alsabase.config file:
options snd-hda-intel model=STAC9205

While I do get different options in the sound controllers, I still get no sound (it works in windows vista).  I am using a Gateway laptop, M-series.

Any other suggestions or am I missing something?

Thanks,

Jim

---

### Post by gnulab on 2009-05-21
I don't know if this thread is obsolete, but I just want to report the results of what I had done.

My laptop is Compaq Presario, CQ40-324TU

```

cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD71B7X
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG
``````

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Alsamixer 1.0.18 reported:
Card: HDA Intel
Chip: Intel G45 DEVCTG

Solved by following instruction from this thread
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Hope this help.
Henry

---

### Post by yasitya on 2009-08-10
Oh joy! I'm a new new newbie.. Finally got the sound to work! I had no sound in firefox, or system sounds either. I'm running Ubuntu Jaunty 9.04

I'm on an Acer Aspire 5670..

I kept getting permission denied to edit the script.

This worked
sudo nano /etc/modprobe.d/alsa-base
then within the editor
options snd-hda-intel model=*acer*
to Exit ctrl-shift-number 6 then X- 

saved 

rebooted.

sound all around.

---

### Post by sadalsuud on 2009-08-13
Thank you guys! You solved my problem. I have a Benq Joybook P52 and after adding the model=basic I can listen to music also on my headphones. Thank again and keep helping the helpless!

---

### Post by Yehudama on 2010-08-23
Helpppppp Please!

I have installed 10.4 lucid , my laptop is ACER ASPIRE 4930ZG
Need configuration for the alsa.conf file , my internal mic is noisy
and in Skype is dead.

ehudama@yehudama-laptop:~$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices:1/1
  Subdevices: #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevices: #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevices: #0: subdevice #0

Try to put in alsa.conf file:

options snd-hda-intel model=acer-aspire-4930g 

doesn't help much.  any solution?

---

### Post by wazzuup on 2010-11-01
Hello, comrades. I've bought Asus k52d laptop. Installed Ubuntu 10.04 on it. At first time sound worked fine. But after I have installed Radeon drivers, it disappeared. After some manipulations I made it working, but ONLY through headphones jack. As I think, the problem now is that I cannot set correct audiodevice type in   [FONT=&quot]
"options snd-hda-intel model=" [/FONT]string.
My analog audio device is ALC259, but I cannot find model definitions for it anywhere. I tried to use such ones as "asus-mode1..6" some of them don't work, and some allows only headphones.
And don't ask me about mixer volume/mute :D

Thank you guys.

---

