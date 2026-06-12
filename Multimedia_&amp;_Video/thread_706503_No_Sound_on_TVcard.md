---
title: "No Sound on TVcard"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by hrisk on 2008-02-24
Hello i am new to ubuntu and a have a problem with my TV card.
I will try to explain all the steps i have done
[LIST=1]
[*]After the installation of Ubuntu the card (Hauppauge PCI Win TV-radio (with the bt878 chip set) was normally recognized*. 
I have an sound card incorporated in the motherboard (ASUS)
[*] I choose the tvtime application from the synaptic package manager which was installed.
[*] I started the application and i search for channels (Europe PAL)
[*] I found only 7 channels (because i have an internal antenna) with very good image and colors but with no sound at all.
[*] I looked in the ALSAMIXER for mute channels which was not found. The sound plays ok in other applications (Amarok, SMPlayer).
[/LIST]

*multimedia video controller Brooktree Corp. Bt878 video capture (rev 11)
*multimedia video controller Brooktree Corp. Bt878 audio capture (rev 11)

Sorry if this question is asked before but after days of searching i get confused from the answers an i am afraid that i will mesh up with the system
thanks!

---

### Post by VMan on 2008-02-24
Check the card.  It may require that a cable be routed from the "sound out" on the TV card to the "line in" or "mic" inputs on the sound card.  This is the way my Hauppage TV card worked.  I don't remember the model (not at home to check it).

---

### Post by hrisk on 2008-02-25
I use the external cable and do it but still no sound.
Here a some screen shots from the alsamixer.

---

### Post by genesain on 2008-02-26
Fixed my issue. Loaded ALSAGUI mixer and found Master volume turned off ... although system sounds and playing music worked ... this apparently impacted the Tuner sound. I also switched back to an old ESS Solo sound card.


I seem to have same issue with TVtime not playing sound. My card is WINTV 878.  I did display dmesg and see the following which looks suspicious  ... audio processor is none ??. Video works fine. Cable connections seem fine. Audigy sound card.

[   53.834144] bttv: Bt8xx card found (0).
[   53.834195] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   53.834221] bttv0: Bt878 (rev 17) at 0000:00:0f.0, irq: 11, latency: 64, mmio: 0xfc9fd000
[   53.834249] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   53.834258] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   53.834310] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   53.836803] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   53.864428] tveeprom 0-0050: Hauppauge model 44981, rev E199, serial# 8226809
[   53.864439] tveeprom 0-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   53.864448] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   53.864456] tveeprom 0-0050: audio processor is None (idx 0)
[   53.864464] tveeprom 0-0050: decoder processor is BT878 (idx 14)
[   53.864471] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   53.864478] bttv0: Hauppauge eeprom indicates model#44981
[   53.864485] bttv0: using tuner=50
[   53.864493] bttv0: i2c: checking for MSP34xx @ 0x80... <6>Real Time Clock Driver v1.12ac
[   55.052538] not found
[   55.052556] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>input: PC Speaker as /class/input/input2
[   55.475241] not found

---

### Post by hrisk on 2008-02-27
I used the command dmesg | less with these results (among others):

[COLOR="Magenta"][   37.955351] bttv0: Bt878 (rev 17) at 0000:04:01.0, irq: 16, latency: 64, mmio: 0xf8ffe000
[   37.955363] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   37.955365] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   37.955389] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   37.957872] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   37.989698] tveeprom 0-0050: Hauppauge model 44354, rev D147, serial# 5127945
[   37.989701] tveeprom 0-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
[   37.989704] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[   37.989705] tveeprom 0-0050: audio processor is MSP3415 (idx 6)
[   37.989707] tveeprom 0-0050: has radio
[   37.989709] bttv0: Hauppauge eeprom indicates model#44354
[   37.989711] bttv0: using tuner=28
[   37.989719] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   38.019882] msp3400 0-0040: MSP3415D-B3 found @ 0x80 (bt878 #0 [sw])
[   38.019884] msp3400 0-0040: MSP3415D-B3 supports nicam, mode is autodetect

[   38.021788] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.024373] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   38.081217] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   38.125955] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   38.125980] tuner 0-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[   38.125983] tuner 0-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[   38.146552] bttv0: registered device video0
[   38.146569] bttv0: registered device vbi0
[   38.146586] bttv0: registered device radio0
[   38.155748] bttv0: PLL: 28636363 => 35468950 .. ok[/COLOR]

I saw that the param [COLOR="Magenta"]bttv : i2c[/COLOR] has a problem (The no-sound-at-all problem exist in the radio too - gradio application)

In this link [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789#2978](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789#2978) i found that:

[COLOR="Magenta"]...I solved a problem passing i2c_udelay parameter for bttv module. Now my /etc/modprobe.conf looks like this:

  options bttv radio=1 tuner=28 card=10 [COLOR="Black"](My commend: card=10 is for Hauppauge)[/COLOR] gbuffers=4 i2c_udelay=128

  Perhaps i2c_udelay=16 will be enough too - need to check. With this parameter sound from tv works ok on 2.6.22 (from Gutsy) as well as on 2.6.24rc5 (from Hardy Alpha2).

  Hope this info will be useful...
[/COLOR]

Questions
1) I didn't found that file (/etc/modprobe.conf) - sould i create it?
2) How can i run a srcipt from command line as a admin?

---

### Post by hrisk on 2008-03-03
The problem was semi-solved.
I connected the speakers directly to the line out of the tv card (Hauppage Win TV Radio - PCI - Bt878A).
Now i have sound both in tvtime and in gnomeradio.:)

In windows though there is no problem like that. 

I will search more . I will post my findings there as soon as i find them.

My settings in /etc/modprobe.conf is

options bttv
card=10 tuner=28 radio=1 gbuffers=4 i2c_udelay=128

---

### Post by hrisk on 2008-05-01
[SIZE="3"][/SIZE]Update:
The new 8.04 hardy has solve the problems of sound both in tvtime and GnomeRadio
I use a Hauppauge WinTv PCI card (bt878A chip set) and use a externally cable to link it with the line-in of the onboard sound card.

---

