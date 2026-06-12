---
title: "FlyDVB-T Hybrid card installation problems"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by RupertHenry on 2007-03-06
Hello,
    I would very much appreciate some help with a problem that I am haiving installing my FlyDVB-T video card. I have spent many hours seaching the various forums and all similar thread seem to end without a clear answer. I should mention that whilst I used Solaris and SunOS Unix regularly some 7 years ago, my Unix knowledge is a little rusty so I might need a fairly detailed reply. I am using Ubuntu 6.10.

    I have installed the card and am able to watch analogue TV using TvTime so I am sure that the card is OK. From my /var/log/messages...

Mar  6 09:02:56 Myst kernel: [17179593.452000] saa7130/34: v4l2 driver version 0.2.14 loaded
Mar  6 09:02:56 Myst kernel: [17179593.452000] saa7133[0]: quirk: PCIPCI_NATOMA
Mar  6 09:02:56 Myst kernel: [17179593.452000] saa7133[0]: found at 0000:00:10.0, rev: 208, irq: 9, latency: 181, mmio: 0xf4001000
Mar  6 09:02:56 Myst kernel: [17179593.452000] saa7133[0]: subsystem: 5168:3306, board: LifeView FlyDVB-T Hybrid Cardbus [card=94,autodetected]
Mar  6 09:02:56 Myst kernel: [17179593.452000] saa7133[0]: board init: gpio is 210000
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 00: 68 51 06 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 16 ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 32 15 ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.592000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Mar  6 09:02:56 Myst kernel: [17179593.952000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
Mar  6 09:02:56 Myst kernel: [17179594.104000] saa7133[0]: registered device video0 [v4l2]
Mar  6 09:02:56 Myst kernel: [17179594.104000] saa7133[0]: registered device vbi0
Mar  6 09:02:56 Myst kernel: [17179594.104000] saa7133[0]: registered device radio0
Mar  6 09:02:56 Myst kernel: [17179594.192000] saa7134 ALSA driver for DMA sound loaded
Mar  6 09:02:56 Myst kernel: [17179594.192000] saa7133[0]/alsa: saa7133[0] at 0xf4001000 irq 9 registered as card -1


I started to read the linuxtv.org pages on installing the DVB-T part and found that I needed to use modprobe; so 'modprobe saa7134-dvb' seems to work and gives in the messages file...

Mar  6 09:16:17 Myst kernel: [17180406.560000] DVB: registering new adapter (saa7133[0]).
Mar  6 09:16:17 Myst kernel: [17180406.560000] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...


I then tried to use 'scan' from the dvb-utils collection and this is when the ptoblems started. scan failed and in the messages file...

Mar  6 09:17:53 Myst kernel: [17180502.556000] tda1004x: setting up plls for 48MHz sampling clock
Mar  6 09:17:55 Myst kernel: [17180504.828000] tda1004x: found firmware revision 0 -- invalid
Mar  6 09:17:55 Myst kernel: [17180504.828000] tda1004x: booting from eeprom
Mar  6 09:17:57 Myst kernel: [17180507.196000] tda1004x: found firmware revision 0 -- invalid
Mar  6 09:17:57 Myst kernel: [17180507.196000] tda1004x: firmware upload failed

So, I used get_dvb_firmware to get both dvb-fe-tda10045.fw and dvb-fe-tda10046.fx which I placed in /lib/firmware. If I use scan again, I get the same messages as without the .fw files so I am dubious that they are being found and loaded.

So, to my questions...
1) After rebooting my machine, I needed to rerun the modprobe command; how can I get this to happen on reboot? I am familiar with the /etc/rc file structure, but I do not know what to put where.

2) How can I confirm that the hotplug service is at least finding the .fw files? 

3) Is this likely to be the cause of scan failing?

Many thanks in advance, sorry if they are dumb questions, but we all have to learn from somewhere :)

---

