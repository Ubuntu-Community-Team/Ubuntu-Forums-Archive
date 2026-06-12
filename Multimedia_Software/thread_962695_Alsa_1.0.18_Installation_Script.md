---
title: "Alsa 1.0.18 Installation Script"
date: 2008-10-29
forum: Multimedia Software
---

### Post by soundcheck on 2008-10-29
Latest post update 01/21/2009


THIS THREAD IS FROM NOW ON CONTINUED OVER HERE:

[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

---

### Post by skinnie on 2008-10-29
worked very good for me..
HP DV9575Ep with intel HDA (realtek alc268 )
Thank you very much :)

---

### Post by ~TheMik on 2008-10-29
Finally the other two kept failing on me, but this worked....well sort of.

Now when I open amarok and trying to play it freezes.  If I select pulseaudio it will play no problems through 2 speakers only, even though the daemon.conf says 6 speakers.  If I restart the x server then sound is fine and through pref < sounds I can play test sounds on pulse or alsa it is fine.  As soon as I try to play through amarok with alsa then it freezes and I can no longer do test sounds.  So I tryed mplayer set to pulse, just fine.  I tryed it again with alsa set and unlike amarok it did play, but it was very slow and popped and clicked.  I did notice that it said it was 44100 Hz, and I am not sure but I believe my cmi9761 (SI7012) is 48000 Hz only.  So I will look into that.

As far as the script goes, thanks seemed to work great!!

Edit:

I got sick of messing with it and opened the package manager, searched alsa, and everything marked installed I set to reinstall and now it is fine.  So I guess if you need to rollback you can try that.

---

### Post by soundcheck on 2008-10-30
> **~TheMik said:**
> Finally the other two kept failing on me, but this worked....well sort of.

Now when I open amarok and trying to play it freezes.  If I select pulseaudio it will play no problems through 2 speakers only, even though the daemon.conf says 6 speakers.  If I restart the x server then sound is fine and through pref < sounds I can play test sounds on pulse or alsa it is fine.  As soon as I try to play through amarok with alsa then it freezes and I can no longer do test sounds.  So I tryed mplayer set to pulse, just fine.  I tryed it again with alsa set and unlike amarok it did play, but it was very slow and popped and clicked.  I did notice that it said it was 44100 Hz, and I am not sure but I believe my cmi9761 (SI7012) is 48000 Hz only.  So I will look into that.

As far as the script goes, thanks seemed to work great!!

Edit:

I got sick of messing with it and opened the package manager, searched alsa, and everything marked installed I set to reinstall and now it is fine.  So I guess if you need to rollback you can try that.

Did you reboot the system after the upgrade?
Did you check alsamixer if all channels are active and unmuted?
You should run the uxchecker script. This will deliver most of the data
needed to track down the issue.
Pulse might upsample - depending on your settings - to 48khz by default. Amarok also upsamples to 48khz by default. Alsa sounds are usually also played in 48khz. Strange that Amarok locks up the system. That should never happen.

---

### Post by jimifelony on 2008-10-30
Hi I'm running ubuntu 8.04 64 bit, I selected 1.0.18, the script failed compiling utils, the log says: 

```
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
alsa-utils-1.0.18 make failed

```

I've done a sudo apt-get install libasound2-dev but am told I have the latest version.

Any ideas?

---

### Post by jimifelony on 2008-10-30
So ihacked my way through the dependency issues by installing the debs for libasound2 and libasound2-dev from the intrepid repository, now I have the following issue:

```
gcc  -g -O2   -o aplay  aplay.o  -lasound -lm -ldl -lpthread
aplay.o: In function `do_test_position':
/usr/src/Alsa-1.0.18/alsa-utils-1.0.18/aplay/aplay.c:1403: undefined reference to `snd_pcm_avail_delay'
collect2: ld returned 1 exit status
make[1]: *** [aplay] Error 1
make[1]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-utils-1.0.18/aplay'
make: *** [all-recursive] Error 1
alsa-utils-1.0.18 make failed

```

now I'm stumped, I guess I'll just have to dist-upgrade to intrepid...

---

### Post by soundcheck on 2008-10-30
> **jimifelony said:**
> Hi I'm running ubuntu 8.04 64 bit, I selected 1.0.18, the script failed compiling utils, the log says: 

```
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
alsa-utils-1.0.18 make failed

```

I've done a sudo apt-get install libasound2-dev but am told I have the latest version.

Any ideas?

Hi.

1. The script downloads the latest libasound-dev from the repositories by itself. No need to do it manually.
2. All packages compiled OK except the alsa-utils. 
3. I am wondering if the newly build libasound needs to be installed (make install) prior to building the utils. When testing the whole thing I started off from an 1.0.18-rc3 installation.

I separated this step "configure/make" from "make install" on purpose. If a configure or make would fail on a later compiled package this would cause inconsistencies. Such a thing would have happened in your case. But now - your system is still untouched.

Perhaps we need to tell the utils-package where to find the new libasound-headers.

I'll check it out.

---

### Post by jimifelony on 2008-10-30
I went to the sources folder and ran make install for alsa-lib, and then afterwards for utils and utils compiled without error.

Hope this helps.

---

### Post by ~TheMik on 2008-10-30
Hey soundcheck I did use uxchecker and didn't see anything out of the ordinary as compared to the to the check to installing.  Then again I have been at this a week now so though I am learning quickly I certainly don't know much.  Everything thing in the mixer was good to go as well.  Amarok didn't lock the system, it froze during play.  I would hit the play button the graphic EQ at the bottom would start (no sound) and then just freeze.  I would have to force quit then go into System Manager and manually close amarokapp as it was using the cpu fulload.

So the "rollback" didn't quite work as excepted either.  I do have 5.1 and softvol again via the asoundrc, but there is no /ect/asound.conf anymore just the state file.  Which upon reboot sets everything back to mute (center and lfe) with no master control.  When and if I play a song then the asoundrc loads and everything is back to normal until a reboot.  I did try the apt-get to uninstall alsa with the purge command and reloading everything but that did nothing for me.  So I went into the package manager and reinstalled that way and at least I can listen to music again.  I will try more troubleshooting and see what I can find.  Right now it looks like a reinstall of hardy maybe in order (would be my 5th time cause I keep breaking things lol).

---

### Post by karltron on 2008-10-30
> **jimifelony said:**
> Hi I'm running ubuntu 8.04 64 bit, I selected 1.0.18, the script failed compiling utils, the log says: 

```
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
alsa-utils-1.0.18 make failed

```

I've done a sudo apt-get install libasound2-dev but am told I have the latest version.

Any ideas?


I have the same issue.  My other problem is that I'm a linux newbie, so i might have trouble following these directions.

I have an old intel motherboarded pentium3 with a newish install of Hardy Heron.  The sound card is onboard and I havent checked the chipset name yet.  Sound works under Windows without special drivers due to the age of the board, and I don't really know what to do with linux.  This was the first thing I tried, because this script looks like it takes care of everything for me. I ran the 1.0.18 under the assumption that bigger numbers are better.

This was the result:
```
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
alsa-utils-1.0.18 make failed

```

Thanks for any support, and let me know if I can get you any extra information about the system environment.

---

### Post by Yellow Pasque on 2008-10-31
Many people will find this useful:

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

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8, ICH9, ICH10,
			PCH, SCH),
		ATI SB450, SB600, R600, RS600, RS690, RS780, RV610, RV620,
			RV630, RV635, RV670, RV770,
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
	  hp-dc7600	HP DC7600
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
	  toshiba-s06	Toshiba S06
	  toshiba-rx1	Toshiba RX1
	  ultra		Samsung Q1 Ultra Vista model
	  lenovo-3000	Lenovo 3000 y410
	  nec		NEC Versa S9100
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC267/268
	  quanta-il1	Quanta IL1 mini-notebook
	  3stack	3-stack model
	  toshiba	Toshiba A205
	  acer		Acer laptops
	  acer-aspire	Acer Aspire One
	  dell		Dell OEM laptops (Vostro 1200)
	  zepto		Zepto laptops
	  test		for testing/debugging purpose, almost all controls can
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC269
	  basic		Basic preset
	  quanta	Quanta FL1
	  eeepc-p703	ASUS Eeepc P703 P900A
	  eeepc-p901	ASUS Eeepc P901 S101

	ALC662/663
	  3stack-dig	3-stack (2-channel) with SPDIF
	  3stack-6ch	 3-stack (6-channel)
	  3stack-6ch-dig 3-stack (6-channel) with SPDIF
	  6stack-dig	 6-stack with SPDIF
	  lenovo-101e	 Lenovo laptop
	  eeepc-p701	ASUS Eeepc P701
	  eeepc-ep20	ASUS Eeepc EP20
	  ecs		ECS/Foxconn mobo
	  m51va		ASUS M51VA
	  g71v		ASUS G71V
	  h13		ASUS H13
	  g50v		ASUS G50V
	  asus-mode1	ASUS
	  asus-mode2	ASUS
	  asus-mode3	ASUS
	  asus-mode4	ASUS
	  asus-mode5	ASUS
	  asus-mode6	ASUS
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
	  lenovo-sky	Lenovo Sky
	  haier-w66	Haier W66
	  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
	  6stack-dell	Dell machines with 6stack (Inspiron 530)
	  mitac		Mitac 8252D
	  clevo-m720	Clevo M720 laptop series
	  fujitsu-pi2515 Fujitsu AMILO Pi2515
	  3stack-6ch-intel Intel DG33* boards
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

	AD1882 / AD1882A
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
	  intel-mac-auto Intel Mac (detect type according to subsystem id)
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
```

---

### Post by soundcheck on 2008-10-31
Hi folks.

I need to update the script. You'll find a revision 1.11. for download

Obviously the lib has to be installed with "make install", prior to 
compiling the utils. So - my guess was right.


BTW: I am not available for the next 3 days!!! Don't expect me to answer your questions while I am away.

THX for the feedback.

---

### Post by fjf on 2008-10-31
Does this help in getting spdif out with pulseaudio?.  If so I may try it.

---

### Post by koruptid on 2008-10-31
Is there a launchpad repository for 1.0.18? as much as source builds sounds like an adventure almost worth trying, I'd rather be garnering packages from the ubuntu development team.

---

### Post by knap on 2008-10-31
make: *** [compile] Error 2
alsa-driver-1.0.18 make failed

Your ALSA information is located at 
[http://www.alsa-project.org/db/?f=fe34ce703acc1fd58819eafa9c1ae9f2b4fa1071]("http://www.alsa-project.org/db/?f=fe34ce703acc1fd58819eafa9c1ae9f2b4fa1071")

```

-------------------------------------------------------------
-  Working on following Alsa packages...
-------------------------------------------------------------

Driver: alsa-driver-1.0.18
Library: alsa-lib-1.0.18
Plugins: alsa-plugins-1.0.18
Utils: alsa-utils-1.0.18
Firmware: alsa-firmware-1.0.17
OSS: alsa-oss-1.0.17

-------------------------------------------------------------
-  Installing packages required to build ALSA...
-------------------------------------------------------------

Lettura della lista dei pacchetti in corso...
Generazione dell'albero delle dipendenze in corso...
Lettura informazioni sullo stato...
build-essential è già alla versione più recente.
libsysfs-dev è già alla versione più recente.
libncurses5-dev è già alla versione più recente.
libncurses5-dev impostato per installazione manuale.
gettext è già alla versione più recente.
gettext impostato per installazione manuale.
linux-headers-2.6.27-7-generic è già alla versione più recente.
libpulse-dev è già alla versione più recente.
I seguenti pacchetti erano stati automaticamente installati e non sono più richiesti:
  libmime-types-perl libnet-ssleay-perl libfile-remove-perl
  libdigest-sha1-perl bison libboost-signals1.34.1 libossp-uuid-perl
  libboost-program-options1.34.1 libmudflap0-dev libcrypt-ssleay-perl quilt
  libboost-date-time1.34.1 libestools1.2 libmime-tools-perl
  libboost-test1.34.1 libboost-iostreams1.34.1 libboost-wave1.34.1
  libboost-graph1.34.1 libfcgi-perl cdbs libaspell-dev festlex-cmu intltool
  libsoap-lite-perl fdupes festvox-kallpc16k kttsd libmikmod2
  libboost-thread1.34.1 libmudflap0 libmail-box-perl module-assistant flex
  debconf-utils kernel-package xli libboost-serialization1.34.1 libcamel1.2-13
  festival festlex-poslex libboost-regex1.34.1 libobject-realize-later-perl
  libuser-identity-perl libconvert-binhex-perl libio-socket-ssl-perl
  libossp-uuid15 libdigest-hmac-perl libboost-filesystem1.34.1
Usare 'apt-get autoremove' per rimuoverli.
I seguenti pacchetti verranno inoltre installati:
  docbook-xsl docbook-xsl-doc-html python-all python2.4 python2.4-dev
  python2.4-minimal
Pacchetti suggeriti:
  fop libsaxon-java xalan python2.4-doc python-profiler
I seguenti pacchetti NUOVI (NEW) saranno installati:
  docbook-xsl docbook-xsl-doc-html libspeex-dev python-all python-all-dev
  python2.4 python2.4-dev python2.4-minimal xmlto
