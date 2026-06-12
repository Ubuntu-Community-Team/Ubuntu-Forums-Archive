---
title: "TV Card Help"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by denham2010 on 2007-04-17
Hi,

After much searching on several forums and the Linux TV Wiki, I have had no success in getting my TV Card to work on Ubuntu. I am also getting conflicting answers from different sources on whether my TV card is actually supported on Linux.

So I am wondering, has anyone been able to get this TV card working on Linux (preferrably Ubuntu), and if so, any assistance in getting my card to work is greatly appreciated.

My TV Card is an Aver Media Hybrid+FM PCI (A16R) - I'm not certain about the A16R part......

It is a Digital / Analogue TV + FM Radio card.

The output of "lspci" (if this helps) is:

01:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Being a fairly recent convert to Linux from the dreaded MS Curtains (after several false starts and many CD's being destroyed) I am only 2 steps away from deleting my Windows partition for good....that is, getting my TV Card to work, and getting album art on my iPod with Amarok (but that's another story).

All help is greatly appreciated.

---

### Post by denham2010 on 2007-04-17
** Bump **

---

### Post by denham2010 on 2007-04-18
Has anyone had experience with this card?

---

### Post by denham2010 on 2007-04-18
Anyone at all? I really need help with this please.

---

### Post by Gina on 2007-04-18
I have the same TV card chipset though mine's a USB device.  I have had no success in getting it to work having tried several TV apps.  One or two recognise it but not find any channels - others don't even see it.  I found  info (somewhere) that said this chipset was supported by the latest kernel versions.  I'm currently running Dapper (v6.06) but intending to update to Feisty (v7.04) shortly.  I'm hoping I may have more joy with the latest OS version.

If I get any more info or get it working I'll post another reply.

---

### Post by crispy_420 on 2007-04-19
[http://www.linuxtv.org/v4lwiki/index.php/Kworld_NB-TV_100_(VS-NBTV100)_CardBus](http://www.linuxtv.org/v4lwiki/index.php/Kworld_NB-TV_100_(VS-NBTV100)_CardBus)

[http://www.linuxtv.org/v4lwiki/index.php/AVerMedia_AverTV_Hybrid_FM_PCI_A16D](http://www.linuxtv.org/v4lwiki/index.php/AVerMedia_AverTV_Hybrid_FM_PCI_A16D)

Should be a start for you.

---

### Post by denham2010 on 2007-04-19
Thanks Gina and Crispy.

At work at the moment, so will have to wait until I get home to have a proper look and see if I can make heads or tails of the info.

I had a look at the Aver Media website, and have found my card is definitely the A16AR, for which Aver have released drivers for somewhat older linux kernels.

It gives me hope that the card will work in Linux, given there are drivers for older kernels.

Just on that note, I have tried to install a couple of the Aver drivers previously, converting the RPM to DEB using alien, and i have also tried using configure - make - make install.

I never got past configure as it requires (from memory) a 2.6.11 kernel.

Does anyone know a way to compile these drivers against newer kernels? (I am running Edgy 2.6.17-11)

Thanks.

---

### Post by denham2010 on 2007-04-20
Ok, here is my progress so far.

Looking in 

```
http://linuxtv.org/v4lwiki/index.php/CARDLIST.saa7134
```

states that my card is supported in the v4l-dvb-kernel (my card is entry 100 - card number 99)

It appears that the v4l-dvb-kernel that is pre-installed with Edgy is not quite up to date (card number 99 is not recognised)

So I downloaded and installed the latest v4l-dvb-kernel from 
```

http://mcentral.de/hg/~mrec/v4l-dvb-kernel
```

After a reboot I did the following:

```
sudo rmmod tuner saa7134-alsa saa7134
sudo modprobe xc3028-tuner
sudo modprobe saa7134 card=99
```

Now correct me if I am wrong, but it appears my card may now be detected

Output of dmesg

```
[17181230.600000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17181230.604000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 201
[17181230.604000] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 201, latency: 64, mmio: 0xfe9ed800
[17181230.604000] saa7133[0]: subsystem: 1461:2c00, board: AVerMedia TV Hybrid A16AR [card=99,insmod option]
[17181230.604000] saa7133[0]: board init: gpio is effffff
[17181230.752000] saa7133[0]: i2c eeprom 00: 61 14 00 2c 00 00 00 00 00 00 00 00 00 00 00 00
[17181230.752000] saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a3 ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181230.752000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181230.812000] tuner 2-0043: chip found @ 0x86 (saa7133[0])
[17181230.812000] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[17181230.828000] tuner 2-0060: TEA5767 detected.
[17181230.828000] tuner 2-0060: chip found @ 0xc0 (saa7133[0])
[17181230.828000] tuner 2-0060: type set to 62 (Philips TEA5767HN FM Radio)
[17181230.832000] saa7133[0]: registered device video0 [v4l2]
[17181230.832000] saa7133[0]: registered device vbi0
[17181230.832000] saa7133[0]: registered device radio0
[17181230.848000] saa7134 ALSA driver for DMA sound loaded
[17181230.848000] saa7133[0]/alsa: saa7133[0] at 0xfe9ed800 irq 201 registered as card -1
```

But lspci still says "unknown device"

```
01:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device 2c00
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at fe9ed800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

Prior to doing all this, opening TVTime gave me an error "Cannot open device /dev/video0"

Now, TVTime opens the device, I am able to select the input (Television, Composite etc), and run a channel configuration, but unfortunately it is not tuning.

I am thiniking xc3028-tuner may be the problem.

I got this far following:

```
http://www.linuxtv.org/v4lwiki/index.php/AVerMedia_Cardbus_Hybrid_TV_FM_E506R
```

But as you can see, it's for the Cardbus, not the A16AR.

Does anyone have an idea which tuner I should use?

Thanks.

UPDATE:

I just plugged my digital camera into the composite input of the tv card, and I get video from the camera in tv time (but tv time input is still set as Television not Composite)....so I am thinking it must be the tuner.

Any ideas on which tuner module I should use to view the tv signal?

Thanks.

---

### Post by denham2010 on 2007-04-20
Another quick question.

I have seen somewhere how to load modules at boot, but cant seem to find it again.

Can anyone tell me how to load

xc3028-tuner
saa7134 card=99

at boot?

saa7134 is currently loading at boot but is defaulting to card=0.

Thanks.

---

### Post by Gruelius on 2007-06-15
Why are you loading xc3028-tuner?

Try just 
```
modprobe saa7134 card=85
modprobe saa7134-dvb
```

I cant get mine working because UDEV doesnt make the device, im going to try specifying the card at bootup.

---

### Post by Gruelius on 2007-06-15
Solution:
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid-FM_PCI](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid-FM_PCI)
that is for the A16AR ;)

---

### Post by voltagex on 2007-06-22
Edit: Sorry, the A16D is a different card from the A16R

[http://mcentral.de/wiki/index.php/AVerMedia_AverTV_Hybrid_FM_PCI_A16D](http://mcentral.de/wiki/index.php/AVerMedia_AverTV_Hybrid_FM_PCI_A16D)

---

