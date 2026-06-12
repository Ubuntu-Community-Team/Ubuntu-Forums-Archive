---
title: "After 5 days of work, I got my ATI drivers working.."
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by Auctionedllama@gmail.com on 2008-04-19
Hi, I am just posting this for anyone who is having trouble with an ATI card, and can't seem to get it installed. It took me 5 days and 4 complete formats later to get this installed. Almost every guide I followed seemed to be bogus, and did nothing for me. I have an ATI X1650 pro.. Anyways.. First, after a fresh format, I downloaded and installed all the updates and did a restart. I then enabled the driver via Restricted Driver manager and DID not restart. After that I downloaded the ATI driver for my card from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) and installed that with the directions from here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0) 
I skipped the first line of code (about getting the proper tools) and stopped after installing the driver (I did not do the aticonfig --initial command).. Also, every package extracted did not work except one, so don't fret if you get errors. I then restarted, and edited the xorg.conf and made the composite factor at the bottom true and restarted again. I then had full 3d acceleration and resolution support. After 5 days. Pheww.. Also free to sticky this if you want..

---

