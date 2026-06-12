---
title: "Tuning failed with Wintv Nova-T"
date: 2007-12-22
forum: Mythbuntu
---

### Post by badalf33 on 2007-12-22
Hello,
I've a problem with MythTV and a DVB-T Nova-T card (Connexant PCI model, ref 9003).
I can watch TV well with Xine, but not with Mythtv.
I've added my channels with the same channels.conf as Xine...
When I'm adding a channel, the signal is between 18% to 38% ...

Signal in MythTV is always : Signal 100%, S/B : 4.5dB, BE 16383 "Pas de verouillage" [I'm French ...]
I'm using MythBuntu 7.10 

example with tzap :
tzap -r "TF1"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 546000000 Hz
video pid 0x0078, audio pid 0x0082
status 01 | signal 2828 | snr ffff | ber 00000000 | unc 00000000 |
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 2727 | snr ffff | ber 00000000 | unc 00000000 | FE_HAS_LOCK

Hardware :
Athlon XP 2500+ on Abit NF7-S mobo
RAM 1 Gb
HDD SATA 120 Gb
DVD-RW IDE
Geforce 4  Ti 4200 Graphic Card
Hauppauge WinTV Nova-T PCI

I don't understand ....:confused:

With this PC, I can watch TV well on Geexbox 1.1 .....

Thanks for your answers .

---

### Post by badalf33 on 2007-12-23
Bad news :

I've tried with another DVB-T card : Avermedia A800. Same result...

So I've tried with Feisty Xubuntu 7.04.
I've done the same configuration as 7.10. It works great !!!!

So I think there's a bug in mythTV 7.10 packages...
( Step 3 : video source)

Where can I explain this to resolve this problem ?

---

