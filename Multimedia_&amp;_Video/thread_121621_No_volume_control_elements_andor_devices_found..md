---
title: "No volume control elements and/or devices found."
date: 2006-01-25
forum: Multimedia &amp; Video
---

### Post by hafunui on 2006-01-25
I cant seem do do anything with my sound at all. In the sound preferences, theres nothing under Default sound card. And when I try and change the volume I get this error:

[COLOR="Sienna"]No volume control elements and/or devices found.[/COLOR]

Im not sure what my soundcard is, but it's inagrated into my DELL OptiPlex GX1 400+

---

### Post by jwmislan on 2006-01-25
Can you give us some more info ?, say from your top panel 
System - Administration - Device Manager - (any info on sound device) in here.

  what does   cat /proc/asound/modules   give you ?
  should tell you if you  have modules loaded for sound 
 
  Do you even have the directory /proc/asound ?

 See what you can find - (a little hunting), and post any new info back here for more help if you need to

JWM

---

### Post by hafunui on 2006-01-25
I didnt recognize anything in the device manager. I dont think it was there.
And I dont seem to have /proc/asound/

I do have windowsXP however. Maybe I could see what card I have there? Sound works in XP.

---

### Post by hafunui on 2006-01-25
Here's another error:

[COLOR="Sienna"]The volume control did not find any elements and/or devices to control. This means either that you do not have the right GStreamer plugins installed, or that you do not have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/COLOR]

I also read something about ALSA and POLYSOUND. Could i be missing some drivers? Could I get these from the synaptic manager?

---

### Post by hafunui on 2006-01-26
I've been doing a little bit more research. I thinks it's just not detecting my card.
And acording to the Official Wiki, i should post what "lspci" and "dmesg" spew out. So here they are.

lspci:

[COLOR="Sienna"]0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)[/COLOR]

dmesg:

[COLOR="Sienna"]tkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14732.599911] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14732.756713] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14732.756734] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14732.955834] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14732.955856] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14733.097242] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14733.097264] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14733.214711] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14733.214732] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14733.356110] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14733.356131] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14736.713613] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14736.713635] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14736.798385] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14736.798408] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14737.191036] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14737.191058] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14737.309305] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14737.309327] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14738.487291] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14738.487314] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14738.605547] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14738.605569] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14739.073513] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14739.073535] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14739.173741] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14739.173762] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14740.054817] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14740.054839] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14740.198810] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14740.198831] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14740.927123] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14740.927145] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14741.076235] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14741.076257] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14741.505527] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14741.505548] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14741.600640] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14741.600663] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14741.623530] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14741.623551] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14741.749516] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14741.749538] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14747.249937] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14747.249960] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14747.386183] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14747.386205] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14748.105861] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14748.105883] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14748.211249] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14748.211271] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14750.703853] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14750.703875] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14750.811812] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14750.811834] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14752.052175] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14752.052198] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14752.149843] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14752.149864] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14752.785545] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14752.785567] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14752.903802] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14752.903823] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14753.186782] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14753.186803] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14753.289593] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14753.289614] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14753.789812] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14753.789834] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14753.910615] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14753.910638] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14754.053881] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14754.053904] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14754.164409] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14754.164431] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14755.079888] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14755.079910] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14755.210971] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14755.210993] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14755.302668] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14755.302688] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14755.418332] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14755.418353] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14756.004630] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14756.004652] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14756.125441] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14756.125463] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14756.378318] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14756.378339] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14756.499146] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14756.499168] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14757.223087] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14757.223110] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14757.359332] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14757.359353] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14758.292063] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14758.292086] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14758.392360] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14758.392382] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14765.043912] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14765.043934] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14765.159612] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14765.159633] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14766.064303] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14766.064325] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14766.228895] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14766.228917] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14766.404402] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14766.404422] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14766.507228] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14766.507250] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14767.609855] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14767.609877] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14767.794983] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14767.795004] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14772.974876] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14772.974898] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14773.085387] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14773.085409] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14774.018072] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14774.018094] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14774.174926] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14774.174948] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14775.210913] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14775.210935] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14775.331726] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14775.331747] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14776.415069] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14776.415091] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14776.487036] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14776.487058] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14777.974725] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14777.974747] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14778.128980] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14778.129002] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14778.366834] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14778.366855] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14778.515945] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14778.515967] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14779.842400] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14779.842422] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14779.963214] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14779.963235] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14780.407527] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14780.407549] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14780.541256] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14780.541277] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14784.718500] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14784.718522] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14784.849605] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14784.849627] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14785.638190] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14785.638212] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14785.759040] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14785.759062] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14787.509293] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14787.509315] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14787.676456] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14787.676478] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14789.246064] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[14789.246086] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[14789.397758] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[14789.397780] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17733.553615] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17733.553637] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17733.679576] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17733.679599] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17734.214216] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17734.214239] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17734.858235] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17734.858258] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.025306] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17735.025328] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.143559] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17735.143582] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.400746] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17735.400768] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.477845] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17735.477868] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.563055] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17735.563077] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.653027] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17735.653050] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.727516] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[17735.727538] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[17735.812326] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[17735.812349] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[/COLOR]

