---
title: "Double check my planned setup pre-purchase!"
date: 2008-11-08
forum: Mythbuntu
---

### Post by TehTux on 2008-11-08
Hi Everyone,

For years my Media Centre has just been Mint (with auto login) and a wireless mouse driving the whole thing. I had no TV capture card, so I could only play what I manually loaded on there.

I'm now wanting to do it properly.

I'm planning on buying:

Leadtek DTV2000H Hybrid TV Tuner Analog & Digital TV card ([http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=252]("http://www.leadtek.com/eng/tv_tuner/overview.asp?lineid=6&pronameid=252")).

The PC is an AMD Semperon LE-1100 (Single core 1.9Ghz), onboard sound, onboard Nvidia 6100, 1TB of storage (2x500GB SATA drives).

Using Mythbuntu 8.10, should I run into any problems or will it simply be a matter of installing and GUI configuring?

Also, the included remote will work fine within Mythbuntu?

Cheers

---

### Post by TehTux on 2008-11-08
Also, will a 1.9Ghz single core 64bit CPU be enough to watch or record HDTV using a software based TV capture card?

I've read the recommended specs and it says 2Ghz, though a Semperon 1.9Ghz will be fine...right?

(I'm not wanting to watch TV while recording or do anything complicated)

---

### Post by tgm4883 on 2008-11-08
> **TehTux said:**
> Also, will a 1.9Ghz single core 64bit CPU be enough to watch or record HDTV using a software based TV capture card?

I've read the recommended specs and it says 2Ghz, though a Semperon 1.9Ghz will be fine...right?

(I'm not wanting to watch TV while recording or do anything complicated)

Either you mis-read it or there is a typo.  The recommended specs for high definition playback is 3Ghz, so no, a 1.9 Ghz Semperon won't do.

I don't know how well supported the card is, but when talking in terms of digital television (which includes HD), there is no hardware encoder.  The stream comes encoded already.

---

### Post by TehTux on 2008-11-09
> **tgm4883 said:**
> Either you mis-read it or there is a typo.  The recommended specs for high definition playback is 3Ghz, so no, a 1.9 Ghz Semperon won't do.

I don't know how well supported the card is, but when talking in terms of digital television (which includes HD), there is no hardware encoder.  The stream comes encoded already.

No typo - though Ghz is such a funny thing. Is 3Ghz in reference to a Pentium 4, Core 2 Duo or a Core i7?

I'm assuming it's talking about Pentium 4 spec 3Ghz, which I think is FLOPS/MIPS power of a Semperon 1.9Ghz (might not be, I'm just guessing).

Can anyone confirm?

Also, I'm really only after SD quality (my LCD screen isn't True HD, just normal 1366x720).

Has anyone walked this path before? Should I be ok?

---

### Post by ian dobson on 2008-11-09
Hi

My Core2Duo E5200 (2.5GHz) can playback HD programs with about 70-80% load.

The Semperon is a low cost/reduced cache CPU so I don't think it'll be enough for HD. SD doesn't take much CPU if your graphic card supports hardware aceleration (xV). My frontend only uses about 10% CPU for SD playback with a Nvidia 7300LT graphic card.

Regards
Ian Dobson

---

### Post by TehTux on 2008-11-09
> **ian dobson said:**
> Hi

My Core2Duo E5200 (2.5GHz) can playback HD programs with about 70-80% load.

The Semperon is a low cost/reduced cache CPU so I don't think it'll be enough for HD. SD doesn't take much CPU if your graphic card supports hardware aceleration (xV). My frontend only uses about 10% CPU for SD playback with a Nvidia 7300LT graphic card.

Cool - the graphics are just onboard Nvidia 6100 so it may or may not be ok.

It's currently ok playing Xvid and Divx (it's currently running Mint and I've had no problems with any playback, even DVD playback), I'm just hoping that playing SD through the software TV tuner will be ok, and recording will be a bonus if it can cut the mustard.

I'll find out soon enough, I'll be buying the card this week!!

Cheers for the info.

---

### Post by tgm4883 on 2008-11-09
> **TehTux said:**
> No typo - though Ghz is such a funny thing. Is 3Ghz in reference to a Pentium 4, Core 2 Duo or a Core i7?

I'm assuming it's talking about Pentium 4 spec 3Ghz, which I think is FLOPS/MIPS power of a Semperon 1.9Ghz (might not be, I'm just guessing).

Can anyone confirm?

Also, I'm really only after SD quality (my LCD screen isn't True HD, just normal 1366x720).

Has anyone walked this path before? Should I be ok?

IIRC, the Semperon compares more to the Celeron processor than anything else.  So no, a 1.9Ghz will not do HD.  It's enough for SD though.

---

### Post by foxbuntu on 2008-11-11
If you are planning on doing any kind of HD video go dual-core or better or you will not be happy with the quality. If it is going to be a frontend-only system you might be able to get by with a fast (6000+ AMD/P4 3.0GHz) single core proc, if its going to be the master backend and frontend (as many systems start out) you will want dual-core or better.

---

### Post by TehTux on 2008-11-12
> **foxbuntu said:**
> If you are planning on doing any kind of HD video go dual-core or better or you will not be happy with the quality. If it is going to be a frontend-only system you might be able to get by with a fast (6000+ AMD/P4 3.0GHz) single core proc, if its going to be the master backend and frontend (as many systems start out) you will want dual-core or better.

The AMD 6000+ is a dual core - but I know what you're getting at.

I'm only after SD quality, so hopefully I'm ok.

A quick update, the Leadtek DTV2000H has two revisions; Revision I and Revision J.

Revision I is detected without issues. Revision J requires some manual terminal tweaking.

Unfortunately, most DTV2000H's are now Revision J (you can tell without opening the box - if it has a little Vista Compatible notice then it's the newer J). The one I bought was a J, though I'm not too worried about making the required tweaks - so long as they go ok.

---

### Post by TehTux on 2008-11-18
Ok, in the hope that someone else is reading this and is interested in the results:

Installed the DTV2000H Rev. J card into my Semperon (single core) 1.9Ghz machine (2GB ram, 2x500GB HDDs).

As it's been previously written, the Revision J doesn't work out of the box (the Revision I does, but good luck finding one!) though with a few config changes it was working.

I was using Mythbuntu 8.10 64bit (Desktop version) and though I was getting a bit confused as to what to do and what to set up, I eventually got HD TV working as well as my video collection.

There's still much I want to do (the remote isn't 100% working, MythGame has to be setup and I want an easy shutdown) but on the whole it's going great.

Hopefully by 9.04 my revision J card can be auto detected, so it will make reinstalls (and upgrades!) that little bit easier.

Oh, my 1.9Ghz CPU plays HDTV fine without any issues, though I do detect slight pausing every now and then - not enough to give me any concerns though the next MythTV setup I do will definitely have a dual core CPU that's around the 2.5Ghz mark so I can record TV while watching pre-recorded TV or DVDs.

Cheers

---

