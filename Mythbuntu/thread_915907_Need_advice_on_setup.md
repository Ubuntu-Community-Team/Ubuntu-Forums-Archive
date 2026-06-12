---
title: "Need advice on setup"
date: 2008-09-10
forum: Mythbuntu
---

### Post by zalnn on 2008-09-10
I want a setup so that I can

1. Record SD content off a digital tuner (STB). I need a digital tuner (STB) because of the extra digital content that a analog tuner (STB) can't pickup.

2. To switch channels on the digital tuner (STB), I would like to use firewire (IEEE 1396) instead of irblaster.

3. Record OTA ATSC channels

What tuner(s) would you recommend?

I have Charter Communication and they have a DCT-6200, which might be overkill because I am not interested in HD right now. 

If I was to get the DCT-6200 would I be able to use the firewire interface to change the non-HD channels? 

Will those non-HD channels stream over firewire or will I have to record them via s-video/composite?

---

### Post by zalnn on 2008-09-10
[QUOTE=newlinux]I always think you should set up a thread as there are plenty of people out there more knowledgeable than me that can help, and others can benefit from the help you receive.

First, let me make sure I understand, by digital tuner you mean a digital Set Top Box like the dct-6200 right? A digital tuner is something different, it is a card that can tune digital frequencies from QAM and OTA ATSC.

Assuming you mean STB, you can record all the channels for sure if you get a capture card like the PVR-150 and capture from the STB to the card's composite or S-video inputs. Then you would need a channel changer (firewire or ir blaster will work). All HD channels will be downconverted to SD this way.

Or you can record and change channels directly through firewire. This will record the channels digitally, and pull down full HD. However, what channels your box will allow you to record via firewire is unknown. You would need to check each channel's 5c/CCI setting to see which channels are allowed (this varies widely even within the same cable provider). I believe there is a scanfw tool that can do this for you if you have firewire connected. Search the mythbuntu forums.

Lots of options for recording digital OTA. Do you need a PCI or PCIe card? Not any difference in quality of recording (a little difference in the sensitivity of the tuner) between cards, so I'd get the one you can get for the least that will fit your MOBO/Case. I use Kworld ATSC 110/115s because they were the cheapest, but you can hardly buy them new anymore.[/QUOTE]

Would the I be able to change the non HD channels via firewire?

Does 5c/CCI apply to HD channels or any digital channel?

---

### Post by newlinux on 2008-09-10
Nope, it applies to all firewire. You'll be able to change channels via firewire regardless of the 5c setting. The 5c setting only affects your ability to record via firewire...

---

### Post by zalnn on 2008-09-15
I have been trying to find a tuner that has 
[LIST=1]
[*] PCI
[*] NTSC (ATCS is a plus)
[*] Easily available (NewEgg or other well know hardware vendor)
[*] Has Linux support, ie; works with MythTV
[/LIST]
What I came up with is the **KWORLD PlusTV HD** (aka KWORLD ATSC 120)

Seems like it should work... 
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120)

**Q:** Am I right in thinking that the drivers from LinuxTV is what MythTV needs to control the tuner card?

**Q:** Does anyone have an alternate suggestion?

**Q:** Does anyone have any experience with this card?

---

### Post by newlinux on 2008-09-15
to me that card's drivers don't look like they are ready for primetime - based on that link. They refer to drivers as expiremental and this "Due to a resource conflict in the driver caused by this card's architecture, a reboot is necessary to switch between analog and ATSC modes. The cause of this issue has been located, and work is ongoing to fix it." concerns me. But that last update was from March, so maybe these issues are fixed in the latest drivers.

You are right about the drivers being what Myth (and ubuntu) will need. Support for this card may not be in the kernel modules so you will probably have to download the latest drivers directly from linuxtv.

I have the Kworld 110/115s and use them for NTSC/ATSC/QAM. You'll probably have a hard time finding them now. Maybe you can find the pchdtv 5500 (way overpriced new if you ask me, since I paid <$50 for each of my Kworlds), or the dvico fusion 5s, both of which I have or have used in the past. the pchdtv 5500 can probably still be bought from the manufacturer. For analog NTSC only (and hardware encoding to boot) there is the PVR-150/PVR-500, but I don't know how easy that is to find these days.

I'm sure you probably already looked at:
[http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards)

But many of these are hard to find these days from your regular vendors (new).

---

### Post by zalnn on 2008-09-24
UPDATE: Got a PVR-150 and it seems to be working pretty well. :)

I want to add another card.

Has anyone tried these cards?
[http://www.kworldcomputer.com/product/mpeg2_tv/MCE201/mce-tv201.htm](http://www.kworldcomputer.com/product/mpeg2_tv/MCE201/mce-tv201.htm)
[http://www.kworldcomputer.com/product/mpeg2_tv/002/mce-tv200.htm](http://www.kworldcomputer.com/product/mpeg2_tv/002/mce-tv200.htm)

---

