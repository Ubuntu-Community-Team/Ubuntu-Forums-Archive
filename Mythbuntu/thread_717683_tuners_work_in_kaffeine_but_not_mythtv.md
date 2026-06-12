---
title: "tuners work in kaffeine but not mythtv"
date: 2008-03-07
forum: Mythbuntu
---

### Post by mikeyandmary on 2008-03-07
Hi all,

I am running mythtv on ubuntu 7.10. 

I have recently installed a dvico dual digital 4 and dvico nano usb tuner following the instructions at [https://help.ubuntu.com/community/DViCO_Dual_Digital_4]("https://help.ubuntu.com/community/DViCO_Dual_Digital_4")

Both tuners on the dual digital 4 work perfectly in Kaffeine. In mythtv The tuners setup fine in mythbackend but cannot lock on any channels in mythfrontend. 

The nano also works perfectly in kaffeine. The nano is recognised by mythbackend but cannot scan channels at all. 

Any help would be greatly appreciated. 
Thanks... Michael

---

### Post by bawilson2 on 2008-03-07
I just setup Mythtv for the first time and wasn't able to scan for channels either.  I found that I had to scan for the channels using a package in the dvb-utils.  The command I used was:

scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > channels.conf

One I had that file I tried importing in through the channel scanner in Mythtv but that failed as well.  I had to take that file and manually enter the number in the second column as a transport.  After I added them all as transports I was able to have Mythtv scan the channels on existing transports and everything worked out.

You may not have the same problem but that's what I did to fix something similar.

---

