---
title: "Headphones work-no internal speaker sound?"
date: 2010-04-30
forum: Multimedia Software
---

### Post by TBABill on 2010-04-30
My sound card works well because I have audio from the headphone jack, and adjustment with volume control works fine, but no sound at all from internal speakers. Any suggestions?

I am running 10.04 and all updates are applied. I also have duplicated this problem on Mint 8, Karmic, PCLinuxOS and OpenSUSE so it is not distro-unique. As stated, sound card configuration is fine with headphones so it is an output/config issue from what I can tell.

Output of aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci output

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9bf8000 irq 21


I continue to search the forums and do web searches hoping for specific guidance to get the speakers going. Any assistance is appreciated! I do realize the HDA Intel is a major pain for users so I am trying to find problems specific to my card or exact issue :)

---

### Post by Elmer Fudd on 2010-04-30
Had same problem.
Here is what worked for me.

Go to system menu
-Select "Sound"
In "Sound preferences" dialog
-select "Output" tab
Go to "Connector:" pop up list.
Change to "Analog Speaker"

This is also the only hiccup that I had in my upgrade.

---

### Post by TBABill on 2010-04-30
I had tried that previously. My only options are "analog output" and "analog headphones". Somehow I need speakers to be enabled in my configuration.

---

### Post by Elmer Fudd on 2010-04-30
The Intel 82801H seems to have had a lot of issues with linux over the last few years- Including:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2240239.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2240239.html)

Is this a 32 or 64 bit install?
Have the speakers ever worked- previous distro, windows?
Any settings in the BIOS re Speakers.
Any key combos that toggle the speakers.

Until someone with real knowledge responds, these are the straws I would be grabbing at:
Reload all the audio components with the package manager (Pulseaudio and ALSA) then check the Sound Preferences "Output" tab for speaker choice. Play with the choices in the "Hardware" tab of the Sound Preferences dialog and recheck the available choices in the "Output" tab.

Please don't be frustrated with my obvious nu-b status. Just trying to throw some stuff out there- until someone who actually knows something contributes.

---

### Post by TBABill on 2010-04-30
This is a system that worked perfectly in Vista with speakers. It's never worked with the other distros of Linux I listed. However, it's a wireless keyboard with volume control that works well with headphones. Sound is perfectly clear and volume can be muted, increased and decreased normally. But when the headphones are not plugged in the internal speakers do not operate at all. It's a known issue with the Intel HDA configuration but I have not found a solution that fits my machine. 

One example of the problem is any mixer installed does not have a speaker option listed, even with alsamixer via terminal. I have many others, such as headphones, mic, etc., but none for the speaker volume, as if the system does not even recognize them as available. I'm still digging through previous forum posts and looking for ideas. Thanks for the help offering. This driver seems to have caused a lot of problems for many users. Perhaps just getting a set of speakers to plug into the headphone jack would be the easiest and most immediate "fix", although that's just a workaround to a real problem.

---

### Post by lidex on 2010-04-30
Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by TBABill on 2010-04-30
uname -a

Linux bill-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*

Codec: Analog Devices AD1984B

This machine is a HP TouchSmart IQ804t with a Core 2 Duo, nVidia driver, 4GB RAM, 1TB HD, Intel sound, 25 inch HD monitor

---

### Post by lidex on 2010-04-30
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1
  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by TBABill on 2010-04-30
still no sound from speakers. I am in alsamixer and I have no speaker option. In sound configuration my output choices are still analog output and analog headphones. No speaker option.

Other things I can try? I did select the card using F6 in alsamixer.

Alsamixer also shows version 1.0.22 in case that's important. I did adjust different levels up into the red zones of each to see if I gained sound through the speakers, but nothing yet. I do have a visible option in alsamixer of "front" but it is at 00 and has no bar/graph above it and you cannot adjust it up or down.

---

### Post by TBABill on 2010-04-30
Here is a line from blacklist.conf within /etc/modprobe.d and I'm not sure why it is blacklisted:

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

Here is my /etc/modprobe.d as a result of the changes you recommended:

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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

---

### Post by TBABill on 2010-05-01
Last response was 20 hours ago. Anyone have any thoughts on steps I can take to try to enable the speaker on my machine based upon the above steps taken?

---