0 aggiornati, 9 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 7655kB di archivi. 
Dopo quest'operazione, verranno occupati 37,4MB di spazio su disco.
Get:1 http://it.archive.ubuntu.com intrepid/main docbook-xsl 1.73.2.dfsg.1-4 [1345kB]
Get:2 http://it.archive.ubuntu.com intrepid/main docbook-xsl-doc-html 1.73.2.dfsg.1-4 [551kB]
Get:3 http://it.archive.ubuntu.com intrepid/main libspeex-dev 1.2~beta4-2 [82,5kB]
Get:4 http://it.archive.ubuntu.com intrepid/main python2.4-minimal 2.4.5-5ubuntu1 [1063kB]
Get:5 http://it.archive.ubuntu.com intrepid/main python2.4 2.4.5-5ubuntu1 [2931kB]
Get:6 http://it.archive.ubuntu.com intrepid/main python-all 2.5.2-1ubuntu1 [892B]
Get:7 http://it.archive.ubuntu.com intrepid/main python2.4-dev 2.4.5-5ubuntu1 [1644kB]
Get:8 http://it.archive.ubuntu.com intrepid/main python-all-dev 2.5.2-1ubuntu1 [910B]
Get:9 http://it.archive.ubuntu.com intrepid/main xmlto 0.0.20-3 [35,8kB]
Scaricato 7655kB in 1min58s (64,4kB/s)
Selezionato il pacchetto docbook-xsl, che non lo era.
(Lettura del database ... 203538 file e directory attualmente installati.)
Spacchetto docbook-xsl (da .../docbook-xsl_1.73.2.dfsg.1-4_all.deb) ...
Selezionato il pacchetto docbook-xsl-doc-html, che non lo era.
Spacchetto docbook-xsl-doc-html (da .../docbook-xsl-doc-html_1.73.2.dfsg.1-4_all.deb) ...
Selezionato il pacchetto libspeex-dev, che non lo era.
Spacchetto libspeex-dev (da .../libspeex-dev_1.2~beta4-2_amd64.deb) ...
Selezionato il pacchetto python2.4-minimal, che non lo era.
Spacchetto python2.4-minimal (da .../python2.4-minimal_2.4.5-5ubuntu1_amd64.deb) ...
Selezionato il pacchetto python2.4, che non lo era.
Spacchetto python2.4 (da .../python2.4_2.4.5-5ubuntu1_amd64.deb) ...
Selezionato il pacchetto python-all, che non lo era.
Spacchetto python-all (da .../python-all_2.5.2-1ubuntu1_all.deb) ...
Selezionato il pacchetto python2.4-dev, che non lo era.
Spacchetto python2.4-dev (da .../python2.4-dev_2.4.5-5ubuntu1_amd64.deb) ...
Selezionato il pacchetto python-all-dev, che non lo era.
Spacchetto python-all-dev (da .../python-all-dev_2.5.2-1ubuntu1_all.deb) ...
Selezionato il pacchetto xmlto, che non lo era.
Spacchetto xmlto (da .../xmlto_0.0.20-3_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for menu ...
Configuro docbook-xsl (1.73.2.dfsg.1-4) ...

Configuro docbook-xsl-doc-html (1.73.2.dfsg.1-4) ...

Configuro libspeex-dev (1.2~beta4-2) ...
Configuro python2.4-minimal (2.4.5-5ubuntu1) ...
Linking and byte-compiling packages for runtime python2.4...

Configuro python2.4 (2.4.5-5ubuntu1) ...

Configuro python-all (2.5.2-1ubuntu1) ...
Configuro python2.4-dev (2.4.5-5ubuntu1) ...
Configuro python-all-dev (2.5.2-1ubuntu1) ...
Configuro xmlto (0.0.20-3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Lettura della lista dei pacchetti in corso...
Generazione dell'albero delle dipendenze in corso...
Lettura informazioni sullo stato...
libavutil-dev è già alla versione più recente.
libasound2-dev è già alla versione più recente.
libasound2-dev impostato per installazione manuale.
I seguenti pacchetti erano stati automaticamente installati e non sono più richiesti:
  libmime-types-perl libnet-ssleay-perl libfile-remove-perl
  libdigest-sha1-perl bison libboost-signals1.34.1 libossp-uuid-perl
  libboost-program-options1.34.1 libmudflap0-dev libcrypt-ssleay-perl quilt
  libboost-date-time1.34.1 libestools1.2 libmime-tools-perl
  libboost-test1.34.1 libboost-iostreams1.34.1 libboost-wave1.34.1
  libboost-graph1.34.1 libfcgi-perl cdbs libaspell-dev festlex-cmu intltool
  libsoap-lite-perl fdupes festvox-kallpc16k kttsd libmikmod2
  libboost-thread1.34.1 libmudflap0 libmail-box-perl module-assistant flex
  debconf-utils kernel-package xli libboost-serialization1.34.1 libcamel1.2-13
  festival festlex-poslex libboost-regex1.34.1 libobject-realize-later-perl
  libuser-identity-perl libconvert-binhex-perl libio-socket-ssl-perl
  libossp-uuid15 libdigest-hmac-perl libboost-filesystem1.34.1
Usare 'apt-get autoremove' per rimuoverli.
I seguenti pacchetti verranno inoltre installati:
  libdc1394-22-dev libgsm1-dev libmpeg4ip-0 libtheora-dev libvorbis-dev
I seguenti pacchetti NUOVI (NEW) saranno installati:
  liba52-0.7.4-dev libavcodec-dev libavformat-dev libdc1394-22-dev libgsm1-dev
  libmpeg4ip-0 libmpeg4ip-dev libtheora-dev libvorbis-dev
0 aggiornati, 9 installati, 0 da rimuovere e 0 non aggiornati.
È necessario prendere 4601kB di archivi. 
Dopo quest'operazione, verranno occupati 16,6MB di spazio su disco.
Get:1 http://it.archive.ubuntu.com intrepid/universe liba52-0.7.4-dev 0.7.4-11ubuntu1 [47,1kB]
Get:2 http://it.archive.ubuntu.com intrepid/main libgsm1-dev 1.0.12-1 [35,1kB]
Get:3 http://it.archive.ubuntu.com intrepid/main libtheora-dev 1.0~beta3-1 [341kB]
Get:4 http://it.archive.ubuntu.com intrepid/main libvorbis-dev 1.2.0.dfsg-3.1 [479kB]
Get:5 http://it.archive.ubuntu.com intrepid/main libdc1394-22-dev 2.0.2-1 [146kB]
Get:6 http://it.archive.ubuntu.com intrepid/main libavcodec-dev 3:0.svn20080206-12ubuntu3 [2002kB]
Get:7 http://it.archive.ubuntu.com intrepid/main libavformat-dev 3:0.svn20080206-12ubuntu3 [407kB]
Get:8 http://it.archive.ubuntu.com intrepid/multiverse libmpeg4ip-0 1:1.6dfsg-0.2ubuntu3 [518kB]
Get:9 http://it.archive.ubuntu.com intrepid/multiverse libmpeg4ip-dev 1:1.6dfsg-0.2ubuntu3 [625kB]
Scaricato 4601kB in 59s (77,0kB/s)
Selezionato il pacchetto liba52-0.7.4-dev, che non lo era.
(Lettura del database ... 206167 file e directory attualmente installati.)
Spacchetto liba52-0.7.4-dev (da .../liba52-0.7.4-dev_0.7.4-11ubuntu1_amd64.deb) ...
Selezionato il pacchetto libgsm1-dev, che non lo era.
Spacchetto libgsm1-dev (da .../libgsm1-dev_1.0.12-1_amd64.deb) ...
Selezionato il pacchetto libtheora-dev, che non lo era.
Spacchetto libtheora-dev (da .../libtheora-dev_1.0~beta3-1_amd64.deb) ...
Selezionato il pacchetto libvorbis-dev, che non lo era.
Spacchetto libvorbis-dev (da .../libvorbis-dev_1.2.0.dfsg-3.1_amd64.deb) ...
Selezionato il pacchetto libdc1394-22-dev, che non lo era.
Spacchetto libdc1394-22-dev (da .../libdc1394-22-dev_2.0.2-1_amd64.deb) ...
Selezionato il pacchetto libavcodec-dev, che non lo era.
Spacchetto libavcodec-dev (da .../libavcodec-dev_3%3a0.svn20080206-12ubuntu3_amd64.deb) ...
Selezionato il pacchetto libavformat-dev, che non lo era.
Spacchetto libavformat-dev (da .../libavformat-dev_3%3a0.svn20080206-12ubuntu3_amd64.deb) ...
Selezionato il pacchetto libmpeg4ip-0, che non lo era.
Spacchetto libmpeg4ip-0 (da .../libmpeg4ip-0_1%3a1.6dfsg-0.2ubuntu3_amd64.deb) ...
Selezionato il pacchetto libmpeg4ip-dev, che non lo era.
Spacchetto libmpeg4ip-dev (da .../libmpeg4ip-dev_1%3a1.6dfsg-0.2ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Configuro liba52-0.7.4-dev (0.7.4-11ubuntu1) ...
Configuro libgsm1-dev (1.0.12-1) ...
Configuro libtheora-dev (1.0~beta3-1) ...
Configuro libvorbis-dev (1.2.0.dfsg-3.1) ...
Configuro libdc1394-22-dev (2.0.2-1) ...
Configuro libavcodec-dev (3:0.svn20080206-12ubuntu3) ...
Configuro libavformat-dev (3:0.svn20080206-12ubuntu3) ...
Configuro libmpeg4ip-0 (1:1.6dfsg-0.2ubuntu3) ...

Configuro libmpeg4ip-dev (1:1.6dfsg-0.2ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

-------------------------------------------------------------
-  Downloading and extracting ALSA packages...
-------------------------------------------------------------

--2008-10-31 17:00:11--  ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18.tar.bz2
           => `alsa-driver-1.0.18.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/driver ... fatto.
==> SIZE alsa-driver-1.0.18.tar.bz2 ... 2817277
==> PASV ... fatto.    ==> RETR alsa-driver-1.0.18.tar.bz2 ... fatto.
Lunghezza: 2817277 (2,7M)

     0K .......... .......... .......... .......... ..........  1%  149K 18s
    50K .......... .......... .......... .......... ..........  3%  360K 13s
   100K .......... .......... .......... .......... ..........  5% 39,9K 30s
   150K .......... .......... .......... .......... ..........  7% 37,8K 39s
   200K .......... .......... .......... .......... ..........  9% 96,8K 36s
   250K .......... .......... .......... .......... .......... 10% 44,8K 38s
   300K .......... .......... .......... .......... .......... 12% 44,1K 40s
   350K .......... .......... .......... .......... .......... 14% 40,7K 41s
   400K .......... .......... .......... .......... .......... 16% 43,1K 42s
   450K .......... .......... .......... .......... .......... 18%  124K 39s
   500K .......... .......... .......... .......... .......... 19% 41,2K 39s
   550K .......... .......... .......... .......... .......... 21% 40,7K 40s
   600K .......... .......... .......... .......... .......... 23% 41,2K 40s
   650K .......... .......... .......... .......... .......... 25%  137K 37s
   700K .......... .......... .......... .......... .......... 27% 41,9K 37s
   750K .......... .......... .......... .......... .......... 29% 40,5K 37s
   800K .......... .......... .......... .......... .......... 30% 40,6K 36s
   850K .......... .......... .......... .......... .......... 32% 42,7K 36s
   900K .......... .......... .......... .......... .......... 34%  126K 34s
   950K .......... .......... .......... .......... .......... 36% 40,2K 33s
  1000K .......... .......... .......... .......... .......... 38% 40,8K 33s
  1050K .......... .......... .......... .......... .......... 39% 41,3K 32s
  1100K .......... .......... .......... .......... .......... 41%  149K 30s
  1150K .......... .......... .......... .......... .......... 43% 39,7K 30s
  1200K .......... .......... .......... .......... .......... 45% 41,3K 29s
  1250K .......... .......... .......... .......... .......... 47% 39,8K 29s
  1300K .......... .......... .......... .......... .......... 49% 41,8K 28s
  1350K .......... .......... .......... .......... .......... 50%  151K 26s
  1400K .......... .......... .......... .......... .......... 52% 39,7K 25s
  1450K .......... .......... .......... .......... .......... 54% 41,0K 25s
  1500K .......... .......... .......... .......... .......... 56% 40,7K 24s
  1550K .......... .......... .......... .......... .......... 58%  149K 22s
  1600K .......... .......... .......... .......... .......... 59% 41,1K 22s
  1650K .......... .......... .......... .......... .......... 61% 39,7K 21s
  1700K .......... .......... .......... .......... .......... 63% 41,7K 20s
  1750K .......... .......... .......... .......... .......... 65% 40,7K 19s
  1800K .......... .......... .......... .......... .......... 67%  149K 18s
  1850K .......... .......... .......... .......... .......... 69% 40,6K 17s
  1900K .......... .......... .......... .......... .......... 70% 39,6K 16s
  1950K .......... .......... .......... .......... .......... 72% 41,2K 15s
  2000K .......... .......... .......... .......... .......... 74% 43,1K 14s
  2050K .......... .......... .......... .......... .......... 76%  130K 13s
  2100K .......... .......... .......... .......... .......... 78% 39,1K 12s
  2150K .......... .......... .......... .......... .......... 79% 41,3K 11s
  2200K .......... .......... .......... .......... .......... 81% 42,3K 10s
  2250K .......... .......... .......... .......... .......... 83%  135K 9s
  2300K .......... .......... .......... .......... .......... 85% 41,6K 8s
  2350K .......... .......... .......... .......... .......... 87% 40,7K 7s
  2400K .......... .......... .......... .......... .......... 89% 41,0K 6s
  2450K .......... .......... .......... .......... .......... 90% 43,2K 5s
  2500K .......... .......... .......... .......... .......... 92%  121K 4s
  2550K .......... .......... .......... .......... .......... 94% 41,0K 3s
  2600K .......... .......... .......... .......... .......... 96% 40,4K 2s
  2650K .......... .......... .......... .......... .......... 98% 42,0K 1s
  2700K .......... .......... .......... .......... .......... 99%  153K 0s
  2750K .                                                     100%  310K=55s

2008-10-31 17:01:08 (50,1 KB/s) - "alsa-driver-1.0.18.tar.bz2" salvato [2817277]

--2008-10-31 17:01:09--  ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2
           => `alsa-firmware-1.0.17.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/firmware ... fatto.
==> SIZE alsa-firmware-1.0.17.tar.bz2 ... 3408524
==> PASV ... fatto.    ==> RETR alsa-firmware-1.0.17.tar.bz2 ... fatto.
Lunghezza: 3408524 (3,2M)

     0K .......... .......... .......... .......... ..........  1%  129K 25s
    50K .......... .......... .......... .......... ..........  3%  327K 17s
   100K .......... .......... .......... .......... ..........  4% 43,0K 36s
   150K .......... .......... .......... .......... ..........  6% 38,1K 47s
   200K .......... .......... .......... .......... ..........  7%  152K 41s
   250K .......... .......... .......... .......... ..........  9% 43,1K 45s
   300K .......... .......... .......... .......... .......... 10% 39,1K 49s
   350K .......... .......... .......... .......... .......... 12% 41,7K 51s
   400K .......... .......... .......... .......... .......... 13% 41,0K 52s
   450K .......... .......... .......... .......... .......... 15%  102K 49s
   500K .......... .......... .......... .......... .......... 16% 42,8K 50s
   550K .......... .......... .......... .......... .......... 18% 41,8K 50s
   600K .......... .......... .......... .......... .......... 19% 41,0K 51s
   650K .......... .......... .......... .......... .......... 21%  136K 47s
   700K .......... .......... .......... .......... .......... 22% 41,7K 48s
   750K .......... .......... .......... .......... .......... 24% 40,9K 48s
   800K .......... .......... .......... .......... .......... 25% 40,7K 48s
   850K .......... .......... .......... .......... .......... 27% 43,0K 47s
   900K .......... .......... .......... .......... .......... 28%  123K 45s
   950K .......... .......... .......... .......... .......... 30% 41,0K 44s
  1000K .......... .......... .......... .......... .......... 31% 40,6K 44s
  1050K .......... .......... .......... .......... .......... 33% 41,8K 44s
  1100K .......... .......... .......... .......... .......... 34%  140K 41s
  1150K .......... .......... .......... .......... .......... 36% 39,8K 41s
  1200K .......... .......... .......... .......... .......... 37% 41,6K 40s
  1250K .......... .......... .......... .......... .......... 39% 40,1K 40s
  1300K .......... .......... .......... .......... .......... 40% 41,9K 39s
  1350K .......... .......... .......... .......... .......... 42%  136K 37s
  1400K .......... .......... .......... .......... .......... 43% 40,9K 37s
  1450K .......... .......... .......... .......... .......... 45% 41,1K 36s
  1500K .......... .......... .......... .......... .......... 46% 40,7K 35s
  1550K .......... .......... .......... .......... .......... 48%  166K 34s
  1600K .......... .......... .......... .......... .......... 49% 39,1K 33s
  1650K .......... .......... .......... .......... .......... 51% 40,4K 32s
  1700K .......... .......... .......... .......... .......... 52% 41,9K 31s
  1750K .......... .......... .......... .......... .......... 54% 41,0K 31s
  1800K .......... .......... .......... .......... .......... 55%  149K 29s
  1850K .......... .......... .......... .......... .......... 57% 40,2K 28s
  1900K .......... .......... .......... .......... .......... 58% 40,8K 27s
  1950K .......... .......... .......... .......... .......... 60% 40,9K 27s
  2000K .......... .......... .......... .......... .......... 61% 43,3K 26s
  2050K .......... .......... .......... .......... .......... 63%  134K 24s
  2100K .......... .......... .......... .......... .......... 64% 39,4K 23s
  2150K .......... .......... .......... .......... .......... 66% 40,9K 23s
  2200K .......... .......... .......... .......... .......... 67% 41,5K 22s
  2250K .......... .......... .......... .......... .......... 69%  148K 20s
  2300K .......... .......... .......... .......... .......... 70% 41,5K 20s
  2350K .......... .......... .......... .......... .......... 72% 39,7K 19s
  2400K .......... .......... .......... .......... .......... 73% 41,1K 18s
  2450K .......... .......... .......... .......... .......... 75% 43,4K 17s
  2500K .......... .......... .......... .......... .......... 76%  121K 16s
  2550K .......... .......... .......... .......... .......... 78% 38,4K 15s
  2600K .......... .......... .......... .......... .......... 79% 41,3K 14s
  2650K .......... .......... .......... .......... .......... 81% 43,1K 13s
  2700K .......... .......... .......... .......... .......... 82%  135K 12s
  2750K .......... .......... .......... .......... .......... 84% 40,9K 11s
  2800K .......... .......... .......... .......... .......... 85% 41,0K 10s
  2850K .......... .......... .......... .......... .......... 87% 40,2K 9s
  2900K .......... .......... .......... .......... .......... 88% 41,2K 8s
  2950K .......... .......... .......... .......... .......... 90%  136K 7s
  3000K .......... .......... .......... .......... .......... 91% 41,0K 6s
  3050K .......... .......... .......... .......... .......... 93% 41,1K 5s
  3100K .......... .......... .......... .......... .......... 94% 39,9K 4s
  3150K .......... .......... .......... .......... .......... 96%  155K 3s
  3200K .......... .......... .......... .......... .......... 97% 39,5K 2s
  3250K .......... .......... .......... .......... .......... 99% 41,2K 1s
  3300K .......... .......... ........                        100% 28,7K=68s

2008-10-31 17:02:18 (49,2 KB/s) - "alsa-firmware-1.0.17.tar.bz2" salvato [3408524]

--2008-10-31 17:02:18--  ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.18.tar.bz2
           => `alsa-lib-1.0.18.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/lib ... fatto.
==> SIZE alsa-lib-1.0.18.tar.bz2 ... 790052
==> PASV ... fatto.    ==> RETR alsa-lib-1.0.18.tar.bz2 ... fatto.
Lunghezza: 790052 (772K)

     0K .......... .......... .......... .......... ..........  6%  110K 7s
    50K .......... .......... .......... .......... .......... 12%  182K 5s
   100K .......... .......... .......... .......... .......... 19% 47,0K 7s
   150K .......... .......... .......... .......... .......... 25% 41,5K 9s
   200K .......... .......... .......... .......... .......... 32%  193K 7s
   250K .......... .......... .......... .......... .......... 38% 39,9K 7s
   300K .......... .......... .......... .......... .......... 45% 37,2K 7s
   350K .......... .......... .......... .......... .......... 51% 41,2K 7s
   400K .......... .......... .......... .......... .......... 58% 41,8K 6s
   450K .......... .......... .......... .......... .......... 64% 83,0K 5s
   500K .......... .......... .......... .......... .......... 71% 47,8K 4s
   550K .......... .......... .......... .......... .......... 77% 41,7K 3s
   600K .......... .......... .......... .......... .......... 84% 40,7K 2s
   650K .......... .......... .......... .......... .......... 90%  136K 1s
   700K .......... .......... .......... .......... .......... 97% 39,3K 0s
   750K .......... .......... .                               100% 23,6K=15s

2008-10-31 17:02:34 (51,8 KB/s) - "alsa-lib-1.0.18.tar.bz2" salvato [790052]

--2008-10-31 17:02:34--  ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.18.tar.bz2
           => `alsa-plugins-1.0.18.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/plugins ... fatto.
==> SIZE alsa-plugins-1.0.18.tar.bz2 ... 312656
==> PASV ... fatto.    ==> RETR alsa-plugins-1.0.18.tar.bz2 ... fatto.
Lunghezza: 312656 (305K)

     0K .......... .......... .......... .......... .......... 16%  116K 2s
    50K .......... .......... .......... .......... .......... 32%  143K 2s
   100K .......... .......... .......... .......... .......... 49% 50,5K 2s
   150K .......... .......... .......... .......... .......... 65% 40,6K 2s
   200K .......... .......... .......... .......... .......... 81%  185K 1s
   250K .......... .......... .......... .......... .......... 98% 38,0K 0s
   300K .....                                                 100%  208K=4,6s

2008-10-31 17:02:41 (66,1 KB/s) - "alsa-plugins-1.0.18.tar.bz2" salvato [312656]

alsa-plugins-1.0.18/
alsa-plugins-1.0.18/depcomp
alsa-plugins-1.0.18/usb_stream/
alsa-plugins-1.0.18/usb_stream/Makefile.in
alsa-plugins-1.0.18/usb_stream/pcm_usb_stream.c
alsa-plugins-1.0.18/usb_stream/Makefile.am
alsa-plugins-1.0.18/usb_stream/usb_stream.h
alsa-plugins-1.0.18/ltconfig
alsa-plugins-1.0.18/COPYING.GPL
alsa-plugins-1.0.18/ltmain.sh
alsa-plugins-1.0.18/acinclude.m4
alsa-plugins-1.0.18/configure.in
alsa-plugins-1.0.18/jack/
alsa-plugins-1.0.18/jack/Makefile.in
alsa-plugins-1.0.18/jack/pcm_jack.c
alsa-plugins-1.0.18/jack/Makefile.am
alsa-plugins-1.0.18/oss/
alsa-plugins-1.0.18/oss/pcm_oss.c
alsa-plugins-1.0.18/oss/Makefile.in
alsa-plugins-1.0.18/oss/ctl_oss.c
alsa-plugins-1.0.18/oss/Makefile.am
alsa-plugins-1.0.18/pulse/
alsa-plugins-1.0.18/pulse/pulse.c
alsa-plugins-1.0.18/pulse/Makefile.in
alsa-plugins-1.0.18/pulse/ctl_pulse.c
alsa-plugins-1.0.18/pulse/conf_pulse.c
alsa-plugins-1.0.18/pulse/pcm_pulse.c
alsa-plugins-1.0.18/pulse/Makefile.am
alsa-plugins-1.0.18/pulse/pulse.h
alsa-plugins-1.0.18/maemo/
alsa-plugins-1.0.18/maemo/types.h
alsa-plugins-1.0.18/maemo/reporting.h
alsa-plugins-1.0.18/maemo/dsp-protocol.c
alsa-plugins-1.0.18/maemo/dsp-protocol.h
alsa-plugins-1.0.18/maemo/Makefile.in
alsa-plugins-1.0.18/maemo/Makefile.am
alsa-plugins-1.0.18/maemo/constants.h
alsa-plugins-1.0.18/maemo/dsp-ctl.c
alsa-plugins-1.0.18/maemo/debug.h
alsa-plugins-1.0.18/maemo/alsa-dsp.c
alsa-plugins-1.0.18/maemo/list.h
alsa-plugins-1.0.18/mix/
alsa-plugins-1.0.18/mix/pcm_upmix.c
alsa-plugins-1.0.18/mix/Makefile.in
alsa-plugins-1.0.18/mix/Makefile.am
alsa-plugins-1.0.18/mix/pcm_vdownmix.c
alsa-plugins-1.0.18/configure
alsa-plugins-1.0.18/Makefile.in
alsa-plugins-1.0.18/rate-lavc/
alsa-plugins-1.0.18/rate-lavc/gcd.h
alsa-plugins-1.0.18/rate-lavc/Makefile.in
alsa-plugins-1.0.18/rate-lavc/rate_lavcrate.c
alsa-plugins-1.0.18/rate-lavc/Makefile.am
alsa-plugins-1.0.18/version
alsa-plugins-1.0.18/rate/
alsa-plugins-1.0.18/rate/Makefile.in
alsa-plugins-1.0.18/rate/Makefile.am
alsa-plugins-1.0.18/rate/rate_samplerate.c
alsa-plugins-1.0.18/doc/
alsa-plugins-1.0.18/doc/lavcrate.txt
alsa-plugins-1.0.18/doc/upmix.txt
alsa-plugins-1.0.18/doc/README-jack
alsa-plugins-1.0.18/doc/speexrate.txt
alsa-plugins-1.0.18/doc/a52.txt
alsa-plugins-1.0.18/doc/Makefile.in
alsa-plugins-1.0.18/doc/README-pcm-oss
alsa-plugins-1.0.18/doc/README-pulse
alsa-plugins-1.0.18/doc/README-maemo
alsa-plugins-1.0.18/doc/samplerate.txt
alsa-plugins-1.0.18/doc/Makefile.am
alsa-plugins-1.0.18/doc/vdownmix.txt
alsa-plugins-1.0.18/config.guess
alsa-plugins-1.0.18/gitcompile
alsa-plugins-1.0.18/Makefile.am
alsa-plugins-1.0.18/a52/
alsa-plugins-1.0.18/a52/Makefile.in
alsa-plugins-1.0.18/a52/Makefile.am
alsa-plugins-1.0.18/a52/pcm_a52.c
alsa-plugins-1.0.18/config.h.in
alsa-plugins-1.0.18/aclocal.m4
alsa-plugins-1.0.18/COPYING
alsa-plugins-1.0.18/missing
alsa-plugins-1.0.18/install-sh
alsa-plugins-1.0.18/pph/
alsa-plugins-1.0.18/pph/Makefile.in
alsa-plugins-1.0.18/pph/fixed_generic.h
alsa-plugins-1.0.18/pph/speex_resampler.h
alsa-plugins-1.0.18/pph/Makefile.am
alsa-plugins-1.0.18/pph/rate_speexrate.c
alsa-plugins-1.0.18/pph/arch.h
alsa-plugins-1.0.18/pph/resample.c
alsa-plugins-1.0.18/config.sub
--2008-10-31 17:02:41--  ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.18.tar.bz2
           => `alsa-utils-1.0.18.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/utils ... fatto.
==> SIZE alsa-utils-1.0.18.tar.bz2 ... 1039779
==> PASV ... fatto.    ==> RETR alsa-utils-1.0.18.tar.bz2 ... fatto.
Lunghezza: 1039779 (1015K)

     0K .......... .......... .......... .......... ..........  4%  120K 8s
    50K .......... .......... .......... .......... ..........  9%  175K 6s
   100K .......... .......... .......... .......... .......... 14% 47,3K 10s
   150K .......... .......... .......... .......... .......... 19% 40,6K 12s
   200K .......... .......... .......... .......... .......... 24%  169K 10s
   250K .......... .......... .......... .......... .......... 29% 39,5K 11s
   300K .......... .......... .......... .......... .......... 34% 40,6K 11s
   350K .......... .......... .......... .......... .......... 39% 39,6K 11s
   400K .......... .......... .......... .......... .......... 44% 42,1K 10s
   450K .......... .......... .......... .......... .......... 49%  127K 9s
   500K .......... .......... .......... .......... .......... 54% 42,4K 8s
   550K .......... .......... .......... .......... .......... 59% 41,1K 8s
   600K .......... .......... .......... .......... .......... 64% 40,1K 7s
   650K .......... .......... .......... .......... .......... 68%  222K 6s
   700K .......... .......... .......... .......... .......... 73% 40,2K 5s
   750K .......... .......... .......... .......... .......... 78% 37,6K 4s
   800K .......... .......... .......... .......... .......... 83% 41,4K 3s
   850K .......... .......... .......... .......... .......... 88% 41,4K 2s
   900K .......... .......... .......... .......... .......... 93%  165K 1s
   950K .......... .......... .......... .......... .......... 98% 39,9K 0s
  1000K .......... .....                                      100%  188K=19s

2008-10-31 17:03:02 (53,1 KB/s) - "alsa-utils-1.0.18.tar.bz2" salvato [1039779]

--2008-10-31 17:03:02--  ftp://ftp.alsa-project.org/pub/tools/alsa-tools-1.0.18.tar.bz2
           => `alsa-tools-1.0.18.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/tools ... fatto.
==> SIZE alsa-tools-1.0.18.tar.bz2 ... 1556113
==> PASV ... fatto.    ==> RETR alsa-tools-1.0.18.tar.bz2 ... fatto.
Lunghezza: 1556113 (1,5M)

     0K .......... .......... .......... .......... ..........  3%  112K 13s
    50K .......... .......... .......... .......... ..........  6%  181K 10s
   100K .......... .......... .......... .......... ..........  9% 50,9K 16s
   150K .......... .......... .......... .......... .......... 13% 39,4K 20s
   200K .......... .......... .......... .......... .......... 16%  148K 17s
   250K .......... .......... .......... .......... .......... 19% 40,9K 18s
   300K .......... .......... .......... .......... .......... 23% 40,1K 19s
   350K .......... .......... .......... .......... .......... 26% 41,1K 20s
   400K .......... .......... .......... .......... .......... 29% 40,8K 20s
   450K .......... .......... .......... .......... .......... 32%  150K 17s
   500K .......... .......... .......... .......... .......... 36% 40,0K 17s
   550K .......... .......... .......... .......... .......... 39% 42,0K 17s
   600K .......... .......... .......... .......... .......... 42% 39,2K 16s
   650K .......... .......... .......... .......... .......... 46%  159K 15s
   700K .......... .......... .......... .......... .......... 49% 42,2K 14s
   750K .......... .......... .......... .......... .......... 52% 40,3K 13s
   800K .......... .......... .......... .......... .......... 55% 40,2K 13s
   850K .......... .......... .......... .......... .......... 59% 41,6K 12s
   900K .......... .......... .......... .......... .......... 62%  146K 11s
   950K .......... .......... .......... .......... .......... 65% 40,8K 10s
  1000K .......... .......... .......... .......... .......... 69% 39,9K 9s
  1050K .......... .......... .......... .......... .......... 72% 40,7K 8s
  1100K .......... .......... .......... .......... .......... 75%  186K 7s
  1150K .......... .......... .......... .......... .......... 78% 40,6K 6s
  1200K .......... .......... .......... .......... .......... 82% 40,2K 5s
  1250K .......... .......... .......... .......... .......... 85% 39,7K 4s
  1300K .......... .......... .......... .......... .......... 88% 41,0K 3s
  1350K .......... .......... .......... .......... .......... 92%  151K 2s
  1400K .......... .......... .......... .......... .......... 95% 41,5K 1s
  1450K .......... .......... .......... .......... .......... 98% 40,4K 0s
  1500K .......... .........                                  100%  153K=30s

2008-10-31 17:03:33 (51,3 KB/s) - "alsa-tools-1.0.18.tar.bz2" salvato [1556113]

--2008-10-31 17:03:34--  ftp://ftp.alsa-project.org/pub/oss-lib/alsa-oss-1.0.17.tar.bz2
           => `alsa-oss-1.0.17.tar.bz2'
Risoluzione di ftp.alsa-project.org... 160.217.9.25
Connessione a ftp.alsa-project.org|160.217.9.25|:21... connesso.
Accesso come utente anonymous ... Login eseguito!
==> SYST ... fatto.    ==> PWD ... fatto.
==> TYPE I ... fatto.  ==> CWD /pub/oss-lib ... fatto.
==> SIZE alsa-oss-1.0.17.tar.bz2 ... 248726
==> PASV ... fatto.    ==> RETR alsa-oss-1.0.17.tar.bz2 ... fatto.
Lunghezza: 248726 (243K)

     0K .......... .......... .......... .......... .......... 20%  128K 2s
    50K .......... .......... .......... .......... .......... 41%  197K 1s
   100K .......... .......... .......... .......... .......... 61% 45,0K 1s
   150K .......... .......... .......... .......... .......... 82% 40,9K 1s
   200K .......... .......... .......... .......... ..        100%  169K=3,2s

2008-10-31 17:03:39 (75,2 KB/s) - "alsa-oss-1.0.17.tar.bz2" salvato [248726]

alsa-oss-1.0.17/
alsa-oss-1.0.17/depcomp
alsa-oss-1.0.17/compile
alsa-oss-1.0.17/ltmain.sh
alsa-oss-1.0.17/configure.in
alsa-oss-1.0.17/oss-redir/
alsa-oss-1.0.17/oss-redir/Makefile.in
alsa-oss-1.0.17/oss-redir/oss-redir.h
alsa-oss-1.0.17/oss-redir/README
alsa-oss-1.0.17/oss-redir/Makefile.am
alsa-oss-1.0.17/oss-redir/oss-redir.c
alsa-oss-1.0.17/configure
alsa-oss-1.0.17/Makefile.in
alsa-oss-1.0.17/test/
alsa-oss-1.0.17/test/Makefile.in
alsa-oss-1.0.17/test/testaoss.in
alsa-oss-1.0.17/test/osstest.c
alsa-oss-1.0.17/test/lmixer.cc
alsa-oss-1.0.17/test/mixctl.h
alsa-oss-1.0.17/test/Makefile.am
alsa-oss-1.0.17/config.guess
alsa-oss-1.0.17/alsa/
alsa-oss-1.0.17/alsa/alsa-local.h
alsa-oss-1.0.17/alsa/pcm.c
alsa-oss-1.0.17/alsa/Makefile.in
alsa-oss-1.0.17/alsa/testaoss.in
alsa-oss-1.0.17/alsa/mixer.c
alsa-oss-1.0.17/alsa/aoss.in
alsa-oss-1.0.17/alsa/alsa-oss-emul.h
alsa-oss-1.0.17/alsa/Makefile.am
alsa-oss-1.0.17/alsa/aoss.1
alsa-oss-1.0.17/alsa/aoss.old.in
alsa-oss-1.0.17/alsa/stdioemu.c
alsa-oss-1.0.17/alsa/alsa-oss.c
alsa-oss-1.0.17/Makefile.am
alsa-oss-1.0.17/aclocal.m4
alsa-oss-1.0.17/COPYING
alsa-oss-1.0.17/missing
alsa-oss-1.0.17/install-sh
alsa-oss-1.0.17/config.sub

-------------------------------------------------------------
-  Prepare for compilation and installation...
-------------------------------------------------------------


-------------------------------------------------------------
-  Compiling drivers...
-------------------------------------------------------------

rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore'
Makefile:6: /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/Makefile.conf: Nessun file o directory
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/Rules.make:75: /Rules.make1: Nessun file o directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore'
make: *** [clean] Error 1
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/Alsa-1.0.18/alsa-driver-1.0.18
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.27-7-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.27-7-generic
checking for GCC version... ./configure: eval: line 5117: syntax error near unexpected token `)'
./configure: eval: line 5117: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... yes
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.27-7-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for i386 machine type... default
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver extra-version... 
checking for driver version... 1.0.18
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... no
checking for gfp_t... no
checking for GFP_DMA32... no
checking for page_to_pfn... no
checking for PnP suspend/resume... no
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... no
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
make dep
make[1]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore'
copying file alsa-kernel/core/info.c
patching file info.c
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 924 (offset 14 lines).
Hunk #3 succeeded at 940 (offset 14 lines).
Hunk #4 succeeded at 952 (offset 14 lines).
Hunk #5 succeeded at 1007 (offset 15 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #4 succeeded at 1564 (offset -15 lines).
Hunk #5 succeeded at 2813 (offset -15 lines).
Hunk #6 succeeded at 2866 (offset -15 lines).
Hunk #7 succeeded at 2894 (offset -15 lines).
Hunk #8 succeeded at 2910 (offset -15 lines).
Hunk #9 succeeded at 2936 (offset -15 lines).
Hunk #10 succeeded at 3024 (offset -15 lines).
Hunk #11 succeeded at 3043 (offset -15 lines).
Hunk #12 succeeded at 3057 (offset -15 lines).
Hunk #13 succeeded at 3114 (offset -15 lines).
Hunk #14 succeeded at 3142 (offset -15 lines).
Hunk #15 succeeded at 3199 (offset -15 lines).
Hunk #16 succeeded at 3228 (offset -15 lines).
Hunk #17 succeeded at 3258 (offset -15 lines).
Hunk #18 succeeded at 3336 (offset -15 lines).
Hunk #19 succeeded at 3368 (offset -15 lines).
Hunk #20 succeeded at 3433 (offset -15 lines).
Hunk #21 succeeded at 3463 (offset -15 lines).
Hunk #22 succeeded at 3507 (offset -15 lines).
Hunk #23 succeeded at 3668 (offset -15 lines).
copying file alsa-kernel/core/control.c
patching file control.c
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1293 (offset 4 lines).
Hunk #4 succeeded at 1377 (offset 4 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 997 (offset 5 lines).
Hunk #4 succeeded at 1919 (offset 5 lines).
Hunk #5 succeeded at 1964 (offset 5 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 58 (offset -11 lines).
Hunk #3 succeeded at 207 (offset -11 lines).
Hunk #4 succeeded at 245 (offset -11 lines).
Hunk #5 succeeded at 267 (offset -11 lines).
Hunk #6 succeeded at 293 (offset -11 lines).
Hunk #7 succeeded at 311 (offset -11 lines).
Hunk #8 succeeded at 519 (offset -49 lines).
Hunk #9 succeeded at 658 (offset -49 lines).
Hunk #10 succeeded at 668 (offset -49 lines).
Hunk #11 succeeded at 707 (offset -49 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/ioctl32'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/ioctl32'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #3 succeeded at 383 (offset 4 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2607 (offset 17 lines).
Hunk #4 succeeded at 2658 (offset 17 lines).
Hunk #5 succeeded at 2781 (offset 17 lines).
Hunk #6 succeeded at 2964 (offset 17 lines).
Hunk #7 succeeded at 3091 (offset 17 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/oss'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #3 succeeded at 2209 (offset 6 lines).
Hunk #4 succeeded at 2561 (offset 10 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 250 (offset 2 lines).
make[4]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #3 succeeded at 192 (offset 3 lines).
Hunk #4 succeeded at 227 (offset 4 lines).
Hunk #5 succeeded at 330 (offset 4 lines).
make[4]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/seq/oss'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/seq'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c/l3'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c/l3'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c/other'
copying file alsa-kernel/i2c/other/tea575x-tuner.c
patching file tea575x-tuner.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c/other'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/i2c'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/mpu401'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #2 succeeded at 438 (offset 2 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/opl3'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/opl4'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/opl4'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/pcsp'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/pcsp'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/vx'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers/vx'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/drivers'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/ad1816a'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/ad1816a'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/ad1848'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/ad1848'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/cs423x'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/cs423x'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/es1688'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/es1688'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/gus'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/gus'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/msnd'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/msnd'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/opti9xx'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/opti9xx'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 711 (offset 1 line).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/sb'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1947 (offset 1 line).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/wavefront'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/wss'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa/wss'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/isa'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/synth'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/synth/emux'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/synth/emux'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/synth'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1673 (offset 2 lines).
Hunk #3 succeeded at 1718 (offset 2 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3134 (offset -42 lines).
Hunk #3 succeeded at 3429 (offset -42 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2120 (offset -11 lines).
Hunk #3 succeeded at 2496 (offset -11 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #3 succeeded at 712 (offset 6 lines).
Hunk #4 succeeded at 722 (offset 6 lines).
Hunk #5 succeeded at 3173 (offset 45 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2433 (offset -3 lines).
Hunk #3 succeeded at 2443 (offset -3 lines).
Hunk #4 succeeded at 2458 (offset -3 lines).
Hunk #5 succeeded at 2469 (offset -3 lines).
Hunk #6 succeeded at 2480 (offset -3 lines).
Hunk #7 succeeded at 2563 (offset -3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1184 (offset 4 lines).
Hunk #3 succeeded at 1244 (offset 4 lines).
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1914 (offset 3 lines).
Hunk #4 succeeded at 1926 (offset 3 lines).
Hunk #5 succeeded at 1950 (offset 3 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ac97'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2207 (offset 2 lines).
Hunk #3 succeeded at 2377 (offset 2 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ali5451'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/asihpi'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/asihpi'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 339 (offset -2 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/au88x0'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/aw2'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/aw2'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1365 (offset 12 lines).
Hunk #4 succeeded at 1734 (offset 12 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ca0106'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/cs46xx'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/cs46xx'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/cs5535audio'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1894 (offset -32 lines).
Hunk #2 succeeded at 1957 (offset -32 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/echoaudio'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1636 (offset 8 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/emu10k1'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 359 (offset 80 lines).
Hunk #3 succeeded at 397 with fuzz 2 (offset 80 lines).
Hunk #4 succeeded at 412 (offset 80 lines).
Hunk #5 succeeded at 428 (offset 80 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/hda'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ice1712'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ice1712'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2342 (offset 3 lines).
Hunk #3 succeeded at 2498 (offset 3 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/korg1212'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/mixart'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/mixart'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/nm256'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/nm256'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/oxygen'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/oxygen'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/pcxhr'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/pcxhr'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/pdplus'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/pdplus'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #2 succeeded at 1280 (offset 1 line).
Hunk #3 succeeded at 2243 (offset 9 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/riptide'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/rme9652'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/rme9652'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/trident'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/trident'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/vx222'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/vx222'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2006 with fuzz 2 (offset -38 lines).
Hunk #3 succeeded at 2026 with fuzz 2 (offset -40 lines).
Hunk #4 succeeded at 2366 (offset -40 lines).
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci/ymfpci'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pci'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/codecs'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/codecs'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/core'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/core'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/fabrics'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/fabrics'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/soundbus'
make[4]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa/soundbus'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/aoa'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/at32'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/at32'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/at91'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/at91'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/au1x'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/au1x'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/blackfin'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/blackfin'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/codecs'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/codecs'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/davinci'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/davinci'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/fsl'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/fsl'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/omap'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/omap'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/pxa'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/pxa'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/s3c24xx'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/s3c24xx'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/sh'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc/sh'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/soc'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 70 with fuzz 2.
Hunk #3 succeeded at 689 (offset 30 lines).
Hunk #4 succeeded at 716 (offset 30 lines).
Hunk #5 succeeded at 797 with fuzz 2 (offset 30 lines).
Hunk #6 succeeded at 812 with fuzz 2 (offset 30 lines).
Hunk #7 succeeded at 1188 with fuzz 1 (offset 28 lines).
Hunk #8 succeeded at 2119 (offset 37 lines).
Hunk #9 succeeded at 2138 (offset 37 lines).
Hunk #10 succeeded at 2150 (offset 37 lines).
Hunk #11 succeeded at 2163 (offset 37 lines).
Hunk #12 succeeded at 2744 (offset 57 lines).
Hunk #13 succeeded at 2816 (offset 57 lines).
Hunk #14 succeeded at 3104 (offset 57 lines).
Hunk #15 succeeded at 3175 (offset 57 lines).
Hunk #16 succeeded at 3296 (offset 57 lines).
Hunk #17 succeeded at 3314 (offset 57 lines).
Hunk #18 succeeded at 3328 (offset 57 lines).
Hunk #19 succeeded at 3341 (offset 57 lines).
Hunk #20 succeeded at 3544 (offset 56 lines).
Hunk #21 succeeded at 3637 (offset 56 lines).
Hunk #22 succeeded at 3775 (offset 57 lines).
Hunk #23 succeeded at 3836 (offset 57 lines).
Hunk #24 succeeded at 3855 (offset 57 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1510 (offset 148 lines).
Hunk #6 succeeded at 1862 (offset 156 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #3 succeeded at 1737 (offset 2 lines).
Hunk #4 succeeded at 1786 (offset 2 lines).
Hunk #5 succeeded at 1807 (offset 2 lines).
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #1 succeeded at 1 with fuzz 2.
Hunk #2 succeeded at 448 with fuzz 1 (offset -13 lines).
Hunk #3 succeeded at 511 (offset -8 lines).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
Hunk #2 succeeded at 120 (offset 6 lines).
Hunk #3 succeeded at 370 (offset 6 lines).
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb/caiaq'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb/usx2y'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/usb'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia/vx'
make[3]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia/vx'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/pcmcia'
make[2]: Entering directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/misc'
make[2]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/misc'
make[1]: Leaving directory `/usr/src/Alsa-1.0.18/alsa-driver-1.0.18'
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/usr/src/Alsa-1.0.18/alsa-driver-1.0.18  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.o
In file included from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:283:1: warning: "GFP_DMA32" redefined
In file included from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:26,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
include/linux/gfp.h:105:1: warning: this is the location of the previous definition
In file included from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:832: error: static declaration of ‘jiffies_to_msecs’ follows non-static declaration
include/linux/jiffies.h:286: error: previous declaration of ‘jiffies_to_msecs’ was here
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:851: error: static declaration of ‘msecs_to_jiffies’ follows non-static declaration
include/linux/jiffies.h:288: error: previous declaration of ‘msecs_to_jiffies’ was here
In file included from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:949,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
include/linux/pci.h:621: error: expected identifier or ‘(’ before numeric constant
In file included from include/asm/pci.h:4,
                 from include/linux/pci.h:983,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:949,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
include/linux/mm.h:261: error: conflicting types for ‘snd_compat_vmalloc_to_page’
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:753: error: previous declaration of ‘snd_compat_vmalloc_to_page’ was here
In file included from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:1198: error: too many arguments to function ‘pci_save_state’
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:1202: error: too many arguments to function ‘pci_restore_state’
In file included from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:1564:1: warning: "page_to_pfn" redefined
In file included from include/asm/page.h:196,
                 from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/include/adriver.h:26,
                 from /usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.c:1:
include/asm-generic/memory_model.h:78:1: warning: this is the location of the previous definition
make[3]: *** [/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.18/alsa-driver-1.0.18/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18/alsa-driver-1.0.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [compile] Error 2
alsa-driver-1.0.18 make failed

```

---

### Post by blackest_knight on 2008-11-02
Oh dear The **first** scripton this thread seems to have broke on my Aspire one running Hardy.

1.0.18final Alsa drivers installed but didn't work, alsamixer failed too alsactl -v says 1.0.18
 

however the earlier script 1.0.18r3 works a treat :)

So I am reuploading it here with this Post.

I havent tried the latest revision a cpl of posts up from this one. but the first one in this thread seems broke to me.

---

### Post by MichaelRX8 on 2008-11-03
Please excuse any of my stupidity as I am very new to this. I have been trying to get sound on my acer 6920 working with intrepid. I am trying to install Alsa 1.0.18, but whenever I check the logfile it says "-------------------------------------------------------------
-  Prepare for compilation and installation...
-------------------------------------------------------------

/usr/src/Alsa-1.0.18 not found".                                                                                                  I believe I have done this script correctly but I'm very new to this stuff so any help would be greatly appreciated.

---

### Post by boluc91 on 2008-11-03
I'm getting errors when i try to "sudo modprobe snd-hda-intel"

> 
sudo modprobe snd-hda-intel
[sudo] password for bob: 
FATAL: Error inserting snd (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-7-generic/kernel/sound/modules/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I added dmesg to you're uxchecker -a output...
If you need more info, just say so.

Additional info:
I have a ICH8 (Asus p5b) on board soundcard, Ubuntu 8.10, linux 2.6.27-7-generic and alsa 1.18 installed with AlsaUpgrade-1.0.x-rev-1.11.sh
aplay -l returns nothing, lspci | grep Audio does return the soundcard.
And well I was about to try modprobe snd-hda-intel and then add it to the modules list.

Oh and the sound didn't work before either....
But modprobe did.

-Bob

---

### Post by soundcheck on 2008-11-03
Hi there.

Quite some strange errors around here?!?

If all the 160 people who downloaded the script by now have used it
successfully, we are talking not about a generic issue with the script -
I hope.

1. The guys with the alsa-utils-error: Did you make it work?

2. Hint: During these early days of Intrepid the kernel will be upgraded more often.
If aplay -l doesn't show anything you should try to install the drivers again. 

The same if you're using two kernels. You can just install Alsa on one kernel. I discussed it with the Alsa guys. (This is the same with e.g. the
fglrx driver.) 
The Alsa guys are planning to introduce Alsa to dkms sooner or later.
This way Alsa would be autoinstalled on different kernels. 

3. You can or even should also issue 1.0.18 TroubleTickets especially driver related problems - on the Alsa-Mailing List. 
[http://mailman.alsa-project.org/mailman/listinfo/alsa-devel](http://mailman.alsa-project.org/mailman/listinfo/alsa-devel)
They don't really use bugtracker or launchpad or similar.
You can of course limit the risk of failure if you compile the alsa-drivers just for your particular soundcard.

4. The whole Alsa installation procedure should be done only by people, who know what they are doing and who are able to understand what's done in the script. Linux
beginners should not start with a manual installation of Alsa. 
This for sure will cause quite some frustration. 

5. In any way in case of problems the way to go is - "Google" . 
I do not do it any different in most of the cases. 
Usually you can Google the exact error message.



6. If you look for new features something like "SPDIF over pulseaudio", ;) what I wouldn't call a feature. Since SPDIF is a driver issue and 
if the driver/codec shows an SPDIF output you'd be able to run it with pulse. This would be the wrong place You should know that you need 1.0.18
or you're a hacker who's happy only with the very latest revision number
of everything.

In case of new features or bugfixes you need to look up the revision changelogs at the Alsa homepage. Just do this exercise for fun and you'll start appreciate what these poor guys have to manage. I 
think it is ridiculous that the soundcard industry is not putting at least a bit support into this. 

Alsa is getting more and more complex. Some cards need even e.g. video drivers loaded to compile properly. I personally won't be able to cover it.

If it turns out that the script is very unstable and causing damage I'll 
take it out again.

Cheers

---

### Post by strigia on 2008-11-06
Hi,
I used the alsa upgrade script on Acer Aspire one 150L with ubuntu, the log said me "Installation successfully finished". Now I have alsa 1.0.18 the sound, mic, headphone work but when I put headphone the system doesn't mute speakers.
I tried the command *alsamixer -V all* to see the mixer but the command return "snd_mixer_load failed =invalid argument".

The gnome-alsamixer give me "segmentation fault".

How can I solve?

(excuse me from my english)

---

### Post by koschi on 2008-11-08
Thanks for the script soundcheck! I needed 1.0.18 in order to fully support my Asus Xonar DX. 
It worked like a charm for me...

---

### Post by Robbyx on 2008-11-08
I used the scripts at 

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

and changed it to 1.0.18.

I have just compiled Alsa and still no sound comes from my headphones. Since my upgrade to Intrepid I have had no sound working.

Could anyone help me get it back?

Robin

---

### Post by sreekanth27 on 2008-11-12
Hello Soundcheck,

I have tried everything possible from upgrading my ram, to reinstalling UBUNTU, to unistalling pulse, to using this forum to help but nothing helped yet. The problemw with sound still exists. Any help will be really great.

Some information from running the script and some basic information available here:

sree@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sree@ubuntu:~$ 

The rport from the script is available below:
[http://www.alsa-project.org/db/?f=83f2dfe6376edfe26a207c84d4b121a7441b3ee5](http://www.alsa-project.org/db/?f=83f2dfe6376edfe26a207c84d4b121a7441b3ee5)

I have allready checked the permissions and everything looks ok to me.. I even tried using headphones instead of my creative 4.1 speakers. When on windows I use soundmax drivers..

Thanks in advance.

regards,

---

### Post by soundcheck on 2008-11-12
Folks.

I today upgraded the script. Alsa launched a new driver package.

You'll find the changelog over here:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a](http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a)

Enjoy and Good luck.

---

### Post by Nikos.Alexandris on 2008-11-12
> **soundcheck said:**
> Folks.

I today upgraded the script. Alsa launched a new driver package.

You'll find the changelog over here:

[http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a](http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a)

Enjoy and Good luck.

Hi! I am trying to run the script... I guess it needs to be executed like
```
sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -i
```

EDIT: or better with ```
sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -f
``` (??)

since executing without "-i" doesn't do anything. I get```
-------------------------------------------------------------
-  Script usage: ./AlsaUpgrade-1.0.x-rev-1.12.sh {-f down+inst|-d ownload |-c compile | -i nstall}
-------------------------------------------------------------
``` If that's the case could you please correct the instructions in the first page?


EDIT: Also, which packages should be backed-up? Or do you mean data of the entire system? It's not clear to me.

Thank you, Nikos

---

### Post by jpichie on 2008-11-12
First off I would like to thank soundcheck for this great script.
I was initially having trouble setting all this up the way they explained it on [www.alsa-project.org](www.alsa-project.org) (for my razer ac-1). Alsa-utils-1.0.18 would always fail on compile. The only difference was they said to use arguments for the compile of alsa-driver.

So everything installed awesome on a fresh Ubuntu Intrepid. The only problem I am having is I have no sound coming out of my center speaker (5.1 setup) in any program I try (be it VLC or Amarok).

Is there possibly something I am missing? I am new to sound in Linux as I have never really used one as a desktop before.

I have kubuntu-resticted-extras installed, medibuntu repos, etc.
My VLC is set to "output module" Alsa (C-Media CMI8788(multichannel-hw:2,0)).

Any help is greatly appreciated.

---

### Post by jpichie on 2008-11-12
As a reply to Nikos:
I believe the -i didn't do anything because it was not first Downloaded ( -d ) and Compiled ( -c ).
The full install ( -f ) will do all these steps for you.

---

### Post by Nikos.Alexandris on 2008-11-12
> **jpichie said:**
> As a reply to Nikos:
I believe the -i didn't do anything because it was not first Downloaded ( -d ) and Compiled ( -c ).
The full install ( -f ) will do all these steps for you.

Thank you. I found the way to go... but I think for beginners it can be a bit confusing. I really appreciate the work that has been done. Nevertheless, the instructions (if somebody has the time) could use some nicer structuring/formatting. Not too much but some bullets, some bolded fonts, etc. would make it more attractive :-).

Cheers, Nikos

P.S. The script was installed successfully but it doesn't activate the built-in speakers on a MBP5,1. I'll try again another time...

---

### Post by Gazelem on 2008-11-13
"alsamixer -c1" was the one line that I needed from this post.  And it worked. I am now :guitar: rocking.  I can't believe that it took me so long to figure out how to change the settings.

---

### Post by costre on 2008-11-13
Thanks to this script, and Jan Saell's fine tutorial, I am now having awesome sound on my Acer 8920! 
All is good, but if anyone has tips on how to activate the extra speakers in this laptop, feel free to leave some tips!

---

### Post by wells24 on 2008-11-13
Tkx for the script

I'm having problem to have my sound card to work with Intrepid Ibex 8.10
my laptop is an acer aspire 6920
running Intrepid Ibex 8.10
Kernel 2.6.27-7-generic
Chip ALC889

Everything was working grate on ubuntu 8.04 :)
than upgrade to Ibex and sound card went down.:(



Tkx to reply

---

### Post by costre on 2008-11-14
Well, I can describe my way of getting it to work.

1.) Download and install the latest Alsa update, as described by soundcheck:
[http://ubuntuforums.org/attachment.php?attachmentid=92330&d=1226491630](http://ubuntuforums.org/attachment.php?attachmentid=92330&d=1226491630)

2.) Sudo open /etc/modprobe.d/alsa-base and find the line "options snd-hda-intel model=". Make it look like 

```
options snd-hda-intel model=acer-aspire
```

3.) Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2) . Unpack it, and use "make" in the folder to compile the files.

4.) Copy the created files into /usr/local/bin

5.) Sudo open /etc/rc.local and add the line 

```
/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
```

6.) Reboot, and it should work from now on.

That's how I did it, thanks to jansaell and soundcheck!

---

### Post by Nikos.Alexandris on 2008-11-14
> **Nikos.Alexandris said:**
> 
P.S. The script was installed successfully but it doesn't activate the built-in speakers on a MBP5,1. I'll try again another time...

Well, finally I got *some* sound out after repeating all steps. But I have only "Mono" output and not stereo. I have no idea how to fix that! Any recomendations?

EDIT: I have already posted some info about it in this thread/post [http://ubuntuforums.org/showpost.php?p=6170259&postcount=9](http://ubuntuforums.org/showpost.php?p=6170259&postcount=9).

P.S. soundcheck, thank you for your efforts.

---

### Post by clarkey45 on 2008-11-14
I've tried using this script but the driver is failing to compile. Can anyone help?

I'm running Mythbuntu 8.04 kernel 2.6.24-16-generic

My compile error:

```
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o
In file included from /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.c:2:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c: In function âsnd_hrtimer_callbackâ:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c:29: error: implicit declaration of function âhrtimer_forward_nowâ
make[3]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2

```

---

### Post by soundcheck on 2008-11-15
> **Nikos.Alexandris said:**
> Hi! I am trying to run the script... I guess it needs to be executed like
```
sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -i
```

EDIT: or better with ```
sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -f
``` (??)

since executing without "-i" doesn't do anything. I get```
-------------------------------------------------------------
-  Script usage: ./AlsaUpgrade-1.0.x-rev-1.12.sh {-f down+inst|-d ownload |-c compile | -i nstall}
-------------------------------------------------------------
``` If that's the case could you please correct the instructions in the first page?


EDIT: Also, which packages should be backed-up? Or do you mean data of the entire system? It's not clear to me.

Thank you, Nikos

Hi.

1. Yes I mean backup the system. It is always better to do that,       
   before touching the system.

2. Options:

   -f: Complete upgrade 
   
    download+compile+install. This is the choice for
    people with limited background, especially if you run the script the
    first time. 

   -d: download only
   
    Some people might want to just download all packages
    to be able to tailor the installation. 
   Some might want to patch source code before running the installation.  

   -c: compile only
    
    You can run this option as a kind of dry run. Nothing will be touched in the system. Note: Data must be "downloaded" first. Look for error messages in the output log. 
  
   -i: compile and install
   
   The -i compiles and installs the already "downloaded" source-code
   If there are no data on the disk, nothing will happen.
   The intention with this option is a) to avoid downloading data all the 
   time, especially if nothing has changed at the Alsa front and b) to avoid overwriting patched data and c) it'll speed up the process
   if you have to re-run the script e.g. after Ubuntu has overwritten Alsa data during an upgrade, kernel-upgrade or similar, or you run multiple kernels on one machine.
   
   
 Cheers

---

### Post by soundcheck on 2008-11-15
> **Nikos.Alexandris said:**
> Well, finally I got *some* sound out after repeating all steps. But I have only "Mono" output and not stereo. I have no idea how to fix that! Any recomendations?

EDIT: I have already posted some info about it in this thread/post [http://ubuntuforums.org/showpost.php?p=6170259&postcount=9](http://ubuntuforums.org/showpost.php?p=6170259&postcount=9).

P.S. soundcheck, thank you for your efforts.

Perhaps you check first which soundchip/codec is used. I guess it is a  Realtek ALC885/889A.
In the past there have been some issues with the codec. People had to patch the sound-drivers.

You can run the uxchecker.sh script. The log will tell you quite a lot about your setup.

A soundcard should - with all its features - function properly, if the correct model-id "model=XXXX" is assigned 
to your driver. 

In the uxchecker.log under "Codec" you find the ID for your device listed. Which is then probably ALC885

Within /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/alsa-kernel/Documentation/ALSA-Configuration.txt you'll find a "macpro"
model-id for this codec.

Now you need to edit /etc/modprobe.d/alsa-base and add the model:  snd-hda-intel index=0 mode=macpro

Reboot afterwards.


See also here.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If all this is not working a chat with the Alsa guys wouldn't be a bad idea.


Good luck

---

### Post by jpichie on 2008-11-15
> First off I would like to thank soundcheck for this great script.
I was initially having trouble setting all this up the way they explained it on [www.alsa-project.org](www.alsa-project.org) (for my razer ac-1). Alsa-utils-1.0.18 would always fail on compile. The only difference was they said to use arguments for the compile of alsa-driver.

So everything installed awesome on a fresh Ubuntu Intrepid. The only problem I am having is I have no sound coming out of my center speaker (5.1 setup) in any program I try (be it VLC or Amarok).

Is there possibly something I am missing? I am new to sound in Linux as I have never really used one as a desktop before.

I have kubuntu-resticted-extras installed, medibuntu repos, etc.
My VLC is set to "output module" Alsa (C-Media CMI8788(multichannel-hw:2,0)).

Any help is greatly appreciated.

Welcome back soundcheck, any idea how I could get sound from my center speaker? everything else sounds great. uxchecker log is on page 3.

---

### Post by Nikos.Alexandris on 2008-11-15
> **soundcheck said:**
> Perhaps you check first which soundchip/codec is used. I guess it is a  Realtek ALC885/889A.
In the past there have been some issues with the codec. People had to patch the sound-drivers.

You can run the uxchecker.sh script. The log will tell you quite a lot about your setup.

A soundcard should - with all its features - function properly, if the correct model-id "model=XXXX" is assigned 
to your driver. 

In the uxchecker.log under "Codec" you find the ID for your device listed. Which is then probably ALC885

Within /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/alsa-kernel/Documentation/ALSA-Configuration.txt you'll find a "macpro"
model-id for this codec.

Now you need to edit /etc/modprobe.d/alsa-base and add the model:  snd-hda-intel index=0 mode=macpro

Reboot afterwards.


See also here.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If all this is not working a chat with the Alsa guys wouldn't be a bad idea.


Good luck

soundcheck,
thank you for the support. Just some quick-feedback:

```
cat /proc/asound/card0/codec#* | grep Codec

Codec: Realtek ALC889A
```

This chip/Codec does not exist in the file *ALSA-Configuration.txt*.

Now, according to other MB(P)5,1 users [1][2] which got their sound work using the line ```
options snd_hda_intel model=mbp3
```in the file **/etc/modprobe.d/options**, I also use this setting. But this model referes to the chip/Codec **ALC882/885**.

I have found some post on the web[3] concerning the **ALC889A** chip but it will take me some time till I get into it and understand the patche that is being discussed. And maybe it's irrelevant with my hardware.

Or not even necessary!? I have sound but it's Mono. I thought that setting this in some configuration file would be easy but, I guess, it's more complex.

Tha strange thing is that before the installation of the new alsa-drivers, I had 3 *Input Sources* fields under the *Options Tab* in alsamixer and now they are gone.

Regards, Nikos

[1] [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Aluminum
[2] [http://ph.ubuntuforums.com/showthread.php?t=971236](http://ph.ubuntuforums.com/showthread.php?t=971236)
[3] [http://www.gossamer-threads.com/lists/linux/kernel/904495](http://www.gossamer-threads.com/lists/linux/kernel/904495)

---

### Post by daximus on 2008-11-15
> **clarkey45 said:**
> I've tried using this script but the driver is failing to compile. Can anyone help?

I'm running Mythbuntu 8.04 kernel 2.6.24-16-generic

My compile error:

```
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o
In file included from /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.c:2:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c: In function âsnd_hrtimer_callbackâ:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c:29: error: implicit declaration of function âhrtimer_forward_nowâ
make[3]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2

```

I got this as well.  Anyone have an idea what's missing/wrong?

---

### Post by kowic on 2008-11-15
I had no sound at all after upgrade from 8.04 to 8.10. I did instalation from the guide but problem is still here. No sound from any application nor the system "beeps". Only sound is its a short "crack" at system startup (like sound heard when you turn on your speakers). 

Testing sound with aplay gave this:

kowic@Strangedevice:/$ aplay -Dplughw:0,0 -fcd /mnt/Lovrajder.wav
aplay: main:590: audio open error: Device or resource busy


Attached logfile from uxchecker should contain required system info.

thanks for any suggestions

---

### Post by Compulsion on 2008-11-15
Thanks for the script.

1.0.17 didn't support my on-board sound, 1.0.18 does.

Motherboard: ASUSP5QL
Southbridge: Intel ICH10
Codec: VIA VT 1708S

---

### Post by copyrights on 2008-11-16
Very good work, thanks for the script. Now my macbook 5.1 runs ubuntu all the time.

But I didn't get the build-in microphone working so far. Has anyone the same problem or suggestions how to get it working?

---

### Post by soundcheck on 2008-11-16
> **daximus said:**
> I got this as well.  Anyone have an idea what's missing/wrong?

OK. Folks I check it out, with the Alsa guys. 

Perhaps you attach the Alsa log script.

---

### Post by soundcheck on 2008-11-16
> **copyrights said:**
> Very good work, thanks for the script. Now my macbook 5.1 runs ubuntu all the time.

But I didn't get the build-in microphone working so far. Has anyone the same problem or suggestions how to get it working?


Interesting that your MacBook works. What codec are you using?

Mic: Checkout Alsamixer. The mic is muted by default.

---

### Post by soundcheck on 2008-11-16
> **kowic said:**
> I had no sound at all after upgrade from 8.04 to 8.10. I did instalation from the guide but problem is still here. No sound from any application nor the system "beeps". Only sound is its a short "crack" at system startup (like sound heard when you turn on your speakers). 

Testing sound with aplay gave this:

kowic@Strangedevice:/$ aplay -Dplughw:0,0 -fcd /mnt/Lovrajder.wav
aplay: main:590: audio open error: Device or resource busy


Attached logfile from uxchecker should contain required system info.

thanks for any suggestions

You run the ALC660 codec. Please read the other posts related to 
configuring a particular sound card/codec!!


Try following: Add following line at the bottom of your alsa-base file:

options snd-hda-intel index=0 model=3stack-660

You edit it from a terminal with 

$ sudo gedit /etc/modbprobe.d/alsa.base

save&exit&reboot

Good luck

---

### Post by soundcheck on 2008-11-16
> **jpichie said:**
> Welcome back soundcheck, any idea how I could get sound from my center speaker? everything else sounds great. uxchecker log is on page 3.

Hi.

I am not really a multichannel guy. There is a lot of stuff on the web. 

However:

Try the utility speaker-test from Alsa-Utils
which generates some pink noise on each of the available channels.

E.g. for two channels:

$ speaker-test -Dplughw:0,0 -c2
or
$ speaker-test -D front -c2

or e.g. 6 channels (Note: type $aplay -L  to find out about your pcm devices)

$ speaker-test -D your-virtual51-device-as-shown-in-"aplay -L" -c6
in my case:
$ speaker-test -D surround51 -c6

If this works you need to select the correct output device within your application. 

Perhaps you also need to setup your .asoundrc properly. 
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)


Perhaps this helps.

Cheers

---

### Post by guggi on 2008-11-16
MacBook5,1

cat /proc/asound/card1/codec#0 
Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3f00
Revision Id: 0x100103
No Modem Function Group found

Mic works here!
Look at the instructions [https://help.ubuntu.com/community/MacBook%20Aluminum#Microphone](https://help.ubuntu.com/community/MacBook%20Aluminum#Microphone)

---

### Post by kowic on 2008-11-16
I have added suggested line, but it didn´t work. Then I ran alsa-info script and here´s output 
[http://www.alsa-project.org/db/?f=786ed515c4208c49799cfb5efa03c8ace2b53e17](http://www.alsa-project.org/db/?f=786ed515c4208c49799cfb5efa03c8ace2b53e17)


I have found this line as script output too :

WARNING: /etc/modprobe.d/alsa-base line 43: ignoring bad line starting with 'option'


It refers to the exact line I had added, I changed it to "options" and I´m going to reboot...be back with feedback :)

---

### Post by kowic on 2008-11-16
Problem solved by editing the early reffered line. Only sound is little rusty, but its maybe my old speakers (I hope :)

be back if sth wrong again (I hope not :)

thanks for help to SOUNDCHECK...cheers

---

### Post by copyrights on 2008-11-16
> **guggi said:**
> MacBook5,1

cat /proc/asound/card1/codec#0 
Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3f00
Revision Id: 0x100103
No Modem Function Group found

Mic works here!
Look at the instructions [https://help.ubuntu.com/community/MacBook%20Aluminum#Microphone](https://help.ubuntu.com/community/MacBook%20Aluminum#Microphone)

cat /proc/asound/card0/codec#0 
Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3f00
Revision Id: 0x100103
No Modem Function Group found

That seems to be the same, but still don't work. Under alsamixer I got the following entries.

Playback:
Master, PCM, Front, Line, Line Boost, Line-Out, Mic, Mic Boost, IEC958 (no slider), IEC958 Default PCM (no slider), Channel Mode (6ch), Speaker (no slider)

Capture:
Line Boost, Mic Boost, IEC958 (no slider), Digital

I think the capture side can't be right.

---

### Post by soundcheck on 2008-11-16
> **kowic said:**
> Problem solved by editing the early reffered line. Only sound is little rusty, but its maybe my old speakers (I hope :)

be back if sth wrong again (I hope not :)

thanks for help to SOUNDCHECK...cheers

I had a typo in the instruction above. I changed it.;)

Rusty sound? ) Hmmh. That doesn't sound right to me. 
If you experience kind of scratchy noise, usually something is wrong with your samplerate config. E.g. if you run 48khz material on a 44.1 soundcard setting. You'd better check it out. Never heard of rusty PC-speakers. :D

Cheers

---

### Post by soundcheck on 2008-11-16
> **copyrights said:**
> cat /proc/asound/card0/codec#0 
Codec: Realtek ALC889A
Address: 0
Vendor Id: 0x10ec0885
Subsystem Id: 0x106b3f00
Revision Id: 0x100103
No Modem Function Group found

That seems to be the same, but still don't work. Under alsamixer I got the following entries.

Playback:
Master, PCM, Front, Line, Line Boost, Line-Out, Mic, Mic Boost, IEC958 (no slider), IEC958 Default PCM (no slider), Channel Mode (6ch), Speaker (no slider)

Capture:
Line Boost, Mic Boost, IEC958 (no slider), Digital

I think the capture side can't be right.

Hi.

Perhaps you might want to try this:

[https://help.ubuntu.com/community/MacBook?#Microphone](https://help.ubuntu.com/community/MacBook?#Microphone)

There are some bugs reported at launchpad. But it seems that it is rather a setup issues than a real bug.

Cheers

---

### Post by jpichie on 2008-11-16
> Originally Posted by jpichie  
Welcome back soundcheck, any idea how I could get sound from my center speaker? everything else sounds great. uxchecker log is on page 3.

Hi.

I am not really a multichannel guy. There is a lot of stuff on the web. 

However:

Try the utility speaker-test from Alsa-Utils
which generates some pink noise on each of the available channels.

E.g. for two channels:

$ speaker-test -Dplughw:0,0 -c2
or
$ speaker-test -D front -c2

or e.g. 6 channels (Note: type $aplay -L to find out about your pcm devices)

$ speaker-test -D your-virtual51-device-as-shown-in-"aplay -L" -c6
in my case:
$ speaker-test -D surround51 -c6

My aplay -L
```
front:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    Front speakers
surround40:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

When I tried speaker-test -Dsurround51 -c6 I received:
```
jason@Ascension:~$ speaker-test -Dsurround51 -c6

speaker-test 1.0.18

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

```

This would loop until I Ctrl+C.

Any help is appreciated.

---

### Post by jesuspresley on 2008-11-16
> **soundcheck said:**
> 

Short AlsaUpgrade script install instructions:
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.x-rev-1.10.tar
4. sudo ./AlsaUpgrade-1.0.x-rev-1.10.sh


Awesome. That script worked for me!
Just a hint: After I downloaded it regarding the instructions, I had to run the script three times seperately, once with each parameter:

```
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -d
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -c
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -i
```

[the option -f for full install resulted in an error]

Thanks so much.

---

### Post by soundcheck on 2008-11-17
> **jesuspresley said:**
> Awesome. That script worked for me!
Just a hint: After I downloaded it regarding the instructions, I had to run the script three times seperately, once with each parameter:

```
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -d
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -c
 sudo ./AlsaUpgrade-1.0.x-rev-1.12.sh -i
```

[the option -f for full install resulted in an error]

Thanks so much.

Do you have the first log (-f) available?

---

### Post by soundcheck on 2008-11-17
> **jpichie said:**
> My aplay -L
```
front:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    Front speakers
surround40:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CMI8788,DEV=0
    C-Media CMI8788, Multichannel
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```

When I tried speaker-test -Dsurround51 -c6 I received:
```
jason@Ascension:~$ speaker-test -Dsurround51 -c6

speaker-test 1.0.18

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy

```

This would loop until I Ctrl+C.

Any help is appreciated.

Have a look here: [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

---

### Post by hannemann on 2008-11-18
Helo there,

I've been searching for so long now and you made my day :-)

I executed the Script on Intrepid with Asus P5Q Deluxe OnBoard. The Sound worked after the next reboot without any further configuration.

Thank you so much

:KS:KS:KS:KS:KS

---

### Post by rossiFan on 2008-11-18
Running the script worked great for me.  Sound broke on a Thinkpad R50e when I did a clean install of 8.10.  Nice and loud, too.  Brilliant.

---

### Post by no0ne on 2008-11-22
> **costre said:**
> Well, I can describe my way of getting it to work.

1.) Download and install the latest Alsa update, as described by soundcheck:
[http://ubuntuforums.org/attachment.php?attachmentid=92330&d=1226491630](http://ubuntuforums.org/attachment.php?attachmentid=92330&d=1226491630)

2.) Sudo open /etc/modprobe.d/alsa-base and find the line "options snd-hda-intel model=". Make it look like 

```
options snd-hda-intel model=acer-aspire
```

3.) Download hda-verb from [ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2](ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2) . Unpack it, and use "make" in the folder to compile the files.

4.) Copy the created files into /usr/local/bin

5.) Sudo open /etc/rc.local and add the line 