Did I do something wrong? :|

---

### Post by FarEast on 2006-01-26
Hi hafunui;) ,

It seems that your sound chip is on ISA bus.
If you can boot Windows, get information of it with 'device manager'.
Else install 'isapnptools' and do the following:
```
$ pnpdump > isabus.txt
$ less isabus.txt
```
Then paste the information regarding the sound chip.
For example, the output will contain information like this:

```
# Card 1: (serial identifier 4c 00 00 bf 35 49 00 8c 0e)
# Vendor Id CTL0049, Serial Number 48949, checksum 0x4C.
# Version 1.0, Vendor version 1.0
# ANSI string -->Creative SB32 PnP<--
```

---

### Post by hafunui on 2006-01-26
Ok, I got isapnptools. This is what i got:

```
# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
#
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
#
# For details of the output file format, see isapnp.conf(5)
#
# For latest information and FAQ on isapnp and pnpdump see:
# http://www.roestock.demon.co.uk/isapnptools/
#
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
#
# Trying port address 0273
# Board 1 has serial identifier b6 ff ff ff ff 35 68 63 0e

# (DEBUG)
(READPORT 0x0273)
(ISOLATE PRESERVE)
(IDENTIFY *)
(VERBOSITY 2)
(CONFLICT (IO FATAL)(IRQ FATAL)(DMA FATAL)(MEM FATAL)) # or WARNING
```

---

### Post by FarEast on 2006-01-26
OK;) 
Do 'less isabus.txt' again and look for the informaition
by hitting Page Up/Down.
Or you can use 'gedit'(gnome text editor) instead of 'less'.

---

### Post by hafunui on 2006-01-26
Oh, heh, thanks.

[COLOR="Sienna"]# Card 1: (serial identifier b6 ff ff ff ff 35 68 63 0e)
# Vendor Id CSC6835, No Serial Number (-1), checksum 0xB6.
# Version 1.0, Vendor version 0.1
# ANSI string -->CS4236B<--[/COLOR]

---

### Post by FarEast on 2006-01-26
Now read this thread :).
[http://ubuntuforums.org/showthread.php?t=24877&highlight=cs4236](http://ubuntuforums.org/showthread.php?t=24877&highlight=cs4236)

EDIT:

You may have to edit /etc/modprobe.d/sound to describe some options.
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4235%2C+CS4236%2C+CS4236B%2C+CS4237B%2C+CS4238B%2C+CS4239&module=cs4236](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4235%2C+CS4236%2C+CS4236B%2C+CS4237B%2C+CS4238B%2C+CS4239&module=cs4236)

options snd-cs4236 port=0x530 cport=0x538 \
mpu_port=-1 fm_port=0x388 irq=5 dma1=1 \
dma2=0 dma1_size=16 dma2_size=16 isapnp=0 \
index=0 sb_port=0x220