### Post by lidex on 2010-05-01
Comment out the second to last line and reboot:
```
# options snd-cmipci mpu_port=0x330 fm_port=0x388
```

---

### Post by TBABill on 2010-05-01
No joy with that one either. Could this be one that can't be fixed?

---

### Post by lidex on 2010-05-01
Alright, remove those previous options from alsa-base.conf.
How many analog audio jacks are there and is there a digital (spdif) out?

Another to try:
```
options snd-hda-intel model=hp enable_msi=1 
```
This one also (only one at a time please):
```
options snd-hda-intel model=mbp3

```

---

### Post by TBABill on 2010-05-02
I have 1 audio out headphone jack, 1 audio out jack (probably the same thing as the headphone jack - at least in appearance) and 1 SPDIF jack. 

I will try the options you just listed 1 at a time in place of the previous suggestions and I will report back. Thanks for all the help so far.

---

### Post by TBABill on 2010-05-02
Neither of those did the trick either. Is there a list of options like those somewhere I can just keep trying? I checked alsamixer again and my "front" has no "slider" to adjust and in system>preferences>sound I still have no speaker option (only analog output and analog headphones). 

Thanks again. I'm still searching for a database or some sort of list of options I can try. My model of HP (IQ804t) in a search didn't provide any results.

---

### Post by lidex on 2010-05-02
Try these (singly):
```
options snd-hda-intel model=3stack-dig 
options snd-hda-intel model=laptop-dig
options snd-hda-intel model=basic
options snd-hda-intel model=touchsmart
```
Also if you haven't installed alsa-backports, it's worth a shot:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

---

### Post by TBABill on 2010-05-02
Lidex you are awesome! The key to fixing the problem was the last one for the touchsmart (options snd-hda-intel model=touchsmart)

I will marked this solved but I want to put all the info in here in case someone searches the forum for a similar problem on a HP TouchSmart with HDA issues. My machine is a model IQ804t and the fix was to disable the last line of alsa-base.conf and add:

options snd-hda-intel model=touchsmart

Now my PC Speakers work AND my headphones work! Thank you for taking so much time to help me solve this issue. Best regards!

---

### Post by lidex on 2010-05-02
Wow. I didn't even think it would be that easy. [-o<

---

### Post by YesImaLinuxWanabee on 2010-05-08
I would like to just post here that I was having the same issue, but I have an Asus G1Sn laptop. Sound would only come out of the headphone jack. The fix for me was this:

In the **/etc/modprobe.d/alsa-base.conf** file
comment out (put a # in front of) or remove ```
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

and add ```
options snd-hda-intel model=3stack-dig
```

I would like to thank lidex and TBABill for finding this out.
Now I wonder if there is a specific place this should be posted as well?

---

### Post by Niej on 2010-05-09
Hi, I was experiencing the same problem on a Sony Vaio VPCF11 with intel sound card.
I was able to fix it by adding the following at /etc/modprobe.d/alsa-base.conf
```

options snd-hda-intel model=laptop-dig

```

Very Nice!
I want to thank you all for such a helpful post!!
Sebastian

---

### Post by Jaimix3 on 2010-05-15
Hey, 

I know this has already been solved, but I have been trying to fix my internal speakers for the longest and want to know if anyone can help. Headphones only work, and I've read through these posts and don't understand anything (I'm not so advanced with laptops or computers -.-). I have warranty on this laptop and called for assistance (thinking it's hardware problems), but no one has replied back on that. So,after waiting a while now I'm getting frustrated and just want to fix this on my own. I've tried reinstalling drivers, system restoring to factory settings, and many other things, which haven't worked. I have a Sony Vaio VPCEB15FM and my operating system is Windows 7. If anyone can please help me !! I would really appreciate it.

---

### Post by lidex on 2010-05-16
*Jaimix3*,
You'll need to upgrade alsa to latest version. Use the upgrade link in my sig.

---

### Post by prat0318 on 2012-03-16
Finally, my internal speakers started singing too :) :)

Thanks Lidex for the hint. For my Dell Vostro laptop this worked :

> options snd-hda-intel model=generic

---

### Post by Ni-el on 2012-05-06
This list and your "options snd-hda-intel model=  ", is what worked on Sony VGC-JS90S:

  Model name    Description
  ----------    -----------
