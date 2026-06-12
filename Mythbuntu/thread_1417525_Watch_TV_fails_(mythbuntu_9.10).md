---
title: "Watch TV fails (mythbuntu 9.10)"
date: 2010-02-27
forum: Mythbuntu
---

### Post by felix.okeefe on 2010-02-27
Fresh install of Mybuntu 9.10
Having endless trouble getting my tv cards to work
have 2 x Saa7134 based compro DVB-T300 cards. They are hybrid DVB-T / analog cards.
I only want to use the analog tuners as have no unencrypted DVB-T signal here in The Netherlands.

Successfully set up xmltv grabber for the netherlands.
Analog tv viewable in TV Time and XawTV. Although so far no sound without linking the cards line out to the line in of the sound card. Less than ideal..

Can not scan for channels in mythTV backend setup so have manually entered the channel details with frequencies eg: 175.250

I wasn't sure if there is any specific syntax necessary when entering freqency instead of channel for tuning. The problem i have with channels is that every analog tv viewing program seems to use different channel designations. The application bundled with the cards under windows uses totally different channels than tv time. XawTV and TV Time use different channel designations also. strange.

When i try to watch tv in the front end i get a screen with please wait... and then get dumped back to the menu after a few seconds.

Please inform which log files i should dump.

Have these lines added to modules:

tuner
tda9887 qss=0
saa7134 card=70,70 tuner=67,67 video_nr=0,1 vbi_nr=0,1

---

### Post by nickrout on 2010-02-27
mythbackend.log and mythfrontend.log

---

