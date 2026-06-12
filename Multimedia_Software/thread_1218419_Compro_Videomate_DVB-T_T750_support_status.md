---
title: "Compro Videomate DVB-T T750 support status"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Jimbley on 2009-07-20
Hi all,

This is a quick post to update everyone as to the status of support for the above PCI card.

**This device is unsupported in the v4l-dvb project.**

There is a patch formerly in development at [http://www.chrysocome.net/downloads/v4l-dvb-t750-0.1.diff]("http://www.chrysocome.net/downloads/v4l-dvb-t750-0.1.diff") but the reports indicate that the only supported part of this card is its composite input.

The patch author (John Newbigin) is no longer working on this. However, links to his work are available on the v4l mailing lists.

From the information on the v4l mailing list, it is apparent that there are probably two issues getting the card to work:

[LIST=1]
[*]Lack of explicit driver support
[*]Mulitple frontends
[/LIST]

The sections of the v4l source code that should  contain information about the configuration of this card are empty. It is listed as card number 139 in the saa7134.cards file in the source.

Multiple frontends are not fully supported by the saa7134 module. This card has an Xceive xc2028 analog tuner/demodulator and a Quantek QT1010 digital tuner, along with an Intel 6353/Zarlink MT352 CODFM demodulator. It is very likely that the initialization and switching between these two frontends is the main difficulty in getting it to work. John Newbigin has done some i2c traces in case anyone is interested in further development.

I2c dumps are also available from the [_V4L-DVB wiki page_]("http://linuxtv.org/wiki/index.php/Compro_Videomate_T750").

Cheers,

Jim

---