ALC880
======
  3stack    3-jack in back and a headphone out
  3stack-digout    3-jack in back, a HP out and a SPDIF out
  5stack    5-jack in back, 2-jack in front
  5stack-digout    5-jack in back, 2-jack in front, a SPDIF out
  6stack    6-jack in back, 2-jack in front
  6stack-digout    6-jack with a SPDIF out
  w810        3-jack
  z71v        3-jack (HP shared SPDIF)
  asus        3-jack (ASUS Mobo)
  asus-w1v    ASUS W1V
  asus-dig    ASUS with SPDIF out
  asus-dig2    ASUS with SPDIF out (using GPIO2)
  uniwill    3-jack
  fujitsu    Fujitsu Laptops (Pi1536)
  F1734        2-jack
  lg        LG laptop (m1 express dual)
  lg-lw        LG LW20/LW25 laptop
  tcl        TCL S700
  clevo        Clevo laptops (m520G, m665n)
  medion    Medion Rim 2150
  test        for testing/debugging purpose, almost all controls can be
        adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y
  auto        auto-config reading BIOS (default)

ALC260
======
  fujitsu    Fujitsu S7020
  acer        Acer TravelMate
  will        Will laptops (PB V7900)
  replacer    Replacer 672V
  favorit100    Maxdata Favorit 100XS
  basic        fixed pin assignment (old default model)
  test        for testing/debugging purpose, almost all controls can
        adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y
  auto        auto-config reading BIOS (default)

ALC262
======
  N/A

ALC267/268
==========
  N/A

ALC269
======
  laptop-amic    Laptops with analog-mic input
  laptop-dmic    Laptops with digital-mic input

ALC662/663/665/272
==============
  asus-mode1    ASUS
  asus-mode2    ASUS
  asus-mode3    ASUS
  asus-mode4    ASUS
  asus-mode5    ASUS
  asus-mode6    ASUS
  asus-mode7    ASUS
  asus-mode8    ASUS

ALC680
======
  N/A

ALC882/883/885/888/889
======================
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack digital with SPDIF I/O
  arima        Arima W820Di1
  targa        Targa T8, MSI-1049 T8
  asus-a7j    ASUS A7J
  asus-a7m    ASUS A7M
  macpro    MacPro support
  mb5        Macbook 5,1
  macmini3    Macmini 3,1
  mba21        Macbook Air 2,1
  mbp3        Macbook Pro rev3
  imac24    iMac 24'' with jack detection
  imac91    iMac 9,1
  w2jc        ASUS W2JC
  3stack-2ch-dig    3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig    6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer        Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire    Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion    Medion Laptops
  targa-dig    Targa/MSI
  targa-2ch-dig    Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e    Lenovo 101E
  lenovo-nb0763    Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky    Lenovo Sky
  haier-w66    Haier W66
  3stack-hp    HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell    Dell machines with 6stack (Inspiron 530)
  mitac        Mitac 8252D
  clevo-m540r    Clevo M540R (6ch + digital)
  clevo-m720    Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a    Intel IbexPeak with ALC889A
  intel-x58    Intel DX58 with ALC889
  asus-p5q    ASUS P5Q-EM boards
  mb31        MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto        auto-config reading BIOS (default)

ALC861/660
==========
  N/A

ALC861VD/660VD
==============
  N/A

CMI9880
=======
  minimal    3-jack in back
  min_fp    3-jack in back, 2-jack in front
  full        6-jack in back, 2-jack in front
  full_dig    6-jack in back, 2-jack in front, SPDIF I/O
  allout    5-jack in back, 2-jack in front, SPDIF out
  auto        auto-config reading BIOS (default)

AD1882 / AD1882A
================
  3stack    3-stack mode (default)
  6stack    6-stack mode

AD1884A / AD1883 / AD1984A / AD1984B
====================================
  desktop    3-stack desktop (default)
  laptop    laptop with HP jack sensing
  mobile    mobile devices with HP jack sensing
  thinkpad    Lenovo Thinkpad X300
  touchsmart    HP Touchsmart

AD1884
======
  N/A

AD1981
======
  basic        3-jack (default)
  hp        HP nx6320
  thinkpad    Lenovo Thinkpad T60/X60/Z60
  toshiba    Toshiba U205

