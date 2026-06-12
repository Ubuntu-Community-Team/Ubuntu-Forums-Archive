---
title: "No longer able to get BBC HD channels on satellite"
date: 2012-08-19
forum: Mythbuntu
---

### Post by timswait on 2012-08-19
I've just done a full re-scan of all the channels on my Myth TV set up as I needed to update some channel names and numbers and thought it was easiest to start from scratch. Now I'm no longer able to get either of the BBC high definition channels. I was still receiving them a few days ago, although I didn't specifically check immediately before the re-scan.
I've tried doing a scan entering the following parameters:
```
Freq: 10847000
Polarity: Vertical
Symbol rate: 23000000
Mod Sys: DVB-S2
FEC: 8/9
Modulation: QPSK
Inversion: leave at auto
Rolloff: leave at 0.35

```
but it finds nothing (gets no lock)
On the BBC's website they have a statement about not supporting MythTV ([http://www.bbc.co.uk/bbchd/faqs.shtml#linux]("http://www.bbc.co.uk/bbchd/faqs.shtml#linux")) Have they in some way cut off the service for Linux users? :( Is anyone else still able to get BBC HD and BBC One HD through satellite?

---

### Post by timswait on 2012-08-19
Panic over! ;)
Just had to set it to include encrypted channels but to check if they could be decrypted, and now it's found them again!
:)

---

