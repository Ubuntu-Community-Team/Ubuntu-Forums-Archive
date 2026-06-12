---
title: "How Do I Get a  Leadtek Winfast 2000XP Expert Card to work in Ubuntu?"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by Banny706 on 2007-05-08
Hi folks,  Got a  Leadtek Winfast 2000XP Expert Tuner card and have no idea on how to enable it.  Basically, I want to use it to capture all my analog video from a VCR or camcorder so I can put them on DVD.  Don't really care about the TV part.   I looked around and checked out bttv but it is all gobledy-gook to me.  I do an[COLOR="Red"] lspci [/COLOR] and get:

01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

[COLOR="Red"]lspci -vv[/COLOR] gives me:

01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

[COLOR="Red"]lspci -n[/COLOR] gives me:

01:08.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

Need help in a big way.  Need to be taken by the hand.  Don't know how to enable bttv.  Ubuntu Rocks:guitar:

---

### Post by teet on 2007-05-24
I realize this is a couple of weeks late, but you may want to check out my guide.  Note that it was written for a leadtek winfast tv 2000 xp RM (not expert) so your "card=" and "tuner=" values may differ.  Also, I did try this part of my guide on Feisty Fawn 7.04 and it still works.  

[http://web.missouri.edu/~datcnc/htpc_single.html#htpc2](http://web.missouri.edu/~datcnc/htpc_single.html#htpc2)

-teet

---

### Post by beefbowel on 2007-11-11
the expert card is not bttv.  how do you do the thing that you do with an expert cx88? thing?

---

