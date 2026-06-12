---
title: "MythTV:  Dvico Fusion 5 RT Lite ATSC Install Problem"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by strat_53711 on 2007-08-05
I'm having problems getting MythTV to recognize the Dvico Fusion 5 RT Lite PCI card.

I go to Capture cards:  DVB DTV capture card (v3.x) and no information is returned for any DVB card number.

Any help appreciated.

---

### Post by newlinux on 2007-08-05
Have you loaded the dvb_bt8xx module? I believe the card needs that module to work:

```

sudo modprobe dvb_bt8xx

```

If that works you will need to put that module in your /etc/modules file to have it load on boot. If it doesn't work find out if your computer is recognizing the card.

What does dmesg state (type dmesg at the command prompt and look through the output to see if the card is recognized).

---

### Post by strat_53711 on 2007-08-05
I tried that.  I can get MythTV to recognize the analog part of the card but not the digital.

I've played around with card=135 and  tuner=64.

The MythTV setup isn't finding the card.

---

### Post by newlinux on 2007-08-05
So the frontend ID is blank when you set it up as a DVB card? If not what does it read? And when you set it up as a analog (Did you mean you set it up as a v4L card) it read BT878 card or something? Also, as I asked earlier, what is the dmesg output after loading the module? This would help rule out any problems with your hardware and the card, just to be sure. If your already sure of this information feel free to ignore...

---

### Post by strat_53711 on 2007-08-05
So the frontend ID is blank when you set it up as a DVB card? 

Yes

And when you set it up as a analog (Did you mean you set it up as a v4L card) it read BT878 card or something? 

BT878 card, I can get MythTV to accept the analog part.

Also, as I asked earlier, what is the dmesg output after loading the module? 

[   28.864780] bttv0: registered device video0
[   28.864794] bttv0: registered device vbi0
[   28.866092] bttv0: add subdevice "dvb0"
[   28.884934] bt878: AUDIO driver version 0.0.0 loaded
[   28.884968] bt878: Bt878 AUDIO function found (0).
[   28.884986] ACPI: PCI Interrupt 0000:01:0a.1[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   28.884992] bt878_probe: card id=[0xd50018ac],[ DViCO FusionHDTV 5 Lite ] has DVB functions.
[   28.884999] bt878(0): Bt878 (rev 17) at 01:0a.1, irq: 18, latency: 4, memory: 0xfdffe000

I'm new to Ubuntu.  Any other suggestions

---

### Post by huffy@charter.net on 2007-10-12
Greetings:
I would be very interested with resolving this issue since I am having the same problem. In addition the analog channels are only in bw.

---

