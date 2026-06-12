---
title: "Excitable Dos files"
date: 2024-08-06
forum: Multimedia Software
---

### Post by angel mike on 2024-08-06
Does anyone know if it's possible to run an excitable DOS file with Ubuntu?

---

### Post by The Cog on 2024-08-06
There is an application called dosbox that can run DOS programs. I don't know how good its multimedia support is, but I think it can emulate something like a soundblaster for games.

---

### Post by angel mike on 2024-08-06
Thanks 'The Cog' will investigate.

---

### Post by Holger_Gehrke on 2024-08-06
'dosbox' is an absolute powerhouse if you want to run old games. It emulates Soundblaster (1,2,pro,pro2,16,GameBlaster), Gravis Ultrasound, and can pass MIDI data to a running MIDI software synthesizer. It can emulate various graphics cards up to SVGA and there are forks / variants of dosbox which also emulate a 3dfx card. The problem is that it also emulates the processor, so on a 2 Ghz Machine you can expect the speed of about a 25Mhz 386. Also it's support for printing is almost non-existent. Network support is also limited to netware/IPX and there too it's limited to what's needed for games. So if you want or need to run DOS-applications (as opposed to games) you might be better of running FreeDOS in a virtual machine.

Holger

---

### Post by yancek on 2024-08-06
You haven't indicated what type of dos executable you want to run in Ubuntu and for what purpose.   Did you read through the community wiki for Ubuntu on the dosbox software?

[https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)

---

### Post by guiverc on 2024-08-06
> **Holger_Gehrke said:**
> So if you want or need to run DOS-applications (as opposed to games) you might be better of running FreeDOS in a virtual machine.


I use a number of old DOS programs happily in dosbox (inc. some I wrote on OS/2).  I still have a really old DOS machine under the house setup to run specific DOS programs, as well as an old thinkpad which runs the same apps using `dosbox` that I usually use, as the more modern IBM Thinkpad doesn't require me to turn on coax-UTP network convertors.

I have access to my really old files from that era still on network storage; as well as copies of word perfect 5.1, wordstar etc, and can run them on this modern Ubuntu system fine, as long as I remember to start them using WP.EXE for example (ie. almost all files of that era were all uppercase filenames; which matters if starting the programs whilst in a *nix terminal)..   Note: I've never attempted to print anything in them; my usage is really only extracting historical details from them; so I'm usually copying text/data from them & doing processing on native *nix apps.

---

