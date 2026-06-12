---
title: "Speakers AND headphones playing sound simultaneously."
date: 2009-12-28
forum: Multimedia Software
---

### Post by bdws1975 on 2009-12-28
Hi all,

I just noticed today that when I plug in my headphones, I still hear sound through my laptop speakers.

I'm on an HP pavillion, running ubuntu 9.10 and I use rhythmbox as my media player.

Thanks!
Brett

---

### Post by garryknight on 2009-12-28
I'm running Kubuntu 9.10 and it behaves exactly the same. And I'm happy about this because it means that I can control the volume of both my headphones/headset and my speakers myself. On the rare occasion that I use Windows, I don't get this choice; it thinks that if I plug in the headphones, I don't want the sound coming out of the speakers.

But I want to leave my headset plugged into the front of my PC so that I can handle skype calls by simply switching on the mic. And I have the option to leave the speaker volume up so that others in the room can hear both sides of the conversation, or to mute it if it's private.

---

### Post by bdws1975 on 2009-12-28
Hi there,

I actually agree, except there are times when i don't' want others to hear what I'm listening to.  I've looked around and can't find where to turn the speakers down without turning the headphones down also.

Any suggestions?

Thanks,
Brett

> **garryknight said:**
> I'm running Kubuntu 9.10 and it behaves exactly the same. And I'm happy about this because it means that I can control the volume of both my headphones/headset and my speakers myself. On the rare occasion that I use Windows, I don't get this choice; it thinks that if I plug in the headphones, I don't want the sound coming out of the speakers.

But I want to leave my headset plugged into the front of my PC so that I can handle skype calls by simply switching on the mic. And I have the option to leave the speaker volume up so that others in the room can hear both sides of the conversation, or to mute it if it's private.

---

### Post by Yellow Pasque on 2009-12-28
Usually, this means you need to specify a model keyword in /etc/modprobe.d/alsa-base.conf so jack sensing will work properly.

---

### Post by bdws1975 on 2009-12-28
thanks for the reply.  What do I do to specify the model keyword?

Thanks,
Brett

> **Temüjin said:**
> Usually, this means you need to specify a model keyword in /etc/modprobe.d/alsa-base.conf so jack sensing will work properly.

---

### Post by Yellow Pasque on 2009-12-28
It depends on your computer model and audio codec.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add a line like the following:
```
options snd_hda_intel model=hp-dv5
```

Use this to figure out what codec you have:
```
aplay -l
```

*model* could be one of the following:
```
  Model name	Description
  ----------    -----------
ALC880
======
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
======
  hp		HP machines
  hp-3013	HP machines (3013-variant)
  hp-dc7600	HP DC7600
  fujitsu	Fujitsu S7020
  acer		Acer TravelMate
  will		Will laptops (PB V7900)
  replacer	Replacer 672V
  favorit100	Maxdata Favorit 100XS
  basic		fixed pin assignment (old default model)
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC262
======
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
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)

ALC267/268
==========
  quanta-il1	Quanta IL1 mini-notebook
  3stack	3-stack model
  toshiba	Toshiba A205
  acer		Acer laptops
  acer-dmic	Acer laptops with digital-mic
  acer-aspire	Acer Aspire One
  dell		Dell OEM laptops (Vostro 1200)
  zepto		Zepto laptops
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

ALC662/663/272
==============
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
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
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
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

ALC861/660
==========
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
==============
  3stack	3-jack
  3stack-dig	3-jack with SPDIF OUT
  6stack-dig	6-jack with SPDIF OUT
  3stack-660	3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo	Lenovo 3000 C200
  dallas	Dallas laptops
  hp		HP TX1000
  asus-v1s	ASUS V1Sn
  auto		auto-config reading BIOS (default)

CMI9880
=======
  minimal	3-jack in back
  min_fp	3-jack in back, 2-jack in front
  full		6-jack in back, 2-jack in front
  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
  allout	5-jack in back, 2-jack in front, SPDIF out
  auto		auto-config reading BIOS (default)

AD1882 / AD1882A
================
  3stack	3-stack mode (default)
  6stack	6-stack mode

AD1884A / AD1883 / AD1984A / AD1984B
====================================
  desktop	3-stack desktop (default)
  laptop	laptop with HP jack sensing
  mobile	mobile devices with HP jack sensing
  thinkpad	Lenovo Thinkpad X300

AD1884
======
  N/A

AD1981
======
  basic		3-jack (default)
  hp		HP nx6320
  thinkpad	Lenovo Thinkpad T60/X60/Z60
  toshiba	Toshiba U205

AD1983
======
  N/A

AD1984
======
  basic		default configuration
  thinkpad	Lenovo Thinkpad T61/X61
  dell_desktop	Dell T3400

AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)
  samsung-p50	2-channel with HP-automute (Samsung P50)

AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)

Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq		Benq R55E
  laptop-hp530	HP 530 laptop
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5047
=============
  laptop	Basic Laptop config 
  laptop-hp	Laptop config for some HP models (subdevice 30A5)
  laptop-eapd	Laptop config with EAPD support
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5051
=============
  laptop	Basic Laptop config (default)
  hp		HP Spartan laptop
  hp-dv6736	HP dv6736
  lenovo-x200	Lenovo X200 laptop

Conexant 5066
=============
  laptop	Basic Laptop config (default)
  dell-laptop	Dell laptops
  olpc-xo-1_5	OLPC XO 1.5

STAC9200
========
  ref		Reference board
  oqo		OQO Model 2
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
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)

STAC9205/9254
=============
  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)

STAC9220/9221
=============
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
  ecs202	ECS/PC chips
  dell-d81	Dell (unknown)
  dell-d82	Dell (unknown)
  dell-m81	Dell (unknown)
  dell-m82	Dell XPS M1210
  auto		BIOS setup (default)

STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  5stack-no-fp	D965 5stack without front panel
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  auto		BIOS setup (default)

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)
  auto		BIOS setup (default)

STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  auto		BIOS setup (default)

STAC92HD83*
===========
  ref		Reference board
  mic-ref	Reference board with power managment for ports
  dell-s14	Dell laptop
  auto		BIOS setup (default)

STAC9872
========
  vaio		VAIO laptop without SPDIF
  auto		BIOS setup (default)

Cirrus Logic CS4206/4207
========================
  mbp55		MacBook Pro 5,5
  auto		BIOS setup (default)
```

---

### Post by bdws1975 on 2009-12-28
this is what I see when I type aplay -l in the command terminal.

Brett

---

### Post by budgieboy on 2009-12-28
are you running pulse audio sound server?

---

### Post by bdws1975 on 2009-12-28
no, I'm not.  should I be?

thanks,
brett

---

### Post by bdws1975 on 2009-12-28
Ok, I installed pulse and now it doesn't recognize any soundcards.

Anyone help?

thanks,
Brett

---

### Post by budgieboy on 2009-12-28
No, not particularly. But if you had then the pulse audio control allows simulaneous playback on your soundcoard and headphones - I just thought it could have been a reason for the multi-playback. This can be switched on and off at will using the pulseaudio applet volume control.

---

### Post by punkdrummer09 on 2009-12-29
I too started experiencing this problem earlier. I have an HP Pavilion Slimline desktop. When I type 'alsamixer' in the terminal, the headphone volume is at 0 and I cant change it. I'm also unsure of what model should go into this line: 
options snd_hda_intel model=model
 If anyone can help me out, I would greatly appreciate it.

---

### Post by platypus1000 on 2010-01-31
I have this problem as well. I have a Toshiba Satellite T135-1309. It has a Conexant 5066 chip. I have tried passing all three values of model listed for the Contexant 5066. No luck with any of them.
 
Any one else able to figure this out?
 
Punkdrummer: 
[LIST=1]
[*]Find out what codec you have ```
cat /proc/asound/card0/codec#* | grep Codec
```
[*]Look up the codec in the list Temujin provided on the first page.  That will tell you the different models that the codec supports
[*]Replace MODEL in ```
options snd-hda-intel model=MODEL
``` with each one, reboot, and test the sound.
[/LIST]More details about this are at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by sahayes on 2010-02-11
Hi, I'm new to Ubuntu, and I noticed my Compaq Presario CQ-60 laptop has sound coming out of the speakers and the headphones.  My sound chip is Conexant ID 5067.  Since it wasn't listed, am I out of luck?  Thanks, sahayes

