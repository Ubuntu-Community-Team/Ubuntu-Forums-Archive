---
title: "instructions for installing driver tv tuner card saa7134"
date: 2008-08-05
forum: Multimedia Software
---

### Post by amado738 on 2008-08-05
Hi I'am a bit green on ubuntu I need step by step instructions to manually set up my tv tuner card a tvr7134x (with the popular chipset philips saa7134) I believe this has been written in multiple forums but I cant make much sense of where to begin. my computer has not detected the tuner (as far as I know! any help will be very much appreciated!

---

### Post by xc3RnbFO8P on 2008-08-05
To get more information about your TV card,
do this in Terminal:
> dmesg

---

### Post by amado738 on 2008-08-05
ok I have done that and found a card that should match 

[   34.659303] saa7134:   card=6 -> Tevion MD 9717                    now how do I tell it to install that one

---

### Post by xc3RnbFO8P on 2008-08-05
Just try Tvtime in Add/Remove (all available application)

---

### Post by amado738 on 2008-08-07
I have tv time installed but I still need to tell the system which card to use. how do I do that! 

please include any other instructions I may need to do after so I don't have to bother you any more!

---

### Post by xc3RnbFO8P on 2008-08-10
> **amado738 said:**
> I have tv time installed but I still need to tell the system which card to use. how do I do that! 

please include any other instructions I may need to do after so I don't have to bother you any more!

In /etc/modprobe.d/options
you add: 
options (???????)  card=6
It is very important to list all the messages about the tuner from dmesg.

---

### Post by NIKOLCE77 on 2008-08-14
My TV Tuner Card also doesnt work and I have this dmesg:

[   45.068586] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 5, latency: 32, mmio: 0xda100000
[   45.068613] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   45.068654] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[   45.069958] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   45.069965] bttv0: tuner type unset
[   45.069971] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   45.070573] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   45.071162] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   45.071857] bttv0: registered device video0
[   45.071936] bttv0: registered device vbi0
[   45.147691] bt878: AUDIO driver version 0.0.0 loaded
[   45.147860] bt878: Bt878 AUDIO function found (0).
[   45.147896] ACPI: PCI Interrupt 0000:02:02.1[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   45.147909] bt878_probe: card id=[0x0], Unknown card.
[   45.147912] Exiting..
[   45.147920] ACPI: PCI interrupt for device 0000:02:02.1 disabled
[   45.147933] bt878: probe of 0000:02:02.1 failed with error -22
[   48.525487] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   48.525499] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11

I have tried with many programs but it doesnt work, on windows it worked with WinDVR II program is there any similar in Linux Ubuntu?
Please Help

---

### Post by amado738 on 2008-08-18
[I]In /etc/modprobe.d/options
you add:
options (???????) card=6
It is very important to list all the messages about the tuner from dmesg.[/I]

When I try */etc/modprobe.d/options* I get:

[I]amado@amado-desktop:~$ /etc/modprobe.d/options
bash: /etc/modprobe.d/options: Permission denied
amado@amado-desktop:~$ 
[/I]

Also what do you mean by *(???????)* please explain???

here is an extract of the first six cards showing ( there are over 100):
[I]
[   48.417935] saa7134[0]: found at 0000:00:09.0, rev: 1, irq: 20, latency: 32, mmio: 0xdfff8c00
[   48.417942] saa7134: <rant>
[   48.417943] saa7134:  Congratulations!  Your TV card vendor saved a few
[   48.417944] saa7134:  cents for a eeprom, thus your pci board has no
[   48.417945] saa7134:  subsystem ID and I can't identify it automatically
[   48.417946] saa7134: </rant>
[   48.417947] saa7134: I feel better now.  Ok, here are the good news:
[   48.417948] saa7134: You can use the card=<nr> insmod option to specify
[   48.417950] saa7134: which board do you have.  The list:
[   48.417953] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   48.417957] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   48.417962] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   48.417967] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   48.417971] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   48.417975] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   48.417978] saa7134:   card=6 -> Tevion MD 9717                          
[/I]



what is the (?????) refering to? which numbers or letters? 
I'am sorry but I have difficulties understanding what you are advising me to do. Please d'ont hesitate to treat me like an idiot!

step by step instructions would be good using one of those examples just so I can understand how to do it!

---

