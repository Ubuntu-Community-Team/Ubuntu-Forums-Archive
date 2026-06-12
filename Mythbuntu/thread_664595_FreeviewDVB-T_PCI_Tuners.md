---
title: "Freeview/DVB-T PCI Tuners?"
date: 2008-01-11
forum: Mythbuntu
---

### Post by wikrok on 2008-01-11
I'm thinking about building a HTPC and I've spent most of this afternoon looking at tuner cards, but I can't seem to find a card that does what I want and is supported under linux. I've had a look at [http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards), and still can't find a PCI tuner which is DVB-T and has hardware encoding. The Nova-T 500 looked perfect, until I read that the latest version of it isn't working. I expect I've probably missed something obvious...

Anyway, if anybody has any suggests they'd be much appreciated.

Cheers,
Phil

---

### Post by ozybushwalker on 2008-01-11
But what do you want the card to do?

I've had good experience with the Leadtek Winfast DTV1000T but I'm not interested in analogue broadcast TV. The remote for this card doesn't work but I've seen a solution posted and I'm looking into it.

---

### Post by wikrok on 2008-01-12
> **ozybushwalker said:**
> But what do you want the card to do?


Ideally I'd like it to be able to record Freeview stuff in MythTV without eating up CPU. The Leadtek DTV1000T/DTV2000H's look nice, but as far as I can tell they don't have the hardware encoder? 

Thanks,
Phil

---

### Post by ozybushwalker on 2008-01-12
My understanding is that DVB broadcasts the video stream already encoded as MPEG2. If thats so, then there is no need for an MPEG2 encoder. (Hardware MPEG2 encoder could be useful though for analogue transmission or capture of analogue signals from, say, a VCR.)

However, having a video card that supports MPEG2 decoding allows a lower power CPU to be used since the CPU doesn't need to decode the MPEG2 for display.

I'm running MythTV on a GA-PCV2 motherboard with 512MB and a Leadtek DTV1000T tuner card. The CPU on this motherboard is a 1GHz VIA C3 which is no speed demon (in many applications probably slower than a 800MHz PIII). The "video card" is an integrated CLE-266 with hardware MPEG-2 decode. I'm still exploring the capabilities of this system, after some tweaking, it successfully displays standard definition live TV. I haven't looked at recorded programs yet, but I believe I sucessfully recorded a show while watching it.

[http://www.mythtv.org/docs/mythtv-HOWTO-3.html]("http://www.mythtv.org/docs/mythtv-HOWTO-3.html")
might be useful reading through its more oriented to analogue capture rather than digital.

---

### Post by twin_57103 on 2008-01-12
I just went through this.  Here are a couple links that may help:
[http://ubuntuforums.org/showthread.php?t=655848]("http://ubuntuforums.org/showthread.php?t=655848")

[http://ubuntuforums.org/showthread.php?t=651745]("http://ubuntuforums.org/showthread.php?t=651745")

Be sure to check the MythTV web site (top link) - they have a more current list.  I just finished repairing the ethernet on my own computer and will be updating the top thread once I find out how it goes.

---