```
/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
```

6.) Reboot, and it should work from now on.

That's how I did it, thanks to jansaell and soundcheck!

Well, you don't need the alsa 1.0.18 at all to do this so you may just skip step one. Also this set of instructions flooded all over the forum only works for Hardy.

> **wells24 said:**
> Tkx for the script

I'm having problem to have my sound card to work with Intrepid Ibex 8.10
my laptop is an acer aspire 6920
running Intrepid Ibex 8.10
Kernel 2.6.27-7-generic
Chip ALC889

Everything was working grate on ubuntu 8.04 :)
than upgrade to Ibex and sound card went down.:(



Tkx to reply

I second this. Running Intrepid Ibex 8.10 i386 kernel 2.6.27-7-generic on an Acer Aspire 6920G which has the same Realtek ALC889 chip.

```
cat /proc/asound/card0/codec#* | grep Codec
``` output:
Codec: Realtek ALC889
Codec: LSI ID 1040

---

### Post by n3ro. on 2008-11-22
hmm i cant install it on my samsung nc10

[http://www.alsa-project.org/db/?f=c75c6b790629797d74e0a2f43dbae62ef102a4c3](http://www.alsa-project.org/db/?f=c75c6b790629797d74e0a2f43dbae62ef102a4c3)

i have tested all options...

---

### Post by soundcheck on 2008-11-24
> **n3ro. said:**
> hmm i cant install it on my samsung nc10

[http://www.alsa-project.org/db/?f=c75c6b790629797d74e0a2f43dbae62ef102a4c3](http://www.alsa-project.org/db/?f=c75c6b790629797d74e0a2f43dbae62ef102a4c3)

i have tested all options...


We're getting in the area of 1000 downloads of the  current and earlier scripts I guess. Shouldn't be the script causing the trouble!

It is still not working? What does the installation log file say?

---

### Post by EasyRiderOnTheStorm on 2008-11-24
It didn't work for me.

I ran first the download only, that finished without errors.
Then I tried to run compile, which failed with the attached log.

I'm running Ubuntu 8.04.1 with a 2.6.24-21-generic kernel, so this may or may not be related to the note in the first post regarding my kernel version and alsa 18. I have Intel HDA on-board sound, with an ALC880 on it. Unfortunately, I can't make heads or tails of make error messages in general :( - I only know it won't compile. Help, please...?

---

### Post by knoppers on 2008-11-24
> **EasyRiderOnTheStorm said:**
> It didn't work for me.

I ran first the download only, that finished without errors.
Then I tried to run compile, which failed with the attached log.

I'm running Ubuntu 8.04.1 with a 2.6.24-21-generic kernel, so this may or may not be related to the note in the first post regarding my kernel version and alsa 18. I have Intel HDA on-board sound, with an ALC880 on it. Unfortunately, I can't make heads or tails of make error messages in general :( - I only know it won't compile. Help, please...?

Ran into the same problem. Any suggestion?

---

### Post by soundcheck on 2008-11-25
I am aware that 1.0.18a is not compiling on 2.6.24.  This is a known problem.

I issued a TT to the ALSA-mailing list. No answer yet.

I again issued a mail today.

---

### Post by soundcheck on 2008-11-25
Hi.

I received a new git snapshot of the ALSA drivers. The 2.6.24 problem
should be solved with this. This is a very early revision- nothing official!!

I am not really sure how to handle this. I'd need somebody capable
to test this manually. 

Volunteers?

What you would have to do:

Download the snapshot from here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

NOTE: Above snapshot can be also used for getting the very latest design status, that might resolve also other probelms. For people willing to 
play around a bit, I'd recommend to try it.

Then execute following commands:

```

cd <your-downloaddir>
sudo tar xvvf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --with-cards=all --with-card-options=all --with-sequencer=yes --with-oss=yes  --prefix=/usr
sudo make

```

Let me know if this works! 

If yes - we got two options: Either you install this snapshot manually or I'll check
with the Alsa guys when we can expect an offical update.

If above compiles properly, the manual installation would look like this.

1. You copy the alsa-driver directory to /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a
```
   cd alsa-driver
   sudo cp -rf * /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a

```
2. Now you run the Upgrade script with -i option ( don't use the -d or -f options anymore !!!)

THX

---

### Post by joka. on 2008-11-26
Can anyone answer this for me?... [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) says that the audio is fixed, but someone reported that he followed those steps exactly for his macbook pro 5,1 and it messed up his system. I'm planning on getting a macbook pro 5,1 and installing Intrepid 8.10, can anyone confirm if the audio is working or maybe that person did something wrong?

---

### Post by soundcheck on 2008-11-26
> **joka. said:**
> Can anyone answer this for me?... [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) says that the audio is fixed, but someone reported that he followed those steps exactly for his macbook pro 5,1 and it messed up his system. I'm planning on getting a macbook pro 5,1 and installing Intrepid 8.10, can anyone confirm if the audio is working or maybe that person did something wrong?

I guess that the Macbook should work by now. We  had a discussion ongoing earlier. 
That's also what it says in the "sound" section of the Macbook-Wiki you're referring to. 

Good luck.

---

### Post by mactron on 2008-11-26
It worked amazing on ubunt 8.10 but I'm wondering if its also working on Fedora 10.

---

### Post by soundcheck on 2008-11-26
> **mactron said:**
> It worked amazing on ubunt 8.10 but I'm wondering if its also working on Fedora 10.

Bad luck. Fedora is not based on Debian. You won't get it working.

In principle it could be used if you allign the required packages, package installer and the target directories inside the script.
Beside that Alsa needs to be compiled as a module on your Fedora kernel. If Alsa is a fixed part of the kernel, you won't have a chance to get it working ,unless you compile your own kernel and configure all ALSA relevant config-parameters to "m".

Good luck

---

### Post by EasyRiderOnTheStorm on 2008-11-26
Hi Soundcheck, and thank you for your efforts. You rock.

> **soundcheck said:**
> Hi.
I am not really sure how to handle this. I'd need somebody capable
to test this manually. 

Volunteers?

What you would have to do:

Download the snapshot from here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

[...] Let me know if this works! 


I did what you said, and the unpacked alsa-driver compiled successfully (in the download folder). I'm stopping here for now because this is a live mythbuntu box and I need it to work, and I'm basically a noob, it's bloody late here, and I'm not ready for a meltdown; but I'll attempt to copy it over and do it properly as you proposed tomorrow. I'll get back with the results. Thanks again.

---

### Post by frankypc on 2008-11-26
soundcheck it worked awesome with the manual install thing. thank you very much

---

### Post by EasyRiderOnTheStorm on 2008-11-27
I'm in a pretty foul mood right now; meltdown has occured right on schedule. ](*,)

I tried to compile / install this new alsa package, and it completed without errors; after a reboot I had alsa 1.0.18 on all fronts ("cat /proc/asound/version", "alsactl --version", "aplay --version"). So much for the good part.

I came here looking for a new ALSA version for improved hda-intel support (see [this thread]("http://ubuntuforums.org/showthread.php?t=991240") for details), but the new driver seems to be even worse: not only did it not get me the missing controls/get rid of the noise but now I had no capture mixer controls whatsoever. Only playback.

Even worse, ALSA 0.18 might have compiled OK, but killed my tv tuner's DMA sound, normally serviced by saa7134_alsa, which now refused to start with this:

```
[ 1996.615704] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[ 1996.615715] saa7134_alsa: Unknown symbol snd_ctl_add
[ 1996.615786] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[ 1996.615789] saa7134_alsa: Unknown symbol snd_pcm_new
[ 1996.615921] saa7134_alsa: disagrees about version of symbol snd_card_register
[ 1996.615923] saa7134_alsa: Unknown symbol snd_card_register
[ 1996.616058] saa7134_alsa: disagrees about version of symbol snd_card_free
[ 1996.616061] saa7134_alsa: Unknown symbol snd_card_free
[ 1996.616176] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[ 1996.616178] saa7134_alsa: Unknown symbol snd_pcm_stop
[ 1996.616318] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[ 1996.616321] saa7134_alsa: Unknown symbol snd_ctl_new1
[ 1996.616654] saa7134_alsa: disagrees about version of symbol snd_card_new
[ 1996.616656] saa7134_alsa: Unknown symbol snd_card_new
[ 1996.616723] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1996.616725] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[ 1996.616853] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[ 1996.616856] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[ 1996.617049] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 1996.617053] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[ 1996.617280] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[ 1996.617283] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[ 1996.617333] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 1996.617335] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step

```

My problem is that I haven't been able to undo this ever since. I had made a copy of the entire /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/ folder before attempting install; now I tried to copy it back over; it didn't help. Tried to obliterate (purge/uninstall) alsa-base from the package manager, it didn't help. Tried to do it again, for "linux-sound-base", "alsa-base", "alsa-utils", as described in the sticky "comprehensive sound problems...", then tried to get the official "alsa-source" and compile it as described in the same sticky; It compiled eventually; but it didn't help. Same error, saa7134_alsa cannot be loaded.

The wall starts to crack where I bang my head on it.

I am aware that this is not Soundcheck's script's fault, probably not even ALSA's fault, since the same saa7134_alsa seems to have had similar problems around may this year. Allegedly fixed. And same about two years ago. Surely fixed by now. Or is it? 

But the thing is I'm sitting here with an almost-broken Myth-box (fell back to the noisy CD-cable-sound as described in the other thread). Does anybody have any idea how to get out of this? It worked fine before... :( Help. Pretty please...?

---

### Post by soundcheck on 2008-11-28
> **EasyRiderOnTheStorm said:**
> I'm in a pretty foul mood right now; meltdown has occured right on schedule. ](*,)

I tried to compile / install this new alsa package, and it completed without errors; after a reboot I had alsa 1.0.18 on all fronts ("cat /proc/asound/version", "alsactl --version", "aplay --version"). So much for the good part.

I came here looking for a new ALSA version for improved hda-intel support (see [this thread]("http://ubuntuforums.org/showthread.php?t=991240") for details), but the new driver seems to be even worse: not only did it not get me the missing controls/get rid of the noise but now I had no capture mixer controls whatsoever. Only playback.

Even worse, ALSA 0.18 might have compiled OK, but killed my tv tuner's DMA sound, normally serviced by saa7134_alsa, which now refused to start with this:

```
[ 1996.615704] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[ 1996.615715] saa7134_alsa: Unknown symbol snd_ctl_add
[ 1996.615786] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[ 1996.615789] saa7134_alsa: Unknown symbol snd_pcm_new
[ 1996.615921] saa7134_alsa: disagrees about version of symbol snd_card_register
[ 1996.615923] saa7134_alsa: Unknown symbol snd_card_register
[ 1996.616058] saa7134_alsa: disagrees about version of symbol snd_card_free
[ 1996.616061] saa7134_alsa: Unknown symbol snd_card_free
[ 1996.616176] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[ 1996.616178] saa7134_alsa: Unknown symbol snd_pcm_stop
[ 1996.616318] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[ 1996.616321] saa7134_alsa: Unknown symbol snd_ctl_new1
[ 1996.616654] saa7134_alsa: disagrees about version of symbol snd_card_new
[ 1996.616656] saa7134_alsa: Unknown symbol snd_card_new
[ 1996.616723] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[ 1996.616725] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[ 1996.616853] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[ 1996.616856] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[ 1996.617049] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 1996.617053] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[ 1996.617280] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[ 1996.617283] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[ 1996.617333] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 1996.617335] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step

```

My problem is that I haven't been able to undo this ever since. I had made a copy of the entire /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/ folder before attempting install; now I tried to copy it back over; it didn't help. Tried to obliterate (purge/uninstall) alsa-base from the package manager, it didn't help. Tried to do it again, for "linux-sound-base", "alsa-base", "alsa-utils", as described in the sticky "comprehensive sound problems...", then tried to get the official "alsa-source" and compile it as described in the same sticky; It compiled eventually; but it didn't help. Same error, saa7134_alsa cannot be loaded.

The wall starts to crack where I bang my head on it.

I am aware that this is not Soundcheck's script's fault, probably not even ALSA's fault, since the same saa7134_alsa seems to have had similar problems around may this year. Allegedly fixed. And same about two years ago. Surely fixed by now. Or is it? 

But the thing is I'm sitting here with an almost-broken Myth-box (fell back to the noisy CD-cable-sound as described in the other thread). Does anybody have any idea how to get out of this? It worked fine before... :( Help. Pretty please...?

If you want to get the things being solved you need to get a bit more relaxed.

I think you are pretty aware that playing with this manual upgrade bears some kind of risk and it is rather meant for Linux hackers then standard users.

As you've seen in the recent posts, if I am able to communicate properly to Alsa, the way I described it in my opening post, they'll provide us with patches respectively updates.

THX

---

### Post by EasyRiderOnTheStorm on 2008-11-28
> **soundcheck said:**
> If you want to get the things being solved you need to get a bit more relaxed.
Sorry if I sound a bit dramatic, but this really feels like drowning for a non-hacker, and I do try to stay relevant to the subject save one or two sentences. I did state that your script now basically works for me too. If one tries to upgrade Alsa this way they'll thoroughly break their Philips tuner audio support, and the previous post is a chance for them to find that out beforehand.

> **soundcheck said:**
> I think you are pretty aware that playing with this manual upgrade bears some kind of risk and it is rather meant for Linux hackers then standard users.
Crystal clear. I hope you are aware as well that given the state of support for fairly common hardware in Linux and the policy of not backporting updates even for Ubuntu LTS releases one does not really have a choice whether to tinker with "hacker stuff" or not the very moment one wishes to do more than open Firefox. See, I'm not messing with Alsa because I want to...

Also, I expressed that I don't particularly hold anyone "responsible" for my mess: I did it. But it's there, and it's quite scary - for me. People who can compile Alsa while they sleep don't come here. They just do it.

> **soundcheck said:**
> As you've seen in the recent posts, if I am able to communicate properly to Alsa, the way I described it in my opening post, they'll provide us with patches respectively updates.
That's great. Now, with all due respect - would you/anyone have any ideas regarding how one can undo what the script does if one needs to, how Alsa relates to saa7134_alsa, or perhaps what's wrong with Alsa's previous/current support for Intel HDA / ALC880...?

---

### Post by nomega on 2008-11-28
Worked great - thanks a lot! :)

> **soundcheck said:**
> Latest update 11/27/2008
Latest Alsa upgrade script update 11/12/2008 Rev. 1.12
Latest uxchecker script update 11/16/2008 Rev. 1.05
Latest Alsa-Package update:  11/12/2008 (1.0.18a)

BACKGROUND:

The main idea of upgrading ALSA (the mainline Linux sound layer including all soundcard drivers) with attached script, 
it is the delay of updates through official channels in the range of at least half a year. 
You can imagine that half a hear means a lot in this fast moving soundcard business. 
Especially people buying new machines can't wait half a year to get their soundcards going. 

GENERAL REMARK (my personal point of view):

Some general comments to ALSA or better Linux Audio and the partial lack of soundcard or soundcard feature support:

ALSA's sometimes limited or restricted soundcard support is first of all a soundcard industry problem and second a resource 
shortage of the ALSA-team. 
Many card manufactures neither offer interface descriptions to ALSA, nor they're getting involved in developing the drivers.
This might have to do something with "opensource only" at ALSA. 

I don't really understand why it is so difficult to handle soundcard drivers the same way as done with GPU drivers such as fglrx from AMD.  
There is a way to get proprietary closed-source drivers in place. OSS - an ALSA alternative - from 4-Front-Technologies.
For a very limited number of soundcards (e.g. Lynx cards) they offer proprietary non-open drivers. 

Beside that ALSA is always looking for serious volunteers to be able to cope with the high demands arising from a continuous technology evolution and permanently growing number of (non-)standardized soundcards, countless distributions and kernels. 

I personally hope that due to the power of the fast growing number of Linux users and also PC manufacturers this situation might improve 
in the future.

UPGRADE:

Disclaimer:
The script is currently not in line with Debian/Ubuntu rules for package handling. It just overwrites existing files. 
You won't see a change on the ALSA package-id within Synaptic!
It is gonna be difficult to rollback to the original. You might try to reinstall your kernel-image and headers and all ALSA packages from Synaptics
if you experience problems. However, usually the script recognizes severe problems and won't mess up your setup. If the script stops with an 
error-message nothing should have been touched! 
 
Ubuntu upgrades/updates might overwrite your manual installation once in a while (e.g. kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script with the -i option in this case. 
Major upgrades can also overwrite some important configuration files such as /etc/modprobe.d/alsa-base. 
You need to restore your old configuration manually in this case. Keep always a copy of your modified alsa-base file!

I won't take any responsibility for mess-ups by using the scripts!
However - I do my best to avoid these. ;)


I also rely on your support to improve the script and really appreciate your involvement.


The current script supports 

Alsa 1.0.18a (stabil)
See changelog: [http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a](http://www.alsa-project.org/main/index.php/Changes_v1.0.18_v1.0.18a)

and

Ubuntu kernels: 2.6.24, 2.6.26, 2.6.27 family (including rt-kernel & ZEN-kernel)

Temporary Restriction:
11/16/2008: Ubuntu 8.04 with kernel 2.6.24-xx:  latest alsa-drivers 1.0.18a won't compile on 2.6.24-x kernel familiy !!! ), 
For now, you can use a preliminary workaround [http://ubuntuforums.org/showpost.php?p=6249579&postcount=65](http://ubuntuforums.org/showpost.php?p=6249579&postcount=65) . 
As soon as I know at what date an official update can be expected, I'll let you know.


Supported packages:

ALSA 1.0.18a

DRIVER=alsa-driver-1.0.18a
FIRMWARE=alsa-firmware-1.0.17
LIB=alsa-lib-1.0.18
PLUGINS=alsa-plugins-1.0.18
UTILS=alsa-utils-1.0.18
TOOLS=alsa-tools-1.0.18
OSS=alsa-oss-1.0.17


Compare above list with [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download) before you start the script.

You can run the script as many times as you want!

As usual - Make a backup first! - You never know.

Changelogs you'll find inside the scripts!

Hint:
The easiest and most reliable test to verify if Alsa is working is "aplay" - the Alsa player application.

Type in a terminal:
$ aplay -l

If you see your soundcards, you're almost there.

To test your first (default-index 0 X=0) soundcard, type e.g.:
$ aplay -Dplughw:X,0 -fcd /<your-music-directory>/<replace-this-with-your-soundfile>.wav
or e.g.
$ speaker-test -Dplughw:X,0 -c2 
replace the X with the index of your soundcard index , which you find out by typing "aplay -l" - look for "card X"

Multichannel you can test the following way:
1. Type $aplay -L to find out about your pcm device . e.g "surround51"
2. Type $speaker-test -D surround51 -c6
Note: If the channel mapping should be wrong you need to adjust it in .asoundrc

AND PLEASE: Before reporting "NO SOUND" problems - check if your alsamixer-channels are unmuted !! If your alsamixer controls show "MM" for muted at the bottom press "m" to toggle between unmute/mute. To access your 2nd soundcard respectively the index 1 soundcard you need to start alsamixer with "alsamixer -c1" . There are quite often  headphone-jack, Toslink, SPDIF or microphone issues reported. Usually this also has something to do with a wrong alsamixer setting or more seldom with a wrong model-id of your soundcard assigned to your sound-driver.   

Please read also this post [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) if you don't get any further


The uxchecker-1.X.sh script will help you to collect environmental information with a special focus on your sound setup and Alsa for troubleshooting purposes.
If you run it during playback, you'll also be able to log data-stream relevant parameters.
Note: I would not recommend to post the entire logfile to the public! It contains partially sensitive data, which you might not want to expose! ;)

The alsa-info.tar is a shell script collecting data, which are requested by the Alsa-Designers in case we encounter a real Alsa problem over here. 

To make troubleshooting a bit more efficient, report:

1. Name your Ubuntu revision
2. Kernel revision
3. Alsa revision
4. Upgrade script revision
5. A bit of background what you've done resp. done before
6. Attach the relevant logs
(System related infos you'll find in the uxchecker.log)

Short AlsaUpgrade script install instructions:
1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.x-rev-1.10.tar
4. sudo ./AlsaUpgrade-1.0.x-rev-1.10.sh

(The same way you'll handle the uxchecker-1.0x.tar)

---

### Post by soundcheck on 2008-11-29
> **EasyRiderOnTheStorm said:**
> S

That's great. Now, with all due respect - would you/anyone have any ideas regarding how one can undo what the script does if one needs to, how Alsa relates to saa7134_alsa, or perhaps what's wrong with Alsa's previous/current support for Intel HDA / ALC880...?

As you can read now in the opening post - under General Comment - I made some comments why ALSA resp. the restricted/limited soundcard support is the way it is in Linux. 
OSX comes with a similar Unix structure, it shouldn't be very difficult to port OSX driver to Linux - if you really want it. 
All this is obviously highly political stuff.Believe me you're not the only one being annoyed about it. 

All this is mainly my driving force for maintaining this script. 

And it is people like you - lacking the hacker-gene - who need to put in a constructive manner more and more pressure on manufacturers and
Linux to get this deficiency solved.

------------

I am working on a "restore" option. This will just reinstall all Ubuntu ALSA packages and your actual kernel with the driver modules. Should be available during this weekend.

I am also looking into making deb compliant packages for easier handling
of the upgrade.

-------------

The ALC880 should be fully supported. We had that discussion earlier.

Please run the uxchecker-script and post the outputs.

---

### Post by cgam14 on 2008-11-30
Friend compiles correctly

---

### Post by soundcheck on 2008-11-30
Hi folks.

I just uploaded the new script 1.13-beta version of the upgrade script.


It now supports:

1: Restore of latest Ubuntu Alsa (related to your kernel version)

   NOTE: For obvious reasons the Restore function is not working for non-Ubuntu-kernels. This should affect a minority only.

2: Kernel 2.6.28 (also Zen-kernel)

I put it up as Beta release, because I'd like to see some guys confirming that it is working on other machines then mine. You can restore and install
as many times as you want.

Works like a charm on my machine. ;)

Good luck.

Cheers

---

### Post by flowflow2 on 2008-11-30
Thanks the script worked fine for me.....mic gets a little fuzzy on the front speakers if left on, but headphones on the \nc10 work fine for intrepid now......mic is working also both from the front mic and the normal headphones......seems to be way more options for turning things on and off for mic/headphones etc...and about 4 different boosts for mics!!

---

### Post by heluani on 2008-11-30
Hello, I'm running 8.10 on a Macbook Air 2,1 that shows up an
```
heluani@vino:~$ lspci | grep Audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
```

After running the script I see the following card with aplay
```
heluani@vino:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

but alsamixer shows card: HDA Nvidia (which is correct) Chipset: Realtek ALC889A (which is not what I was expecting from the output above). Needless to say, I still don't have any sound from the internal speakers. Any help will be really appreciated.

R.

Edit I should add perhaps that I get the following:
```
heluani@vino:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A 
```

---

### Post by soundcheck on 2008-12-01
@heluani: Did you add "options snd_hda_intel model=mbp3" to your /etc/modprobe.d/alsa.base ?

---

### Post by heluani on 2008-12-01
[Quote=soundcheck]Did you add "options snd_hda_intel model=mbp3" to your /etc/modprobe.d/alsa.base ? [/quote] Yes I did (should've mentioned it). That allows the headphone to work, but no main speaker sound. I think this was the case in the Aluminum MBP with Alsa 1.0.17 and 1.0.18 solved that issue, that's why I was hoping that upgrading to 1.0.18 would solve this issue in the Air 2,1 as well.

R.

---

### Post by klss on 2008-12-02
> **heluani said:**
> Yes I did (should've mentioned it). That allows the headphone to work, but no main speaker sound. I think this was the case in the Aluminum MBP with Alsa 1.0.17 and 1.0.18 solved that issue, that's why I was hoping that upgrading to 1.0.18 would solve this issue in the Air 2,1 as well.

R.

If' you're sure that is is not a configuration issue,

try to install the very the latest driver set manually. 

Some posts earlier I brought it up to solve the 2.6.24 problem.

Good luck

---

### Post by EasyRiderOnTheStorm on 2008-12-02
> **soundcheck said:**
> 
And it is people like you - lacking the hacker-gene - who need to put in a constructive manner more and more pressure on manufacturers and Linux to get this deficiency solved.

I'll try to find some place to mention this, but quite frankly, I don't have illusions about Acer being overly impressed by Linux driver requests for a 2004 desktop... :(

> 
I am working on a "restore" option. This will just reinstall all Ubuntu ALSA packages and your actual kernel with the driver modules. Should be available during this weekend.

I am also looking into making deb compliant packages for easier handling
of the upgrade.

Thanks. I'll try it as soon as possible - right now I'm messing around with the Alsa .16 I've finally managed to compile (and install), since it's just as good for codec-node-tests and it doesn't have issues with my capture mixer and tv-tuner driver.

> 
The ALC880 should be fully supported. We had that discussion earlier.

Yes and no. It sure does make sound and it has most of the inputs and outputs labeled right, but none of it's modes seems to support my AUX mobo input, so there. Except the TEST mode, of course, but from what I glanced that works highly weird in .16 - input selectors that are supposed to be, well, selectable are stuck on a single input in the mixer, others toggle endlessly between options #2 and #3 (0->1->2->3->2->3->2->3...), there are pin states labeled as "N/A" (I haven't seen this option in the datasheet) yet the 50% AVDD option is missing, and so on. I'll take another look though...

Also, there was the issue of noise, as I explained [[here]("http://ubuntuforums.org/showthread.php?t=991240")]. As you can see there, I'm no longer sure where the noise originates, so this might or might not be an Alsa issue yet. In particular, the existence of left-open pathways that could pick up noise might not get noticed on mobos that manage to not introduce (too much) noise to said pathways. Similar codecs (the ALC882, perhaps?) turned out to have a summing-selector instead of a MUX one, which caused just such noise, and ultimately prompted an Alsa bug report (-and fix; It's in the .18; does not apply for my codec, so inconsequential). I'm not saying this is the case here, though. 

> Please run the uxchecker-script and post the outputs.
I'll do that, when configuration stabilizes a bit and I move on to .18 (=can afford to lose tv tuner direct capture). As it is now, I don't think it would make much sense. To much mess... ;)

---

### Post by heluani on 2008-12-02
[quote=klss]try to install the very the latest driver set manually.[/quote]
Did it, compiled fine, then ran the script again with -i option. Same situation as before, headphones work, main speaker doesn't. This time the installation didn't edit my /etc/modprobe.d/alsa-base, but did mute the PCM channel.


[quote=klss]If' you're sure that is is not a configuration issue,[/quote]

I am certainly not sure of this. What I am sure is that I tried every relevant tip I could find here, including the macbook's community helps and every thread relevant to the aluminum mbp. I thought sound in the macbook air 2,1 should be the same as in the mbp. Perhaps I'm wrong. Most probably I'm just making a stupid mistake somewhere.

R.

---

### Post by soundcheck on 2008-12-05
Hi there.

I think it is a very typical problem with the codecs that this and that
feature is not working. At least that's the impression I got since being 
on the ALSA developper mailing list.

Try to phrase your issues more sharp in 10 lines - no prose - with all the data needed.

And I'll issue a TT.

Cheers

---

### Post by heluani on 2008-12-07
@soundcheck: Thanks!

No sound on main internal speaker. Headphones do work fine. 
Macbook Air 2,1
Ubuntu Intrepid server Kernel 2.6.27-9 
Alsa Driver version 1.0.18a GIT snapshot from 12/4/08
Sound card nVidia MCP79 (device id 10de:0ac0)
aplay -l: ALC885 
/proc/asound/card0/codec#0 CODEC ALC889a

lspci -nv 
00:08.0 0403: 10de:0ac0 (rev b1)
        Subsystem: 10de:cb79

---

### Post by Bluetrunk on 2008-12-10
This script allowed me to get my sound working on my new Dell Studio PC with ALC888 on board running Ubuntu Linux 8.10. Thanks a lot!

---

### Post by kqian on 2008-12-11
Hi there, I ran the 1.0.18a script, and the speakers are working now. 
However, I have the one last issue that I can't work out, my headphones do not produce any sound. 
Here's my specs. 

HP Pavillion tx2000z, 
Realtek AC861VD, 
Alsa version 1.0.18a. 
Running Ubuntu Studio Intrepid 8.10
Kernel 2.6.27-9-generic

I restarted my laptop after the upgrade, and have went to modprobe.d/alsa-base and added the line 
options snd-hda-intel model=hp

I even searched for alsa everywhere and deleted everything, and went to Synaptec to do a reinstall of all alsa* packages, and then ran your script again, and added that line again, still, headphones do not produce sound. 

heres a couple of commands that I ran, and the output attached

kqian@kkqian:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kqian@kkqian:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC861-VD
Codec: Motorola Si3054

Oh, I should also add, headphones do not show up in volume control. 
I have checked the switches, as well as the main interface. The only things that are there are: 

Master, 
PCM,
Front, 
Front Mic,
Front Mic Boost,
Microphone,
Mic Boost,
Speaker,
Capture,
IEC958,
IEC958 Default PCM,
Caller ID,
Off-hook,
Input Source,

All of them are checked, and none of them are muted.

Thanks, and I really appreciate the time and effort you've put into this.

---

### Post by soundcheck on 2008-12-12
> **heluani said:**
> @soundcheck: Thanks!

No sound on main internal speaker. Headphones do work fine. 
Macbook Air 2,1
Ubuntu Intrepid server Kernel 2.6.27-9 
Alsa Driver version 1.0.18a GIT snapshot from 12/4/08
Sound card nVidia MCP79 (device id 10de:0ac0)
aplay -l: ALC885 
/proc/asound/card0/codec#0 CODEC ALC889a

lspci -nv 
00:08.0 0403: 10de:0ac0 (rev b1)
        Subsystem: 10de:cb79

Hi.

Accoding to ALSA it shouldn't be an ALSA problem. It is probably a broken BIOS.

Try following model-ids:

model=macpro, model=mbp3, model=imac24

Cheers

---

### Post by soundcheck on 2008-12-12
Hi folks.


REMINDER:

Please supply the alsa-info.sh output if you want to get your issue resolved by ALSA. Otherwise it is impossible to get your issue tracked down from remote.

I won't forward any issues any longer to ALSA if you don't supply that 
information.

You can PM me with related information.  This way I can put you also on the distribution list of that particular trouble ticket.

THX

---

### Post by heluani on 2008-12-14
> **soundcheck said:**
> Hi.

Accoding to ALSA it shouldn't be an ALSA problem. It is probably a broken BIOS.

Try following model-ids:

model=macpro, model=mbp3, model=imac24

CheersThanks, I did try those models (and many more :) ) but no success. Not that I understand anything, but how can it not be an ALSA issue if sound works fine on mac os X and in Linux only the headphones work?

R.

---

### Post by kqian on 2008-12-14
[FIXED] Headphones sound issue. 

So after running the alsa-info.sh script, i discovered that my computer was loading option snd-hda-intel model=z71v although I added the line 
snd-hda-intel model=hp. 

So I did a grep, and discovered that somehow in the alias file under modprobe.d there is this line 

snd-hda-intel model=z71v, so I deleted that line, and did 

sudo /etc/init.d/alsasound restart

and voila! headphones/sound/speaker/mic everything magically started working!!! 

Thanks soundcheck!

---

### Post by soundcheck on 2008-12-15
> **heluani said:**
> Thanks, I did try those models (and many more :) ) but no success. Not that I understand anything, but how can it not be an ALSA issue if sound works fine on mac os X and in Linux only the headphones work?

R.

That's a good question first of all.

One possible reason:

You need to consider that Apple, just have to adapt OSX to their own HW-platform respectively BIOS only. What makes live obviously much easier
for them.
Nobody knows if there are following all the standards. They also might add workarounds to get things going. 
Takashi Iwai ( one of the leading designers at ALSA) is telling me that very often non standard BIOS implementations causing quite some trouble.

However. Send me the alsa-info.sh (again?) and I'll hand it over.

BTW: I agreed with Takashi to let you guys try the latest driver tar-ball as described over here: [http://ubuntuforums.org/showpost.php?p=6249579&postcount=65](http://ubuntuforums.org/showpost.php?p=6249579&postcount=65)
     to make sure that we're not chasing ghosts.  

I will add an option to the upgrade-script during this week , which will let you folks download and install the latest snapshot automatically. 
The above link will always refer to the latest snapshot in the future.

Cheers

---

### Post by soundcheck on 2008-12-15
> **kqian said:**
> [FIXED] Headphones sound issue. 

So after running the alsa-info.sh script, i discovered that my computer was loading option snd-hda-intel model=z71v although I added the line 
snd-hda-intel model=hp. 

So I did a grep, and discovered that somehow in the alias file under modprobe.d there is this line 

snd-hda-intel model=z71v, so I deleted that line, and did 

sudo /etc/init.d/alsasound restart

and voila! headphones/sound/speaker/mic everything magically started working!!! 

Thanks soundcheck!

Great to hear that you tracked it down by yourself. Would be interesting to know how the entry got there!
All ALSA related stuff should be located in alsa-base.

---

### Post by pedja_portugalac on 2008-12-15
I had problem with sound on my new Acer Aspire 8920. Following script method from this page I lost master button on panel. But fortunately there was simple way to get all working and I found it on launchpad written by guy called Jojo and now everything work like it should.

This is what I have done:

Install fresh Ubuntu 8.10
Update system and reboot
Install proprietary graphics driver for NVIDIA cards (177) and reboot
Open terminal and type:

```
sudo gedit /etc/modprobe.d/alsa-base
```

Add this to the end:

```
# added by myself
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
```

Reboot and it works perfectly on 5.1 integrated speakers and on headphones too.

Bye Bye Vista...

---

### Post by soundcheck on 2008-12-15
Folks.

I today uploaded revision 1.14 of the script.

Changes:

1. It now allows you to install the latest driver-snapshot supplied
   by ALSA. This way you potentially get the chance to get things even 
   earlier going. But please consider that this a snapshot from a 
   designers-source-tree. Don't expect that  everything is fully integrated
   and tested.
   This function is very useful for trouble-shooting purposes to avoid
   reporting already fixed faults.
   I still need to checkout if there is a changelog available.

2. I introduced a little help-function


Let me know, if you experience problems.


Cheers

---

### Post by blackest_knight on 2008-12-15
hi pretty much sorted here with the help of this thread but there is a niggle
 
if I setup the mixer with the settings I want (internal mic for one)
I can store the settings with 
alsactl store

however after rebooting the settings are back to the original defaults external mic master vol 81% 

with 

sudo alsactl restore 

The settings are restored 

however I am too ignorant to be able to get the settings to be restored automatically after a reboot can you suggest a solution please.

---

### Post by druellan on 2008-12-15
@soundcheck first of all thanks very much for this script. Its awesome how it works. If I can propose an enhancement could be a cleanup option, to uninstall all the *-dev packages.

I'm using Ubuntu on my eeePC 1000h ALC269 since Hardy + Alsa 1.0.16. When I installed Intrepid (Alsa 1.0.17) I noticed a brutal regression on the gnome-volume-control:

[img]http://members.lycos.co.uk/biosfera/Ubuntu/gnome-volume-control-regression.png[/img]

As you can see, even on Alsa 10.0.18a volume controls are far inferior from Hardy's default. Sound quality is good thought. The mic on Alsa 10.0.17 sound horrible, but that got fixed on 10.0.18a. Still I'm wondering whats going on: I want to know if this is a gnome problem, an Alsa problem or Ubuntu one.

Should I post a Launchpad bug report or you can elevate this to Alsa people?

Thanks again and keep the good work!

BTW: I have an alsa-info.txt I get using Alsa 10.0.17 and 2.6.27-8-eeepc kernel (I reverted back from 10.0.18a for now, but I can reinstall if you need info).

---

### Post by Rhubarb on 2008-12-16
Thankyou soundcheck :)

Thanks to your script (and my lazyness to compile alsa manually - as I had done so a few years ago), it was easy to get the latest alsa compiled and installed.

So my Intel ICH7 with ALC269 codec's microphone works nicely on my eee PC S101.

Thanks again soundcheck :)

---

### Post by soundcheck on 2008-12-16
@druelan

Did you check the "preferences" for switching on the other controls?

---

### Post by druellan on 2008-12-16
Thanks for the quick reply. On Alsa 10.0.17 all controls are checked and they are what you can see in the pic, but I can't remember if I rechecked after the upgrade to Alsa 10.0.18a. I'm going to reinstall it today using the .14 version of your script to see if there are new controls among the mic boost.

---

### Post by soundcheck on 2008-12-16
> **blackest_knight said:**
> hi pretty much sorted here with the help of this thread but there is a niggle
 
if I setup the mixer with the settings I want (internal mic for one)
I can store the settings with 
alsactl store

however after rebooting the settings are back to the original defaults external mic master vol 81% 

with 

sudo alsactl restore 

The settings are restored 

however I am too ignorant to be able to get the settings to be restored automatically after a reboot can you suggest a solution please.


Hi there.


I do have similar issues! Controls always load default values after
login.

I just had a look at the start script /etc/init.d/alsa-utils , which 
is in charge for restoring the config.

perhaps you try following:

1. cd /var/lib/alsa
2. sudo ln -s /etc/asound.state asound.state
3. Play around with the controls and restart

Let me know, if it works. I guess it will.

I am not sure yet if it is gonna be an ALSA or Ubuntu issue. I doubt though that it has something to do
with the upgrade-script.

BTW:
When playing with the controls of my 2nd soundcard by muting them
I realized that the sliders are moved to the bottom when reopening 
the gnome-mixer-applet. 
Instead of just muting the channels they put them to 0, which is IMO a fault.
Can anybody confirm this behaviour?

Cheers

---

### Post by soundcheck on 2008-12-16
ALSA just confirmed that the alsactl issue is an Ubuntu/Debian issue.

I also reported the issue on launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308587](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308587)

Cheers

---

### Post by soundcheck on 2008-12-16
I actually closed the Ubuntu ticket again, since I learned that Debian
is patching  alsa-utils and the asound.state issue on purpose just to 
put that file under /var/lib/alsa.

My earlier workaround was in fact the solution to the issue.

So - for now I'll stay with the workaround. I'll implement it into the
script Rev. 1.15.

I recommend to implement above workaround or to run Rev. 1.15.

Let me know if you're experiencing problems.

Cheers

---

### Post by druellan on 2008-12-16
> **soundcheck said:**
> Did you check the "preferences" for switching on the other controls?
[IMG]http://members.lycos.co.uk/biosfera/Ubuntu/alsa.1.0.18a.allcheck.png[/IMG]

Reinstalled using your script 1.15. All checked. Seems that the mic boost is the only new control I gained on the upgrade.

I'm attaching alsa-info.sh output for Intrepid + Alsa 1.0.17 and Intrepid + Alsa 1.0.18a

---

### Post by soundcheck on 2008-12-16
Try these module options on snd-hda-intel in /etc/modprobe.d/alsa-base:

ALC269
	  basic		Basic preset
	  quanta	Quanta FL1
	  eeepc-p703	ASUS Eeepc P703 P900A
	  eeepc-p901	ASUS Eeepc P901 S101
	  fujitsu	FSC Amilo
	  auto		auto-config reading BIOS (default)

e.g.

snd-hda-intel index=0 model=eeepc-p901

---

### Post by druellan on 2008-12-16
Ok:

* Auto, eeepc-p703 eeepc-p901 and fujitso did not show anything new.
* Basic enables something similar to 1.0.16 + Hardy (even the internal beeper, wich I thoght this machine lacked).
* Quanta shows something similar to basic, but different labels (PC speaker instead of beeper, seems more for desktop than notebook).

So, basic seems the best here. Later I will do some tests in Skype.
Final picture to complete the collection :)

[IMG]http://members.lycos.co.uk/biosfera/Ubuntu/alsa.1.0.18a.basic.png[/IMG]

BTW, I've tested this setting on a non upgraded 1.0.17 kernel and has no effect, so seems that Alsa 1.0.18a got improvements but needs to improve the bios detection.

Thank you so much soundcheck for the help solving this. Here, another "thank" for your collection :P

---

### Post by soundcheck on 2008-12-16
You made my day. ;)

---

### Post by Jaciss on 2008-12-16
Thank you for taking the time to write this, soundcheck.  It's taken me further than any other method thus far.  My problems are certainly not caused by the script, but might be good to know about.

Short story - sound was working, I upgraded to 8.04 then 8.10 and somewhere during this my sound stopped working.  Ubuntu will recognize the card via lspci:```
lspci -v
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Device 30bf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable+ Fixed+
	Kernel modules: snd-hda-intel
```
and alsaconf can find the card and complete, but aplay -l returns nothing but an error:
```
aplay: device_list:217: no soundcards found...
```
Any of the mixer or sound control tools also return errors, as will (dun dun dun) modprobe snd-hda-intel:
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

dmesg
snd_hda_intel: Unknown parameter `stack'
```

Of note - AlsaUpdater installed the link here: 

/lib/modules/2.6.27-9-generic/kernel/sound/modules

but I found an snd-hda-intel.ko file here:

/lib/modules/2.6.27-9-generic/kernel/sound/pci/hda

which I replaced with a link to the AlsaUpdater files like the one in the first directory, much like another user in this topic.

Plenty of reboots and --purge and permission checking and whatnot.  I followed [Debugging Sound Problems]("https://wiki.ubuntu.com/DebuggingSoundProblems") and the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and several other guides as far as possible - I'm running short on things to try and hoping someone can see something I can't.  If not, I'll run through one of the officialish guides again and see about filing a bug.

---

### Post by soundcheck on 2008-12-17
@Jaciss

Please change your alsa-base file (sudo gedit /etc/modprobe.d/alsa-base) : 

snd-hda-intel model=hp 

to 

snd-hda-intel index=0 model=gateway 

and reboot

If this won't work, please run and attach the log of alsa-info.sh


Cheers

---

### Post by druellan on 2008-12-17
Update: still can't make the internal mic work using mode=basic or mode=quanta. On mode=auto works really well, so I think that perhaps its a matter of found the right combination of controls, perhaps a bad labeled mic.

---

### Post by Jaciss on 2008-12-17
@soundcheck:
Well, alsa-info to the rescue.  The file shows:

snd-hda-intel: index=0 model=3 stack position_fix=0 single_cmd=0

as well as the correct:
snd-hda-intel: index=0 model=3stack position_fix=0 single_cmd=0

under modprobe options, which would explain the 'stack' error.  So it amounts to a typo.  What is amusing is that said typo was in a backup file I'd made and stupidly left in the /etc directory.  Thus, --purge and AlsaUpdater and such did nothing for the problem.

Sometimes I wonder how many of my hours have been spent seeking a missing ; or an added space.  Thank you very much for your time and your script - it's great to have a quick method for updating alsa...and had I not run alsa-info I'd still be being thwarted by a single space.  Doh.

---

### Post by soundcheck on 2008-12-17
> **Jaciss said:**
> @soundcheck:
Well, alsa-info to the rescue.  The file shows:

snd-hda-intel: index=0 model=3 stack position_fix=0 single_cmd=0

as well as the correct:
snd-hda-intel: index=0 model=3stack position_fix=0 single_cmd=0

under modprobe options, which would explain the 'stack' error.  So it amounts to a typo.  What is amusing is that said typo was in a backup file I'd made and stupidly left in the /etc directory.  Thus, --purge and AlsaUpdater and such did nothing for the problem.

Sometimes I wonder how many of my hours have been spent seeking a missing ; or an added space.  Thank you very much for your time and your script - it's great to have a quick method for updating alsa...and had I not run alsa-info I'd still be being thwrted by a single space.  Doh.

Tell me:

Did you get it working with model=3stack now & all controls up'n running? :-k
I looked up model=hp from your alsa-base file in the ux-checker.log!?!? :-k
And option "gateway" should do the trick for your codec!?!? :-k

To look for double entries you can scan the entire directory:
sudo grep -R "snd-hda-intel" /etc/modprobe.d

let me know what it says.

---

### Post by blackest_knight on 2008-12-17
> **soundcheck said:**
> Hi.

I received a new git snapshot of the ALSA drivers. The 2.6.24 problem
should be solved with this. This is a very early revision- nothing official!!

I am not really sure how to handle this. I'd need somebody capable
to test this manually. 

Volunteers?

What you would have to do:

Download the snapshot from here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

NOTE: Above snapshot can be also used for getting the very latest design status, that might resolve also other probelms. For people willing to 
play around a bit, I'd recommend to try it.

Then execute following commands:

```

cd <your-downloaddir>
sudo tar xvvf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --with-cards=all --with-card-options=all --with-sequencer=yes --with-oss=yes  --prefix=/usr
sudo make

```

Let me know if this works! 

If yes - we got two options: Either you install this snapshot manually or I'll check
with the Alsa guys when we can expect an offical update.

If above compiles properly, the manual installation would look like this.

1. You copy the alsa-driver directory to /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a
```
   cd alsa-driver
   sudo cp -rf * /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a

```
2. Now you run the Upgrade script with -i option ( don't use the -d or -f options anymore !!!)

THX

Well the latest version of the installation script was failing with this kernel version on Hardy on an Aspire One.

The above Post solved the issue allowing the drivers to compile properly.
I can confirm a partly working sound system which remembers the mixer settings.
I havent tested very much so far, if I get time tonight I will test further

---

### Post by blackest_knight on 2008-12-17
few problems initially but editing /etc/modprobe.d/alsabase and adding/editing this line to

options snd-hda-intel model=acer-aspire and things started to work better on the aspire one.

HDA Intel (hw:intel,0) selected for input device on skype allowed me to successfully make a test call a bit hissy but it was using a 3g phone as a modem :) (three skype phone amoi wa01 i think).

things are looking up :)

---

### Post by Jaciss on 2008-12-17
@soundcheck
> Did you get it working with model=3stack now & all controls up'n running?
Yes, everything seemed to be up and running, but...
> I looked up model=hp from your alsa-base file in the ux-checker.log!?!?
I did change it back to model=hp since that's what the alsa docs (and the helpful post on page two of this topic) said was correct.  The other options were what I had to use previously for things to work.  The hp option is preferable, though, as 3stack seems to break the headphone jacks.  Alsamixer and gnome-sound* things all seem normal.
> And option "gateway" should do the trick for your codec!?!?
I have no idea.

> To look for double entries you can scan the entire directory:
sudo grep -R "snd-hda-intel" /etc/modprobe.d

let me know what it says.
```

/etc/modprobe.d/sound:alias snd-card-0 snd-hda-intel
/etc/modprobe.d/sound:alias sound-slot-0 snd-hda-intel
/etc/modprobe.d/alsa-base:options snd-hda-intel index=0 model=hp
```

However, it had multiple entries for snd-hda-intel until I removed that backup file.

Thanks again.  I'm happy to answer questions if you've any more - it's the least I can do.

---

### Post by soundcheck on 2008-12-17
> **blackest_knight said:**
> Well the latest version of the installation script was failing with this kernel version on Hardy on an Aspire One.

The above Post solved the issue allowing the drivers to compile properly.
I can confirm a partly working sound system which remembers the mixer settings.
I havent tested very much so far, if I get time tonight I will test further

Did you run  the script three times with  options 1. -d  2. -snap  3. -i  ???? In this case the manual installation of the snapshot shouldn't be needed any longer.
If you just ran -di or -i , no wonder it didn't work.

---

### Post by blackest_knight on 2008-12-17
with kernel 2.6.24.22 on hardy version 1.15 of the script failed to compile (used with option di initially then  just i)

finding your post about the git snapshot i downloaded that, compiled it successfully (couple of warns but nothing related to my hardware) but didnt install it. 
then I moved the driver folder to source as detailed above and ran a slightly modded version of your script ( i just commented out the exec lines so i could watch what was going on as it was compiling. 
There was some audio working (log on sound) but initially the only mic sound was something distorted which might have had some kind of speech in it.

I found there was a new module option module=acer-aspire and then I got a working internal mic. The mixer settings are retained between boots (just checked no skype audio problems ). 

thanks for that 1.0.18rc3 was working quite well, just the having to set the internal mike before using skype was annoying. your solution solves the problem.  

btw didn't realise there was a -snap option for the script, that would have been easier still.

---

### Post by druellan on 2008-12-18
> **druellan said:**
> Update: still can't make the internal mic work using mode=basic or mode=quanta. On mode=auto works really well, so I think that perhaps its a matter of found the right combination of controls, perhaps a bad labeled mic.
Confirmed. mode=basic and mode=quanta seems unable to unmute the mic. So, there is still a regression from Alsa 1.0.16.

---

### Post by heluani on 2008-12-22
> **soundcheck said:**
> That's a good question first of all.

One possible reason:

You need to consider that Apple, just have to adapt OSX to their own HW-platform respectively BIOS only. What makes live obviously much easier
for them.
Nobody knows if there are following all the standards. They also might add workarounds to get things going. 
Takashi Iwai ( one of the leading designers at ALSA) is telling me that very often non standard BIOS implementations causing quite some trouble.

However. Send me the alsa-info.sh (again?) and I'll hand it over.

BTW: I agreed with Takashi to let you guys try the latest driver tar-ball as described over here: [http://ubuntuforums.org/showpost.php?p=6249579&postcount=65](http://ubuntuforums.org/showpost.php?p=6249579&postcount=65)
     to make sure that we're not chasing ghosts.  

I will add an option to the upgrade-script during this week , which will let you folks download and install the latest snapshot automatically. 
The above link will always refer to the latest snapshot in the future.

Cheers

I'm sorry it took me so long to reply, been busy here. I am running a snapshot form Takashi's site from 12/12, can't be too old :). Attached is my log from info.sh... everything seems fine, it'll suck if its a BIOS issue.. [ATTACH]97213[/ATTACH]

---

### Post by DjNDB on 2008-12-22
Thank you so much! This fixed my sound problems.

In case someone has similar problems:
I am using a GigaByte GA-MA78GM-S2H which has a Realtek ALC889A sound chip.

It was first partly working out of the Box with Ubuntu 8.10, and then suddenly SP/DIF IEC958 did not function correctly anymore.

Also when I used totem and activated AC3 passthrough it only played AC3 Videos, the others had no sound. Now I get passthrough on AC3 files and others are played normally, as expected.

Further it is detected correctly now:

> $head -n 1 /proc/asound/card0/codec* 
Codec: Realtek ALC889A

---

### Post by littlewiki on 2008-12-22
Soundcheck,

I bought an Acer 4930G which comes with a realtek 888 sound card. I am having a problem with the microphone which is not switching on when I plugin the headphone. I found a patch just for my model here:

[http://thread.gmane.org/gmane.linux.alsa.devel/58076/focus=58114](http://thread.gmane.org/gmane.linux.alsa.devel/58076/focus=58114)

but the patch is not present in the 1.0.18A but it's present in the daily snapshot :
[http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)
or 
[http://www.alsa-project.org/snapshot/files/alsa-driver-1.0.18a.16.g4012f.139.g6e583.tar.bz2](http://www.alsa-project.org/snapshot/files/alsa-driver-1.0.18a.16.g4012f.139.g6e583.tar.bz2)

My question is I ran your script with the -snap option. so did it install this svn build or did it build the 1.0.18a build? I haven't restarted my system so cannot tell for sure if it's working now.

Regards,
wikz

---

### Post by soundcheck on 2008-12-23
> **littlewiki said:**
> Soundcheck,

I bought an Acer 4930G which comes with a realtek 888 sound card. I am having a problem with the microphone which is not switching on when I plugin the headphone. I found a patch just for my model here:

[http://thread.gmane.org/gmane.linux.alsa.devel/58076/focus=58114](http://thread.gmane.org/gmane.linux.alsa.devel/58076/focus=58114)

but the patch is not present in the 1.0.18A but it's present in the daily snapshot :
[http://www.alsa-project.org/snapshot/](http://www.alsa-project.org/snapshot/)
or 
[http://www.alsa-project.org/snapshot/files/alsa-driver-1.0.18a.16.g4012f.139.g6e583.tar.bz2](http://www.alsa-project.org/snapshot/files/alsa-driver-1.0.18a.16.g4012f.139.g6e583.tar.bz2)

My question is I ran your script with the -snap option. so did it install this svn build or did it build the 1.0.18a build? I haven't restarted my system so cannot tell for sure if it's working now.

Regards,
wikz

It downloads the latest svn snapshot prepared by ALSA and overwrites the 1.0.18a. They won't step the revsions. You won't see anything else than 1.0.18a. Your mic should work now. ;)

Cheers

---

### Post by Da_Teach on 2008-12-24
nevermind, seems to be a TV issue... :(

---

### Post by Cuppa-Chino on 2008-12-28
I do not think this is the script itself but upgrading to 1.1.18a via the script (or a ppa I found) seems to kill my desktop, I end up with a completely corrupted screen.
I using vesa driver etc all does not help, I am wondering what I can do to help find the cause.
using virgin amd64 interpid ibex mythbuntu with geforce 8300 mobo with nvidia 177.80 driver from repo

any ideas where to look, I had to completely rollback

---

### Post by yoshimandk on 2008-12-28
hey folks thanks for all the support so far. im going on a trip and wont be able to work on this for a while but i'll let you know how it comes out when i get back in a week!

---

### Post by soundcheck on 2008-12-28
> **Cuppa-Chino said:**
> I do not think this is the script itself but upgrading to 1.1.18a via the script (or a ppa I found) seems to kill my desktop, I end up with a completely corrupted screen.
I using vesa driver etc all does not help, I am wondering what I can do to help find the cause.
using virgin amd64 interpid ibex mythbuntu with geforce 8300 mobo with nvidia 177.80 driver from repo

any ideas where to look, I had to completely rollback

Any strange messages in the installation log-file? Did you also run the restore?

You need to deliver a bit more meat on the bones.

---

### Post by bradcater on 2008-12-28
Thanks so much, soundcheck. I ran the upgrade script with -di and rebooted, then did both again, and it works!

Acer TravelMate 2480, Ubuntu 8.10

---

### Post by Cuppa-Chino on 2008-12-28
> **soundcheck said:**
> Any strange messages in the installation log-file? Did you also run the restore?

You need to deliver a bit more meat on the bones.

sorry that was bad from on my part.

I am trawling through the log file (which survived the reinstall) and so far the only things I can see are:

```

checking for GCC version... ./configure: eval: line 5136: syntax error near unexpected token `)'
./configure: eval: line 5136: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

libtool: link: warning: `/usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../../lib//libasound.la' seems to be moved
gcc -shared  .libs/alsa-oss.o  -Wl,--rpath -Wl,/usr/src/Alsa-1.0.18a/alsa-oss-1.0.17/alsa/.libs ./.libs/libalsatoss.so -L/usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../../lib/  -Wl,-soname -Wl,libaoss.so.0 -o .libs/libaoss.so.0.0.0

pcm_share.c: In function '_snd_pcm_share_missing':
pcm_share.c:295: warning: ignoring return value of 'read', declared with attribute warn_unused_result
pcm_share.c:297: warning: ignoring return value of 'write', declared with attribute warn_unused_result
pcm_share.c:300: warning: ignoring return value of 'write', declared with attribute warn_unused_result
pcm_share.c:302: warning: ignoring return value of 'read', declared with attribute warn_unused_result
pcm_share.c: In function 'snd_pcm_share_thread':


```

all those do not look drastic at all (I think), output from the script claimed it had been successful.
 also I cannot see why it would have anything to do with me running xcfe
thanks for helping me, sorry again for the earlier post

----------------------------------------------------------------------

to use old fashioned speak: format c:, reinstall and now it works.
GDM was so messed up in the end I decided to reinstall completely, I also opted to install a regular Ubuntu first rather than the mythbuntu. I have the suspicion that the problem was coincidental with the installation of the script, sorry to have taken so much of your time.

---

### Post by mediajunkie on 2008-12-29
HI,

I've tried to run the script as instructed on a fresh installed ubuntu 8.04 on an Acer Aspire 8920. 

script version  rev 1.15, 
kernel 2.6.24-22-generic (hardy 8.04)

actions 

sudo ./AlsaUprade-1.0.x-rev.1.15.sh -d 
sudo ./AlsaUgrade-1.0.x-rev-1.15.sh -snap
sudo ./AlsaUgrade-1.0.x-rev-1.15.sh -i
Reboot

(had to run Nvidia restricted driver setup again) 

log files (attached)

aplay-l does list my sound cards, but speaker test runs with no audio.
All settings in control panel are correct. 
the installed programs HDSPMixer and such don't run either.


any clue what is going wrong?

In the mean I've installed the sound card the old way as pointed out here: [http://jan.saell.org/blog/archives/30](http://jan.saell.org/blog/archives/30) 
however with the latest source for hda-verb-03. from: [ftp://ftp.suse.com/pub/people/tiwai/misc/](ftp://ftp.suse.com/pub/people/tiwai/misc/)  (seems to work with the latest kernel but I'm more interested in the new script provided here, if it works)

---

### Post by 602254985 on 2008-12-31
it didn't working on my 64bit linux?:D
> In file included from /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/pcsp.c:2:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c: &#22312;&#20989;&#25968;&#8216;snd_card_pcsp_probe&#8217;&#20013;&#65306;
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: &#38169;&#35823;&#65306; &#8216;HRTIMER_CB_IRQSAFE&#8217;&#26410;&#22768;&#26126; (&#22312;&#27492;&#20989;&#25968;&#20869;&#31532;&#19968;&#27425;&#20351;&#29992;)
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: &#38169;&#35823;&#65306; (&#21363;&#20351;&#22312;&#19968;&#20010;&#20989;&#25968;&#20869;&#22810;&#27425;&#20986;&#29616;&#65292;&#27599;&#20010;&#26410;&#22768;&#26126;&#30340;&#26631;&#35782;&#31526;&#22312;&#20854;
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: &#38169;&#35823;&#65306; &#25152;&#22312;&#30340;&#20989;&#25968;&#20869;&#20063;&#21482;&#25253;&#21578;&#19968;&#27425;&#12290;)
make[4]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp/pcsp.o] &#38169;&#35823; 1
make[3]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers/pcsp] &#38169;&#35823; 2
make[2]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/drivers] &#38169;&#35823; 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a] &#38169;&#35823; 2
make[1]:&#27491;&#22312;&#31163;&#24320;&#30446;&#24405; `/home/johnnys/linux-2.6.28'
make: *** [compile] &#38169;&#35823; 2
alsa-driver-1.0.18a make failed
Sorry ,I use chinese system> 




[ATTACH]98306[/ATTACH]

---

### Post by enle on 2009-01-01
Hi,

I recently bought a new laptop (Packard Bell Easynote ML65 series), repartitionned the HD (for dual boot) and installed and updated Ubuntu 8.10.
Everything seems OK except for sound:
Headphones: OK
Laptop-speakers: no sound.
The Gnome Alsa Mixer showed 3 volume sliders: Master, PCM and Capture.

Then I applied AlsaUpgrade-1.0.x-rev-1.15.sh => Installation successfully finished!
The Gnome Alsa Mixer now shows: Master, PCM, Front, Front Mic, Front Mic boost, Mic, Mic boost and Capture.
So I made progress, BUT:
Headphones: OK
Laptop-speakers: no sound.

leo@packard:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Searching on the ALSA website I found:
# Changes v1.0.18rc3 v1.0.18 (122,367 bytes)
170: : ALSA: hda - Add support of ALC272
1523: : - ALSA: hda - Add support of ALC272
1525: : Added the support of ALC272 codec. It's almost compatible with ALC663. 

But in ALSA-Configuration1.0.18a.txt, I can't find ALC272 or options that I could use in /etc/modprobe.d/alsa-base.

Any idea's ?

---

### Post by brianh57 on 2009-01-02
Great work on the script.  I used it to update Kubuntu Intrepid to alsa 1.0.18a.  Now the internal microphone on my new Lenovo Ideapad S10 works so I can Skype!

Thanks again!

---

### Post by soundcheck on 2009-01-04
> **enle said:**
> Hi,

I recently bought a new laptop (Packard Bell Easynote ML65 series), repartitionned the HD (for dual boot) and installed and updated Ubuntu 8.10.
Everything seems OK except for sound:
Headphones: OK
Laptop-speakers: no sound.
The Gnome Alsa Mixer showed 3 volume sliders: Master, PCM and Capture.

Then I applied AlsaUpgrade-1.0.x-rev-1.15.sh => Installation successfully finished!
The Gnome Alsa Mixer now shows: Master, PCM, Front, Front Mic, Front Mic boost, Mic, Mic boost and Capture.
So I made progress, BUT:
Headphones: OK
Laptop-speakers: no sound.

leo@packard:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Searching on the ALSA website I found:
# Changes v1.0.18rc3 v1.0.18 (122,367 bytes)
170: : ALSA: hda - Add support of ALC272
1523: : - ALSA: hda - Add support of ALC272
1525: : Added the support of ALC272 codec. It's almost compatible with ALC663. 

But in ALSA-Configuration1.0.18a.txt, I can't find ALC272 or options that I could use in /etc/modprobe.d/alsa-base.

Any idea's ?

I'd try the ALC663 or the latest snapshot. 
I guess you unplugged your earphones to get sound on your PC speakers. ;)

---

### Post by antebe on 2009-01-05
Thank you so much soundcheck for this script, it helped me out a bit when my audio suddenly died, probably because I had installed Miro. 

I have a puzzling problem with my headphones, though. I normally use digital output to my home theater speakers and everything works fine. But when I try to use the headphone output with mythtv I do not understand what is going on: I can listen to music, but not to TV or DVDs. Outside mythtv I hear sound normally through the headphones, for example from youtube movies.

Iwould really appreciate if anyone could get me on the right track to a solution here!

---

### Post by pii on 2009-01-06
Hi,

I've tried the script on my lenovo S10 with ubuntu Intrepid to alsa 1.0.18a but failed. First I've used the -di option and later -d and -c.
During compilation I got the following errors:

make[1]: Betrete Verzeichnis '/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a'
make[2]: Betrete Verzeichnis '/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore'
copying file alsa-kernel/core/info.c
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Fehler 1
make[2]: Verlasse Verzeichnis '/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore'
make[1]: *** [dep] Fehler 1
make[1]: Verlasse Verzeichnis '/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a'
make: *** [include/sndversions.h] Fehler 2
alsa-driver-1.0.18a make failed


Does anyone have an idea what's wrong?

Thanks!
pii

---

### Post by zim2dive on 2009-01-07
> **soundcheck said:**
> 
The uxchecker-1.X.sh script will help you to collect environmental information with a special focus on your sound setup and Alsa for troubleshooting purposes.
If you run it during playback, you'll also be able to log data-stream relevant parameters.
Note: I would not recommend to post the entire logfile to the public! It contains partially sensitive data, which you might not want to expose! ;)

I just took a quick look thru the log.. what sensitive info is there?? (I don't see anything)

(just beginning my debug and was running the posted scripts)

more to follow :)

---

### Post by zim2dive on 2009-01-07
Acer X1200, nvidia 8200, MCP78 chipset.  I am trying to get 5.1 audio from the 3 analog 2-ch jacks on the rear of the machine (I cannot use the HDMI audio).  The jacks are green, orange, and black, and I have them working under Vista (as a proof of concept).

Intrepid 8.10.  nvidia driver 173 (via the Hardware drivers panel in Intrepid).. 173 handles full-screen flash MUCH better than 177 does (this seems to be a bug related to the 8200/8300 and am pursuing this at nvnews).

I have installed alsa 1.0.18a by hand, and did have HDMI 5.1 audio working using 177.82 and the 180.x drivers, but again, they degrade full-screen flash performance to the point of being un-usable, and 180.xx is VERY unstable on the 8200.  Ok, hopefully I have talked folks out of telling me to upgrade nvidia or use HDMI.

Attaching full copy of uxchecker log ```

-----------------------------------------------------------------------------
-    Alsa-Version
-----------------------------------------------------------------------------

Advanced Linux Sound Architecture Driver Version 1.0.18a.
Compiled on Jan  3 2009 for kernel 2.6.27-11-generic (SMP).

-----------------------------------------------------------------------------
-    aplay --version 
-----------------------------------------------------------------------------

aplay: version 1.0.18 by Jaroslav Kysela <perex@perex.cz>

-----------------------------------------------------------------------------
-    aplay -l - all playback devices
-----------------------------------------------------------------------------

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-----------------------------------------------------------------------------
-    aplay -L - all pcms
-----------------------------------------------------------------------------

default:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

-----------------------------------------------------------------------------
-    arecord -l - all recording devices
-----------------------------------------------------------------------------

**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-----------------------------------------------------------------------------
-    /proc/asound/devices
-----------------------------------------------------------------------------

  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  7: [ 0- 3]: hardware dependent
 16: [ 0- 0]: digital audio playback
 19: [ 0- 3]: digital audio playback
 24: [ 0- 0]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer

-----------------------------------------------------------------------------
-    /proc/asound/cards
-----------------------------------------------------------------------------

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 20

-----------------------------------------------------------------------------
-    codec card0
-----------------------------------------------------------------------------

Codec: Realtek ALC888
Address: 0
Vendor Id: 0x10ec0888
Subsystem Id: 0x10250153
Revision Id: 0x100202
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0
Node 0x02 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x18 0x18]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Amp-In caps: ofs=0x0b, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x09 0x09] [0x09 0x09] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x03 0x03]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18566140: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Orange
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x0:
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19850: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19860: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181305f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4017e619: [N/A] Speaker at Ext N/A
    Conn = Analog, Color = White
    DefAssociation = 0x1, Sequence = 0x9
  Pin-ctls: 0x20: IN
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400780: Mono Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x01451130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400680: Mono Digital
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=25
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x411: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: Generic 10de NVIDIA MCP78 HDMI
Address: 3
Vendor Id: 0x10de0002
Subsystem Id: 0x10de0101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x05 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x18560110: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x04
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x07 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560121: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x1
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x06
Node 0x08 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x09 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560122: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x2
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x0a [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0b [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560123: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x3
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0a
Node 0x0c [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0xc0]: 48000 88200
    bits [0xf]: 8 16 20 24
    formats [0x1]: PCM
Node 0x0d [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000014: OUT Detect
  Pin Default 0x58560124: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x4
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x0c

-----------------------------------------------------------------------------
-    codec card1
-----------------------------------------------------------------------------

cat: /proc/asound/card1/codec*: No such file or directory

-----------------------------------------------------------------------------
-    codec card2
-----------------------------------------------------------------------------

cat: /proc/asound/card2/codec*: No such file or directory

-----------------------------------------------------------------------------
-    alsa mixer settings
-----------------------------------------------------------------------------

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 17 [55%] [-21.00dB] [on]
  Front Right: Playback 17 [55%] [-21.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 9 [29%] [-21.00dB] [on]
  Front Right: Playback 9 [29%] [-21.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 9 [29%] [-21.00dB] [on]
  Front Right: Playback 9 [29%] [-21.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 24 [77%] [19.50dB] [on]
  Front Right: Capture 24 [77%] [19.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [off]
  Front Right: Capture 0 [0%] [-16.50dB] [off]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '2ch'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'CD'
  Item0: 'Mic'

-----------------------------------------------------------------------------
-    playback-stream card 0
-----------------------------------------------------------------------------

cat: /proc/asound/card0/stream0: No such file or directory

-----------------------------------------------------------------------------
-    playback-stream card 1
-----------------------------------------------------------------------------

cat: /proc/asound/card1/stream0: No such file or directory

-----------------------------------------------------------------------------
-    playback-stream card 2
-----------------------------------------------------------------------------

cat: /proc/asound/card2/stream0: No such file or directory

-----------------------------------------------------------------------------
-    alsactl -v
-----------------------------------------------------------------------------

alsactl version 1.0.18

-----------------------------------------------------------------------------
-    alsa-base
-----------------------------------------------------------------------------

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=3stack-6ch

-----------------------------------------------------------------------------
-    base-alsa-config - user specific
-----------------------------------------------------------------------------

cat: /home/zimmy/.asoundrc: No such file or directory

-----------------------------------------------------------------------------
-    base-alsa-config - system
-----------------------------------------------------------------------------

cat: /etc/asoundrc: No such file or directory

-----------------------------------------------------------------------------
-    sound-devices
-----------------------------------------------------------------------------

crw-rw----+ 1 root audio 116,  0 2009-01-06 19:08 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 2009-01-06 19:08 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 2009-01-06 19:08 /dev/snd/hwC0D3
crw-rw----+ 1 root audio 116, 24 2009-01-06 19:51 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2009-01-07 07:57 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116, 26 2009-01-06 19:08 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116, 19 2009-01-06 19:08 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116,  1 2009-01-06 19:08 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 2009-01-06 19:08 /dev/snd/timer

-----------------------------------------------------------------------------
-    Ubuntu revision
-----------------------------------------------------------------------------

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

-----------------------------------------------------------------------------
-    kernel
-----------------------------------------------------------------------------

Linux ubuntu 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686 GNU/Linux

-----------------------------------------------------------------------------
-    kernel modules - installed
-----------------------------------------------------------------------------

Module                  Size  Used by
af_packet              25728  2 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
ipv6                  263972  27 
powernow_k8            22148  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
video                  25232  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12680  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         431892  3 
snd_pcm_oss            46496  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83716  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         16776  2 snd_hda_intel,snd_pcm
acer_wmi               19008  0 
snd_hwdep              15492  1 snd_hda_intel
psmouse                45200  0 
pcspkr                 10624  0 
led_class              12164  1 acer_wmi
serio_raw              13444  0 
nvidia               7103300  26 
agpgart                42184  1 nvidia
snd_seq_dummy          11012  0 
i2c_core               31892  1 nvidia
k8temp                 12416  0 
snd_seq_oss            39936  0 
snd_seq_midi           14368  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                58352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         15500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 38036  0 
joydev                 18368  0 
pci_hotplug            34976  1 shpchp
snd                    66340  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
evdev                  17696  10 
wmi                    14504  1 acer_wmi
button                 14224  0 
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
ata_generic            12932  0 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  2 
crc_t10dif              9984  1 sd_mod
usb_storage            82752  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
libusual               30356  1 usb_storage
pata_amd               18692  0 
ohci1394               37936  0 
ahci                   37132  1 
pata_acpi              12160  0 
ieee1394               96324  2 sbp2,ohci1394
libata                178208  4 ata_generic,pata_amd,ahci,pata_acpi
ohci_hcd               32016  0 
ehci_hcd               43788  0 
forcedeth              61328  0 
scsi_mod              155212  6 sbp2,sr_mod,sd_mod,usb_storage,sg,libata
dock                   16656  1 libata
usbcore               149360  6 usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

-----------------------------------------------------------------------------
-    uxchecker.sh revison 1.05 ; logfile at: /var/log/uxchecker-1.05-010709-08.07.log
-----------------------------------------------------------------------------

```

so I can get front left audio pretty well, but can't get speaker-test to output to any other channels, which makes me think I'm not quite set up correctly.

I've tried setting several model types in my alsa-base ie. ```
options snd-hda-intel model=3stack-6ch
``` but no luck.

I get 6-ch audio via VLC by going to audio prefs and selecting ALSA, but only for some content, when 5.1 is listed as an audio device.. other content has "A52 over spdif" and I can't get that out the jacks at anything better than stereo.

Also my speaker-test command```
speaker-test -c6 -l1 -Dplug:surround51 -twav
``` fails to produce audio on any channel except front left/right.

I have un-muted and set volumes on all channels in alsamixer.

No idea what to try next.

thanks for any help.

---

### Post by antebe on 2009-01-07
Please forget my previous post,I got around that. But now I am in deep trouble, I ran the 1.0.18 script a couple days ago after my sound had completely died. It seemed to fix the problem and my system was fully operational.

But only for a night or two. The same thing happened again, and without any seeming reason. I watched a recording, ended it, and went to a new recording... no sound.

Last night I fiddled around and managed to get the sound up again when I ran the automatic update that appeared, for 
asoundconf set default-card

...including executing this command, of course. I also edited the alsa-base file. As I could not find any exact fit for my codec I took the closest (I assume that is not the problem here, but what do I know?):
options snd-hda-intel model=6stack-dig


After that all sound seemed (and still seems) to be fixed. I have sound through my  s/pdif, and headphones from Mythtv as well as from Firefox (Youtube). 

BUT: the problem is that my Hauppauge DVB-T card HVR-1110  stopped working on digital channels (composite works). It seems to be related to the alsa issue I have been having, as dmesg gives me many lines with things like

 18.188140] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[   18.188142] saa7134_alsa: Unknown symbol snd_pcm_stop

My total output from dmesg is attached along the uxchecker output.

As far as I can tell the saa7134 on my TV card is no longer installed, aplay -l gives me only:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I hope someone can please help me with this. I am happy to provide more information, but as a complete newbie I am not sure what you need. Do I need to run the alsa-info.sh as well?

---

### Post by antebe on 2009-01-07
One more thing: I forgot to mention that the asoudconf I ran changed the device number for my hvr-1110 remote. It used to be event7 but changed due to the renewed alsa configuration to event6. So I correspondingly changed the /etc/lirc/hardware.conf and /etc/default/inputlirc settings. After that my remote works perfectly.
In case it matters I have followed the thread 

[http://ubuntuforums.org/showthread.php?t=914128](http://ubuntuforums.org/showthread.php?t=914128)

to get the remote working.

---

### Post by uBeer on 2009-01-09
Just to let you know: I had to install patch to make the script work.
Installed it on a new updated Intrepid.

Thanks by the way for such a convenient script :D

---

### Post by blackest_knight on 2009-01-10
2.6.24-23-generic :( 
compile errors with the snap option or straight d option. 
previous kernels the -snap was working but both options seem broken today.
first error seems to be hrtimer

---

### Post by blattengel on 2009-01-10
Nice scripts, thank you.
Just thought I'd share my experience.  This will probably help you blackest_knight.

I ran the AlsaUpgrade-1.0x-rev-1.15.sh script.  If failed with this error during the make of the ASLA drivers:
In file included from /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.c:2:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c: In function 'snd_hrtimer_callback':
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c:29: error: implicit declaration of function 'hrtimer_forward_now'

I looked around and found this message: [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03550.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg03550.html)

BTW, uname -r ouputs 2.6.24-18-generic for me.  According to that message and this one: [http://www.nabble.com/Anyone-with-problems-upgrading-alsa-driver-on-Hardy-2.6.24-kernel--td21117561.html](http://www.nabble.com/Anyone-with-problems-upgrading-alsa-driver-on-Hardy-2.6.24-kernel--td21117561.html)  The 2.6.24 kernel has issues with this.

To fix the error I did two things.
1) I followed a hint a the first link by adding --with-cards=intel8x0 as an argument to ./configure of the drivers.
intel8x0 is the driver for me, probably not for you:
[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)
You can use that site to find the right driver name.

2) I also also added --with-kernel=/usr/src/linux-headers-$(uname -r)
as this site said:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

So, the driver segment of the script ended up looking like:
```
#alsa-driver Note: Driver to be installed before library
header "Compiling drivers..."
cd $ALSASRCDIR/$DRIVER
make clean
./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=intel8x0 --with-card-options=all --with-sequencer=yes --with-oss=yes --prefix=/usr || die "$DRIVER configure failed"
#./configure --with-cards=usb-audio,hda-intel,emu10k1,hrtimer,rtctimer,hpet --with-card-options=all --with-sequencer=yes --with-oss=yes --with-kernel=/usr/src/linux --prefix=/usr || die "$DRIVER configure failed"
make || die "$DRIVER make failed"
```

I don't know if both of those additional arguments were necessary.  Maybe one or the other would have done the job.

Running the script was without error.  I have yet to reboot and try out my sound.

If it helps attached is alsa-info.txt that was made after upgrade but before reboot.
Also uxchecker file was output before upgrade.  With the -a option I think.

---

### Post by blattengel on 2009-01-11
Peculiar, after rebooting and updating alsa-info.txt, it says
Driver version:     1.0.16
The driver version downloaded and compiled was 1.0.18a

Maybe something I did a few months ago on one of the links of my earlier posts (To fix my sound) caused this.

Here is the description of my problem (and thus my desire to update ALSA):
After freshly installing ALSA, my sound works great.  Crystal clear.  After some time, maybe rebooting, or maybe after an update to the kernel (I don't keep track), my sound gets garbled.  The music I play with aTunes and Songbird is coherent, but not crystal clear.  Think of playing an mp3 with a bitrate of 256 kbps- it should sound crystal clear.  Said mp3 sounds to me like a mp3 with a bitrate of 32 or 64 kbps.  I can hear it and enjoy it, but it sounds wrong and may hurt after a while.

This is my 4th or 3rd time installing ALSA.  This last installation didn't fix it, I'll have to look at the other guides I linked for any difference in procedure that fixed it the other times.

---

### Post by dirtylion on 2009-01-11
> **soundcheck said:**
> Hi.

I received a new git snapshot of the ALSA drivers. The 2.6.24 problem
should be solved with this. This is a very early revision- nothing official!!

I am not really sure how to handle this. I'd need somebody capable
to test this manually. 

Volunteers?

What you would have to do:

Download the snapshot from here:

[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)

NOTE: Above snapshot can be also used for getting the very latest design status, that might resolve also other probelms. For people willing to 
play around a bit, I'd recommend to try it.

Then execute following commands:

```

cd <your-downloaddir>
sudo tar xvvf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --with-cards=all --with-card-options=all --with-sequencer=yes --with-oss=yes  --prefix=/usr
sudo make

```

Let me know if this works! 

If yes - we got two options: Either you install this snapshot manually or I'll check
with the Alsa guys when we can expect an offical update.

If above compiles properly, the manual installation would look like this.

1. You copy the alsa-driver directory to /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a
```
   cd alsa-driver
   sudo cp -rf * /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a

```
2. Now you run the Upgrade script with -i option ( don't use the -d or -f options anymore !!!)

THX
make[3]: *** No rule to make target `/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/soc/soc-jack.o', needed by `/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/soc/snd-soc-core.o'.  Stop.
make[2]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/soc] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2
alsa-driver-1.0.18a make failed

maybe you can help me
evtl. kannst du mir ja helfen ich bin linux anfänger :(
thx

------

someone got stil the 
AlsaUpgrade-1.0.x-rev-1.14.tar
script ?
since i am using 2.6.24-19 kernel

---

### Post by pcjlinux on 2009-01-11
I've successfully configured intel HDA by using this script, and taking some additional steps described here.

my configuration:
Ubuntu 8.10
kernel: 2.6.27-9-generic
alsa driver: 1.0.18a
alsa upgrade script: 1.0.x-rev-1.15

I followed soundcheck's instructions above in using the upgrade script and debugging sound problems. After running the upgrade script, I did the following:

- installed gnome alsa mixer, and verified master channel is unmuted.
- added the following statement to /etc/modprobe.d/alsa-base

	options snd-hda-intel model=ecs

  since ecs corresponds to foxconn, which is the motherboard for my machine.

- I also did a modprobe command for good measure:

	modprobe snd-hda-intel model=ecs

though this was probably unnecessary.

After rebooting, the intel-hda sound worked, partially. I could play CD's in rhythmbox, but could not get sound for desktop events.

So, I then followed instructions at [http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506) to configure pulseaudio.

I also installed and re-installed esd-related packages.. 

At this point I could play CD's using rhythmbox and play music at youtube. I could also play desktop event sounds.

However, I could only get sound from one of these sources at a time -- I couldn't get a mix of sound from multiple sources. I was also getting a static sound for the ubuntu login music...

Doublechecking, I followed the instructions at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) for configuring PulseAudio.

As a result, all problems are solved! I can play sound from multiple sources at once (CD, youtube, desktop sounds, etc.) and the sounds are automatically mixed by pulseaudio, played on my speakers via intel HDA. And the ubuntu login music now sounds fine.

In retrospect, I probably didn't need to install and re-install esd packages, since pulseaudio is supposed to be a replacement for esd...

:guitar:

---

### Post by dirtylion on 2009-01-11
someone can pls upload the old 
AlsaUpgrade-1.0.x-rev-1.14.sh version
thank you !

---

### Post by jparrill on 2009-01-15
Soundcheck wrote:
Temporary restriction:
11/16/2008: Ubuntu 8.04 with kernel 2.6.24-xx: latest alsa-drivers 1.0.18a won't compile on 2.6.24-x kernel family !!! ),
You should run the script >= rev 1.14 with "-d" first and than "-snap" and finally "-i" to get the packages installed.
As soon as I know at what date an official update can be expected, I'll let you know.

Ok, so this appears to be my problem, as I have this version of Ubuntu.

I realize this is a complete-noob question, but:
How do you run the script with a version other than 1.0.18a?  When I run it with the -d option, the only option is 1.0.18a.  How do I change it to a different version?

---

### Post by becvert on 2009-01-17
thank you very much!
the script worked perfectly.
applied to mythbuntu 8.10 booted via NFS on a DG45FC motherboard.
Optical SPDIF output is back!
had to run alsaconf manually after the reboot though.

---

### Post by sistja on 2009-01-19
The script worked parfectly and has solved my sound problems after spending hours on trying other solutions from the web...Thanks so much!
My details:
Ubuntu 8.10
Kernel 2.6.27-9
Driver: alsa-driver-1.0.18a
ASUS M50V laptop, motherboard M50VN

---

### Post by EasterSunshine on 2009-01-19
For the impatient who want 1.0.19:

I just quickly replaced the strings 1.0.18a with 1.0.19 (alsa-oss stays at version 1.0.17 because I don't think it was bumped) and re-ran the script and it seemed to work for me. /proc/asound/version reads 1.0.19 as well as alsamixer and probably a lot of other things. Only tested PCM playback.

My headphone sense still didn't work. =(

I did this really quickly---I didn't read the docs for alsa if any configuration options or anything changed. Also, I didn't update the changelog or anything...use at your own risk?

---

### Post by soundcheck on 2009-01-21
> **jparrill said:**
> Soundcheck wrote:
Temporary restriction:
11/16/2008: Ubuntu 8.04 with kernel 2.6.24-xx: latest alsa-drivers 1.0.18a won't compile on 2.6.24-x kernel family !!! ),
You should run the script >= rev 1.14 with "-d" first and than "-snap" and finally "-i" to get the packages installed.
As soon as I know at what date an official update can be expected, I'll let you know.

Ok, so this appears to be my problem, as I have this version of Ubuntu.

I realize this is a complete-noob question, but:
How do you run the script with a version other than 1.0.18a?  When I run it with the -d option, the only option is 1.0.18a.  How do I change it to a different version?

Hi.

It loads the latest Alsa src snapshot on the 1.0.18a tree, without stepping revisions if you run it this way.

Cheers

---

### Post by soundcheck on 2009-01-21
Hi folks.

I uploaded the new 1.0.19 Alsa upgrade script.

I need to open a new thread. Since the title of this thread is kind of 
misleading.

Cheers

---

### Post by soundcheck on 2009-01-21
Latest post update 01/21/2009


THIS THREAD IS FROM NOW ON CONTINUED OVER HERE:

[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

Reshuffle your subscriptions!

See you over there! ;)

---

### Post by ucjb on 2009-01-22
That fixed mine, after many hours of troubleshooting.... THANK YOU!

---

### Post by medodly on 2009-04-07
Im very new with linux so I am a little confused. I installed those files cause i had a problem with sound, both laptop speakers and headphones were working at the same time and did not know how 2 make laptop speakers switch off when headphones are on. Anyways after installing alsa 1.0.18 I have NO SOUND AT ALL now...any help guyz..?

---

### Post by blattengel on 2009-04-08
> **medodly said:**
> Im very new with linux so I am a little confused. I installed those files cause i had a problem with sound, both laptop speakers and headphones were working at the same time and did not know how 2 make laptop speakers switch off when headphones are on. Anyways after installing alsa 1.0.18 I have NO SOUND AT ALL now...any help guyz..?

Look a couple posts up.  Also at the first post.  Follow the directions on that thread.  Perhaps your issue was resolved with the new ALSA.

---

### Post by alexbirkett on 2009-04-13
Running the AlsaUpgrade-1.0.x-rev-1.16.sh script and installing alsa 1.0.19 on my mythbuntu janunty system fixes the problem I have with hdmi audio on one sound card but stops the two other sound cards in the system from functioning.
[URL="http://www.alsa-project.org/db/?f=5b961a1e08caf035e39217813159d1aa94e4e3a6"]
Alsa info here http://www.alsa-project.org/db/?f=5b961a1e08caf035e39217813159d1aa94e4e3a6
[/URL]

dmesg | grep symbol shows (full dmesg output attached)
[    9.007907] cx88_alsa: Unknown symbol snd_card_new
[   17.331819] em28xx_alsa: Unknown symbol snd_card_new

Is the script building against the wrong kernel headers?

AlsaUpgrade logs also attached

Any help appreciated.

---

### Post by emotional_friend on 2009-04-18
This upgrade script actually worked GREAT for me. I had spent several hours trying to manually download and compile the source, but kept getting errors. Somehow, this script pulled off the impossible.

Appreciatively,


Emotional Friend

---

### Post by emo1912 on 2009-04-26
Any feedbacks about **Intel 82801H (ICH8 Family) whit Ubuntu 9.04** ?
I'm updated to alsa 1.0.19 (using this script) but have no sound :(

=====EDIT=====

I resolved my problems with sound with [THIS SCRIPT]("http://ubuntuforums.org/attachment.php?attachmentid=111182&d=1240758387") (lite fixes about original script), [orginal script and manual from here]("http://ubuntuforums.org/showthread.php?t=921637"). **_For user at Acer Aspire 6920_**

---

### Post by chris2kn5 on 2009-08-05
I'm curious if the author of this script installed some extra packages because I like to keep my system minimal (XBMC + HTPC in this case), so I wanted to know what packages or if you could write an purge-packages script too. Please let me know. Thanks. :)

---

### Post by Stevi on 2009-08-10
Hi,

I'm trying to get sound via HDMI. Over the weekend I changed several settings without success.

Hopefully someone can help me.

Some info from alsa-info script:

```
name=root&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=
!!################################
!!ALSA Information Script v 0.4.57
!!################################

!!Script ran on: Mon Aug 10 16:23:41 UTC 2009


!!Linux Distribution
!!------------------




!!DMI Information
!!---------------

Manufacturer:      System manufacturer
Product Name:      System Product Name


!!Kernel Information
!!------------------

Kernel release:    2.6.28-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       No


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.19
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe8f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeae8000 irq 19


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
04:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:14.2 0403: 1002:4383
	Subsystem: 1043:8289
--
01:05.2 0403: 1002:7919
	Subsystem: 1043:8287


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-ati: model=3stack-dig


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
-ne 	
bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1
-ne 	
enable : Y,Y,Y,Y,Y,Y,Y,Y
-ne 	
enable_msi : 0
-ne 	
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne 	
index : -1,-1,-1,-1,-1,-1,-1,-1
-ne 	
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne 	
position_fix : 0,0,0,0,0,0,0,0
-ne 	
power_save : 0
-ne 	
power_save_controller : Y
-ne 	
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
-ne 	
probe_only : N,N,N,N,N,N,N,N
-ne 	
single_cmd : N

!!Module: snd_hda_intel
-ne 	
bdl_pos_adj : 32,32,-1,-1,-1,-1,-1,-1
-ne 	
enable : Y,Y,Y,Y,Y,Y,Y,Y
-ne 	
enable_msi : 0
-ne 	
id : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne 	
index : -1,-1,-1,-1,-1,-1,-1,-1
-ne 	
model : <NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>,<NULL>
-ne 	
position_fix : 0,0,0,0,0,0,0,0
-ne 	
power_save : 0
-ne 	
power_save_controller : Y
-ne 	
probe_mask : -1,-1,-1,-1,-1,-1,-1,-1
-ne 	
probe_only : N,N,N,N,N,N,N,N
-ne 	
single_cmd : N


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC883
Address: 0
Function Id: 0x1
Vendor Id: 0x10ec0883
Subsystem Id: 0x10438289
Revision Id: 0x100002
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x01 0x01]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Amp-In caps: ofs=0x08, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x160]: 44100 48000 96000
    bits [0x6]: 16 20
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x01 0x01]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x11 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x12 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01011412: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01016411: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003e: IN OUT HP Detect Trigger
  Pin Default 0x01012414: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x01a19c40: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02a19c50: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x0181344f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000173e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x00:
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01441130: [Jack] SPDIF Out at Ext Rear
    Conn = RCA, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400200: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=17
  Processing Coefficient: 0x00
  Coefficient Index: 0x0c
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Amp-Out caps: N/A
  Amp-Out vals:  [0x00 0x00]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 2
     0x25 0x0b
Codec: ATI RS690/780 HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002791a
Subsystem Id: 0x00791a00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18565010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Red
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
--endcollapse--

```

I tried several settings and don't know what to change any more. Some more info:

alsa-base.conf:
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-ati model=3stack-

```

/etc/pulse/default.pa:
```

#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

# This startup script is used only if PulseAudio is started per-user
# (i.e. not in system mode)

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav
load-sample-dir-lazy /usr/share/sounds/ubuntu/stereo

.fail

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

### Automatically augment property information from .desktop files
### stored in /usr/share/application
load-module module-augment-properties

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

### Automatically load driver modules for Bluetooth hardware
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Make sure we always have a sink around, even if it is a null sink.
load-module module-always-sink

### If autoexit on idle is enabled we want to make sure we only quit
### when no local session needs us anymore.
load-module module-console-kit

### Enable positioned event sounds
load-module module-position-event-sounds

### Cork music streams when a phone stream is active
load-module module-cork-music-on-phone

# X11 modules should not be started from default.pa so that one daemon
# can be shared by multiple sessions.

### Load X11 bell module
#load-module module-x11-bell sample=bell-windowing-system

### Register ourselves in the X11 session manager
#load-module module-x11-xsmp

### Publish connection data in the X11 root window
#.ifexists module-x11-publish.so
#.nofail
#load-module module-x11-publish
#.fail
#.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

/etc/modules:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
sbp2
```

There's no sound. Default Sound Card is changed to HDMI. Sound Preferences is set to HDA ATI HDMI (Alsa Mixer) - IEC958. I'm using Mythbuntu 9.04 (32bit). My Asus Pundit PC is connected to a Panasonic Plasma via HDMI Cable.

Thanks in advance

Stevi.

---

### Post by Yellow Pasque on 2009-08-10
Stevi, what video driver are you using?

---

### Post by guy0089 on 2009-12-25
I installed this last night and have been having problems.
 
First some system info:
-I'm dual booting Windows 7 and Ubuntu (9.04)
-This is on a Gateway laptop T-1631
 
My laptop is shutting down "randomly".  Basically this came up like this:
 
I run this script, fine.  I restart my computer, fine.  I log into Ubuntu, fine.  Then the problem starts: when everything is nearly loaded, it shuts down (power just cuts out).  I restarted it and the problem got worse.  Everytime I restart, it shut down faster and faster, until it was shutting down just 11 seconds after start up (before even getting to grub loader to allow me to choose my OS).  Even if I'm in the BIOS, it will still restart.
 
I'm not familiar enough with the workings of this script or computer hardware to know what is going on, but this never happened before and it happened right after running this script.
 
Another weird thing: sometimes it starts up in windows without restarting.  What I have found is that if I manage to log onto windows, I'm home free.  It won't restart (as far as I know), and I have had windows up and running for about an hour (normally this problem shows up within seconds, so this leads me to believe it will run indefinietly in windows).
 
Ideas?

---

### Post by kovit on 2010-06-08
It seems to me that Toshiba L30-134 (codec Realtek ALC861-VD) with Lucid has some strange sound conflicts between ALSA and Pulseaudio and can take all processor's speed during this. I have a sound but randomly it turns to a noise when this conflict appears. It can begin when I start OpenArena (and I hear only a noise besides hard game slowlyness) or can appear when I open sound-volume applet (with a hard breakings). I didn't find something alike my problem here. Do someone had the same problems and may be someone know how it could be solved? Thank you.

---

### Post by youboontu on 2010-07-24
I just installed pulse audio and the alsa mixer and it didn't work so I tried this script and I got some errors during compile. Audio worked fine in Ubuntu 9.04, but I'm having trouble with 9.10.

I have an Acer 5102WLMi, i386, with kernel 2.6.28-18-generic

```
***************************************************************************
*  Compiling drivers...
***************************************************************************
rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
Makefile:6: ../Makefile.conf: No such file or directory
make[1]: *** No rule to make target `../Makefile.conf'.  Stop.
make[1]: Leaving directory `/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/include'
make: *** [clean] Error 1
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/Alsa-1.0.23/alsa-driver-1.0.23
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

***************************************************************************
*  alsa-driver-1.0.23 configure failed
***************************************************************************

```

---

### Post by blackest_knight on 2010-07-25
Looks like kernel headers are missing.

sudo apt-get install build-essential 

should do the trick.

if not then you probably need some packages with dev in the name 

alternatively you might want to try ubuntu 10.4

pulse was quite buggy initially but 10.4 seems to have got everything working properly (only issue I have now is the internal mike is sort of stereo and out of phase so you need to  turn left or right down and the other side up  or the net result is silence),

---

### Post by edde_e on 2010-12-10
Hi, I am a new ubuntu user and I love it but I have a major problem:
I cant get alsa-drive to install on my system, i have tried everything  and i look all over the net and tried every work aound and even the Alsa  Upgrade Script and nothing I get the same error:

```
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:489: error:  implicit declaration of function ‘pm_qos_remove_requirement’
/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore/pcm_native.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.23/alsa-driver-1.0.23/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.23/alsa-driver-1.0.23] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [compile] Error 2

**************************************************  *************************
*  alsa-driver-1.0.23 make failed
**************************************************  *************************
```It always happens on the make cmd. I have no sound at all. Here my system out put:
```

!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Sat Dec 11 00:09:05 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Acer           
Product Name:      Aspire 7736                    

!!Kernel Information
!!------------------

Kernel release:    2.6.35-23-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes

!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23

!!Loaded ALSA modules
!!-------------------

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) Realtek ACL888


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
    Subsystem: 1025:0296
```
I had used Fedora and Mandriva One before and never had this problem with this laptop.
I like the way Ubuntu is design and is more easy for my kids to use it.

---

### Post by Nethippy on 2010-12-26
> **clarkey45 said:**
> I've tried using this script but the driver is failing to compile. Can anyone help?

I'm running Mythbuntu 8.04 kernel 2.6.24-16-generic

My compile error:

```
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o
In file included from /usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.c:2:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c: In function âsnd_hrtimer_callbackâ:
/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/../alsa-kernel/core/hrtimer.c:29: error: implicit declaration of function âhrtimer_forward_nowâ
make[3]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore/hrtimer.o] Error 1
make[2]: *** [/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a/acore] Error 2
make[1]: *** [_module_/usr/src/Alsa-1.0.18a/alsa-driver-1.0.18a] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2

```

I'm getting this as well. Tried removing hrtimer from the cards list in the script but I still get it.Running mythbuntu 10.10. Integrated nvidia audio on motherboard and geforce 210 graphics card w/hdmi output.

---

### Post by Yellow Pasque on 2010-12-27
> **Nethippy said:**
> I'm getting this as well. Tried removing hrtimer from the cards list in the script but I still get it.Running mythbuntu 10.10. Integrated nvidia audio on motherboard and geforce 210 graphics card w/hdmi output.
Maverick already has the latest stable ALSA (1.0.23). Also, this thread (and the script it has) is obsolete (please use this one: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137) )

---

