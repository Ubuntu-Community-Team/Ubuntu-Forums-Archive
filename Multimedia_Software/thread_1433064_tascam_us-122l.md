---
title: "tascam us-122l"
date: 2010-03-18
forum: Multimedia Software
---

### Post by JacobJuby on 2010-03-18
Hello

I am using the tascam us-122l, I cant seem to get it to work for playback I have followed the wiki how to from 

  -> [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)

but it is talking to music recorders more than just music listeners

I have a krk rockit speaker attached to my usb sound card and I just want it to work for playing all of my sound out of any help would be greatly appreciated 

also the output of cat /proc/asound/cards is

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff4000 irq 23
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/002)

thanks, 
Jake

---

### Post by bohemier on 2010-04-30
Hi,

did you find a solution for this? I'm in the same situation... using 10.04. US-122L is detected as per cat /proc/asound/cards:

```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc240000 irq 22
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/002)

```

but not available in the system: aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks!

---

### Post by RgnKjnVA on 2010-05-02
Exact same boat here, US-122 with KRK Rockits. I kinda forgot what a hassle it was to get working on Gutsy.

---

### Post by RgnKjnVA on 2010-05-02
> **RgnKjnVA said:**
> Exact same boat here, US-122 with KRK Rockits. I kinda forgot what a hassle it was to get working on Gutsy.

Actually, my bad, I have a US-122 not US-122l however FWIW I just got my audio working on the first try in Lucid following the steps for Fiesty here: [http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)

---

### Post by JacobJuby on 2010-05-05
Yeah this is getting old not being able to use the hardware I bought that should work with this new version but it doesnt any help on this would be niiiice!

---

### Post by OFobbs on 2010-06-08
> **JacobJuby said:**
> Yeah this is getting old not being able to use the hardware I bought that should work with this new version but it doesnt any help on this would be niiiice!


Has anybody got this working for 10.04.  It seemed to slightly work for me in 9.10, but could not connect it to JACK.  I can't get any sound out of the 122L from 10.04.


Thanks.

---

### Post by gnomicon on 2010-07-29
I cannot get the us122L working with lucid 10.04

hi have this in .asoundrc:
```
pcm.!usb_stream {
        @args [ CARD ]
        @args.CARD {
                type string
                default "1"
        }

        type usb_stream

        card $CARD
}

ctl.!usb_stream {
        @args [ CARD ]
        @args.CARD {
                type string
                default "1"
        }

        type hw

        card $CARD
}
```

I redirect pulseaudio to jack

In qjackctl in set only "software mode" and "force 16bit", but i dont see the card in "Interface"

I have this in dmesg:
[  177.144026] usb 1-6: new high speed USB device using ehci_hcd and address 8
[  177.276500] usb 1-6: config 1 interface 1 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 9
[  177.277748] usb 1-6: configuration #1 chosen from 1 choice
[  179.276183] 8: cannot set freq 44100 to ep 0x81
[  179.680034] us122l_set_sample_rate error 
[  179.680077] snd-usb-us122l: probe of 1-6:1.1 failed with error -22

And no US122L in /proc/asound/cards (had it one time but cannot reproduce..)

Using kernel 2.6.32-24-generic
and alsa-firmware package from medibuntu

When the usb cable is plugged at startup, system is frozen until timeout or i disconnect the cable:
[   31.140049] usb 1-6: device descriptor read/64, error -110
[   31.356044] usb 1-6: new high speed USB device using ehci_hcd and address 5
[   46.468049] usb 1-6: device descriptor read/64, error -110
[   61.684033] usb 1-6: device descriptor read/64, error -110
[   61.900044] usb 1-6: new high speed USB device using ehci_hcd and address 6
[   72.308096] usb 1-6: device not accepting address 6, error -110
[   72.420045] usb 1-6: new high speed USB device using ehci_hcd and address 7
[   82.828036] usb 1-6: device not accepting address 7, error -110
[   82.828064] hub 1-0:1.0: unable to enumerate USB device on port 6


Please help me before im going crazy and kill somebody throwing the US122L in the street through the window and finish my life in jail for it... 
.

---

### Post by Thidrek on 2010-10-31
Hi and sorry for grave digging,

I have experiencing this problem for a while now and have not found a solution, yet. That's why I haven't used Ubuntu, either, what's kinda sad.

Right now I am using 10.10 but have had the same problem under 10.04.

$ cat /proc/asound/cards outputs

```

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfeabc000 irq 44
 1 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/004)

```and $ asound -l displays

```

Karte 0: Generic [HD-Audio Generic], Gerät 3: ATI HDMI [ATI HDMI]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0

```System -> Settings -> Sound does not list the card, either. Only the HDMI (I deactivated the on board sound card).
Jack seems to find it but it does not matter whether it's running or not.

And yes, I did everything listed in the usual manuals.

Did anyone of you who posted above find a solution?

Best regards.

---

