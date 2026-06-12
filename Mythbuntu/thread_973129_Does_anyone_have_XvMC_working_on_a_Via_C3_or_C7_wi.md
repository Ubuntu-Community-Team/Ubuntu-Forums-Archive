---
title: "Does anyone have XvMC working on a Via C3 or C7 with Mythbuntu 8.04 or 8.10?"
date: 2008-11-06
forum: Mythbuntu
---

### Post by andyfromtucson on 2008-11-06
I have not been able to get XvMC to work on my Via Epia SP8000e (C3 processor) using Mythbuntu 8.04 or 8.10 with Openchrome driver, and no amount of fiddling with settings or googling has turned up a solution.  Does anyone out there have a recent version of Mythbuntu successfully using XvMC for playback on any Via motherboard?

---

### Post by SiHa on 2008-11-06
Nope - I gave up after about three weeks, got rid of the Mini-ITX system, and bought an old P4 2GHz off ebay for £10. Never looked back.
Bit hungrier on the power, but still uses less than 60w.

---

### Post by freymann on 2008-11-06
I don't know if that processor in particular suffers from problems, but you can refer to this page for more help:

[http://parker1.co.uk/epia_ubuntu.php](http://parker1.co.uk/epia_ubuntu.php)

I used some of their suggestions when I set up a couple of my Via boxes.

---

### Post by ozybushwalker on 2008-11-07
I had Mythbuntu 7.10 working on two separate motherboards, one with a 800MHz VIA C3 CPU and the other a 1GHz VIA C3 CPU.

Mythbuntu 8.04 was built for a CPU with a CMOV instruction. Once I found that out (after many hours on trying to figure out why it wouldn't work) I gave up trying to get Mythbuntu working on the 800MHz C3 because my 800MHz VIA C3 doesn't have a CMOV. 

My 1GHz VIA C3 does have a CMOV instruction. Despite spending many hours trying to figure out why Mythbuntu 8.04 hung a long way into startup on the 1GHz VIA C3 I couldn't find a solution and gave up. I tried KnoppMyth and that at least started up but then got into problems and wasn't able to get any help in the forums so I gave up on that as well.

When Mythbuntu 8.10 alpha 6 came out I thought I would have one last go trying to get it working on the VIA 1GHz C3, and to my pleasant surprise it all worked straight away though I did have to fiddle a little bit to invoke the VIA XvMC decoder. I then installed the official release of 8.10 and again had to fiddle a little bit to invoke the VIA XvMC decoder but it now works fine. I haven't tried a lot of the 'extras', only live digital TV.

Both the VIA CPUs are on mini-ITX motherboards with CLE-266 chipsets and 512MB RAM. The motherboards appear to have been made by Gigabyte (GA-PCV2 marked on them) but on startup announce themselves as Idot.

---

### Post by andyfromtucson on 2008-11-07
> **ozybushwalker said:**
> 
When Mythbuntu 8.10 alpha 6 came out I thought I would have one last go trying to get it working on the VIA 1GHz C3, and to my pleasant surprise it all worked straight away though I did have to fiddle a little bit to invoke the VIA XvMC decoder. I then installed the official release of 8.10 and again had to fiddle a little bit to invoke the VIA XvMC decoder

So it sounds like getting XvMC working with a C3 should be possible since you got it to work.  Could you please describe what kind of fiddling you did to get the XvMC decoder to work? That is what I am having trouble with.

---

### Post by ozybushwalker on 2008-11-08
I presume you have Mythfrontend running.

Here's what I did (as best I remember) on Mythbuntu 8.10. From the main Mythfrontend menu select *Utilities/Setup* then *Setup* then *TV Settings* then *Playback*. That should get you to the *General Playback (1/9*) screen. Go on to the *Playback Profiles (3/9)* screen. There change *Current Video Playback Profile* to *CPU--* then select *Edit* of the first rule which probably reads something like *if rez <= 720 576 & > 0 0 -> * (my national TV standard is PAL, if yours is NTSC the numbers may be different) and change the decoder to *VIA XvMC* and its done.

I don't recall having to change video driver.

---

### Post by ozybushwalker on 2008-11-08
The Epia SP8000 apparently has a CN400 chipset. The OpenChrome website ([http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats")) says of the CN400: >  ... The mpeg2 decoder of CN400 / PM800 is capable of decoding HDTV. However, none of the developers have had any decent HDTV output devices (or sources for that matter) to test the implementation. There are reports that HDTV stutters when subtitles are used, but we have been unable to verify this. ...

If you are working with Digital TV it may be best to try watching standard definition broadcasts first before attempting to watch attempting high definition broadcasts.

---

