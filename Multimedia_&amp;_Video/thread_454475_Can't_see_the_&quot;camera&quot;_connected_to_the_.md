---
title: "Can't see the &quot;camera&quot; connected to the FireWire"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by mac.ryan on 2007-05-25
I am trying to enable my Feisty 32bit to capture video.

Actually, I am trying to capture my old VHS with a analog-digital converter that is reported to work under GNU/linux: Canopus ADVC-55.

I bought a PCI firewire card (Hamlet Firewire 400 PCI) and from the output of **testlibraw**, I got the impression the card works correctly:

```
successfully got handle
current generation number: 1
1 card(s) found
  nodes on bus:  0, card name: ohci1394
using first card found: 0 nodes on bus, local ID is 0, IRM is 0

doing transactions with custom tag handler

using standard tag handler and synchronous calls

testing FCP monitoring on local node
got fcp command from node 0 of 8 bytes: 01 23 45 67 89 ab cd ef
got fcp response from node 0 of 8 bytes: 01 23 45 67 89 ab cd ef
testing config rom stuff
get_config_rom returned 0, romsize 120, rom_version 3
here are the first 10 quadlets:
0. quadlet: 0x1ca80404
1. quadlet: 0x34393331
2. quadlet: 0x37f264e0
3. quadlet: 0xffffffff
4. quadlet: 0xffffffff
5. quadlet: 0x1f360400
6. quadlet: 0xffffff03
7. quadlet: 0x03000081
8. quadlet: 0x090000d1
9. quadlet: 0xc083000c
update_config_rom returned 0

polling for leftover messages

```Now, I have tried to use kino (v.0.92, standard ubuntu repo at the moment of writing), but I got persistent error messages about modules not loaded and wrong rw permissions. I tried all the available tricks I found, but - even if **lsmod** report all the modules I need correctly running and **ls -l** shows that I have all the rw permissions I need on the devices... it still doesn't work.

So, I decided to download the latest version of kino (v.1.0) and - following the README instruction - I ran (as a test) **dvgrab**, but all I obtained is:

```
Error: no camera exists
```I am now stuck on this and in search for help. I don't have another computer with powered firewire, nor I have other firewire devices, so I can't check neither the device on another computer, nor the firewire card with another device.

Any help / suggestion is welcome.

Many thanks in advance!

---

### Post by mac.ryan on 2007-05-28
Bump... anybody having a clue?

---

### Post by mac.ryan on 2007-05-29
Just in case I am not the only unlucky one: it looks like the problem is linked to the FireWire card. [Here]("http://ubuntuforums.org/showthread.php?p=2745134") a new thread dealing specifically with the problem.

---

### Post by carlosponti on 2007-05-30
i get the same problem and so far no one is able to help. I try captureing from a Canon Zr200 DV camera into Kino and get the same no camera exists error havent tried testlibraw though.

---

### Post by leo1981 on 2008-07-16
Hi,
I'd like to buy a PCI-Firewire card.
I found an online shop that states the the Hamlet is compatible with Linux.
Have you tested you card with newer Ubuntu release?

---

