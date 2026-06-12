---
title: "Nova-S Plus with corrupted EEPROM as second TV-Card"
date: 2008-09-21
forum: Mythbuntu
---

### Post by MartinusEx on 2008-09-21
Hi out there,
well, here we go.
I do have a hauppauge Nova-S Plus running under mythbuntu 8.04.1
I have a second one with a corrupt EEPROM.

The first one is detected by the system as cx88[0]
The second one naturally as cx88[1] with the message that it cannot be correctly identified.
I need to tell mythbuntu  that this is a hauppauge nova-s plus.

what i found on this is, to enter "options cx88xx card=37" into /etc/modules.config

mythbuntu detects a generic CX23888 grabber card with all composite inputs but no DVB input.

that doesn't work.

any knowledge to share?

thx a lot in advance

dmesg dump
[   50.341936] cx88[0]: hauppauge eeprom: model=92001
[   50.348568] input: cx88 IR (Hauppauge Nova-S-Plus  as /devices/pci0000:00/0000:00:0c.0/input/input6
[   50.376475] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 23, latency: 165, mmio: 0xf5000000
[   50.376575] cx88[0]/0: registered device video0 [v4l2]
[   50.376621] cx88[0]/0: registered device vbi0
[   50.376678] cx88[0]/2: cx2388x 8802 Driver Manager
[   50.376700] ACPI: PCI Interrupt 0000:00:0c.2[A] -> GSI 18 (level, low) -> IRQ 23
[   50.376712] cx88[0]/2: found at 0000:00:0c.2, rev: 5, irq: 23, latency: 64, mmio: 0xf7000000
[   50.384447] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 19 (level, low) -> IRQ 16
[   50.384522] cx88[1]: Your board has no valid PCI Subsystem ID and thus can't
[   50.384524] cx88[1]: be autodetected.  Please pass card=<n> insmod option to
[   50.384526] cx88[1]: workaround that.  Redirect complaints to the vendor of
[   50.384527] cx88[1]: the TV card.  Best regards,
[   50.384528] cx88[1]:         -- tux
[   50.384530] cx88[1]: Here is a list of valid choices for the card=<n> insmod option:
[   50.384533] cx88[1]:    card=0 -> UNKNOWN/GENERIC
... tatata
[   50.384610] cx88[1]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
.. end tatata
[   50.384658] cx88[1]: subsystem: 0000:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   50.384661] cx88[1]: TV tuner type -1, Radio tuner type -1
[   50.529773] cx88[1]/0: found at 0000:00:0e.0, rev: 5, irq: 16, latency: 165, mmio: 0xf9000000
[   50.671611] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   50.671618] cx88/2: registering cx8802 driver, type: dvb access: shared
[   50.671622] cx88[0]/2: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[   50.671627] cx88[0]/2: cx2388x based DVB/ATSC card

end dump

Martinus

---

### Post by MartinusEx on 2008-09-23
Too bad,
 does no one have an idea?!

---

### Post by house82 on 2008-09-23
Patch the code responsible for detection and compile?

---

### Post by MartinusEx on 2008-09-23
> **house82 said:**
> Patch the code responsible for detection and compile?

öhhhhh... (deutsch für Eeeerrrr :) )
How to do that??
I'm unluckily so out of system programming that I am to be counted as a silly newbee. :confused:

I even don't know what part of the system does the detection and have to look up "ls -lah" and other basic stuff.

OK.
to be serious, if this is the only possibility to solve that I need a cookbook solution (at least partly)

I tried Hauppauge Germany for support.
Let's see what they say.

rgds and Thanx

Martinus

---

### Post by MartinusEx on 2008-09-24
Hi,

Hauppauge germany is not able to help (or doesn't want to?)
They tell me to give the card back if still in warranty

(They must out of their f.. minds to tell me to trash a 90$ hardware because a 0.30$ chip is not even dead but contents corrupted data :(:(:(:( )

I looked up the EEPROM data sheet and I planning for the future to set up a repair tool.
By extracting the eeprom content from a known good card 
**(does anone have a dump already? 256 Byte)**

Byuing an exchange chip to programm it with the tool and replace to odd one on the card.

One other possibility might be to reprogram the chip already on the card but I have to dig into that.
This is for a different forum and story
I'll let you know if I have a soluition.

---