---

### Post by ancientrustic on 2010-02-26
I have a Toshiba Satellite with a Conexant 5067. Can anyone out there help?

---

### Post by secondstage on 2010-03-15
Hopefully this will be fixed in 10.04 but for now I'm also in the same boat. Got a Toshiba T135D-S1324 a few days ago, and wish I had done some research prior to purchase. Mine has a Conexant ID 5066

---

### Post by eternal243 on 2010-03-18
> **Temüjin said:**
> It depends on your computer model and audio codec.
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Add a line like the following:
```
options snd_hda_intel model=hp-dv5
```

Use this to figure out what codec you have:
```
aplay -l
```

*model* could be one of the following:
```
  Model name	Description
  ----------    -----------
ALC880
======
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
======
  hp		HP machines
  hp-3013	HP machines (3013-variant)
  hp-dc7600	HP DC7600
  fujitsu	Fujitsu S7020
  acer		Acer TravelMate
  will		Will laptops (PB V7900)
  replacer	Replacer 672V
  favorit100	Maxdata Favorit 100XS
  basic		fixed pin assignment (old default model)
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC262
======
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
  tyan		Tyan Thunder n6650W (S2915-E)
  ultra		Samsung Q1 Ultra Vista model
  lenovo-3000	Lenovo 3000 y410
  nec		NEC Versa S9100
  basic		fixed pin assignment w/o SPDIF
  auto		auto-config reading BIOS (default)

ALC267/268
==========
  quanta-il1	Quanta IL1 mini-notebook
  3stack	3-stack model
  toshiba	Toshiba A205
  acer		Acer laptops
  acer-dmic	Acer laptops with digital-mic
  acer-aspire	Acer Aspire One
  dell		Dell OEM laptops (Vostro 1200)
  zepto		Zepto laptops
  test		for testing/debugging purpose, almost all controls can
		adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y
  auto		auto-config reading BIOS (default)

ALC269
======
  basic		Basic preset
  quanta	Quanta FL1
  eeepc-p703	ASUS Eeepc P703 P900A
  eeepc-p901	ASUS Eeepc P901 S101
  fujitsu	FSC Amilo
  lifebook	Fujitsu Lifebook S6420
  auto		auto-config reading BIOS (default)

ALC662/663/272
==============
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
  dell		Dell with ALC272
  dell-zm1	Dell ZM1 with ALC272
  samsung-nc10	Samsung NC10 mini notebook
  auto		auto-config reading BIOS (default)

ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
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
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

ALC861/660
==========
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
==============
  3stack	3-jack
  3stack-dig	3-jack with SPDIF OUT
  6stack-dig	6-jack with SPDIF OUT
  3stack-660	3-jack (for ALC660VD)
  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
  lenovo	Lenovo 3000 C200
  dallas	Dallas laptops
  hp		HP TX1000
  asus-v1s	ASUS V1Sn
  auto		auto-config reading BIOS (default)

CMI9880
=======
  minimal	3-jack in back
  min_fp	3-jack in back, 2-jack in front
  full		6-jack in back, 2-jack in front
  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
  allout	5-jack in back, 2-jack in front, SPDIF out
  auto		auto-config reading BIOS (default)

AD1882 / AD1882A
================
  3stack	3-stack mode (default)
  6stack	6-stack mode

AD1884A / AD1883 / AD1984A / AD1984B
====================================
  desktop	3-stack desktop (default)
  laptop	laptop with HP jack sensing
  mobile	mobile devices with HP jack sensing
  thinkpad	Lenovo Thinkpad X300

AD1884
======
  N/A

AD1981
======
  basic		3-jack (default)
  hp		HP nx6320
  thinkpad	Lenovo Thinkpad T60/X60/Z60
  toshiba	Toshiba U205

AD1983
======
  N/A

AD1984
======
  basic		default configuration
  thinkpad	Lenovo Thinkpad T61/X61
  dell_desktop	Dell T3400

AD1986A
=======
  6stack	6-jack, separate surrounds (default)
  3stack	3-stack, shared surrounds
  laptop	2-channel only (FSC V2060, Samsung M50)
  laptop-eapd	2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra		2-channel with EAPD (Samsung Ultra tablet PC)
  samsung	2-channel with EAPD (Samsung R65)
  samsung-p50	2-channel with HP-automute (Samsung P50)

AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack	6-jack
  6stack-dig	ditto with SPDIF
  3stack	3-jack
  3stack-dig	ditto with SPDIF
  laptop	3-jack with hp-jack automute
  laptop-dig	ditto with SPDIF
  auto		auto-config reading BIOS (default)

Conexant 5045
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq		Benq R55E
  laptop-hp530	HP 530 laptop
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5047
=============
  laptop	Basic Laptop config 
  laptop-hp	Laptop config for some HP models (subdevice 30A5)
  laptop-eapd	Laptop config with EAPD support
  test		for testing/debugging purpose, almost all controls
		can be adjusted.  Appearing only when compiled with
		$CONFIG_SND_DEBUG=y

Conexant 5051
=============
  laptop	Basic Laptop config (default)
  hp		HP Spartan laptop
  hp-dv6736	HP dv6736
  lenovo-x200	Lenovo X200 laptop

Conexant 5066
=============
  laptop	Basic Laptop config (default)
  dell-laptop	Dell laptops
  olpc-xo-1_5	OLPC XO 1.5

STAC9200
========
  ref		Reference board
  oqo		OQO Model 2
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
  gateway-m4	Gateway laptops with EAPD control
  gateway-m4-2	Gateway laptops with EAPD control
  panasonic	Panasonic CF-74
  auto		BIOS setup (default)

STAC9205/9254
=============
  ref		Reference board
  dell-m42	Dell (unknown)
  dell-m43	Dell Precision
  dell-m44	Dell Inspiron
  eapd		Keep EAPD on (e.g. Gateway T1616)
  auto		BIOS setup (default)

STAC9220/9221
=============
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
  ecs202	ECS/PC chips
  dell-d81	Dell (unknown)
  dell-d82	Dell (unknown)
  dell-m81	Dell (unknown)
  dell-m82	Dell XPS M1210
  auto		BIOS setup (default)

STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  5stack-no-fp	D965 5stack without front panel
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  auto		BIOS setup (default)

STAC92HD71B*
============
  ref		Reference board
  dell-m4-1	Dell desktops
  dell-m4-2	Dell desktops
  dell-m4-3	Dell desktops
  hp-m4		HP mini 1000
  hp-dv5	HP dv series
  hp-hdx	HP HDX series
  hp-dv4-1222nr	HP dv4-1222nr (with LED support)
  auto		BIOS setup (default)

STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  auto		BIOS setup (default)

STAC92HD83*
===========
  ref		Reference board
  mic-ref	Reference board with power managment for ports
  dell-s14	Dell laptop
  auto		BIOS setup (default)

STAC9872
========
  vaio		VAIO laptop without SPDIF
  auto		BIOS setup (default)

Cirrus Logic CS4206/4207
========================
  mbp55		MacBook Pro 5,5
  auto		BIOS setup (default)
```

Thanks for this, this solution worked very well for me on an acer aspire 7736ZG defining my model as **"acer-aspire-7730g"**.

---

### Post by saiganeshb on 2010-05-30
> **eternal243 said:**
> Thanks for this, this solution worked very well for me on an acer aspire 7736ZG defining my model as **"acer-aspire-7730g"**.
Hi,
I am using conexant 5069 
which is the output of:
head -n 1 /proc/asound/card0/codec*

output:
Codec: Conexant ID 5069

but this model is absent from the above list. Where do i find the complete list ?

---

### Post by lidex on 2010-05-30
> **saiganeshb said:**
> Hi,
I am using conexant 5069 
which is the output of:
head -n 1 /proc/asound/card0/codec*

output:
Codec: Conexant ID 5069

but this model is absent from the above list. Where do i find the complete list ?

I haven't seen it. Do this for me. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version