AD1983
======
  N/A

AD1984
======
  basic        default configuration
  thinkpad    Lenovo Thinkpad T61/X61
  dell_desktop    Dell T3400

AD1986A
=======
  6stack    6-jack, separate surrounds (default)
  3stack    3-stack, shared surrounds
  laptop    2-channel only (FSC V2060, Samsung M50)
  laptop-eapd    2-channel with EAPD (ASUS A6J)
  laptop-automute 2-channel with EAPD and HP-automute (Lenovo N100)
  ultra        2-channel with EAPD (Samsung Ultra tablet PC)
  samsung    2-channel with EAPD (Samsung R65)
  samsung-p50    2-channel with HP-automute (Samsung P50)

AD1988/AD1988B/AD1989A/AD1989B
==============================
  6stack    6-jack
  6stack-dig    ditto with SPDIF
  3stack    3-jack
  3stack-dig    ditto with SPDIF
  laptop    3-jack with hp-jack automute
  laptop-dig    ditto with SPDIF
  auto        auto-config reading BIOS (default)

Conexant 5045  Venice/CX20549
=============
  laptop-hpsense    Laptop with HP sense (old model laptop)
  laptop-micsense   Laptop with Mic sense (old model fujitsu)
  laptop-hpmicsense Laptop with HP and Mic senses
  benq        Benq R55E
  laptop-hp530    HP 530 laptop
  test        for testing/debugging purpose, almost all controls
        can be adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y

Conexant 5047  Waikiki/CX20551
=============
  laptop    Basic Laptop config 
  laptop-hp    Laptop config for some HP models (subdevice 30A5)
  laptop-eapd    Laptop config with EAPD support
  test        for testing/debugging purpose, almost all controls
        can be adjusted.  Appearing only when compiled with
        $CONFIG_SND_DEBUG=y

Conexant 5051  Hermosa/CX20561
=============
  laptop    Basic Laptop config (default)
  hp        HP Spartan laptop
  hp-dv6736    HP dv6736
  hp-f700    HP Compaq Presario F700
  ideapad    Lenovo IdeaPad laptop
  lenovo-x200    Lenovo X200 laptop
  toshiba    Toshiba Satellite M300

Conexant 5066  Pebble/CX20582 
=============
  laptop    Basic Laptop config (default)
  hp-laptop    HP laptops, e g G60
  asus        Asus K52JU, Lenovo G560
  dell-laptop    Dell laptops
  dell-vostro    Dell Vostro
  olpc-xo-1_5    OLPC XO 1.5
  ideapad       Lenovo IdeaPad U150
  thinkpad    Lenovo Thinkpad

STAC9200
========
  ref        Reference board
  oqo        OQO Model 2
  dell-d21    Dell (unknown)
  dell-d22    Dell (unknown)
  dell-d23    Dell (unknown)
  dell-m21    Dell Inspiron 630m, Dell Inspiron 640m
  dell-m22    Dell Latitude D620, Dell Latitude D820
  dell-m23    Dell XPS M1710, Dell Precision M90
  dell-m24    Dell Latitude 120L
  dell-m25    Dell Inspiron E1505n
  dell-m26    Dell Inspiron 1501
  dell-m27    Dell Inspiron E1705/9400
  gateway-m4    Gateway laptops with EAPD control
  gateway-m4-2    Gateway laptops with EAPD control
  panasonic    Panasonic CF-74
  auto        BIOS setup (default)

STAC9205/9254
=============
  ref        Reference board
  dell-m42    Dell (unknown)
  dell-m43    Dell Precision
  dell-m44    Dell Inspiron
  eapd        Keep EAPD on (e.g. Gateway T1616)
  auto        BIOS setup (default)

