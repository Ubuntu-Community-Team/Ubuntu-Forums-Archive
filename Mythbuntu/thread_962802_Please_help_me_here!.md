---
title: "Please help me here!"
date: 2008-10-29
forum: Mythbuntu
---

### Post by thomas.mckay on 2008-10-29
I've set up mythbuntu 8.04. I went with standard so that it configured most everything. I have one Hauppauge PVR-350 TV Tuner card. Where do I go from here? I'm trying to connect to a TV that is connected to a Comcast box, and I'm going to hook up through composite cables. 

Basically what I'm asking is where do I plug stuff in (Because I'm using a Comcast box, not a TV), and what else do I need to configure int eh frontend/backend?

I read through the guide but it did not help me with these questions.

---

### Post by eddietours on 2008-10-29
the comcast box has to have composite out is that what you ask ?

---

### Post by thomas.mckay on 2008-10-29
Well I'm really just asking where to plug everything in, and what else I'd have to configure. I'm really not familiar with Linux and I've never set up a mythTV box before. The guid seems to just end after installation, and it never mentions anything about my card specifically or about the comcast box.

---

### Post by DutchLoki on 2008-10-29
> **thomas.mckay said:**
> Well I'm really just asking where to plug everything in, and what else I'd have to configure. I'm really not familiar with Linux and I've never set up a mythTV box before. The guid seems to just end after installation, and it never mentions anything about my card specifically or about the comcast box.

Besides the mythBuntu guide you can read the MythTV manuals (both of complement each other, so use them both):  

[http://www.mythtv.org/modules.php?name=MythInstall](http://www.mythtv.org/modules.php?name=MythInstall)

[http://www.mythtv.org/wiki/index.php/User_Manual:Index](http://www.mythtv.org/wiki/index.php/User_Manual:Index)

---

### Post by thomas.mckay on 2008-10-29
I need to first get everything hooked up right so that I can then troubleshoot from there. The problem is that none of these guides mention how to connect it to a comcast box, where there is a TON of  input types. I want to connect mine by composite, which does't really narrow it down at all. If anyone out there has connected it to a comcast box before, or has any ideas on how to, please hlep me out.

---

### Post by fryed_1 on 2008-10-29
I connected RGB (simple red, yellow, green for stereo audio and video) to the input on my pvr-150.

I hooked a splitter into the cable line, one coax goes to the 150, the other to the cable box.

I setup schedulesdirect and named it Cable.

Then I make sure to setup the Cable input for both the tuner and composite inputs.


Now inside LiveTV, I can switch inputs to the comcast box or PVR-150 tuner.  I don't have my blaster yet working, but I can change channels with the cable remote when using that (mostly just use it for on-demand from comcast) or have full capabilities when using any of the PC tuners.

---

### Post by thomas.mckay on 2008-10-29
WHat did you do to set up the input for teh tuner and the composite? Because I'm really confused I did the standard install and mainly went with the defaults like it told me to for the configuring stuff, and I have like 3 composite thing I can configure under the configure area.

---

### Post by fryed_1 on 2008-10-29
> **thomas.mckay said:**
> WHat did you do to set up the input for teh tuner and the composite? Because I'm really confused I did the standard install and mainly went with the defaults like it told me to for the configuring stuff, and I have like 3 composite thing I can configure under the configure area.

The inputs are set to the schedulesdirect account I setup.  I have 2 tuners and the cable box.  They all use the same video source.

---

### Post by thomas.mckay on 2008-10-30
I got it hooked up. My issue was that I had deleted to reconfigure my card, and when I did the NTSC got reset to PAL, and I didn't realize that. I changed it back, and now it works, although TV quality seems a bit low.

I am, however, unable to hook it up to my TV (I have a normal TV, but I have a comcast box). Do I hook it up to the box, or my TV, and how? I tried all the things I can think to (channels, VCR,AUX1 and 2, etc.)

---

### Post by thomas.mckay on 2008-10-31
Although now I'm getting static again! I was able to watch TV, then set it to record a 30 minute show. It said it was recording, but after the show was done I was unable to find it under watch recordings (If I looked in the TV listings, it said it was recorded). Now I can't see anything but static, but like before I'm getting listings and able to update them. Can anyone help me here?

---

