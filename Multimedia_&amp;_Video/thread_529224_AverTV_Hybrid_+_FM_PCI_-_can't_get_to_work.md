---
title: "AverTV Hybrid + FM PCI - can't get to work"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by Harlequin on 2007-08-18
I've hit a total brick wall with this card.

relevant part of lspci -vv


> 
02:08.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device f936
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 15
        Region 0: Memory at fb005000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


What I have tried

 sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo rmmod tuner

sudo modprobe saa7134 card=99 tuner=##  <-- where I have tried every number under the sun.

I have also installed the firmware for an XC3028 tuner.

I have compiled against a v4l kernel snapshot as well

 All I can get though is a blank tv - I can't get any channels.  I'm stuck.  HELP!

---

### Post by wolfen69 on 2007-08-19
Originally posted by tropicflite

I have a Hauppauge 150pvr card running on my Feisty box, and I get live tv by going to VLC player:

File -> open Capture Device -> PVR -> OK

Did you already install ivtv-utils by doing

sudo apt-get install ivtv-utils

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

---

### Post by Harlequin on 2007-08-19
I din't have that installed 

Have now - but it just appears to be a way of controlling the channels etc on the card

TvTime has been letting me do that already - also able to change input sources between tuner, Svideo and composite.  Just can't get the tuner to pick up anything.

---

### Post by Harlequin on 2007-08-20
Bump

Anyone pls!

---

