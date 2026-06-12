---
title: "Mythbuntu can't see second tv card"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by Vonagio on 2008-03-25
I have a mythbuntu setup, using:

Asus M2N-VM HDMI
AMD X2 3800
1 gig RAM
500 GB HDD
2 x KWorld cx88 dvbt cards

I previously had this setup with ati IGP, but obviously mythtv doesn't like this so i installed the new motherboard yesterday. The tv cards worked perfectly on the old install/motherboard. I reinstalled mythbuntu (as my meddling with xorg and fglrx broke it!). Now I have reinstalled it, the first tuner card works perfectly, I can watch/record TV all day... The second card isn't even detected, when I try to add a new capture card (card type - DVB DTV capture card) and change the card number to 1, it cant see it (frontend ID: Could not open card #1, subtype: No such file or directory).

I have tried looking in /dev/dvb/ and there is only one folder - adapter0. I have also tried looking in the BIOS to enable the second PCI slot and there are no options with that in...

Any help would be much appreciated, Steve

---

### Post by Vonagio on 2008-03-29
Strangely, after leaving the computer for a few days (off), the second card is detected and now works perfectly!

Ah well...

---

