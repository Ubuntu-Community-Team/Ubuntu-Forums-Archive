---
title: "HALP! Can't play MP3 via my Audigy Card"
date: 2009-09-11
forum: Multimedia Software
---

### Post by CSHANKY on 2009-09-11
Folks: I am a recent Ubuntu convertee, with 0 coding skills. 

Was able to install Ubuntu 9.04 fine and am quite happy with it EXCEPT I can't hear my MP3 through my Audigy sound card.

I can hear the system sounds through my 5.1 Speakers connected to the card, when the system boots up.

I have tried various things suggested in the forum(s) - nothing worked. Could a kind soul please hand-hold me and give some step-by-step guidance ? Please bear in my mind I am a novice - so please be patient. Tnx !

Please help - I miss my MP3's !  :cry:

Some info:

lspci -v
01:04.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs Device 100a
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at dce0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106


Also did [SIZE=2]sudo nano /etc/modules  

and added snd-CA0106 to it
[/SIZE]

---

### Post by CSHANKY on 2009-09-11
Solved....updated the ALSA drivers and presto ! :)

However, still can't play my MP3 in 5.1 surround (Center, and Rear Speakers are dead).

Tested all channels - they work fine.

Can anyone help?

---

### Post by Liolikas on 2009-09-11
Looks difficult, but just copy paste code parts and you should get basic 5.1:
[http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)

---

