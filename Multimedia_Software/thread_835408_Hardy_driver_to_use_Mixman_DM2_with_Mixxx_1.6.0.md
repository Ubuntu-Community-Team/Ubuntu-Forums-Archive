---
title: "Hardy: driver to use Mixman DM2 with Mixxx 1.6.0"
date: 2008-06-20
forum: Multimedia Software
---

### Post by openversus on 2008-06-20
D
Hi people!
I use ubuntu hardy and I buy the Mixman DM2 (after watching this video: [COLOR="Red"][SIZE="4"][SIZE="1"][COLOR="Sienna"][http://www.youtube.com/watch?v=e7tonj6_Oik](http://www.youtube.com/watch?v=e7tonj6_Oik).[/COLOR][/SIZE][/SIZE][/COLOR]
I download the ALSA MIDI Driver (but I think I have a kernel problem: Jan in the video say that you need 2.6.24 kernel), but I have this on the terminal:

[I]root@joda:~# cd /home/versus/Scrivania/dm2/
root@joda:/home/versus/Scrivania/dm2# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/versus/Scrivania/dm2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
CC [M] /home/versus/Scrivania/dm2/dm2.o
Building modules, stage 2.
MODPOST 1 modules
WARNING: "snd_card_register" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_set_ops" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_new" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_card_new" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_receive" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_transmit_ack" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_transmit_peek" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_card_free" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
CC /home/versus/Scrivania/dm2/dm2.mod.o
LD [M] /home/versus/Scrivania/dm2/dm2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

root@joda:/home/versus/Scrivania/dm2# make install
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/versus/Scrivania/dm2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
Building modules, stage 2.
MODPOST 1 modules
WARNING: "snd_card_register" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_set_ops" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_new" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_card_new" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_receive" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_transmit_ack" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_rawmidi_transmit_peek" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
WARNING: "snd_card_free" [/home/versus/Scrivania/dm2/dm2.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
mkdir -p /lib/modules/2.6.24-19-generic/misc
install dm2.ko /lib/modules/2.6.24-19-generic/misc
[/I]
I also write to Jan, but now I ask you to help me.
What I have to do?
Do I need to compile the Kernel?

Thanks and have a nice time!

[COLOR="Red"]Buena vida!!![/COLOR]



[COLOR="Silver"][SIZE="1"]PS
I need to use Mixman DM2 with Mixxx because I want to be a Linux/Ubuntu DJ
I also dream to have a great party in Domodossola (Italy) with all the DJ's that play music with a linux pc (see [www.earthdance.it](www.earthdance.it) for details)
[/SIZE][/COLOR]

---

### Post by openversus on 2008-07-02
Hi ubuntu people!
I'm still tring to play music with ubuntu 8.04, mixxx 1.6.0 and MixMan DM2.
Until now I only see some improvement with the mixxx community help.
So I post it to have any suggestion from you about this problem.
This is the link:
[http://www.mixxx.org/forums/viewtopic.php?f=3&t=123](http://www.mixxx.org/forums/viewtopic.php?f=3&t=123)

:guitar:

Thank you

Buena vida!

---

### Post by openversus on 2008-07-12
The problem I had is now solved.
I play music with mixxx, mixman dm2 and ubuntu studio 8.04.
See the solution here:
[http://www.mixxx.org/forums/viewtopic.php?f=3&t=123&p=449#p449](http://www.mixxx.org/forums/viewtopic.php?f=3&t=123&p=449#p449)

Buena vida!

---

