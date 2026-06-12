---
title: "Reccomend a tuner card?"
date: 2011-01-27
forum: Mythbuntu
---

### Post by Sctmon on 2011-01-27
I current have a Nova T500 dual dvb-t card which is causing me a lot of problems with 1 or both tuners constantly locking up. I have tried enabling the LNA and a few other things but have come to the conclusing that I need to replace it.

Can anyone reccomend a good and _reliable_ dual DVB-T card for use in the UK that would be happy with around 60% signal strength?

I have a Pinnacle PCTV dual hybrid proc pci-e from my old Windows days but MythTV does not seem to like it.

After the digital switchover in the UK the broadcast signal strength is going to be increased so perhaps that will cure my NovaT problems.

---

### Post by AlecJ on 2011-01-27
This issue I cured with a cheap signal booster on the coax, right at the back of the PC. Pushed the signal upto about 75-80%.

I don't use DVB-t any more as the picture quality on freesat from the old sky dish is way better, and I get HD now.
I got 4 budget Nova DVB-S cards from ebay, so 8 inputs from a quad LNB.
OK so I don't get Dave anymore??

---

### Post by Sctmon on 2011-01-28
May be a better idea. I already have a mast head amp and any other amplifiers I have used just seem to boost the signal noise.

---

### Post by BicyclerBoy on 2011-01-28
What have you tried with nova 500 ?

There are recommendations to:
disable IR polling (do not use this remote)
enable LNA
set tuner timeouts >150ms
set tuner timeout different on 2 tuners
etc

This tuner card gets very mixed feedback..I think it works great but many people curse them.

Use a UHF only antenna on this card.
All amplifiers decrease signal to noise ratio. Nothing is better than more antenna gain unless you are overloading the input with adjacent channels.

---

### Post by Sctmon on 2011-02-05
Sorry about the delay but I have been away.

I have tried all of your suggestions apart from an antenna amplifier. My antenna has a masthead amp powered by little box that sends it a DC supply. It is split by a 75ohm passive splitter in the attic and then goes to 3 rooms from there.

I do have an active 6 way splitter / amplifier but had avoided using it to try and maintain the 75onh impedance but will give it a go before junking the tuner card. It seems to be crashing every other day now.

I have also tried disabling suspend for USB devices in the kernal which I understand can also cause problems.

---

