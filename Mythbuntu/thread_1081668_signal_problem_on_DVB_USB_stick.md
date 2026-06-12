---
title: "signal problem on DVB USB stick"
date: 2009-02-26
forum: Mythbuntu
---

### Post by Harani on 2009-02-26
I have a really odd problem with signal strength on a DVD USB stick i am
running

My setup is running Mythbuntu 8.10 and i have 2 usb Freeview sticks plugged
into it. One Haupphauge WinTV Nova-T and a SEAL DVB

The two are fed by an antenna splitter from an outside aerial

I  used to run this exact same hardware set up running the latest version of MythTV on Ubuntu 8.10
If i had the antenna plugged directly into either DVB stick i got 70% signal strength and with the splitter in place and both sticks running i got around 66-67% on each and good steady pictures with no breakups.

Since switching to Mythbuntu I am getting  67% on the SEAL DVB but only 26%
on the Haupphauge DVB which is so borderline the picture keeps breaking up.

At first i thought the splitter had developed a fault either one lead was
faulty or there was interference from one output to the other.  But that
turned out not to be the case. I tried both outputs individually in both
sticks with the other disconnected and tried both outputs together but
reversed. The result were always the same
S-DVB 67%
H-DVB 26%

Then i thought maybe the H-DVB had gone faulty so i tried the antenna in
both sticks one at a time without the splitter
both were 70%. Same as they used to be on my old system.

This has got me stumped. Both use the DiBCOM7000 firmware  why should the
H-DVB work ok on the antenna but drop to an unusable level with the splitter in but the S-DBV does not ?

and why do they both work fine on my old system which is based on the same underlying version of Ubuntu

---

### Post by ian dobson on 2009-02-27
Hi,

I can't imagine that thats a software problem. Mythbuntu is Ubuntu with a modified installer and afew extra packages.

I would first try swapping your hardware around abit (Only 1 tuner, swap tuner wiring around etc.)

I don't know your hardware but maybe check if there's an option to enable an amplifier on one/both tuners.

Regards
Ian Dobson

---

