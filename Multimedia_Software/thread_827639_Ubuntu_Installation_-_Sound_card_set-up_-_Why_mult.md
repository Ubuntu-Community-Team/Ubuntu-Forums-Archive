---
title: "Ubuntu Installation - Sound card set-up - Why multiple cards?"
date: 2008-06-13
forum: Multimedia Software
---

### Post by Barking_Mad on 2008-06-13
Hi all,

Ive recently been through a few Ubuntu installations from scratch, on Hardy from 8.04 disk. Each time i run through the process its relatively straightforward with the exception of a few things, namely sound setup.

In order to get it working from the get-go i have to modify some things as recommended in the extensive sound setup & troubleshooting thread.

This was primarily due to my rig having two soundcards (as many do), the **onboard** card and the **PCI Audigy** card. I had to modify some config files to put the desired card as the primary or default soundcard.

If i compare this to a windows setup, Windows ***doesnt*** detect my onboard sound, it just sets up the audigy card from the beginning without trouble.

With Ubuntu/Linux regardless of the BIOS status (enable/disable) of the onboard sound, it attempts to configure it (which is where a streamlined setup becomes an annoyance).

So i have Onboard sound (BIOS **disabled**) and PCI sound yet Ubuntu tries to configure both, and erroneously sets the Onboard as priority.

Its no big deal for me, easy fix. But i wonder why it doesn't recognize that the onboard is not wanted (disabled) and just ignore it, i dont know enough about the Architecture to understand this, anyone want to enlighten me?

---

