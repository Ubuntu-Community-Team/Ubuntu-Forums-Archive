---
title: "SB Live! users: Does lspci ID  your SB correctly?"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by johnpipe on 2007-01-11
Information from my  [SB Live! Value Howto]("http://www.ubuntuforums.org/showthread.php?t=205449&page=45") on this board will be added by the maintainer to the next revision of the [Linux Sound HOWTO]("http://tldp.org/HOWTO/Sound-HOWTO/") .8) 

 I am therefore requesting data from any SB Live! users; does the output of "lspci -v" correctly identify your SB as a "Media" device? If so, will you please post your "lspci -v" code here?

The issue to resolve here is whether the identification error mentioned in my [ Howto]("http://www.ubuntuforums.org/showthread.php?t=205449&page=45") is limited to certain motherboard chipsets, or endemic to the SB Live! and/or its variants.

Thanks in advance, Johnpipe

---

### Post by budgie9 on 2007-01-11
Can't say if mine is a value unit ( it is too long since I last saw it) But if this helps by all means use it.

0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>

---

### Post by technoteen on 2007-01-12
02:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, latency 64, IRQ 169
        I/O ports at df00 [size=32]
        Capabilities: <access denied>

i have SB Live 24bit PCI Card on ubuntu 6.10

---

### Post by peebly on 2007-01-12
> **johnpipe said:**
> Information from my  [SB Live! Value Howto]("http://www.ubuntuforums.org/showthread.php?t=205449&page=45") on this board will be added by the maintainer to the next revision of the [Linux Sound HOWTO]("http://tldp.org/HOWTO/Sound-HOWTO/") .8) 

 I am therefore requesting data from any SB Live! users; does the output of "lspci -v" correctly identify your SB as a "Media" device? If so, will you please post your "lspci -v" code here?

The issue to resolve here is whether the identification error mentioned in my [ Howto]("http://www.ubuntuforums.org/showthread.php?t=205449&page=45") is limited to certain motherboard chipsets, or endemic to the SB Live! and/or its variants.

Thanks in advance, Johnpipe

How do I find this info, So I can post it.

---

### Post by johnpipe on 2007-01-12
> **budgie9 said:**
> Can't say if mine is a value unit ( it is too long since I last saw it) But if this helps by all means use it.

```
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at d800 [size=32]
        Capabilities: <available only to root>
```

Thanks, budgie,

I see from the post editor window that you do have a rev 08, although  not  a "Value";  the "Value" will ID itself as such in the "Subsystem:" line where the model number is shown. Your model listing has helped narrow the possibilities.

 If anyone has a rev 08 that identifies itself as a "Value" as well as a 'Multimedia" it will definitely close in on the problem area.

BTW, When posting code on the forum, it helps  to enclose the code within the "#" code tag available from the posting window menubar, as I have done in quoting this post; otherwise   parentheses will often render as a smiley  in the forum listing.

Thanks for your response,

Johnpipe

---

### Post by johnpipe on 2007-01-12
> **peebly said:**
> How do I find this info, So I can post it.

Go to  "Applications" on the menu bar; select "Accessories" then "Terminal".  type "lspci -v" in  the terminal window ; it will show all PCI devices. You can then copy and paste from the terminal window; or, type "lspci -v > lspci.log" and it will send the output to a new file called "lspci.log" in your "home" folder, and you can copy and paste from there.

HTH, Johnpipe

---

### Post by zenrox on 2007-01-23
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 193
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

02:0b.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at c400 [size=8]
        Capabilities: <access denied>
on edgy

---

### Post by blankSWFC on 2007-01-23
I'm using Ubuntu edgy.  I have a Sound Blaster Live! Value.  It detects it and works just fine straight after install.  However i did have to manually select it in the sound settings, as it defaulted to the on-board nVidia nForce2 SoundStorm card (which i broke the speaker out jack :D )..

But anyway, heres my output....

[B]01:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 04)
        Subsystem: Creative Labs CT4850 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 209
        I/O ports at 9000 [size=32]
        Capabilities: [dc] Power Management version 1

01:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 01)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9400 [size=8]
        Capabilities: [dc] Power Management version 1
[/B]

Are there several different cards available as the Sound Blaster live?  as my model is the "CT4850", and the previous poster has a "CT4780".:confused:

Oh, and just to add, my motherboard is the MSI K7N2 Delta-ILSR, which uses the nVidia nForce2 Ultra 400 Chipset, since the first person wants to know if its just down to certain mobo chipsets...

---

### Post by phillipbeynon on 2008-05-07
Yes.

03:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs CT4780 SBLive! Value
	Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 22
	I/O ports at 2040 [size=32]
	Capabilities: [dc] Power Management version 1

03:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
	Subsystem: Creative Labs Gameport Joystick
	Flags: bus master, fast Back2Back, medium devsel, latency 32
	I/O ports at 2060 [size=8]
	Capabilities: [dc] Power Management version 1

---

