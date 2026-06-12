---
title: "nVidia PCIe x16 card running at x8"
date: 2012-03-08
forum: Multimedia Software
---

### Post by quequotion on 2012-03-08
If this belongs in the hardware subforum, my apologies.

Since the topic is video hardware, I chose this subforum.

My (nVidia) Leadtek WinFast GT 220 1024MB DDR3 PCIe 2.0 x16 card is running at x8.

I've assembled an FAQ from the stories of a lot of people with this problem scattered about many forums & blogs.

-----------------

**-Check the motherboard:** 
*--What motherboard?*
BIOSTAR TA890FXE

*--How many PCIe x16 slots does it have & how many lanes do they run (max)?*
It has four: slot1 & slot3 are x16, slot2 is x1, and slot4 is x4
[I]
--What slots are your cards in?[/I]
The graphics card is in slot1, the topmost slot. Nothing is in slot2 or slot3. In slot4 I have an Intel 82571EB Dual 1Gb NIC.


**-Check the motherboard manual: **
*--Does your motherboard support SLI or Crossfire?*
It was designed for Crossfire and I believe it may also support SLI. However, I am not attempting to use either feature.

*--Does your motherboard support 2 PCIe x16 slots at x16 & x1, x8 & x8, or x16 & x16?*
According to the manual, it supports two PCIe x16 graphics cards in slot1 & slot3 at x16 & x16

**-Check BIOS:**
*--Is your motherboard bios up-to-date?*
Yes. I recently installed the latest (possibly final) update.

*--Is your graphics card bios up-to-date?*
Unknown. Neither nVidia nor Leadtek has released any official updates for the card.
[I]
--Does your motherboard bios have settings to controll PCIe lanes?[/I]
Yes, however the names of the PCIe slots in bios do not correlate to the names in the manual; instead of "PEX16_1",2,3,4 they are "PCIE 03", 09, 04, and 11.* By default they are all set to "auto".
I tried manually setting slot1 & slot3 to x16 & x16 as well as slot1 to x16 & slot3 to x1; in either case the card still reports x8.

*--Are there other settings that could affect PCIe?*
Very likely. Particularly there is an under/overclocking setting called "GPU Phase Control" but it is inactive by default. There are also ASPM settings for each slot, disabled by default. Unfortunately, very few of the bios features are documented and the descriptions provided in the bios are in cryptic and poor English.
[B]
-Check the card:[/B]
*--Is it seated properly?*
Yes. It is fully in the slot and I carefully cleaned and dusted everything before inserting the card.

*--Tried reseating it anyway?*
Not yet. I should do this anyway, but I don't think this is the issue.

*--Tried another PCIe x16 slot?*
Not yet and not easy to do.

**-Check the drivers:**
*--What drivers?*
The proprietary nvidia drivers, currently 295.20; these drivers do not feature any settings to control PCIe lanes.

*from memory

-----------------

I have heard the performance cost for running an x16 card at x8 is relatively low. 
I have also heard of one user who successfully fixed this, after trying everything else, by copying bios from a card that ran properly at x16 to a card that ran at x8.

---

