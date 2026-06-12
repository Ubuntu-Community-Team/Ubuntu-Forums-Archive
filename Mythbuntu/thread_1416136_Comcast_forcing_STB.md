---
title: "Comcast forcing STB?"
date: 2010-02-25
forum: Mythbuntu
---

### Post by dougsnell on 2010-02-25
Comcast sent out a letter stating I'm going to need an STB or Digital Adapter for each TV in my house.  I've been running Myth for years, and have avoided getting a cablebox because I know it's going to create more work :P

Is anyone else going through this, and do they have any suggestions?  My assumption is I'm going to need an STB from them for *each* input, and Myth will need to change channels on each one.  I have 3 inputs (PVR 350 and a dual-tuner PVR 500) ... which sounds as though this is going to suck.  I assume all three tuners can't pull from the STB at once, and not having a clue what the digital adapters are, I'm guessing they aren't going to help me?

And, if that's the case, maybe it's time I bit the bullet and move to satellite (it offers some channels I'd prefer).  I've avoided having to deal with set top boxes, but this might make that decision easier :)

---

### Post by blackoper on 2010-02-26
A QAM hd tuner would allow you to probably get the basic hd channels in the area and possibly some "extra" channels. Anything premium or not covered in the unencrypted qam channels would need to be tuned through the STB. You could use the analog tuners or you could upgrade to the hdpvr and be able to do the high def content (if you get any). ALso, if you throw a bit of a fit with comcast they'll probably give you the cable boxes for free for a year or so.

---

### Post by xinix on 2010-02-26
Have you looked at this?  [http://digitalnow.comcast.com/FAQs.aspx?map=all_faq_map](http://digitalnow.comcast.com/FAQs.aspx?map=all_faq_map)

I'm not sure the faq clears things up.  It sounds like they are going all digital on anything other than their basic line-up.

---

### Post by klc5555 on 2010-02-26
> **dougsnell said:**
> Comcast sent out a letter stating I'm going to need an STB or Digital Adapter for each TV in my house.  I've been running Myth for years, and have avoided getting a cablebox because I know it's going to create more work :P

Is anyone else going through this, and do they have any suggestions?  My assumption is I'm going to need an STB from them for *each* input, and Myth will need to change channels on each one.  I have 3 inputs (PVR 350 and a dual-tuner PVR 500) ... which sounds as though this is going to suck.  I assume all three tuners can't pull from the STB at once, and not having a clue what the digital adapters are, I'm guessing they aren't going to help me?

And, if that's the case, maybe it's time I bit the bullet and move to satellite (it offers some channels I'd prefer).  I've avoided having to deal with set top boxes, but this might make that decision easier :)

Went through this in November. 

If you have the standard analog package (what used to be called "Extended Basic" or some such, channels 2-99), and intend to continue with something as close to this package as possible, then after the transition many of these channels will become weak-encrypted digital, requiring either a STB or a DTA between the coax and (each) analog tuner. The Comcast device will pump in the signal on channel 3 or 4, and mythtv will tune by using a blaster and the Spawn-of-Satan lirc utility to change channels on the device directly. It is possible that in your area you may be issued up to 3 devices with no extra rental fees (so far). Your PVR 500, if I remember correctly, has only one input and therefore can only accomodate 1 device. The devices don't allow signal pass-through, so that the card input hooked to a device gets nothing except what the device pipes to it. Tough for QAM/analog hybrid cards.

The DTA is simpler and a no-brainer to set up, but just receives channels. It can also be a real pain in the tookis to configure the Spawn-of-Satan lirc for (though this is getting better). The STB has the extra features (like On Demand, if you care for such things) and is better supported (faint praise) by lirc.

But depending on your area, the bulk of what used to constitute your extended basic tier (the OTA locals, also the locals in HD, various cable news, history, and some of the cable-only networks in SD) may be piped in on clear QAM. So while you may want some analog tuners to hook up to your Comcast devices to get the encrypted channels, you may find that one or two (or several) QAM tuners will be of great use to you. I'd recommend the pchdtv hd-5500 for QAM use. There are many other good QAM cards out there too. From my own experience, I'd also recommend avoiding the Hauppauge 1600, despite the attraction of it having separate analog and digital inputs --too many QAM problems.

Good luck!

---

### Post by williammanda on 2010-02-26
I have comcast in TN. I have a small package of 25 channels all digital with 6 HD stations for $13. Comcast isn't requiring any stb's for digital channels here. It could be that analog is the issue for you. I would explore the digital packages they offer. I only have one cable input that I use for 3 atsc tuners (HDTV 5500 and 2 - Dvico). One thing to think about concerning satellite, You won't be able to record in HD.

---

### Post by dougsnell on 2010-02-26
Thanks for the replies.  It sounds like I'm on the right track - I'll need an adapter or a DTB for each input *that I want encrypted channels*.  Unfortunately, I actually watch the higher channels more than the lower channels :P

So ... if satellite has channels I would prefer (not to mention prices I would prefer), can anyone clue me in to what I'll need there?  Do they require STBs or adapters (and is that an extra charge), or do signals not require that (clear QAM)?  I have to admit, I'm in the dark about satellite, so if it has qualifications on it like cable (certain channels), please let me know :)

I've got a bit of considering to do, but as a part of it are there any recommendations for a combo card that has both input and output ... or just grab an nVidia card and run it separately?  I suppose I could continue to use the 350 for output, but to be honest, the 350 is holding me back on upgrades.  It's always a pain in the butt, and right now only works with 9.04.

And unless I completely missed something, dual tuners are limited:  they each require an adapter or STB when recording digital (though I do understand analog is still a recording option).

---

### Post by bcgrown on 2010-02-26
> **blackoper said:**
> A QAM hd tuner would allow you to probably get the basic hd channels in the area and possibly some "extra" channels. Anything premium or not covered in the unencrypted qam channels would need to be tuned through the STB. You could use the analog tuners or you could upgrade to the hdpvr and be able to do the high def content (if you get any). ALso, if you throw a bit of a fit with comcast they'll probably give you the cable boxes for free for a year or so.

Make sure you do some real research first.  My cable provider offers zero channels in clear QAM,  so a QAM tuner wouldn't help much.  I don't know what other companies do.  I understand that in the USA there may be a requirement to provide a FireWire output,  so definitely look into that.  FireWire recording works very well for me and you would only need to spend $30 on a FW card if you don't already have one.

---

