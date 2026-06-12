---
title: "B43  Master mode or ad-hoc"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Hillshum on 2009-07-30
Well, I've spent the morning researching and poking around and otherwise trying to get a wifi connection up between my g3 iBook (with the stock airport card) and a desktop with a Broadcom pci card. Both machines run jaunty, the iBook is of course powerpc.

Now, I have two options. One is to use the Broadcom adapter as a WAP and connect the airport to that. The other is to get an ad-hoc network between them.

The first has failed because I've not been able to get my broadcom into master mode. It seems that the b43 driver supports it, but mac80211 doesn't (or something else upstream).

Connecting the two to an ad-hoc network has failed as well. I can create one one the broadcom, and see it on the airport, but am unable to connect.

Note that earlier, in a powermac g4, I had this broadcom functioning as a proper WAP, with the airport connecting to it.

Any ideas?

---