Then execute:
```
$ sudo update-modules
```
Restart the system.
Enter BIOS setting and reserve IRQ5 for ISA PnP devices.

---

### Post by hafunui on 2006-01-26
Wow, thanks it worked :D

---

### Post by FarEast on 2006-01-26
I'm glad that I could help you :):)
When you find anyone having the same problem, please help him(her)!

---

### Post by xdonut on 2006-04-02
Hiya all...
I'm having the same problem, but I the
pnpdump > isabus.txt
command just gives me the following error message:

"REALTIME operation timeout exceeded - Switching to normal scheduling
nanosleep failed: Interrupted system call"

I can find my sound card in my device manager though.
Any help much appreciated...
Thanks.

---

### Post by FarEast on 2006-04-03
Hi xdonut,
For you can find the sound chip in your device manager, you need not to use 'isapnptools':) .
Which sound chip is it?

---

### Post by xdonut on 2006-04-03
Well... umm... I'm pretty noobish at this, but...
The device manager lists my sound card as
"VT8233/A/8235/8237 AC97 Audio Controller"
I don't even know if that's a soundcard. :P Ah well.
Thanks.

---

### Post by FarEast on 2006-04-04
OK... Please join the thread;) 

[http://www.ubuntuforums.org/showthread.php?t=104387&highlight=VT8233](http://www.ubuntuforums.org/showthread.php?t=104387&highlight=VT8233)

---

### Post by sagar on 2006-09-06
hai to all 
i am new to linux.i am using dapper, in that same problem i have.plz any one help me in geting sound in that. note that i am new to use this plz give me suggesions in details

---

### Post by MyBuntu on 2007-01-21
It Could Also Be A Simple Problem
Your Account Doesn't Have The Proper Rights...
Or Because You Installed An Update It Must Have
Deleted Your Old Settings.

If Your Sound Works Before Then It Should Now
Chances Are Your Computer Has The Correct Drivers

Go To Systems-----users And Groups Then  On The User Privileges Tab
Scroll Down The List And Click "use Audio Devices" Then Close

Log Out 

Log In Again

Make Sure You Have Mute Bottom Off And Disconnect Any Headphone

Hope For The Best

---

### Post by samra on 2007-06-16
Hi 
MyBuntu: Thank you for the tip. It worked with me, 
I have got the message that "The volume control did not find any elements and/or devices to control" after I changed the password of my account in ubuntu 6.06. 
What I did to solve was: System> Administration> Users and Groups> click on my user-name under Users tab> Properties> User Privilege tab> tick Use Audio Devices. 
Logged out and then in, I do hear the sound :) Many thanks to all of you

---

### Post by Triple Threat on 2007-10-12
Hi yall,

Ok I HAD sound then I updated something (I think I replaced gAIM with Pidgin) and it said some packages weren't used anymore or something. Also got this same error:

"No volume control GStreamer plugins and/or devices found." I tried to use synaptic to look at what I has installed and it told me (after entering root password) that I didn't have permission to use it???? what the?... and then I tried running the program from terminal (e.g. /usr/sbin/synaptic while root) and it let me in but said I didn't have privileges to update my system, I could only search the packages.

Also, when I boot up i get the default drum sound when you enter in your user id. After that.. nothing. And I dont have a devince manager icon or users and groups icon in my System -> Administration section. Anyone know what these programs are called off hand?

thanks in advance.

---

### Post by meatrun on 2008-07-23
I am very new to linux and unbuntu I loaded it yesterday. I'm also getting the error No volume control elements and/or devices found. I have been going through alot of fixes and i am trying tofolow along with what is susgested but to no avail. From what i have tracked down this is what i have in my system.

03:04.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi XtremeMusic
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at bce0 [size=32]
	Memory at dac00000 (64-bit, non-prefetchable) [size=2M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

But im not sure what to do with the information it would seem that alsa has no support for that card. I looks as if i can see the card just no access to it. thank yo in advance for your help

---

