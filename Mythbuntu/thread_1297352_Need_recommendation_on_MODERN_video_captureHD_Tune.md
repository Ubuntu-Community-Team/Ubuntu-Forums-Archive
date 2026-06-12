---
title: "Need recommendation on MODERN video capture/HD Tuner cards"
date: 2009-10-21
forum: Mythbuntu
---

### Post by Dougga on 2009-10-21
I've been looking at the MythTV product for quite a while and have always noted that people dance around recommendations for tuner/capture cards.  After reading a few dozen posts on the subject I can devine that Hauppauge is better supported than the other vendors.

My problem is, it seems that people have had success with outdated Hauppague cards but it seems very little with modern cards.  Is MythTV only going to work on the cards that Hauppauge no longer sells?

The current lineup is as follows:
WinTV-HVR-1250 PCI Express TV hybrid tuner
WinTV-HVR-1600 high performance PCI TV combo tuner
WinTV-HVR-1850 high performance PCI Express TV combo tuner
WinTV-HVR-2250 Dual Tuner PCI Express combo TV tuners

Will MythBuntu support any of these cards (without rebuilding the kernel and other such tasks)

Thanks for the help.

---

### Post by williammanda on 2009-10-21
You first need to review the linuxtv site. This will tell you if the card is supported and what kernel revision.

[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

---

### Post by Dougga on 2009-10-21
This site is an encyclopedic collection of everything relevant to television and linux.  I will make yet another attempt to navigate it to find specific references to this card.  I'll reply back with specific links to a subsection that might have been helpful.  Thanks.

---

### Post by Dougga on 2009-10-21
The site is a disorganize jumble of links but this is what I could find:

1) The list of chipset vendors ([http://www.linuxtv.org/wiki/index.php/List_of_Chipset_Vendors](http://www.linuxtv.org/wiki/index.php/List_of_Chipset_Vendors)) it claims that they have a demodulator but no tuner.  This is not accurate.  They have HDTV tuners on board.

2)I found a page for ATI/AMD cards here: 
[http://www.linuxtv.org/wiki/index.php/ATI/AMD#ATI_Graphic_cards_with_TV_Tuners_and.2For_Capture_facilities](http://www.linuxtv.org/wiki/index.php/ATI/AMD#ATI_Graphic_cards_with_TV_Tuners_and.2For_Capture_facilities)
Under "Notable IC's" is lists the one in this card, the "Theater 600 Pro"


3) Here we go..
Card Model               Standard     Interface  Supported
TV Wonder 600 PCI 	   ATSC 	 PCI 	 &#10008; No

I'm out of luck.

Thanks for the tip. Despite the bad new, you saved me some time.

---

### Post by williammanda on 2009-10-21
I believe this link gives you all the info you need on your cards.

[http://www.linuxtv.org/wiki/index.php/Hauppauge]("http://www.linuxtv.org/wiki/index.php/Hauppauge")

Its located at the top right of the page: Sortable List of Device Vendors > Hauppauge.

---

### Post by the_pod on 2009-10-22
I've got the 1250 and it works well.  Definitely picks up signal better than my 1600 (kicking myself for that purchase) as the 1600 doesn't p/u a signal for ABC but the 1250 does.

I use it exclusively for QAM 256 so any other uses I can't speak to.  I believe I did end up having to do a V4L update but there's a pretty simple "how-to" floating around on this board somewhere.

Hope that helps.

ETA - Don't buy the 1600 as I've found it's ability to p/u signals to be flakey, although I have no idea why. (Others have voiced this elsewhere...)

---

### Post by bsntech on 2009-10-22
I have the HVR-1600 and am quite pleased with it, actually.  It picked up all of the same channels that my HDTV did with great quality.  I did have one problem where one station had some audio cutting in and out constantly.  After checking the box in Myth to use extra sound buffering, this problem went away.

The HVR-1600 was my choice because I am transitioning from basic cable to OTA antenna TV.  So it has both the Analog and Digital side that can record simultaneously.

I purchased an HVR-1250 on eBay last week and it just arrived at my door today per the USPS tracking site.  I'll be installing that tonight and see if it really is any better than the HVR-1600.

Otherwise, the picture quality of the HVR-1600 is by far superior than the old PVR-150 that I was trying to decommission - but can't now since the HVR-1600 transmitter isn't detected in Ubuntu 9.10.  I even upgraded the drivers today for the v4l-dvb stuff using mercurial per someone's response on my bug report I have in on this issue - but it still isn't working.

But, I would fully recommend the HVR-1600 because in the way of analog/digital TV, you can record simultaneously on both inputs and it is plug-n-play with MythTV without any additional loading of drivers or anything (except the remote part).

---

### Post by bsntech on 2009-10-22
For what its worth, I installed the HVR-1250 in the PC today.  The HVR-1250 will install in either a PCIe x 1 or a PCIe x 16 slot.

I just went into the MythTV backend, went to Capture cards, added it as a DVB, and poof, it worked!

I ran a splitter from the incoming OTA coax cable to split it between the HVR-1600 and HVR-1250.

I actually think that the quality of the HVR-1600 surpasses the HVR-1250.  While the HVR-1250 card is at least half the size of the HVR-1600, the quality of the sound on the HVR-1600 seems to be better.  Within MythTV, I changed the input quickly between the two on the same channel and it seemed the HVR-1600 had a more defined surround sound to it with better spacial sound.  In the way of the image quality, it seemed to be about identical.

---

