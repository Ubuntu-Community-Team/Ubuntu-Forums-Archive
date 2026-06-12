---
title: "ATI All-In-Wonder AIW getting it to work"
date: 2009-05-27
forum: Multimedia Software
---

### Post by nanogeek on 2009-05-27
Hi,

I am trying to salvage a *very old* (circa 2000) ATI All-In-Wonder (AIW) video capture card.
My primary goal is using it to digitize my old VHS tapes.
I am running 8.10 (Intrepid ) on a Pentium III (Coppermine) with on board VGA adaptor.
Getting TV input and Video output from the ATI card may be secondary goals.

I installed the card in an empty PCI slot
When I pulg my monitor into the VGA out of the card I get a black screen
this is not critical but it might be nice to get the monitor video from the card.

When I run lshw I get the following
[INDENT] *-display UNCLAIMED
                [INDENT]description: VGA compatible controller
                product: 3D Rage Pro
                vendor: ATI Technologies Inc
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 5c
                width: 32 bits
                clock: 33MHz
                configuration: latency=32 mingnt=8[/INDENT]
[/INDENT]
So I assume the card is properly recognized

I installed GATOS using Synaptic
When I run  xatitv  or  atitv --version I get:

[INDENT]GATOS: gatos_inita()
GATOS:  ati_inita(): No such device or address
GATOS: ati_inita failed: No such device or address
GATOS: gatos_inita(): No such device or address
xatitv: gatos_init(): No such device or address
[/INDENT]
I assume I am missing something very basic here.
What do I need to do to get the card running and use it for video capture?

Thanks 
Nanogeek

---

### Post by maphew on 2010-04-08
there is another program in gatos called 'gatos-conf' which sets up, I think, the appropriate Xserver settings. You may need to do that first.

I have the same aim, to capture old vhs tapes, but am using a Radeon 7200 card and ubuntu 9.10. So far no luck enabling the tv-in/out parts of the card, though it works fine for regular computer use. Gatos-conf doesn't work on 9.10 - [https://bugs.launchpad.net/ubuntu/+source/gatos/+bug/557836](https://bugs.launchpad.net/ubuntu/+source/gatos/+bug/557836)

---

