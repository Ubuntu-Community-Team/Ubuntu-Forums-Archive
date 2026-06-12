---
title: "Weird alsactl init error"
date: 2010-02-13
forum: Multimedia Software
---

### Post by ShiftyEyes on 2010-02-13
I recently switched from Debian (lenny) to Ubuntu 9.10 Server on a computer that I use as a sound/music server. I installed ALSA but have run into trouble getting it set-up. In the past I just ran 'alsa-conf' and everything worked great, but alsa-conf isn't used anymore. I think I'm supposed to use 'alsactl init' instead, but I get an error:

```
$> sudo alsactl init
alsactl: parse:1639: Unable to open file '/usr/share/alsa/init/ca0106': No such file or directory

```The only problems I found that were similar to this one involved pulseaudio, but I don't have pulse installed on my system.

There's intel sound built into the motherboard, and then there's also a SoundBlaster Live! 24 bit card. I would rather use the Soundblaster card, but I'd be happy if I could get either working.

alsa-mixer c1 shows the motherboard intel card, alsa-mixer shows the CA0106 (volume raised on both). I'm not sure what information is relevant, so I'll just give the output of all the commands I know to try.

```
$> ls /usr/share/alsa/init
00main  default  hda  help  info  test
``````
$> aplay -l
**** List of PLAYBACK Hardware Devices ****
    card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 1: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
``````
$>  cat /proc/asound/cards
    0 [CA0106         ]: CA0106 - CA0106
                         Live! 7.1 24bit [SB0410] at 0xece0 irq 9
    1 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                         Intel 82801BA-ICH2 with AD1885 at irq 10
``````
$> ls /usr/share/alsa/cards
AACI.conf          AU8810.conf    Aureon71.conf       CMI8788.conf   ES1968.conf     ICH4.conf        PMac.conf        SI7018             VIA8233.conf
aliases.alisp      AU8820.conf    CA0106.conf         CS46xx.conf    FM801.conf      ICH.conf         PMacToonie.conf  SI7018.conf        VIA8237.conf
aliases.conf       AU8830.conf    CMI8338.conf        EMU10K1.conf   GUS.conf        ICH-MODEM.conf   PS3.conf         TRID4DWAVENX.conf  VX222.conf
ATIIXP.conf        Audigy2.conf   CMI8338-SWIEC.conf  EMU10K1X.conf  HDA-Intel.conf  Maestro3.conf    RME9636.conf     USB-Audio.conf     VXPocket440.conf
ATIIXP-MODEM.conf  Audigy.conf    CMI8738-MC6.conf    ENS1370.conf   ICE1712.conf    NFORCE.conf      RME9652.conf     VIA686A.conf       VXPocket.conf
ATIIXP-SPDMA.conf  Aureon51.conf  CMI8738-MC8.conf    ENS1371.conf   ICE1724.conf    PC-Speaker.conf  SB-XFi.conf      VIA8233A.conf      YMF744.conf
``` I'm a bit of a noob and I'm thoroughly stumped. Any help would be awesome!

---

