---
title: "I want to DVR my encrypted channels"
date: 2008-07-04
forum: Mythbuntu
---

### Post by mkramer on 2008-07-04
Mythtv + Ubuntu has sure been an adventure these last few months.  Today, I've finally got it working using the firewire output on my motorola 6200 going into the backend server running ubuntu 8.04 and mythtv .21.

Some channels were working, however many more were getting the "partial lock" error.  I ran the scanfw utility and now I have my answer: the partial lock channels are all encrypted.

This is really disappointing.  I thought that, coming out of the set top box, I would get to view all those encrypted channels.  After all, I am paying the monthly fee for those channels.

I've spent the afternoon educating myself on the current state of digital content protection.  I now realize that, for all the new HD content, except over the air news broadcasts, there is an unbroken chain of encryption from the cable, to the set top box, to the HDCP-compliant HDMI display.

What a predicament.  Short of breaking one of the encryption schemes that is used throughout the supply line, the only way to circumvent this system looks to be by spoofing the cable box with a gadget that looks like an HDCP display device that can then pass along the unencrypted raw output.  Then it remains to loop the unencrypted content back into the mythtv server via a capture card (though no DVI capture card exists, presumably because such a device would only be useful for a person that is spoofing an HDCP system.  However, reduced but acceptable quality would be acheivable by converting the DVI-out of the spoofing device into component, and then utilizing a capture card with a component input.  By now our hypothetical convergence living room contains something of a rube-goldberg device, but that is another story).

