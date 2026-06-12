---
title: "completly rebuild channel listings (I screwed up bad)"
date: 2008-11-11
forum: Mythbuntu
---

### Post by iitywygms on 2008-11-11
I have hosed up my channel guide listing good. 
I made some changes to the channel guide using mythweb.  Now half of the channels do not get filled with data when I run mythfilldatabase. I need to start from scratch, completely erase what I have done and start over.

This is what I have done so far.

In mythweb I enter the xmltvid# for each channel from schedules direct.

then run

mythfilldatabase - (not all channels fill)
mythfilldatabase --refresh-all (not all channels fill)
mythfilldatabase --do-channel-update (not all channels fill)

so I

Deleted all input sources in backend.  
Made new sources and re-scanned for channels.

did all the above again.  Still only half of the channels fill, and I see some of the bad input I had previously entered in the data.

How can I purge the information completely and start from scratch?
Please help...

---

### Post by klc5555 on 2008-11-12
> **iitywygms said:**
> I have hosed up my channel guide listing good. 
I made some changes to the channel guide using mythweb.  Now half of the channels do not get filled with data when I run mythfilldatabase. I need to start from scratch, completely erase what I have done and start over.

This is what I have done so far.

In mythweb I enter the xmltvid# for each channel from schedules direct.

then run

mythfilldatabase - (not all channels fill)
mythfilldatabase --refresh-all (not all channels fill)
mythfilldatabase --do-channel-update (not all channels fill)

so I

Deleted all input sources in backend.  
Made new sources and re-scanned for channels.

did all the above again.  Still only half of the channels fill, and I see some of the bad input I had previously entered in the data.

How can I purge the information completely and start from scratch?
Please help...


Is the guide data really missing from half of the channels, or if you scroll through the defective guide, say, 36 hours from now, is there data on those channels?

After the first run on a new installation of mythconverg, mythfilldatabase runs fill in starting "tomorrow" unless "refresh-today" is explicitly set. I don't think "refresh-all" does this; it also starts "tomorrow".

Drove me bonkers when I was first trying to setup a lineup that theerafter needed considerable surgery. It seemed that no matter what I did, I could not get the altered lineup to fill. Then after a couple of dozen runs of mythfilldatabase --refresh-all that didn't solve the problem, I finally scanned ahead through my defective schedule and noticed that the data had started appearing on the affected channels some 24 hrs. ahead.

A first guess at your problem, anyway. 

Cheers! :)

---

### Post by iitywygms on 2008-11-12
> **klc5555 said:**
> Is the guide data really missing from half of the channels, or if you scroll through the defective guide, say, 36 hours from now, is there data on those channels?

After the first run on a new installation of mythconverg, mythfilldatabase runs fill in starting "tomorrow" unless "refresh-today" is explicitly set. I don't think "refresh-all" does this; it also starts "tomorrow".

Drove me bonkers when I was first trying to setup a lineup that theerafter needed considerable surgery. It seemed that no matter what I did, I could not get the altered lineup to fill. Then after a couple of dozen runs of mythfilldatabase --refresh-all that didn't solve the problem, I finally scanned ahead through my defective schedule and noticed that the data had started appearing on the affected channels some 24 hrs. ahead.

A first guess at your problem, anyway. 

Cheers! :)

I dunno.  I will defiantly check that later today.

---

### Post by iitywygms on 2008-11-12
That helped thank you.
I also learned that the same channel can have different xmlid numbers.  That was screwing me up to.
Example, channel 2 and 2.1 are the same channel, only one is high def and one is not.  I was using the same xmlid for both.  That screwed things up.
I guess it is important to use separate xmlid's for each individual channel number.

---

### Post by klc5555 on 2008-11-13
> **iitywygms said:**
> That helped thank you.
I also learned that the same channel can have different xmlid numbers.  That was screwing me up to.
Example, channel 2 and 2.1 are the same channel, only one is high def and one is not.  I was using the same xmlid for both.  That screwed things up.
I guess it is important to use separate xmlid's for each individual channel number.

Glad everything works!

As important as different xmlids is to make sure the nearly identical channels (like your 2 and 2.1) are given different _call signs_ (even if you make them up) along with the different xmlids and different names. Unless the call signs are made unique, mythtv seems generally to conflate the two channels and try to record from both simultaneously when either one is set to record.   

Cheers! :)

---

