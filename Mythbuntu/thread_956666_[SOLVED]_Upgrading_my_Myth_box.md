---
title: "[SOLVED] Upgrading my Myth box"
date: 2008-10-23
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-10-23
I'm in the process of updating my mythbox.  I'm just hoping to get some oppinions from everybody.  I want it to be powerful enough to handle just about all the currently available features that Mythbuntu offers.  And the other motivation (which might actually be the primary motivation) is to get away from the ugly Dell case sitting in my entertainment center.

Here's what I have right now.

Dell Dimension 4600
CPU: P4 2.4 ghz
Motherboard: some proprietary motherboard from dell.
RAM: 1GB of DDR
Hard Drive: 2 320GB PATA
Video Card: Nvidia 6200 AGP
Tuner: PCHDTV 5500 PCI
Optical Drive: 16x Dual-layer burner PATA

Here are my requirements:
1. I don't want to get a new video card so the motherboard still needs to have AGP on it.
2. I don't want to get new RAM so the motherboard still needs to have DDR RAM slots.
3. I want at least three PCI slots, 2 slots for two tuners, and one slot for a sound card with optical out.
4. A much more powerful processor than my P4 2.4GHz proc.
5. I don't want to get new hard drives so the motherboard still needs to have two IDE ATA133 channels.  One channel for both my hard drives and one channel for my optical drive.

Here's what I found on NewEgg.com:

Motherboard: 
ASRock 4CoreDual-SATA2 LGA 775 VIA PT880 Pro/PT880 Ultra ATX Intel Motherboard [http://www.newegg.com/Product/Product.aspx?item=N82E16813157115](http://www.newegg.com/Product/Product.aspx?item=N82E16813157115)

CPU:
Intel Pentium E2180 Allendale 2.0GHz 1MB L2 Cache LGA 775 65W Dual-Core Processor [http://www.newegg.com/Product/Product.aspx?Item=N82E16819116052](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116052)

Do you guys think that this motherboard, CPU combination will do what I'm wanting to do?  Can you guys think of a better combination that will satisfy all of my requirements?  I know I'm asking for a lot, I'm just hoping to get some oppinions.

I've already purchased a new case for everything.  I got the Zalman HD-135 case.  So I think I'm good to go in that department.

I've also purchased my second PCHDTV 5500 TV tuner as well.

---

### Post by volkswagner on 2008-10-23
Well it looks like you did your research.  I think that MOBO is the only thing available, with ddr slots and dual/quad core capable.

I know components add up.  It just seems a waste to me.  Why abandon a capable P4, just to salvage a few components?

Without knowing you total home setup, or if you have enough parts to keep the dell running, why not start fresh?  You could use the dell as a master backend keeping the PATA hard disks.  This would reduce the heat and noise in your HTPC.

As you already know, the combination of keeping your ram and 3 pata devices turns out one MOBO choice.  I don't like such a limited selection.  The MOBO you spec'd does not have stellar reviews.  If you drop the ddr and two pata limitaion your choices will expand.  Two gigs of DDR2 ram can be had for 40 bucks.  A SATA burner can be had for under $30.  This leaves the AGP video still holding you back.  Add a PCIe vid card for another $40.  

So the big question.  Will salvaging the Dell components render the machine useless?  If you keep the Dell running you may get $150 bucks for it with a small hard drive.

Getting new ram and a burner, and vid card, you could choose these:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200280+1297219547&Configurator=&Subcategory=280&description=&Ntk=&SpeTabStoreType=&srchInDesc=]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200280+1297219547&Configurator=&Subcategory=280&description=&Ntk=&SpeTabStoreType=&srchInDesc=")

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200022+1297219547+1070921489&Configurator=&Subcategory=22&description=&Ntk=&SpeTabStoreType=&srchInDesc=]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200022+1297219547+1070921489&Configurator=&Subcategory=22&description=&Ntk=&SpeTabStoreType=&srchInDesc=")

Hmm, still limited.  Upgrading really sucks.

Good luck.

---

### Post by ian dobson on 2008-10-24
Hi,

If possible I'd go split Front/Backend. You can optimise the frontend for small and quite while the backend is optimised for disk space.

I can recommend the Intel Pentium E2180, I had one in my frontend and it was more than enough for almost everything (It had problems with HD playback but that wasn't too important). Have a look for a MATX motherboard/2Gb DDR2 Ram and a E2180 or a E5200 (Thats what I now have in my frontend).

Regards
Ian Dobson

---

### Post by newlinux on 2008-10-24
I have an E2180 and HD playback is no problem for me, using Intel GMA3100.

---

### Post by Meph1st0 on 2008-10-25
Those are all very good suggestions.  Thanks everyone.  

I am actually only interested in watching HD channels now since all the SD channels are all "technically" going away.  And believe it or not, I can actually watch HD on my P4 2.4.  

I am interested in the front end/back end setup.  The only problem is I live in an old crappy house and have found that it'll be very difficult to run a wired network.  And I figure it's best to go wired if your going to stream HD content over a network in a frontend/backend setup, right?  And I don't think 802.11n is a very viable option right now in Linux.  Though I guess I could do powerline networking...

Anyway, I gotta admit, despite the good advice about limited future upgrade options, I went ahead and got that cpu and motherboard combo.  I don't plan on using this machine as a gaming machine, or anything other than a Myth box.  And I figure these specs should be all I will ever need in a mythbox.  But then I digress, I did say that I want it to be able to handle all the mythbuntu features, what happens when new features come out that require a more powerful machine?  Oh well, I guess I'm still stuck in the 'ole vicious upgrading cycle.

Thanks again everyone.

---

### Post by ian dobson on 2008-10-25
Hi,

Don't try running your frontend over wireless. If you look through the forum you'll find lots of posts about choppy video with wireless.

I've just setup a small network for a friend and due to his wife we ended up using powerline modems (Ethernet over power cables). After screwing about abit (One PC just didn't want to connect to the network - Turned out that the onboard lan didn't like the driver we used). The performance is actually not that bad, I'm seeing a fairly consistant 55-60Mbs even though they say that the theoretical maximum is 200Mbps.

Regards
Ian Dobson

---

### Post by tgm4883 on 2008-10-25
If you were going for the split frontend/backend setup I suggest looking at the intel atom processors.  superm1 said that his dell mini 9 can run HD just fine.


And a slight correction.  SD isn't going away, analog is.  Digital doesn't mean HD.

---

### Post by newlinux on 2008-10-25
And analog cable may be around a couple more years. Only analog OTA is definitely going away for everyone February, and I echo the skip the wireless for HD comment. Powerline networking is hit or miss, depending on the quality of your wires, what else is connected on the circuit you will be using, and how your house is wired.

---

### Post by ian dobson on 2008-10-25
> **newlinux said:**
> And analog cable may be around a couple more years. Only analog OTA is definitely going away for everyone February, and I echo the skip the wireless for HD comment. Powerline networking is hit or miss, depending on the quality of your wires, what else is connected on the circuit you will be using, and how your house is wired.

Here in switzerland "analog OTA" will be around for a long time (2012 atleast), so with everyone you mean USA?

Regards
Ian Dobson

---

### Post by newlinux on 2008-10-25
> **ian dobson said:**
> Here in switzerland "analog OTA" will be around for a long time (2012 atleast), so with everyone you mean USA?

Regards
Ian Dobson

Yes, I should've been more specific. From what the original poster was referring to I assumed he was talking U.S.

---

