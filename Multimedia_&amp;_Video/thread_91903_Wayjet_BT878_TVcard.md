---
title: "Wayjet BT878 TVcard"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by Karahana on 2005-11-18
So I've got this crappy TV card that isn't listed on the bttv drivers compatibility list. When I start TVtime I can change inputs, but I get a no-signal message when switching to TV. I guess that would mean that the wrong tuner is selected. I don't know how to check wich tuner I use...

Help pls! :)

---

### Post by oskude on 2005-11-22
[http://www.ubuntuforums.org/showpost.php?p=491066&postcount=2](http://www.ubuntuforums.org/showpost.php?p=491066&postcount=2)

---

### Post by RedLine on 2005-11-24
I have a Wayjet BT878 TvCard to and i can't make the sound working. To get picture i used "modprobe bttv tuner=24", i don't know how to configure the sound.

---

### Post by oskude on 2005-11-24
[QUOTE=RedLine]I have a Wayjet BT878 TvCard to and i can't make the sound working.[/QUOTE]my miroPCTV card has a sound out plug that i have to connect with my soundcards input with a cable...

---

### Post by RedLine on 2005-11-24
It's pluged in the "line in" @ my soundcard. "Line In" it's working properly, but from the tv tuner output comes no sound. It's very strange, i can't understand why.

---

### Post by oskude on 2005-11-24
yeah, some programs dont give any sounds, but some do (dunno why)... try different tv programs (zapping, tvtime, xawtv, etc...). im not at the pc with my tv card atm so i cant try which proram gave audio, but some deffinetly did...

---

### Post by paunivian on 2006-10-04
anyone did made this card work? couse mine is still no signal :(

dmesg: 
tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179592.152000] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[17179592.152000] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[17179592.196000] ts: Compaq touchscreen protocol output
[17179592.228000] parport: PnPBIOS parport detected.
[17179592.228000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179592.336000] bttv0: registered device video0
[17179592.336000] bttv0: registered device vbi0
[17179592.336000] bttv0: registered device radio0
[17179592.336000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179592.368000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179592.368000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179592.696000] NET: Registered protocol family 17
[17179592.744000] bt878: AUDIO driver version 0.0.0 loaded
[17179592.744000] bt878: Bt878 AUDIO function found (0).
[17179592.744000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 185
[17179592.744000] bt878(0): Bt878 (rev 17) at 00:13.1, irq: 185, latency: 32, memory: 0xee800000

lspci

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:13.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:13.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

