---
title: "Atom 1 vs 2 cores. memory,  &amp; optimal install path (Backend Only)"
date: 2009-04-25
forum: Mythbuntu
---

### Post by hillcountry on 2009-04-25
1. Will a system running mythbuntu backend (only), mythweb, and samba benefit from the 2nd core of an Atom 320 (vs an Atom 220).

2. Would such a setup gain anything from 4gb of memory vs 1gb or 2gb of memory?

3. Are there any atom improvements to be gained by installing "ubuntu" and then mythtv vs installing mythbuntu directly?

Background situation is that my current Via C7 (1 gb ram) backend runs flawlessly, with the exception that mythweb is pretty slow, but the motherboard is no longer booting without user intervention. Hard drive is also making some bad clicking sounds. Ugh.

The only reason I don't "just" get the dual core ($10 more) and 4gb is that I'm in Texas but don't have air conditioning - so if it's not going to provide a benefit it's less heat for me to blow out.

Other hardware is a Hauppage 150 and a Haupauge 500.

First post; hope I did this right. Please feel free to address only 1 of the above if you know. Thanks for any help!

---

### Post by ian dobson on 2009-04-25
Hi,

Being a multi processor capable operating system linux can make use of extra CPU's, and as there are quite afew processes that can run in parallel on a mythtv system it would make sense to go dual core (Myth-backend, Mysql, Apache, commflagging, epg download).

The system would run with a single core cpu but it'll run better with a dual core. Atoms don't produce all that much heat so not having an air conditioning shouldn't make a big difference.

I would recommend installing Mythbuntu rather than ubuntu + mythtv, my backend server runs ubuntu with mythtv as packages and it was a real pain to setup (dependances). My frontend runs Mythbuntu and the setup there was just boot CD, follow instructions.

1Gb ram is enough for a system, but if you could install 2Gb you'll be on the safe side.

Do atom boards actually have 2 PCI slots free for you tuners? Most of the boards I've seen only have one.

Regards
Ian Dobson

---

### Post by hillcountry on 2009-04-25
> **ian dobson said:**
> there are quite afew processes that can run in parallel on a mythtv system it would make sense to go dual core

Thank you. That's exactly what I needed to know. 

I'll order the dual core as it sounds like double the heat (16 watts vs 8 watts) would be worthwhile and not just wasted.

> **ian dobson said:**
> I would recommend installing Mythbuntu rather than ubuntu + mythtv

Thanks. In 2007 when I did my ubuntu + mythpvr install the mythbuntu liveboot cd wouldn't even boot on my C7. It's really remarkable what the community has come up with.

I've read that there were some Atom enhancements in the Ubuntu and netbuntu updates, but haven't found out if they've been included in Mythbuntu (yet).

> **ian dobson said:**
> 1Gb ram is enough for a system, but if you could install 2Gb you'll be on the safe side.

The motherboards I'm looking at supports up to 4Gb with 2 slots. I assume going from 2Gb to 4Gb would help with the samba and file caches, but am wondering if there would be any other benefits to offset the additional heat generated. Texas is truly hot without AC. Ugh.

> **ian dobson said:**
>  Do atom boards actually have 2 PCI slots free for you tuners? Most of the boards I've seen only have one.

Yes. The two boards I'm considering have two PCI plus one PCIe.

[http://www.jetway.com.tw/jw/motherboard_view.asp?productid=349&proname=ATOM-GM1-230#](http://www.jetway.com.tw/jw/motherboard_view.asp?productid=349&proname=ATOM-GM1-230#) for the single core.

[http://www.jetway.com.tw/jw/motherboard_view.asp?productid=349&proname=ATOM-GM1-330#](http://www.jetway.com.tw/jw/motherboard_view.asp?productid=349&proname=ATOM-GM1-330#) for the dual core.

This may be a different thread, but now that I've decided on which motherboard, can anyone point me towards a step-by-step for upgrading to another mythpvr version? 

My current install was in 2007 (Ubuntu 7.10 + mythpvr 0.20.2-0ubuntu10) and I've never dared to upgrade. My principal concern is transferring all my recorded episode information over. Any tips beyond mythconverg_backup.pl and mythconverg_restore.pl?

Thank you so much for your response. It's a great community.

---