STAC9220/9221
=============
  ref        Reference board
  3stack    D945 3stack
  5stack    D945 5stack + SPDIF
  intel-mac-v1    Intel Mac Type 1
  intel-mac-v2    Intel Mac Type 2
  intel-mac-v3    Intel Mac Type 3
  intel-mac-v4    Intel Mac Type 4
  intel-mac-v5    Intel Mac Type 5
  intel-mac-auto Intel Mac (detect type according to subsystem id)
  macmini    Intel Mac Mini (equivalent with type 3)
  macbook    Intel Mac Book (eq. type 5)
  macbook-pro-v1 Intel Mac Book Pro 1st generation (eq. type 3)
  macbook-pro    Intel Mac Book Pro 2nd generation (eq. type 3)
  imac-intel    Intel iMac (eq. type 2)
  imac-intel-20    Intel iMac (newer version) (eq. type 3)
  ecs202    ECS/PC chips
  dell-d81    Dell (unknown)
  dell-d82    Dell (unknown)
  dell-m81    Dell (unknown)
  dell-m82    Dell XPS M1210
  auto        BIOS setup (default)

STAC9202/9250/9251
==================
  ref        Reference board, base config
  m1        Some Gateway MX series laptops (NX560XL)
  m1-2        Some Gateway MX series laptops (MX6453)
  m2        Some Gateway MX series laptops (M255)
  m2-2        Some Gateway MX series laptops
  m3        Some Gateway MX series laptops
  m5        Some Gateway MX series laptops (MP6954)
  m6        Some Gateway NX series laptops
  auto        BIOS setup (default)

STAC9227/9228/9229/927x
=======================
  ref        Reference board
  ref-no-jd    Reference board without HP/Mic jack detection
  3stack    D965 3stack
  5stack    D965 5stack + SPDIF
  5stack-no-fp    D965 5stack without front panel
  dell-3stack    Dell Dimension E520
  dell-bios    Fixes with Dell BIOS setup
  volknob    Fixes with volume-knob widget 0x24
  auto        BIOS setup (default)

STAC92HD71B*
============
  ref        Reference board
  dell-m4-1    Dell desktops
  dell-m4-2    Dell desktops
  dell-m4-3    Dell desktops
  hp-m4        HP mini 1000
  hp-dv5    HP dv series
  hp-hdx    HP HDX series
  hp-dv4-1222nr    HP dv4-1222nr (with LED support)
  auto        BIOS setup (default)

STAC92HD73*
===========
  ref        Reference board
  no-jd        BIOS setup but without jack-detection
  intel        Intel DG45* mobos
  dell-m6-amic    Dell desktops/laptops with analog mics
  dell-m6-dmic    Dell desktops/laptops with digital mics
  dell-m6    Dell desktops/laptops with both type of mics
  dell-eq    Dell desktops/laptops
  alienware    Alienware M17x
  auto        BIOS setup (default)

STAC92HD83*
===========
  ref        Reference board
  mic-ref    Reference board with power management for ports
  dell-s14    Dell laptop
  dell-vostro-3500    Dell Vostro 3500 laptop
  hp-dv7-4000    HP dv-7 4000
  auto        BIOS setup (default)

STAC9872
========
  vaio        VAIO laptop without SPDIF
  auto        BIOS setup (default)

Cirrus Logic CS4206/4207
========================
  mbp55        MacBook Pro 5,5
  imac27    IMac 27 Inch
  auto        BIOS setup (default)

VIA VT17xx/VT18xx/VT20xx
========================
  auto        BIOS setup (default)

---

### Post by parminides on 2012-05-26
I run Ubuntu 12.04 on an HP TouchSmart. For a long time I couldn't get sound out of the internal speakers, although the headphones (either usb or in the headphone jack) worked.

I came across this thread this morning and quickly added the magic line

> 
options snd-hda-intel model=touchsmart


to the end of /etc/modprobe.d/alsa-base.conf.

After reboot, I get sound out of the internal speakers for the first time ever in Ubuntu, and the usb headphones still work, but now there's no sound out of the headphone jack.

Does anyone know how I can get all three outputs to work? I apologize if it's considered bad manners to post questions to threads marked solved.

---

### Post by mrmolo on 2012-12-07
> **YesImaLinuxWanabee said:**
> I would like to just post here that I was having the same issue, but I have an Asus G1Sn laptop. Sound would only come out of the headphone jack. The fix for me was this:

In the **/etc/modprobe.d/alsa-base.conf** file
comment out (put a # in front of) or remove ```
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

and add ```
options snd-hda-intel model=3stack-dig
```

I would like to thank lidex and TBABill for finding this out.
Now I wonder if there is a specific place this should be posted as well?

works like a charm for me too, thanks a lot guys !
(asus G1S with G1Sn motherboard)

---

