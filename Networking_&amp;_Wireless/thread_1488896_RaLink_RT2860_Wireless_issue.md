---
title: "RaLink RT2860 Wireless issue"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by kkelly77 on 2010-05-20
I sincerely hope all those suffering with wireless connection issues see this post and have success with it.

I have been having problems with my wireless connection for months now since switching to Ubuntu. Like some people, my laptop would connect occasionally. When it wouldn't, I just kept getting a message on the screen asking to enter the WPA passphrase.

The fix?** I changed the security on the router from WPA and WPA2 to just WPA2. And TKIP and AES to AES only**. For whatever reason changing the cipher settings works.

Prior to doing this I've tried nearly every fix listed on  the forum and I can't believe the fix was so simple :) 

I am using Ubuntu version 10.04 Lucid Lynx

K.

---

### Post by Grench on 2010-06-15
A few additional notes on this bug - yes bug.

10.04 64 bit raw install on xw8600 workstation with EDIMAX 802.11N RT2860 based PCI card = works without changing to the OP's settings.

Yes, I said that works - it works out of the box on a fresh install.

Run update for the first time = fails.

Something being updated in the first 175MB of patches is breaking this driver.

Changing the router to the OP's settings is a viable work around - it worked for me as well.  However, it should work anyway.

Changing the router was OK since I don't have any WPA devices anymore.  If I did, this wouldn't be cool.  The fact that it works then breaks is annoying too.

I'm not sure how the OP figured this out, but THANK YOU!

---

### Post by rwshoemaker on 2010-06-18
I struggled for days trying to get this chipset to work without success.  I followed all the instructions in the forum both for the native driver and ndiswrapper with the XP driver.  Finally, I discovered this simple article in the archives, and it worked for Lucid 64 bit.  [http://ubuntuforums.org/archive/index.php/t-1045703.html](http://ubuntuforums.org/archive/index.php/t-1045703.html)  Don't know why it doesn't work "out of the box," but it does not in Lucid, although I have heard it said it did in previous releases.  Now I am finally operating at N speeds!

---

### Post by gadget3000 on 2010-07-28
I can't believe the fix was that easy! Thank you kkelly77!

---