It looks like the issue with this is that a device like the HDfury, that is precisely an HDCP spoofing widget ([http://www.hdfury.com/](http://www.hdfury.com/)), is going to output a raw HD signal on the order of 1.5Gb/s.  If this is the case, then there is no practical way to record this signal, and all our plans are for naught. 

So - has anyone figured out a way? 

Because really, who cares about OTA broadcasts?  The content providers know what the good stuff is, and that is precisely the stuff that they make sure you can't get.

---

### Post by tgm4883 on 2008-07-04
> **mkramer said:**
> Mythtv + Ubuntu has sure been an adventure these last few months.  Today, I've finally got it working using the firewire output on my motorola 6200 going into the backend server running ubuntu 8.04 and mythtv .21.

Some channels were working, however many more were getting the "partial lock" error.  I ran the scanfw utility and now I have my answer: the partial lock channels are all encrypted.

This is really disappointing.  I thought that, coming out of the set top box, I would get to view all those encrypted channels.  After all, I am paying the monthly fee for those channels.

I've spent the afternoon educating myself on the current state of digital content protection.  I now realize that, for all the new HD content, except over the air news broadcasts, there is an unbroken chain of encryption from the cable, to the set top box, to the HDCP-compliant HDMI display.

What a predicament.  Short of breaking one of the encryption schemes that is used throughout the supply line, the only way to circumvent this system looks to be by spoofing the cable box with a gadget that looks like an HDCP display device that can then pass along the unencrypted raw output.  Then it remains to loop the unencrypted content back into the mythtv server via a capture card (though no DVI capture card exists, presumably because such a device would only be useful for a person that is spoofing an HDCP system.  However, reduced but acceptable quality would be acheivable by converting the DVI-out of the spoofing device into component, and then utilizing a capture card with a component input.  By now our hypothetical convergence living room contains something of a rube-goldberg device, but that is another story).

It looks like the issue with this is that a device like the HDfury, that is precisely an HDCP spoofing widget ([http://www.hdfury.com/](http://www.hdfury.com/)), is going to output a raw HD signal on the order of 1.5Gb/s.  If this is the case, then there is no practical way to record this signal, and all our plans are for naught. 

So - has anyone figured out a way? 

Because really, who cares about OTA broadcasts?  The content providers know what the good stuff is, and that is precisely the stuff that they make sure you can't get.

First, lots of people like whats on OTA broadcasts.  NBC, CBS, ABC, Fox, etc channels have some pretty good shows.

Now to answer your question, what you are looking for is this 
[http://www.hauppauge.com/site/products/data_hdpvr.html](http://www.hauppauge.com/site/products/data_hdpvr.html)

Why you want to output from the cable box through another device to this is beyond me.  Output from the cable box via component directly into the HD PVR.  You don't need to go from HDMI (or DVI) to component first.

*Note - you may want to check on the status of this device support in MythTV before you purchase one.

---

### Post by majoridiot on 2008-07-05
> **mkramer said:**
> Mythtv + Ubuntu has sure been an adventure these last few months.  Today, I've finally got it working using the firewire output on my motorola 6200 going into the backend server running ubuntu 8.04 and mythtv .21.

Some channels were working, however many more were getting the "partial lock" error.  I ran the scanfw utility and now I have my answer: the partial lock channels are all encrypted.

sorry to hear of your encryption woes, but thanks for making this post.
up until now, there has been *very* little feedback on scanfw, and i'm 
just happy to know that someone had found it useful.

a couple of questions, before you give up on firewire altogether:

who is your cable provider?

did you run scanfw with option -s 6 or more, to make sure that all
of the channels are *really* encrypted?  my 6212 will often "flutter" 
the CCI back and forth when changing from an encrypted channel to
one that isn't.  this may help you locate more channels that report
as encrypted, but are not.

> **mkramer said:**
> This is really disappointing.  I thought that, coming out of the set top box, I would get to view all those encrypted channels.  After all, I am paying the monthly fee for those channels.... Short of breaking one of the encryption schemes that is used throughout the supply line...

yes, it is very disappointing.  especially when the cable companies
are violating both the letter and spirit  of the law by encrypting content
that should not be.

a fair-use driver for "record-once" encrypted content was appx
75% completed when the project died due to lack of interest.  unless
interested parties with the needed skills suddenly materialize,
the driver is dead and your best bet is to look into the 1212,
as tgm4883 recommends.

---

### Post by dsbw on 2008-07-05
> **majoridiot said:**
> a fair-use driver for "record-once" encrypted content was appx
75% completed when the project died due to lack of interest.  unless
interested parties with the needed skills suddenly materialize,
the driver is dead and your best bet is to look into the 1212,
as tgm4883 recommends.

What would this driver do, exactly?

---

### Post by majoridiot on 2008-07-05
> **dsbw said:**
> What would this driver do, exactly?

allow firewire streams with a CCI of 0x02, or "record once", to actually
be recorded once, as fair use dictates.

---

### Post by goterror on 2008-07-10
It seems the other product like Hauppauge HVR-1800 worked for the HDTV according to the Hauppauge, but not for recording encrypted HDTV channel. And the site hasn't mentioned if the HD PVR 1212 can record multi channel at the same time, plus the expensive price of PVR 1212, I think I will prosponed my DVR project. BTW, the PVR 1212 only support stereo, watch out!

---

### Post by dsbw on 2008-07-11
> **majoridiot said:**
> allow firewire streams with a CCI of 0x02, or "record once", to actually
be recorded once, as fair use dictates.

And there was a lack of interest in this? Isn't that most channels?

---

### Post by majoridiot on 2008-07-12
> **dsbw said:**
> And there was a lack of interest in this? Isn't that most channels?

yes and yes. amazing, innit?

---

### Post by MrMunkily on 2008-07-12
> **majoridiot said:**
> yes and yes. amazing, innit?

Seems unlikely that that would be why it failed - a license for 5c decryption requires, IIRC , a rather terrifying amount of money and an assumption by the implementing organization of unlimited financial liability for any holes or exploits. There has never been ANY computer device, as far as I know, that supports 5c. The only devices I've heard of are DVHS recorders. I don't even think that tivo and the like support it, though I don't know for sure.

The HD-PVR does not yet work usably in Myth.
The HD-PVR doesn't yet support AC3 but they intend to release an update to make it do so.
The HD-PVR can only record from one source at a time, tuned using an IR Blaster.


edit: I just realized you weren't talking about an effort to secure a license for 5c

---

