---
title: "Channels Me-TV Ubuntu 10.10"
date: 2010-11-28
forum: Multimedia Software
---

### Post by pretender? on 2010-11-28
I am running ubuntu 10.10 and have previously used me-tv and not had a problem getting all the channels

But on ubuntu 10.10 and metv version 13.11 some of my channels have not picked up when i run my scan file GO and SBS Channels as you can see on the below link

[http://img203.imageshack.us/i/metvchannels.png/](http://img203.imageshack.us/i/metvchannels.png/)

channel.conf scan file

   1. Australia / Hervey Bay / Ghost Hill

#
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy

#
# ABC UHF56
T 725500000 7MHz ¾ NONE QAM64 8k 1/16 NONE

   1. Seven UHF59
      T 746500000 7MHz ¾ NONE QAM64 8k 1/16 NONE
   2. Nine UHF62
      T 767625000 7MHz ¾ NONE QAM64 8k 1/16 NONE
   3. Ten UHF68
      T 809500000 7MHz ¾ NONE QAM64 8k 1/16 NONE
   4. SBS UHF28
      T 529500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE
   5. SBS UHF34
      T 704500000 7MHz 2/3 NONE QAM64 8k 1/8 NONE

How can i get the missing channels to scan properly

Regards

Pretender

---

### Post by pretender? on 2010-11-29
Updated to latest ppa version of me-tv and then selected Auto Scan option when scanning for channels fixed the problem

---

