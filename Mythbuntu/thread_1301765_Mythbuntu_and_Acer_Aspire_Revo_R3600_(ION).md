---
title: "Mythbuntu and Acer Aspire Revo R3600 (ION)"
date: 2009-10-26
forum: Mythbuntu
---

### Post by picbits on 2009-10-26
Seriously thinking of using Mythbuntu as a front end for my ageing Myth 0.21 + Ubuntu 8.04 Server setup.

There is currently an Acer Revo R3600 (1GB Ram/160Gb HDD and ION graphics) on its way and I've been looking at options of what to put on it.

So far, Ubuntu (I love Ubuntu) is going on in one form or another and the general recommendation is to put on XBMC (I'm using XBMC on an old Xbox at the moment as a front end for playback).

Anyone tried the R3600 with Mythbuntu ? Does it support the ION graphics chipset in full 1080P ? Any issues I'm going to come up against ?

Will also be putting 9.10 Server on my new HP ML115 when its released along with MythTv 0.22 but thats for another day.

Thanks in advance :)
Dom

---

### Post by fatmonk on 2009-10-27
I can't offer any advice I'm afraid, but hope this bump helps.

I'll be keeping an eye on this thread myself though as I am also intrested in th Revo so would be very interested to see how you get on with it and Mythbuntu.

Cheers,

FM

---

### Post by picbits on 2009-10-27
Well as soon as Ebuyer deliver my R3600 I'll have a play.

I've been using Linux for years but I'm certainly no expert (quite the opposite lol)

I've found some good information online so with that and a bit of luck I should be able to get something cobbled together lol.

I'll update here with my experiences (good or bad)

---

### Post by fatmonk on 2009-10-27
One thing I'd be particularly interested in, which I can't seem to find in any Revo specs, is whether or not the VGA output supports S-Video output. I'd initially want to hook one these up to an old CRT TV which doesn't have HDMI/DVI in so the analogue TV output is a requirement for me at least for now...

Cheers,

FM

---

### Post by Marky Mark on 2009-10-28
Not much help, but I've just bought the Revo 3600 from Ebuyer, 150quid seemed like a good deal.

I did a clean install of KK rc and so far all is well, had to use a cd though as the usb install option had a problem with Ubiquity(?)  I ran the drivers from Nvidia website with no problem, haven't checked the hdmi connection yet.

Anyhoo I put Myth TV on last night but didn't get much time to play, it'll be an ongoing work in progress.  My ultimate plan is to bolt it to the back of a new big telly and use it as a media center and a way of allowing my gf to access Facebook from the living room, freeing up my main pc for me to use again.

Good luck

MyM

ps, Ebuyer delivered Monday, I only ordered Friday on a free delivery, good service.

---

