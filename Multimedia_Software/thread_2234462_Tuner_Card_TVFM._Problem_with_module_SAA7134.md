---
title: "Tuner Card TV/FM. Problem with module SAA7134"
date: 2014-07-14
forum: Multimedia Software
---

### Post by arieleoar on 2014-07-14
[COLOR=#333333][FONT=Ubuntu]Hi there! i need help with my tuner card analog tv/FM radio
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Output of "lspci":

```
02:02.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors SAA7130-based TV tuner card
        Flags: bus master, medium devsel, latency 32, IRQ 23
        Memory at f7effc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: saa7134
```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]The card is branded "SHENGZEN WINSTARS" model: WS-TVP7130FM, it isn't listed between the supported cards by the module saa7134 of the V4L2 driver (video for linux). 

Output of "dmesg":[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu][ 3304.885455] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,insmod option]
[ 3304.886830] saa7130[0]: board init: gpio is c04000
[ 3304.988330] saa7130[0]: Huh, no eeprom present (err=-5)?
[ 3304.988513] saa7130[0]: registered device video0 [v4l2]
[ 3304.988628] saa7130[0]: registered device vbi0[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]Shamely, the vendor saved some $$$ and not writed the eeprom, so the system doesn't recognize as similar to a listed one. 
I tried to use the "modprobe" command with the option "card=42" because is a common answer in other posts, but the tv and radio capture seems to be switched (in tvtime i can see noisetv with some radio fm sound and in gnomeradio i heard some noisy air tv channel, and i can't tune them (even can change the channel).
I've tried with others cards options listed in the module but none works well (some shows tv noise in the composite in), and is tedious :p
Someone has a similar or equal branded card? how do you managed to make it work?

Sorry about some grammar errors, english isn't my home language.[/FONT][/COLOR]

---

