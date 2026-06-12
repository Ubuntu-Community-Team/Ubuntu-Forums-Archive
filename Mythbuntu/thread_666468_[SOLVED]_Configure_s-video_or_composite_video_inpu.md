---
title: "[SOLVED] Configure s-video or composite video input for myth: Help"
date: 2008-01-13
forum: Mythbuntu
---

### Post by thecoolcat on 2008-01-13
Hello,

I trying to connect my set-top-box composite output to my tv-tuner card (kworld atsc 115). I got the digital OTA and analog NTSC (through coax) working. When I try to use composite or s-video as the source, mythtv is giving me an option to scan for channels. Why should it scan? Aren't these raw video outputs from the STB? How do I tell mythtv that it is raw input to the tuner card? Thanks.

---

### Post by rusty0101 on 2008-01-13
You should not need to scan for channels, even if it offers you that option. When you associate a programming source to the interface/input, it should build the channel map for you. You may have to find some way of confirming that the mythtv box can change channels on the stb, via a serial link, firewire, or an ir-blaster of some sort, but I think that's handled separately.

Not sure if that's of help to you. Hopefully someone with more experience can comment as wel.

---

### Post by thecoolcat on 2008-01-26
Oops. I forgot to respond. You are right: even though there is an option to scan in S-video or composite inputs, I should just ignore it.

While watching TV, I should just hit a "C" and to change inputs from coax to composite, etc. This issue is solved.

---

