---
title: "Dvico FusionHDTV Pro issues"
date: 2008-12-04
forum: Mythbuntu
---

### Post by Solicitous on 2008-12-04
Hi all,

I have a DViCO FusionHDTV DVB-T Pro running on Ubuntu 8.10 with mythbuntu-desktop installed.
I've copied over the xc3028-v27.fw firmware into /lib/firmware, and the card is correctly detected during bootup.  However under mythtv-setup attempting to setup the capture card, I am only given the options of S-Video or Composite1 under "Default Input", except when I initially setup with a card type "DVB DTV Capture card", then I'm also given the option of "DVBInput"

When trying to scan for channels, none are found.  I'm assuming this is an issue to do with the Default Input (Should an option such as TV or TV Antenna be listed??)

I do get messages from dmesg when trying to setup the card through mythtv-setup of;
cx88[0]/0: Error: Calling callback for tuner 4
and;
cx88[0]/0: Error: unknown tv audio mode [0]

Here is my dmesg (grep'd for cx)

[   18.020671] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   18.021036] cx8800 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[   18.021743] cx88[0]: subsystem: 18ac:db30, board: DViCO FusionHDTV DVB-T PRO [card=64,autodetected]
[   18.021747] cx88[0]: TV tuner type 4, Radio tuner type -1
[   18.053714] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   18.085632] cx2388x alsa driver version 0.0.6 loaded
[   18.309549] cx88[0]/0: found at 0000:01:08.0, rev: 5, irq: 18, latency: 32, mmio: 0xe6000000
[   18.310699] cx88[0]/0: registered device video0 [v4l2]
[   18.310901] cx88[0]/0: registered device vbi0
[   18.311044] cx88[0]/2: cx2388x 8802 Driver Manager
[   18.311073] cx88-mpeg driver manager 0000:01:08.2: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[   18.311086] cx88[0]/2: found at 0000:01:08.2, rev: 5, irq: 18, latency: 32, mmio: 0xe8000000
[   18.311185] cx88_audio 0000:01:08.1: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18
[   18.311223] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   18.585126] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   18.585132] cx88/2: registering cx8802 driver, type: dvb access: shared
[   18.585138] cx88[0]/2: subsystem: 18ac:db30, board: DViCO FusionHDTV DVB-T PRO [card=64]
[   18.585142] cx88[0]/2: cx2388x based DVB/ATSC card
[   18.822724] cx88[0]/2: xc3028 attached
[   18.822731] DVB: registering new adapter (cx88[0])

I've attached my lsmod (grep'd for cx)

Anyone know how to set this card up or able to steer me in the right direction?

---

### Post by Solicitous on 2008-12-08
*bump* anyone?

---

### Post by cvrse on 2008-12-31
had any luck with this? i've got the exact same problem at the moment

---

### Post by cvrse on 2009-01-03
following the solution on the following bug worked for me

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/287195](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/287195)

---

