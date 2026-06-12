---
title: "Own a Saa7134 DVB-T card - having issues READ ON!"
date: 2010-05-05
forum: Mythbuntu
---

### Post by db260179 on 2010-05-05
Hi Everyone,

I thought I would share this crucial bit of info.

I own several DVB-T PCI cards based on the SAA7134 chipset. HVR-1110, Asus My Cinema and Avermedia Super 007.

I built a pc for my dad using one of these cards. For the life of me I couldnt figure out why the dam cards wouldnt tune or operate in any way once I had setup mythtv!

Looking at the dmesg log, the firmware would always complain - invalid 0 blah blah

Eventually I narrowed the problem down to a setting in the Mythtv Backend setup.

For your card to work you need to turn an option on in the 'Capture Cards'/ recording options section called 'Open DVB card on Demand'

After that you will find the card will function normally.

Since ubuntu has been getting faster at bootup this problem has escalated more and more, it's all down to a timing issue with the mythtv-backend scripts and the udev or upstart loading to quickly. By enabling this option it stops mythtv from interfering with the firmware upload.

Hope this helps!

:p

---

### Post by Iceycabbie on 2010-05-18
Hi

Sounds promising as the simple solution is usually the best.

1 question - did you disable the check box below regarding the EPG & use one of your other cards to gather this data? If you only had one card how would this work (I know that was 2)

I have tried everythng to get this card working including upgrading Kernel & Headers to a PPA version (v2.6.34-rc7-lucid) & am at my wits end - Will be having one last bash this weekend & if this doesn't work you will find my 007 in low orbit as it will fly out the window.

Ian:guitar:

---