```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by slooksterpsv on 2010-05-30
I have a Gateway NV53 - here's the output of aplay and of cat:
[quote=aplay]
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/quote]

[quote=cat]
Codec: Conexant CX20561 (Hermosa)
Codec: Conexant ID 2c06
[/quote]

Let me know, thanks!

---

### Post by Yellow Pasque on 2010-05-30
> **slooksterpsv said:**
> I have a Gateway NV53 
[http://www.backports.ubuntuforums.org/showthread.php?p=9318502](http://www.backports.ubuntuforums.org/showthread.php?p=9318502)

---

### Post by nmfralich on 2010-05-31
With regards to eternal243's post, I would also like to offer an option for filling in the "model=" parameter.  I was browsing an [[COLOR="Blue"]ArchLinux forum[/COLOR]]("http://bbs.archlinux.org/viewtopic.php?id=95506") and one user recommended using 

options snd-hda-intel model=auto

for /etc/modprobe.d/alsa-base.conf

I mention this only because my Lenovo Y510 running 10.04, using model=lenovo nb0763 was giving me subwoofer support but not headphones and with it disabled giving me the opposite and only giving me internal mic support with it disabled, but by using model=auto I have everything at the same time!!!

Just something to try...

---

### Post by phyrewall on 2010-06-01
**Someone please help me fix this problem!** I have an Alienware M9750, and ever since Karmic, pulseaudio has screwed up headphone detection (it doesn't, even though the way the speakers sound changes on the laptop) and plays through both the speakers and the headphones all the time. The only solution I've had is to kill pulseaudio and use alsamixer to turn off the speakers. Also of note is the fact that the optical (digital) out and the surround pugs aren't working correctly either.

Here's the obligatory information:

```
phyrewall@zangetsu:~$ uname -a
Linux zangetsu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

```
phyrewall@zangetsu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
phyrewall@zangetsu:~$ cat /proc/asound/card0/codec#* | grep CodecCodec: Realtek ALC889A
Codec: LSI ID 1040

```

```
phyrewall@zangetsu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```

Thanks in advance, this is really bugging me!!

---

### Post by lidex on 2010-06-01
> **phyrewall said:**
> **Someone please help me fix this problem!** I have an Alienware M9750, and ever since Karmic, pulseaudio has screwed up headphone detection (it doesn't, even though the way the speakers sound changes on the laptop) and plays through both the speakers and the headphones all the time. The only solution I've had is to kill pulseaudio and use alsamixer to turn off the speakers. Also of note is the fact that the optical (digital) out and the surround pugs aren't working correctly either.

Here's the obligatory information:

```
phyrewall@zangetsu:~$ uname -a
Linux zangetsu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

```
phyrewall@zangetsu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
phyrewall@zangetsu:~$ cat /proc/asound/card0/codec#* | grep CodecCodec: Realtek ALC889A
Codec: LSI ID 1040

```

```
phyrewall@zangetsu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```

Thanks in advance, this is really bugging me!!


Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=6stack-dig 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by mykrob on 2010-06-01
figure I'll try my laptop too, why not...

Its an Asus K50IJ.

Here's the info on the sound card:



```

myk@mobileOne:/etc/modprobe.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
myk@mobileOne:/etc/modprobe.d$ cat /proc/asound/card0/codec#* | grep Codec
Codec: VIA VT1708S
myk@mobileOne:/etc/modprobe.d$ 

```

I have the same problem, the speaker still plays when my headphones are plugged in.
Need assistance with the correct model setting for alsa, please.

Thanks in advance.
-myk

---

### Post by mykrob on 2010-06-02
bump

---

### Post by pigphish on 2010-06-02
I have the same issue. I manually direct output to my headphones to resolve the issue. 

Firstly, it's worth pointing out I did not even get a headphone option until I added the correct model to the alsa-base.conf file. 

To switch to headphones I go to:
1. system->preferences->sound
2. Then switch to output tab
3. You should see a drop down (connector). Switch it to headphones or analog headphones. 
4. When done switch back. 

If you don't see a connector drop down you need to correct your model in alsa-base.conf

Hope this helps, George

---

### Post by mykrob on 2010-06-02
I get the headphone connector option all the time, it just still continues to play through both. In the process of trial and error now. Tried the obvious "asus-laptop" for mine, but no dice...

---

### Post by pigphish on 2010-06-02
I would try a few other models. I tried a bunch until one finally worked.

---

### Post by saiganeshb on 2010-06-03
> **lidex said:**
> I haven't seen it. Do this for me. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version

```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)
hi,
sorry for replying late, didn't check this forum in days .

Anyway, heres the output I get:
```

$uname -a

Linux user@laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux


``````

$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


``````

$cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

```Laptop Model: Lenovo G560
Thanks!

---

### Post by lidex on 2010-06-04
> **saiganeshb said:**
> hi,
sorry for replying late, didn't check this forum in days .

Anyway, heres the output I get:
```

$cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

```Laptop Model: Lenovo G560
Thanks!

OK. Follow the alsa-upgrade link in my sig to update your install to 1.0.23

---

