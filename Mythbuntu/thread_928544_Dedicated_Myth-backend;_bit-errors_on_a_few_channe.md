---
title: "Dedicated Myth-backend; bit-errors on a few channels."
date: 2008-09-24
forum: Mythbuntu
---

### Post by argh2k on 2008-09-24
Hi! 
 First of all: Setup.
 MSI K9N NEO-F V3, nForce 560, Socket-AM2
 AMD Athlon 64 X2 4400+ 2.3GHz Socket AM2 1MB
 8G TwinMOS DDR2 PC6400
 4xSamsung SpinPoint T166 500GB SATA2
 Terratec 1200S DVB-S

 Mythbuntu 8.10 alpha 4 amd_64 dedicated backend.
 Dish pointed at 28.2E.

 When tuning to some channels (ITV2+1) I get glitches in playback on my frontend; enough to make it unwatchable. 
A scan / szap gives me:

zapping to 961 'ITV2+1':
sat 0, frequency = 10891 MHz H, symbolrate 22000000, vpid = 0x0947, apid = 0x094            8
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
status 01 | signal bdae | snr 72c0 | ber 0000ff00 | unc fffffffe |
status 1f | signal d340 | snr c9ea | ber 00000600 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d383 | snr c99f | ber 00000200 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d469 | snr c9cc | ber 00000100 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d3a9 | snr c9d5 | ber 00000200 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d419 | snr c99c | ber 00000100 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d44c | snr ca14 | ber 00000000 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d469 | snr ca20 | ber 00000200 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d44a | snr cac5 | ber 00000000 | unc fffffffe | FE_HAS_LOCK
status 1f | signal d46d | snr cb13 | ber 00000100 | unc fffffffe | FE_HAS_LOCK

 BBC1 and others has no biterrors.

 What puzzles me is that I have a:
 
 Dell optiplex Gx260 p4 2,4 Ghz 
 1 GB DDR
 120 GB ATA 100 IDE disk

- which works perfectly with the same DVB-S card, myth 8.04 backend and the same cable to the LNB. 
 When tuning to ITV2+1 I get no BER in szap, no glitches in playback on my frontends.

 When connected to my stb, I get 80% signal strength, 74% Signal quality. And perfect picture. 

 I really need some help here - anybody have an idea how to fix this?

regards
  Anders

---

### Post by SiHa on 2008-09-24
Just a thought - is it a dual tuner card?

...because the NovaT500 has an onboard amplifier to boost the signal, this must be enabled in a config file, otherwise you get terrible glitches.
Perhaps you have a similar setup, and one PC has it enabled, and the other not?

---

### Post by argh2k on 2008-09-24
Nope. Single tuner, no booster.
 The card works perfectly on the Optiplex under both Myth and Windows. 
 I just dont get it...
 No shared irq's, nothing to conflict. I'm even running headless, so theres's no graphicscard to make problems.

---

### Post by SiHa on 2008-09-24
Yeah, Graphics gard was my other guess, but I saw you hadn't listed one.
Oh well, sorry - I'm clueless.

---

### Post by argh2k on 2008-09-24
Yep, me too. Looks like my old GX260 will be the backend. :(
Got 2 TwinHan cards on the way; wonder if the old 2.4 Ghz can handle 3 streams at once? (No hd..)
 Or maybe the twinhans will work on my server...

---