### Post by picbits on 2009-10-28
I ordered £300 worth of stuff from Ebuyer on Friday and its not here yet :( (expected ship date of 29th grrrr)

I've just been playing with ESXi on my new HP ML115G5 server and Mytbuntu 9.10RC installed perfectly and its a great system. Only problem is that it won't allow the passthrough for the TD500 PCI card so thats that plan out of the window :(

Downloading Microsofts Hyper-V 2008 as there are rumours this has PCI passthrough but I'm not holding my breath. It would be rather ironic using a Microsoft product to host a Linux product but if it works ........

Plan C is to use some kind of VM under Ubuntu but I'm in the playing stage at the moment.

Now if only Ebuyer would ship this R3600 I could get on with some more interesting stuff (the wife views the server in the living room next to the telly as not a very exciting development lmao)

---

### Post by Marky Mark on 2009-10-28
I have used VirtualBox with some success, more out of interest than necessity.

---

### Post by picbits on 2009-10-28
Having got ESXi 4.0 up and running with a virtual Mythbuntu 9.10 installed and runing within an hour of unpacking the server, I was reasonably impressed.

Its just a shame it doesn't support PCI Passthrough on this machine or it would have been a more than perfect setup for me.

Now I'm going to have a play with running a VM on Ubuntu which is running under ESXi lmao.

---

### Post by red321 on 2009-10-28
> **fatmonk said:**
> One thing I'd be particularly interested in, which I can't seem to find in any Revo specs, is whether or not the VGA output supports S-Video output. I'd initially want to hook one these up to an old CRT TV which doesn't have HDMI/DVI in so the analogue TV output is a requirement for me at least for now...

Cheers,

FM

In the same boat, although I'm not using a REVO, I am using a VGA to scart cable ( home built) with the right modelines, I have eventually got mythtv working perfectly on my CRT TV. New interlaced settings in Mythtv let you go straight from interlaced content to an interlaced CRT without going through a de-interlace stage, so the picture is as good as a normal set top box

---

### Post by grillmaster on 2009-12-09
Hi
I'm very interested how you managed to run ESXi on the REVO!

Having the following challange at the moment: ESXi tells me I'm having only 3GB instead of 4GB which I can see in the BIOS and also with different tools.
I have tried to flash BIOS and tried it with ESXi3.5,ESXi4.0 without success. When I trie with ESXi update1 it will cause in a error.

Anyone having the same problem?
Thanks

---

### Post by picbits on 2009-12-09
If you read my post again you'll see I was installing ESXi on my HP ML115 G5 server not the Revo.

I wouldn't even contemplate installing ESXi on a Revo - not enough memory, not much processing power and the Revo hardware is probably not supported on ESXi

---

### Post by Entropy512 on 2009-12-09
> **grillmaster said:**
> Hi
I'm very interested how you managed to run ESXi on the REVO!

Having the following challange at the moment: ESXi tells me I'm having only 3GB instead of 4GB which I can see in the BIOS and also with different tools.
I have tried to flash BIOS and tried it with ESXi3.5,ESXi4.0 without success. When I trie with ESXi update1 it will cause in a error.

Anyone having the same problem?
Thanks
Only Atom Z-series chips support Intel VT.  ESXi may require VT.

Only the dual-core Atom 330 has 64-bit support as far as I can tell.  (Although I see conflicting information - some places say no for the 230, others say yes) Based on the pricing discussed, it sounds like you have an Atom 230 based system (The Revo is available with either option).  Only 64-bit systems or systems using Intel PAE can address that much memory.

---

### Post by newlinux on 2009-12-09
If you are using VDPAU you shouldn't have too much problem using mythbuntu with the acer revo 3600 (or even teh 1600 if you add some RAM since VDPAU will need the shared memory). I know a few people using them as pretty nice frontends.

---

### Post by grillmaster on 2009-12-10
I'm running the Atom 330 with 4GB Ram installed...so no problem on the hardware side.
So you are saying I should trie to install mythbuntu and install afterwards ESXi?But does I loose then some RAM capacity?

---

### Post by sinkyboy2000 on 2010-03-03
> **newlinux said:**
> If you are using VDPAU you shouldn't have too much problem using mythbuntu with the acer revo 3600 (or even teh 1600 if you add some RAM since VDPAU will need the shared memory). I know a few people using them as pretty nice frontends.
 
 
Would the 3600 be able to operate as a backend and front end?

---

### Post by ZedThou on 2010-03-03
> **sinkyboy2000 said:**
> Would the 3600 be able to operate as a backend and front end?

I'm using a Zotac IONITX-A system as a combined front and back end. It's working very nicely. Commflagging of two simultaneous HD recordings is nearly real time, for instance.

---

### Post by sinkyboy2000 on 2010-03-03
> **ZedThou said:**
> I'm using a Zotac IONITX-A system as a combined front and back end. It's working very nicely. Commflagging of two simultaneous HD recordings is nearly real time, for instance.

And that's basically what's in the Revo yeah?

Yours is dual core though - is that right?

---

### Post by ZedThou on 2010-03-03
> **sinkyboy2000 said:**
> And that's basically what's in the Revo yeah?

Yours is dual core though - is that right?

Correct. I was under the impression the Revo 3600 was also using an Atom 330 processor. In my case, I'm also overclocking the CPU and IGP a bit, but I don't think that makes too big a difference.

---

### Post by newlinux on 2010-03-03
you can certainly use them as backends, depending on what tuners you want to use (if it will have tuners). The Revo 3600 does have the Atom 330 (dual core). Doing a lot of transcoding might be a little slower...

---

### Post by sinkyboy2000 on 2010-03-04
> **newlinux said:**
> you can certainly use them as backends, depending on what tuners you want to use (if it will have tuners). The Revo 3600 does have the Atom 330 (dual core). Doing a lot of transcoding might be a little slower...
 
It says here that the 3600 has the Atom 230, which I think is single core.  
[http://www.ebuyer.com/product/167153?ref=dotd&hp_deal=10](http://www.ebuyer.com/product/167153?ref=dotd&hp_deal=10)
 
Someone suggested to me that the dual core wouldn't make much difference.
 
Is there any tuners that you would recomend?

---

### Post by newlinux on 2010-03-04
> **sinkyboy2000 said:**
> It says here that the 3600 has the Atom 230, which I think is single core.  
[http://www.ebuyer.com/product/167153?ref=dotd&hp_deal=10](http://www.ebuyer.com/product/167153?ref=dotd&hp_deal=10)
 
Someone suggested to me that the dual core wouldn't make much difference.
 
Is there any tuners that you would recomend?

I think that link is wrong then. Everywhere I've looked at the revo 3600 or 3610 (newegg, amazon, etc.) say it has the Atom 330. That's one of the primary differences from the rEvo 1600. You probably want to be looking at the newer 3610s anyway instead of the 3600 or older 3610. Also, that link says it comes with 1GB of RAM - I'm pretty sure those are the specs for the 1600 (unless they spec them differently in the UK). The 3600 and 3610 have 2GB, and also come with windows 7.

see:
[http://www.engadget.com/2009/09/02/acers-ion-powered-aspire-revo-3600-packs-dual-core-atom-330/](http://www.engadget.com/2009/09/02/acers-ion-powered-aspire-revo-3600-packs-dual-core-atom-330/)

[http://www.amazon.com/Acer-Aspire-R3600-Desktop-LINUX/dp/tech-data/B002POMUUM/ref=de_a_smtd](http://www.amazon.com/Acer-Aspire-R3600-Desktop-LINUX/dp/tech-data/B002POMUUM/ref=de_a_smtd)

or go straight to the source for the info on 3610 (they no longer show the 3600)

[http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68797&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=694780094](http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68797&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=694780094)

Whether dual core makes a difference depends on your use of the machine. It certainly will help multitasking (like multiple commflag jobs if you are using it as a backend or transcoding). The bigger difference is if you are using VDPAU. The 1600 only comes with 1GB of RAM, so you would need to upgrade that (VDPAU will need to use some of the onboard RAM leaving with very little if you are only have 1GB).

I can't recommend a tuner without knowing:
[LIST]
[*]What type of signal you want to tune,
[*]What type of slot (if a an acer revo, I think you stuck with minipci, network and USB)?
[/LIST]

---

### Post by solitaire on 2010-03-04
If you check out the ZOTAC-F it's 330 ION based with a PCI-Ex16 slot as well as a mini pci-e.
I've got one and it's great, perfect playback of 1080p with 25% CPU (25% of 1 hyperthread, not total of all 2CPUs) I've got 4Gb of ram stuffed in it.
I'm just runinng in VGA out not got around (or seen the need) to jump over to HDMI only. But might have to if I ever get a Blu-Ray drive.

Also on a side note the ZOTAC can take a Max of 4Gb and has 2 memory slots, 
But each slot can hold 4Gb each (but if you do that it's dual channel so you only see it as 4Gb total).

---

### Post by sinkyboy2000 on 2010-03-04
> **newlinux said:**
> I think that link is wrong then. Everywhere I've looked at the revo 3600 or 3610 (newegg, amazon, etc.) say it has the Atom 330. That's one of the primary differences from the rEvo 1600. You probably want to be looking at the newer 3610s anyway instead of the 3600 or older 3610. Also, that link says it comes with 1GB of RAM - I'm pretty sure those are the specs for the 1600 (unless they spec them differently in the UK). The 3600 and 3610 have 2GB, and also come with windows 7.
 
see:
[http://www.engadget.com/2009/09/02/acers-ion-powered-aspire-revo-3600-packs-dual-core-atom-330/](http://www.engadget.com/2009/09/02/acers-ion-powered-aspire-revo-3600-packs-dual-core-atom-330/)
 
[http://www.amazon.com/Acer-Aspire-R3600-Desktop-LINUX/dp/tech-data/B002POMUUM/ref=de_a_smtd](http://www.amazon.com/Acer-Aspire-R3600-Desktop-LINUX/dp/tech-data/B002POMUUM/ref=de_a_smtd)
 
or go straight to the source for the info on 3610 (they no longer show the 3600)
 
[http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68797&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=694780094](http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68797&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=450&ctx1.att21k=1&CRC=694780094)
 
Whether dual core makes a difference depends on your use of the machine. It certainly will help multitasking (like multiple commflag jobs if you are using it as a backend or transcoding). The bigger difference is if you are using VDPAU. The 1600 only comes with 1GB of RAM, so you would need to upgrade that (VDPAU will need to use some of the onboard RAM leaving with very little if you are only have 1GB).
 
 

I can't recommend a tuner without knowing:
[LIST]
[*]What type of signal you want to tune,
[*]What type of slot (if a an acer revo, I think you stuck with minipci, network and USB)?
[/LIST]
 
Seems the british version might be different:-
 
[http://www.amazon.co.uk/Acer-Aspire-R3600-Desktop-Premium/dp/B0028QSIY4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1267725390&sr=8-2](http://www.amazon.co.uk/Acer-Aspire-R3600-Desktop-Premium/dp/B0028QSIY4/ref=sr_1_2?ie=UTF8&s=electronics&qid=1267725390&sr=8-2)
 
I bought this and it's just arrived. I'll be disapointed if I can't use it as a backend and frontend (even with a single tuner would be fine). 
 
The type of signal I'd like to tune is UK domestic terestrial television (DVB I think it is?)
 
In the Revo, I think it would have to be USB.

---

### Post by newlinux on 2010-03-04
Well learn something new everyday - the british version just appears to be different then. But it least it has 2GB of RAM - which will make it sufficient with VDPAU. The 230 is probably fine.

I living in the US, I don't have any experience with DVB-T, which is what I think you probably have. I wonder if network tuners (like the hdhomerun for US QAM signals) exist for the signal you are looking for. You can take a look here [http://www.linuxtv.org/wiki/index.php/DVB-T_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_Devices) for starters.

---

### Post by sinkyboy2000 on 2010-03-05
> **newlinux said:**
> Well learn something new everyday - the british version just appears to be different then. But it least it has 2GB of RAM - which will make it sufficient with VDPAU. The 230 is probably fine.
 
I living in the US, I don't have any experience with DVB-T, which is what I think you probably have. I wonder if network tuners (like the hdhomerun for US QAM signals) exist for the signal you are looking for. You can take a look here [http://www.linuxtv.org/wiki/index.php/DVB-T_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_Devices) for starters.
 
Thanks a lot for the help - really appreciate it.  Think I'll be on here a lot over the next while.  Bit of a noob when it comes to linux.

---