### Post by saiganeshb on 2010-06-06
> **lidex said:**
> OK. Follow the alsa-upgrade link in my sig to update your install to 1.0.23
Well, I upgraded it to alsa 1.0.23 .Here are my new outputs(still not working though):
```

$uname -a
Linux user-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
``````
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


``````

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun  6 2010 for kernel 2.6.32-22-generic (SMP).

```Even my codec info changed from conexant id 5059 to CX20585
```

$cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20585


```
I cannot find anything relevant in 
```

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

```
(from [http://ubuntuforums.org/showthread.php?p=9294918#post9294918](http://ubuntuforums.org/showthread.php?p=9294918#post9294918) )

---

### Post by lidex on 2010-06-06
*saiganeshb* Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by saiganeshb on 2010-06-06
> **lidex said:**
> *saiganeshb* Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Earlier ,I used to hear audio from both the internal speakers and the headphones. Now it doesn't play through the headphones even if they are connected.
i.e its not detecting my headphones after upgrading alsa! :(
(if i try to change the output device in system->preferences->sound from 'Internal Audio Analog Stereo' to 'High Definition Audio Controller Digital Stereo(HDMI)' )

I attached my alsa-base configuration file.
Can you please elaborate what do sound levels for 'S/PDIF' represent? they were muted when i tried to run alsamixer .I can only unmute/mute them but none of them seem to send output to my headphones.

---

### Post by lidex on 2010-06-06
The analog card is the one you would use for headphones, not digital(spdif). If those options are not working try changing the model to lenovo. Then try only one line at a time. You'll need to reboot each time for the changes to take effect.

---

### Post by mykrob on 2010-06-06
any advice for me? Still banging my head over this Asus laptop...

Thanks,
-myk

---

### Post by Earth_Quake on 2010-06-08
Hello All!

My laptop Asus K52j series.
My problem, the  headset and the speaker is about the same time...

```

root@earthq:/home/earthq# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@earthq:/home/earthq# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@earthq:/home/earthq# 

``````

root@earthq:/home/earthq# cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20585

``````

root@earroot@earthq:/home/earthq# uname -a
Linux earthq 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux 

``````

root@earthq:/home/earthq# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 27 2010 for kernel 2.6.32-22-generic (SMP).
root@earthq:/home/earthq# 

```thanks!

---

### Post by saiganeshb on 2010-06-14
SOLVED!
After 9 painful days of searching and installing needless stuff ...it's funny when you overlook the obvious(googling for the necessary audio driver) from the simple(googling  endless forums to add a line in the alsa configuration file). For all conexant audio chip problems ,I guess here is the solution :

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

download the .deb package from 
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip)

unzip it
```

unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip 

```run it ! (enter password when prompted) 
```

 sudo dpkg -i  alsa-driver-linuxant_1.0.23.0_all.deb 

```Everything works perfectly on my laptop now. :KS
If you have a similar problem of not finding the correct option to put in that alsa conf file, i suggest you google for the appropriate linux drivers first.

---

### Post by lidex on 2010-06-14
The conexant codecs have definitely been a problem. Thanks for that pointer *saiganeshb*!

---

### Post by sleepitoff on 2010-06-14
Thank you so much!

---

### Post by MrPotter on 2010-06-22
> **mykrob said:**
> any advice for me? Still banging my head over this Asus laptop...

Thanks,
-myk

 Same for me! Anybody knows what model whe need?  
0 [Intel]: HDA-Intel - HDA Intel            
HDA Intel at 0xfe9f4000 irq 22
Codec: [B]VIA VT1708S

[/B]I cannot find a model for Codec **VIA VT1708S **in the configuration manual.

Please help! Thx!

---

### Post by lidex on 2010-06-22
I don't know about that codec either. An upgrade to alsa 1.0.23 might help (follow the link in my sig). Here are the asus options I have cataloged:
```
ASUS
options snd-hda-intel probe_mask=1
options snd-hda-intel enable=1 index=0 model=lenovo
or model=3stack-dig

ASUS G60VX / Realtek ALC663:
options snd-hda-intel model=asus-mode3

ASUS K42JR / ALC269
options snd-hda-intel model=lifebook 

ASUS K70I / Realtek ALC662:
options snd-hda-intel model=asus-mode3

Asus P7P55D (MB) / Via VT2020
options snd-hda-intel model=6stack-digout 
```

And these are from *markbuntu's* [thread]("http://ubuntuforums.org/showthread.php?t=1043568"):
```
ASUS
A7J model= asus-a7j
A7M model=asus-a7m
F2/F3 model= asus-laptop
F6A-2 model=6stack
enable_msi=1
single_cmd=1
G50v model=g50v
G71v model=g71v
H13 model=h13
M2R32-MVP model=6stack
M51SN-AP067G model=lenovo
NV80 model=g50v position_fix=0
X20G, U1E model=lenovo
W2JC model=w2jc
Eeepc P701 model=eeepc-p701
Eeepc-EP20 model=eeepc-ep20
```

---

### Post by leomm20 on 2010-06-25
PERFECTO!!!
con la actualización de [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) me quedó funcionando a la perfección!! (mi note es una ASUS K52F, core i3 350M)

MUCHAS GRACIAS!!

---

### Post by lidex on 2010-06-27
> **leomm20 said:**
> PERFECTO!!!
con la actualización de [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) me quedó funcionando a la perfección!! (mi note es una ASUS K52F, core i3 350M)

MUCHAS GRACIAS!!

**WARNING** _*Do not install linuxant driver unless you have conexant audio chip. It will totally bork your audio on other devices!*_ Find your codec using this command in a terminal:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by MrPotter on 2010-07-05
> **lidex said:**
> I don't know about that codec either. An upgrade to alsa 1.0.23 might help (follow the link in my sig). 

Does not work for me. I tried all possible options from your list before and after the alsa upgrade. Are there any other tips you can provide?

Thx

---

### Post by lidex on 2010-07-05
> **MrPotter said:**
> Does not work for me. I tried all possible options from your list before and after the alsa upgrade. Are there any other tips you can provide?

Thx
Can you provide some more info? 

Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by MrPotter on 2010-07-09
[LEFT]Hi lidex,

here can you find the output from alsa-info script:
[http://www.alsa-project.org/db/?f=2939ed08b62ec9e77435b078ee3aa224b21974e9](http://www.alsa-project.org/db/?f=2939ed08b62ec9e77435b078ee3aa224b21974e9)

Thank's for your support! ;)

**+++++Update++++**

Now it works! I deleted the options-line in the config file completly. Then I changend in the sound preferences in the output-tab the "connection link" to "Headphones". After I turned up the volume from channel "Front" with alsamixer, I can change between speakers and headphones without any problem. [/LEFT]

---

### Post by r7s on 2010-07-11
Hi everybody, it's my first post here.

I've tried almost every method posted in this thread, but nothing has helped. But when I've installed the driver from linuxant my subwoofer (my laptop is Lenovo IdeaPad Y550) has begun to work properly :D That wasn't the main problem and later I've read, that this driver is for Conexant chipsets, so I've removed it.

Now, here's my output from Alsa Info Script. Can you look at it?

[http://www.alsa-project.org/db/?f=fcb13e4ed9c59ba7a271ad67af363a2bfd2a5282](http://www.alsa-project.org/db/?f=fcb13e4ed9c59ba7a271ad67af363a2bfd2a5282)

---

### Post by lidex on 2010-07-11
Try upgrading your alsa install via the alsa-upgrade link in my sig.

---

### Post by r7s on 2010-07-11
Alsa upgraded and the problem still exists.

Hm, take a look at these screenshots (from GNOME Alsamixer):

[LIST]
[*]Screenshot #1: laptop speaker is "muted" by turning down its volume, everything's fine
[*]Screenshot #2: laptop speaker is muted by clicking on a checkbox; the whole sound is muted
[/LIST]

In fact I don't use laptop speaker under Ubuntu, so is it possible to turn it off by running a script at startup? I know, it's only a simple hook, not a solution for this problem, but I don't care ;)

Second edit:

I just realised that even if I turn the speaker volume down, it changes along with the master volume.

---

### Post by lidex on 2010-07-11
First check in gnome-alsamixer, 'Edit>Sound Card Properties' for any elements not enabled resembling 'jack sense'. In Sound Preferences, on the 'Hardware' tab, select that soundcard and adjust the profile - possibly 'analog stereo duplex' and on the 'Output' tab check your connector.

Is this a two channel or six channel model? How many audio jacks are there?

---

### Post by r7s on 2010-07-12
> **lidex said:**
> First check in gnome-alsamixer, 'Edit>Sound Card Properties' for any elements not enabled resembling 'jack sense'.

I've enabled all elements and any of these hasn't been similar to "jack sense".

> **lidex said:**
> In Sound Preferences, on the 'Hardware' tab, select that soundcard and adjust the profile - possibly 'analog stereo duplex' and on the 'Output' tab check your connector.

There are three options: "Analog headphones", "Analog output" and "Analog speakers". When I choose:
[LIST]
[*]"Analog speakers" - *everything's the same*.
[*]"Analog headphones" - situation from screenshot number 2; the speaker volume doesn't change along with the master volume.
[*]"Analog output" - situation from screenshot number 1; the speaker volume doesn't change along with the master volume.
[/LIST]

So, changing the connector to "Analog headphones" or "Analog output" **solves** my problem.

> **lidex said:**
> How many audio jacks are there?

One for mic and one for headphones.

> **lidex said:**
> Is this a two channel or six channel model?

Hard to say, because I don't know how to check it, but I think it's a two channel model.

---

### Post by EllyBilateralCI on 2010-07-14
Hi,

I've got VIA vt1708s audio codec - it's based on ASUS m4a785td-m evo motherboard.  It's a homemade pc kit.

I've got 8 jacks - six at the back and two at the front.  

How do you force Ubuntu to use vt1708s in /etc/modprobe.d/alsa-base.conf?

I've used [http://ubuntuforums.org/showthread.php?t=1515893&page=1](http://ubuntuforums.org/showthread.php?t=1515893&page=1) to ensure that I had the latest alsa and to no avail that I've tried all other methods too - taken two days and am annoyed why the headphone won't work!

Do I report the bug?

---

### Post by arturic on 2010-07-14
Hello! I have the same issue in my desktop, it's like the speaker output (green plug on the back) its "the same" than the headphone output (green plug on the front), I mean, the volume changes equally, and if one is muted, so the other, there is no way to "select" one.

I noticed that my MacBook Pro currently running Karmic, has a separate volume slider labeled HP for the headphones in Gnome Alsa mixer, which my desktop running Lucid has not. Just to make it clear, this post is about de desktop, not the laptop (I'll deal with that later).

I went and booted in WinXP to check about the drivers, and it turns out that the Realtek audio control didn't have a separate volume for headphones, however it switches between speakers and headphones automatically when plugin/unplugin the headphones, and even displays a notification right above the system tray clock. So I guess this is what it's to be expected in Ubuntu too or better yet, let me a choose manual/automatic output or ideally have a separate volume for headphones but I think this is a hardware limitation.

Oh and one more thing about WinXP, it says my audio card is an ALC885 while Ubuntu (Lucid) says it's an ALC889A

So I followed this thread's (and others') advices but the behavior is still the same, here is what i did:

I upgraded ALSA by adding this repository: **"deb http://security.ubuntu.com/ubuntu lucid-security main"** as told on [ THIS LINK]("http://packages.ubuntu.com/lucid/amd64/linux-backports-modules-alsa-lucid-generic/download"), because I saw [THIS COMMENT]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/587786") (see comment 21). Then using synaptic I installed the **linux-backports-modules-alsa-lucid-generic**, wich auto-selected the alsa-2.6.32-24-generic, and installed a new kernel (wich by the way made me had to uninstall/reinstall nvidia propietary drivers)

Then I edited /etc/modprobe.d/alsa-base.conf and added:
**options snd_hda_intel model=6stack-dig**, then changed it to:
**options snd-hda-intel model=6stack-dig** (dashes instead of underscores), and finally
**options snd-hda-intel model=auto**
Rebooted each time, off course, but all of these with the same results -> "linked" speakers and headphones output

In Sound Preferences If I select Analog Stereo Duplex profile, the Output tab shows a drop-down box for Connector, and the options are Analog Output and Analog Headphones, if I select headphones the output is muted and have to go to alsamixer to raise the front volume, and I have sound, but still linked speakers-headphones.

Also in alsamixer if I mute the headphones (or in Gnome Alsa mixer if I uncheck the -Headphone box) all is muted, but unmuting (or cheking back the box) does not bring sound back, I have to go unmute it on Sound Preferences or on the speaker icon in the system tray.

Now all the technical stuff:
Motherboard chipset: nvida nforce 680i (integrated audio), 6 plug + 1 optical on the back, 2 plugs (hp and mic) on the front

```
artfm@Jessica:~$ uname -a
Linux Jessica 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

artfm@Jessica:~$ lspci | grep Audio
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

artfm@Jessica:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).

artfm@Jessica:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

artfm@Jessica:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
```

And my Alsa Info form **lidex** script is [HERE]("http://www.alsa-project.org/db/?f=bb1fbf66b9353f3eda9e20ffc3f8e83ad6e54c03").

Sorry for this LONG post, is just I'd REALLY like to have my audio working properly
THANK YOU very much for your help !

---

### Post by lidex on 2010-07-14
Don't apologize for being thorough, *arturic*. It's quite helpful. I take it this is not a premade PC, and has an EVGA motherboard, correct?
It might be helpful to run the alsa-upgrade script linked in my sig. I'd like to see all these at v. 1.0.23:
```
Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22

```

---

### Post by EllyBilateralCI on 2010-07-15
> **lidex said:**
> Don't apologize for being thorough, *arturic*. It's quite helpful. I take it this is not a premade PC, and has an EVGA motherboard, correct?
It might be helpful to run the alsa-upgrade script linked in my sig. I'd like to see all these at v. 1.0.23:
```
Driver version:     1.0.23
Library version:    1.0.22
Utilities version:  1.0.22

```

Is this an extract from the alsa-base.sh script?

---

### Post by arturic on 2010-07-16
Thank you very much for your quick reply! :D

> **lidex said:**
> I take it this is not a premade PC, and has an EVGA motherboard, correct?

Yes, that's right, the motherboard is an EVGA model 122-CK-NF68-AR, and it's a PC I assembled myself in 2006 (I'm an enthusiast ;) )

> **EllyBilateralCI said:**
> Is this an extract from the alsa-base.sh script?

It's an extract from the file generated by the **Alsa Info Script (alsa-info.sh)** on **lidex** signature.

So I ran the ALSA Upgrade Script and everything went OK, now those 3 items show 1.0.23, Ooh by the way, this is my new [ALSA INFO]("http://www.alsa-project.org/db/?f=e9aeb6b1e9459ee261507d4bea9d5c16ea7a9634"). The sad news is that everything still exactly the same: speakers "linked" to headphones.

What is the expected behavior with ALSA? The headphones checkbox in Gnome Alsa mixer should turn on and off the headphones but not the speakers right? Also automatic switching when plugin/unplugin could be expected with current drivers/library?

Oh, and which one is correct in alsa-base.conf: snd_hda_intel model or  snd-hda-intel?

Thank you!  Cheers!

---

### Post by lidex on 2010-07-16
> **arturic said:**
> Thank you very much for your quick reply! :D



Yes, that's right, the motherboard is an EVGA model 122-CK-NF68-AR, and it's a PC I assembled myself in 2006 (I'm an enthusiast ;) )



It's an extract from the file generated by the **Alsa Info Script (alsa-info.sh)** on **lidex** signature.

So I ran the ALSA Upgrade Script and everything went OK, now those 3 items show 1.0.23, Ooh by the way, this is my new [ALSA INFO]("http://www.alsa-project.org/db/?f=e9aeb6b1e9459ee261507d4bea9d5c16ea7a9634"). The sad news is that everything still exactly the same: speakers "linked" to headphones.

What is the expected behavior with ALSA? The headphones checkbox in Gnome Alsa mixer should turn on and off the headphones but not the speakers right? Also automatic switching when plugin/unplugin could be expected with current drivers/library?

Oh, and which one is correct in alsa-base.conf: snd_hda_intel model or  snd-hda-intel?

Thank you!  Cheers!
To my knowledge it should be with dashes, not underscores. As this model (auto) doesn't seem to be working, I would remove it. You may want to try enabling msi:
```
options snd-hda-intel enable_msi=1
```

One other thing. When you did this:
> In Sound Preferences If I select Analog Stereo Duplex profile, the Output tab shows a drop-down box for Connector, and the options are Analog Output and Analog Headphones, if I select headphones the output is muted and have to go to alsamixer to raise the front volume, and I have sound, but still linked speakers-headphones.

did you try adjusting the PCM slider?

---

### Post by lidex on 2010-07-16
OK. From what  I found in the motherboard specs, this has 8-channel audio. The only model alsa lists that is specifically 8-channel for that codec is a targa, so it may be worth trying next.
```
options snd-hda-intel model=targa-8ch-dig
```

Full list:
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

```

---

### Post by arturic on 2010-07-16
OK, I tried the "**targa-8ch-dig**" mode and there was a little change, it added a "speakers" checkbox in Gnome Alsa mixer but unckecking it had the same effect of the headphones checkbox: it mutes all, and cheking it back doesn't unmute, have to unmute from Sound Preferences.

Also in Sound Preferences output tab it added an "**Analog Speakers**" to the Connector dropbox, but the behavior was the same, however using "**Analog Headphones**" when unchecking/checking "**speakers**" in Gnome Alsa mixer it muted/unmuted the **headphones** only... so it's kind of a "progress", but I find using the "**Analog Headphones**" connector useless, because every time I select it or reboot with it selected, the "**front**" slider is all the way down and muted, so I have to go raise it every reboot, and it's quite annoying. Also I noticed that using "**targa-8ch-dig**" removed most of the profiles in the Hardware tab in Sound preferences, using "**auto**" or "**6stack-dig**" I have a lot of profiles, including surround 4.0, 4.1 5.0, 5.1, 7.0 and 7.1, so I think "**targa-8ch-dig**" is not the right for me.

The "**enable_msi**" option with or without the "targa-8ch-dig" changed nothing.

> **lidex said:**
> did you try adjusting the PCM slider?

Yes I did, but the same thing, it adjusts both speakers and headphones.
And also I found a quirk: adjusting the volume from Sound Preferences or the speaker icon in the system tray, bumps the front volume and PCM all the way up in Gnome Alsa mixer and leaves you only "in sync" with the master slider, also as you slide slowly the volume in sound preferences you can see the PCM slider in (gnome) alsamixer moving between 98% - 100%, my guess is this is for "fine tunning" and make smaller volume steps...

Any ideas what to do next? Meanwhile I'll try some other modes. 
Thank you very much for your help **lidex**
Cheers!

---

### Post by Langsdorf on 2010-08-04
> **saiganeshb said:**
> 
download the .deb package from 
[http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip](http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip)
 
```

 sudo dpkg -i  alsa-driver-linuxant_1.0.23.0_all.deb 

```


headphone jack now works, thanks! ubuntu 10.04, lenovo g560

EDIT: damn, didn't realise, that the internal mic doesn't work anymore. a bug report was already issued: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2330194.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2330194.html)

EDIT2: after removing (sound doesn't work at all) and reinstalling now everything works, as it should.=D>

---

### Post by CarpKing on 2010-08-22
Upgraded ALSA and installed linuxant driver and now everything works!  Thanks everyone!

To help anyone googling for help, my codec is: Conexant CX20585 (Pebble 56-QFN)

My laptop is a Toshiba (I did add a "model=toshiba" in alsa.conf but it didn't fix the issue on its own; I'll have to test without that line to see if it did anything)

Ubuntu should see about adding this driver to the "Restricted Drivers" set (I couldn't find a license for the ALSA driver but the other drivers on that page are not open), so people don't have to install it manually.

---

### Post by CarpKing on 2010-08-27
Hmm...  The fix doesn't seem to be working after a kernel upgrade.  I guess I'll have to run the ALSA script again?

---

### Post by CarpKing on 2010-08-27
Had to re-upgrade ALSA and reinstall the linuxant driver, but now everything works again.  

I wonder what the chances are that I could restore the old ALSA and install the driver on that?  There might be version issues but it would mean less for me to do on each kernel upgrade.

---

### Post by CarpKing on 2010-08-31
Sorry to bump again, but I thought I should mention that, after another kernel upgrade, reinstalling the driver was all that was necessary to get things working right again.  No ALSA upgrade required.

---

### Post by zvqra1111 on 2010-09-03
For Lenovo G560:

gksudo gedit /etc/modprobe.d/alsa-base.conf

and add to the end:

options snd-hda-intel model=ideapad

With the ideapad-model the headphone jack should be working as expected.

Bye!;)

---

### Post by mr-pink on 2010-09-15
> **zvqra1111 said:**
> For Lenovo G560:

gksudo gedit /etc/modprobe.d/alsa-base.conf

and add to the end:

options snd-hda-intel model=ideapad

With the ideapad-model the headphone jack should be working as expected.

Bye!;)

Hi!

Have you tried this workaround on a G560? Is it really working? I'd like buying one but I wouldn't like having to reinstall the linuxant driver after a every kernel upgrade - it would be very annoying.

Bye

---

### Post by jaha777 on 2010-09-16
> **mr-pink said:**
> Hi!

Have you tried this workaround on a G560? Is it really working? I'd like buying one but I wouldn't like having to reinstall the linuxant driver after a every kernel upgrade - it would be very annoying.

Bye

I tried that and it works. I just edited that file then rebooted and now when I plug headphones there is no sound coming from the speakers .

---

### Post by mr-pink on 2010-09-16
> **jaha777 said:**
> I tried that and it works. I just edited that file then rebooted and now when I plug headphones there is no sound coming from the speakers .

What about the internal (and/or external) mic? Is it correctly working? I'm asking because some people are complaining about it.

---

### Post by ancientrustic on 2010-09-20
I fixed this problem a while ago but the last two or three kernel updates have borked it. The terminal messages refer to this log file but I cannot tell what to do to get the speakers muted again. Can anyone help?

rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
echo skipping rm -f alsa-kernel/include/version.h
skipping rm -f alsa-kernel/include/version.h
rm -fr .tmp_versions
rm -f Module.symvers
find include/sound -name "*.h" -type l | xargs rm -f
rm -fr include/generated
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
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

---

### Post by Yellow Pasque on 2010-09-20
> **ancientrustic said:**
> I fixed this problem a while ago but the last two or three kernel updates have borked it. The terminal messages refer to this log file but I cannot tell what to do to get the speakers muted again. Can anyone help?

If you used the alsa upgrade script, you probably need to run it (with -i) again

---

### Post by ancientrustic on 2010-09-21
Thanks for your quick response. This is what I get when I run this command.

"(Reading database ... 198398 files and directories currently installed.)
Preparing to replace alsa-driver-linuxant 1.0.23.0 (using alsa-driver-linuxant_1.0.23.0_all.deb) ...
make: [uninstall] Error 1 (ignored)
Unpacking replacement alsa-driver-linuxant ...
Setting up alsa-driver-linuxant (1.0.23.0) ...
Building modules for the 2.6.32-24-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3336.log
dpkg: error processing alsa-driver-linuxant (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 alsa-driver-linuxant
"
Which is what I had before.

---

### Post by MusicLover9898 on 2010-09-24
Thank you SOOO much! It works great now!:-D

I got VERY frustrated](*,)

---

### Post by thelocust on 2010-10-10
> **zvqra1111 said:**
> For Lenovo G560:

gksudo gedit /etc/modprobe.d/alsa-base.conf

and add to the end:

options snd-hda-intel model=ideapad

With the ideapad-model the headphone jack should be working as expected.

Bye!;)

This works on Leveno s10-t3 ideapad.

---

### Post by CarpKing on 2010-10-13
Anyone get Linuxant working on Maverick?  For me it fails on "building modules" with errors about "implicit declaration of function."

Most recently I've tried applying the patch version of Linuxant to the source downloaded by the ALSA-upgrade script, but it doesn't apply completely and I'm now well outside my knowledge base.

---

### Post by CarpKing on 2010-10-19
I managed to fix this without installing Linuxant.  I added ```
options snd-hda-intel model=ideapad
```
to /etc/modprobe.d/alsa-base.conf and installed updated ALSA modules as per [this page.](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I'm not sure which one fixed it, but now my audio works as expected.

---

### Post by Kopasakis on 2010-10-22
so i think i installed the wrong driver i installed the linuxtant driver but i didn't do the alsa upgrade (don't really know how) and now when i right click my web browser just freezes, when i close the lid on my laptop it won't go into standby mode, when i turn it off it wont turn off it says it is waiting on the modem. I've lost complete control of my sound... i can't open alsa at all and when i click on the speaker nothing happens it just says its muted, and when i try to open up my Hardware drivers i just get a box that says its looking for drivers 

i have a lenovo U350

my alsa-base.conf flie reads ```
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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
alias snd-card-l snd-Si3054
```

---

### Post by lidex on 2010-10-22
> **Kopasakis said:**
> so i think i installed the wrong driver i installed the linuxtant driver but i didn't do the alsa upgrade (don't really know how) and now when i right click my web browser just freezes, when i close the lid on my laptop it won't go into standby mode, when i turn it off it wont turn off it says it is waiting on the modem. I've lost complete control of my sound... i can't open alsa at all and when i click on the speaker nothing happens it just says its muted, and when i try to open up my Hardware drivers i just get a box that says its looking for drivers 

i have a lenovo U350

my alsa-base.conf flie reads ```
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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
alias snd-card-l snd-Si3054
```

This line in your alsa-base.conf is wrong:
```
alias snd-card-l snd-Si3054
```
Try changing that l to a 1 (digit). Reboot. No help, try removing all three lines and reboot.

---

### Post by Kopasakis on 2010-10-23
ok in an interesting turn of events i did an update and the whole thing reset, now i have sound and everything worked like before, unfortunately like before now i get sound through the speakers but when i plug in the headphones i get nothing out of the headphones and the sound keeps playing through the speakers i changed the code to ```
alias snd-card-1 snd-Si3054
``` but it continues as normal

---

### Post by lidex on 2010-10-23
> **Kopasakis said:**
> ok in an interesting turn of events i did an update and the whole thing reset, now i have sound and everything worked like before, unfortunately like before now i get sound through the speakers but when i plug in the headphones i get nothing out of the headphones and the sound keeps playing through the speakers i changed the code to ```
alias snd-card-1 snd-Si3054
``` but it continues as normal
How about a little more info please. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by dt_ on 2010-11-01
Can anyone please help me out? I have the exact problem written in the thread title and I've searched and searched and can't find a solution.
My speakers and headphones are both controlled by the same volume control; the computer doesn't detect when I plug in or unplug headphones (from the front headphone jack on my desktop), and therefore it just plays out of both speakers and headphones.
I tried updating those linux alsa drivers but it had no effect. Yes, I rebooted.

Any help would be muchly appreciated :)

Thanks,
dt

---

### Post by dt_ on 2010-11-01
Anyone? Please :( I don't want to have to use Windows because of this.

---

### Post by CarpKing on 2010-11-02
Post the output of:
```
cat /proc/asound/card0/codec#* | grep Codec

```

Did you try adding "options snd-hda-intel model=<something>" to /etc/modprobe.d/alsa-base.conf?  I think somewhere in this thread there's a link to a list of possibilities for the <something>, which are mostly laptop brands, but from reading this and other threads it seems that which one fixes the problem is unrelated to the actual brand of the laptop.

---

### Post by dt_ on 2010-11-02
Yeah, I tried adding that with model=ideapad at one point, but that had no effect.  Besides, my motherboard is designed for AMD chips and I'm running an AMD CPU... (though maybe that doesn't matter for this?)

The output of that command was:

```
Codec: Realtek ALC888
```

which I assume is the sound chipset builtin to my motherboard? :)

Are there known issues with that one?

Thanks,
dt

> **CarpKing said:**
> Post the output of:
```
cat /proc/asound/card0/codec#* | grep Codec

```

Did you try adding "options snd-hda-intel model=<something>" to /etc/modprobe.d/alsa-base.conf?  I think somewhere in this thread there's a link to a list of possibilities for the <something>, which are mostly laptop brands, but from reading this and other threads it seems that which one fixes the problem is unrelated to the actual brand of the laptop.

---

### Post by ravindra_jain12 on 2010-11-02
I assume you have already tried solution given in comment #52 on page 6 in this thread. I just searched for this problem happening in my new Thinkpad and the solution provided in that comment just worked fine. In my case, I set "Sound Preferences->Output->Connector" property to "Analog Output".

---

### Post by dt_ on 2010-11-02
> **ravindra_jain12 said:**
> I assume you have already tried solution given in comment #52 on page 6 in this thread. I just searched for this problem happening in my new Thinkpad and the solution provided in that comment just worked fine. In my case, I set "Sound Preferences->Output->Connector" property to "Analog Output".

Yep. It's currently on Analog Output and it plays out of both speakers and headphones. If I change it to "Analog Headphones," I get no sound out of either output. :/

---

### Post by lidex on 2010-11-02
> **dt_ said:**
> Yep. It's currently on Analog Output and it plays out of both speakers and headphones. If I change it to "Analog Headphones," I get no sound out of either output. :/
Could use a little more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by dt_ on 2010-11-03
> **lidex said:**
> Could use a little more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Whoa, that's a really good idea for support, if I may say so myself ;) The whole "auto-upload logfile" thing. good on them.

Anyway, here's the link:

[http://www.alsa-project.org/db/?f=a1261020e0e4a42bbc735cbf4763466947e0d965](http://www.alsa-project.org/db/?f=a1261020e0e4a42bbc735cbf4763466947e0d965)

---

### Post by lidex on 2010-11-03
> **dt_ said:**
> Whoa, that's a really good idea for support, if I may say so myself ;) The whole "auto-upload logfile" thing. good on them.

Anyway, here's the link:

[http://www.alsa-project.org/db/?f=a1261020e0e4a42bbc735cbf4763466947e0d965](http://www.alsa-project.org/db/?f=a1261020e0e4a42bbc735cbf4763466947e0d965)

Looks like your audio is defaulting to hdmi. I would imagine it is because you have this option added to alsa-base.conf:
```
options snd-hda-intel index=-2 model=6stack-dig

```
I would remove 'index=-2' so it resembles this:
```
options snd-hda-intel model=6stack-dig
```
Now reboot.

---

### Post by dt_ on 2010-11-03
Unfortunately, that had no effect. :(
Yeah, I had looked at Sound Preferences before and ensured that hdmi wasn't the selected output. When that's selected, no audio is heard (obviously, since I have nothing plugged into HDMI at the moment) :)

> **lidex said:**
> Looks like your audio is defaulting to hdmi. I would imagine it is because you have this option added to alsa-base.conf:
```
options snd-hda-intel index=-2 model=6stack-dig

```
I would remove 'index=-2' so it resembles this:
```
options snd-hda-intel model=6stack-dig
```
Now reboot.

---

### Post by dt_ on 2010-11-03
I tried updating my BIOS too, but that had no effect on sound.

I have no problems at all with sound on my Windows install, of course :rolleyes:

---

### Post by lidex on 2010-11-04
> **dt_ said:**
> I tried updating my BIOS too, but that had no effect on sound.

I have no problems at all with sound on my Windows install, of course :rolleyes:

In alsa-base.conf, change the model to auto. Now reload alsa:
```
sudo alsa force-reload

```
And post this output:
```
aplay -l
```

---

### Post by dt_ on 2010-11-04
Okay. aplay -l outputted the following:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Basically it looks like it's combining the headphone and speaker jacks into one analog output, and then there's the digital S/PDIF output.
Why is it combining the outputs :'(

> **lidex said:**
> In alsa-base.conf, change the model to auto. Now reload alsa:
```
sudo alsa force-reload

```
And post this output:
```
aplay -l
```

---

### Post by lidex on 2010-11-04
Well that did something. Your previous aplay -l output was:
```
APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
How is sound in this state?

---

### Post by dt_ on 2010-11-04
It's still the same -- it sounds just fine ,but it outputs from both the speakers and the headphones at the same time, and there's only one volume control for the both of them. :(

---

### Post by lidex on 2010-11-04
Your output shows a headphone 'switch':
```
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

```
but no headphone volume. I also note you have 6-channel mode selected. Try changing that to 8-channel. You may want to install gnome-alsamixer. Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by dt_ on 2010-11-05
All the options are checked in Sound Card Properties, and I don't see anywhere a place to switch between 6-channel and 8-channel.

For what it's worth, this is what my gnome-alsamixer looks like:

[IMG]http://imgur.com/3KChk.png[/IMG]

Thanks,
dt

> **lidex said:**
> Your output shows a headphone 'switch':
```
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]

```
but no headphone volume. I also note you have 6-channel mode selected. Try changing that to 8-channel. You may want to install gnome-alsamixer. Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by dt_ on 2010-11-06
Any other ideas? >_<

---

### Post by lidex on 2010-11-06
> **dt_ said:**
> Any other ideas? >_<

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
and file a bug report.
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by dt_ on 2010-11-06
OK, did that, and posted the bug here:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672003](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672003)

What're the odds someone will respond reasonably soon? >_<

Also, do you think it's worth trying to update the linux kernel?

Thanks for all your help, btw. :)

---

### Post by lidex on 2010-11-06
> **dt_ said:**
> OK, did that, and posted the bug here:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672003](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/672003)

What're the odds someone will respond reasonably soon? >_<

Also, do you think it's worth trying to update the linux kernel?

Thanks for all your help, btw. :)
You're already using latest stable alsa. Couldn't tell you how long on a response but the devs definitely need to see this. I am currently working four threads all with Gigabyte Mobos.

---

### Post by Kopasakis on 2010-11-20
[http://www.alsa-project.org/db/?f=a29a84e0bfdf2abf6a3af933ebe9aa00bf42ea37](http://www.alsa-project.org/db/?f=a29a84e0bfdf2abf6a3af933ebe9aa00bf42ea37)

sorry it took so long to get to you

---

### Post by vincentpistelli on 2010-11-20
Hello I have an Asus K501J, and I cannot figure out what to put for model.  Can anyone help?

---

### Post by lidex on 2010-11-20
> **Kopasakis said:**
> [http://www.alsa-project.org/db/?f=a29a84e0bfdf2abf6a3af933ebe9aa00bf42ea37](http://www.alsa-project.org/db/?f=a29a84e0bfdf2abf6a3af933ebe9aa00bf42ea37)

sorry it took so long to get to you

Try updating your alsa driver modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
If that's not enough, edit alsa-base.conf:
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop 
```
Save. Close. Reboot. 
Check your levels in alsamixer.

---

### Post by szamito on 2010-11-28
Hi Community,

I am also facing similar problems with my asus f5m running ubuntu 10.10, I have tried to configure "options  snd-hda-intel model=MODEL" based on thread [http://ubuntuforums.org/showpost.php?p=3796486&postcount=1](http://ubuntuforums.org/showpost.php?p=3796486&postcount=1)

But I haven't had any luck, my laptop is still giving sound through headphones and speakers... Muting in alsamixer the speakers results in no sound (sound is mute) and when setting connector "Analog Headphones" in output tab of Sound preference I don't get any sound.

Below is the information you are requesting. Thanks in advance.

The Alsa information script, [http://www.alsa-project.org/db/?f=0add8062fff09b4aff242221f52bd717fcc79c80](http://www.alsa-project.org/db/?f=0add8062fff09b4aff242221f52bd717fcc79c80)

Code:
$uname -a
Linux ricardo-F5M 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC660-VD

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054





Cheers!

---

### Post by lidex on 2010-11-28
> **szamito said:**
> Hi Community,

I am also facing similar problems with my asus f5m running ubuntu 10.10, I have tried to configure "options  snd-hda-intel model=MODEL" based on thread [http://ubuntuforums.org/showpost.php?p=3796486&postcount=1](http://ubuntuforums.org/showpost.php?p=3796486&postcount=1)

But I haven't had any luck, my laptop is still giving sound through headphones and speakers... Muting in alsamixer the speakers results in no sound (sound is mute) and when setting connector "Analog Headphones" in output tab of Sound preference I don't get any sound.


Did you try:
```
options snd-hda-intel model=auto
```
in alsa-base.conf?

---

### Post by szamito on 2010-12-16
> **lidex said:**
> Did you try:
```
options snd-hda-intel model=auto
```
in alsa-base.conf?

Yes, I did it many times. still not working :(

---

### Post by lidex on 2010-12-16
> **szamito said:**
> Yes, I did it many times. still not working :(

Try this one:
```
options snd-hda-intel model=asus-v1s
```

---

### Post by a_flj_ on 2010-12-17
Got a similar problem, with an asus K70AB laptop. Google didn't provide any relevant results for my specific laptop model.

When I tried updating the alsa driver from outside the canonical repos, I got an unusable audio setup - there was a constant beep in the speakers, mutable only by inserting the headphone jack, and pulse was completely damaged. I had to do a fresh install, apt-get purge/install for pulse or any package containing alsa in its name didn't help.

I tried the following models in alsa-base.conf: laptop, asus and asus-laptop. All three have the same effect - i.e. none.

The way alsamixer and pavucontrol play together is weird, so I'll explain it:

Alsamixer shows the following controls for output: front, headphones and master front.

Pavucontrol shows the following output devices: RV7/something (HDMI) and Internal Audio Analog Stereo, for which I have two ports: Analog Output and Analog Headphones. 

Now comes the strange part. Initially, the output port is set to Analog Output in pavucontrol. Speakers and headphones play simultaneously. When I switch to Analog Headphones, both speakers and headphones are muted. If I look into alsamixer, which I haven't touched since reboot, the volume for front is set to zero, whereas it was set to 100 before changing the port in pulse's volume control - must be pavucontrol's doing. If I turn up the volume for front - not for headphones - in alsamixer, I get to listen to music in the headphones, and the speakers stay muted. Changing the volume for headphones in alsamixer seems to have no effect at all.

All that time, all unmentioned volume controls both in alsamixer and in pavucontrol stay untouched.

With a combined use of alsamixer and pavucontrol I can have sound in the headphones only. What I haven't managed is to get sound only to the speakers, and not to the headphones, but that's not that much of a problem.

I have no clue of implementation details of either alsa or pulse, but this behavior, IMO, hints to some streams being mixed up by the two. Can any alsa + pulse guru help me out with this?

On the other hand, is there a way to have some script executed on inserting/extracting the headphone jack to automatically do what I now must do now to switch between headphones/speakers? I guess I'd be able to script the thing myself, but have no clue about how to call it event-driven.

On a hypothetical third hand, I suppose the issue is potentially related to my laptop model not being yet properly supported by alsa, in which case I'm not really able to help with code, but I'm willing to do whatever experiments the alsa developers might need me to perform.

---

### Post by a_flj_ on 2010-12-17
sort of solved all by itself after adding ```
options snd-hda-intel model=auto
options enable_msi=1
``` to /etc/modprobe/alsa-base.conf, and creating an /etc/asound.conf with the following content:```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```
Still, sometimes it seems like going mad, but even then, playing a bit with the ports in pavucontrol and the mute/unmute options in alsamixer it seems it gets right after a while.

I'm still available for debugging if somebody wants my help. I still think there's some messup in the way pulse and alsa talk to each other.

---

### Post by OttoMann on 2010-12-29
> **lidex said:**
> Did you try:
```
options snd-hda-intel model=auto
```in alsa-base.conf?

Thank you lidex!!! :p:)

Adding auto for model solved my problems after nothing else seemed to work on my MSI Megabook 271.

But I have an off topic question:

After messing around with different setup I noticed a red light shining out of my phones jack. 
What is it (maybe an combined jack for digital audio or just an error signal)?

---

### Post by lidex on 2010-12-29
> **OttoMann said:**
> Thank you lidex!!! :p:)

Adding auto for model solved my problems after nothing else seemed to work on my MSI Megabook 271.

But I have an off topic question:

After messing around with different setup I noticed a red light shining out of my phones jack. 
What is it (maybe an combined jack for digital audio or just an error signal)?
I'd say it's a combo jack.

---

### Post by boofly on 2011-01-27
I could not get my sound working properly using the above instructions. However, installing linux-backports-modules-alsa-maverick-generic fixed this for me! Using 10.10 maverick.

---

### Post by CupOfJoe on 2011-02-20
> **lidex said:**
> Try updating your alsa driver modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
If that's not enough, edit alsa-base.conf:
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop 
```
Save. Close. Reboot. 
Check your levels in alsamixer.

This worked perfectly for my Lenovo G560! Appreciate the help, cheers!:D

---

### Post by shaneswick on 2012-01-25
This will fix your problem..Realtek audio manager -> double click bottom analog button -> uncheck line out and check headphone....walla

---

### Post by Betonius on 2012-03-18
[SIZE=3]Hello Comunity.

I'm new in Ubuntu, installed Natty 11.04 in a Lenovo e520. After i installed the system i´m facing a series of problems. I would like to correct this issue with the headphohes and regular sound playing at the same time.[/SIZE]

[SIZE=3]Quoting saiganeshb tread 38[/SIZE]:
"SOLVED!
After 9 painful days of searching and installing needless stuff ...it's  funny when you overlook the obvious(googling for the necessary audio  driver) from the simple(googling  endless forums to add a line in the  alsa configuration file). For all conexant audio chip problems ,I guess  here is the solution :

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

download the .deb package from 
[http://www.linuxant.com/alsa-driver/....0_all.deb.zip]("http://www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.23.0/alsa-driver-linuxant_1.0.23.0_all.deb.zip")

unzip it
     Code:
     unzip alsa-driver-linuxant_1.0.23.0_all.deb.zip 
run it ! (enter password when prompted) 
     Code:
      sudo dpkg -i  alsa-driver-linuxant_1.0.23.0_all.deb 
Everything works perfectly on my laptop now. :KS
If you have a similar problem of not finding the correct option to put  in that alsa conf file, i suggest you google for the appropriate linux  drivers first."

[SIZE=3]I'm not sure if my codecs are good for this alsa driver. Then i haven't try yet.

With gksudo gedit /etc/modprobe.d/alsa-base.conf
[/SIZE][SIZE=3]
[/SIZE] options snd-hda-intel model=[I]laptop, thinkpad, lenovo, auto...
[/I] 
[SIZE=3]didn't get results.

This are my audio info:

uname -a
Linux alberto-laptop 2.6.35-32-generic #66-Ubuntu SMP Mon Feb 13 21:04:32 UTC 2012 x86_64 GNU/Linux
alberto@alberto-laptop:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: PCH [HDA Intel PCH], dispositivo 0: HDA Generic [HDA Generic]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: PCH [HDA Intel PCH], dispositivo 8: INTEL HDMI 2 [INTEL HDMI 2]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
alberto@alberto-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
alberto@alberto-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 506e

==> /proc/asound/card0/codec#3 <==
Codec: Intel CougarPoint HDMI


If anyone can help me.... i would appreciate it.
Thanks
[/SIZE]

---

### Post by tomas4578 on 2012-04-16
> **lidex said:**
> Try updating your alsa driver modules:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
If that's not enough, edit alsa-base.conf:
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=laptop 
```Save. Close. Reboot. 
Check your levels in alsamixer.

hello i have a problem with package...

```
~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Na&#269;ítavajú sa zoznamy balíkov... Hotovo
Vytvára sa strom závislostí             
Na&#269;ítavajú sa stavové informácie... Hotovo
E: Nedá sa nájs&#357; balík linux-alsa-driver-modules-2.6.32-40-generic
E: Nebol nájdený žiaden balík zodpovedajúci regulárnemu výrazu „linux-alsa-driver-modules-2.6.32-40-generic“
```

it cant find this package pls help

```
http://www.alsa-project.org/db/?f=c7c2d25224eae396f7def99e88cecf03ff169bab
```

---

