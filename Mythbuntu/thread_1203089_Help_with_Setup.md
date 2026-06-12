---
title: "Help with Setup"
date: 2009-07-02
forum: Mythbuntu
---

### Post by bitphire on 2009-07-02
Boss would like me to build him a Mythbuntu setup.

I believe he has Dish Network (I know it's satellite). His Dish Box has HDMI and Component out and he would prefer to use the HDMI if possible. He doesn't really want to watch Live TV just wants to record shows for watching later. So I need to get from Dish Box to PC (Need help finding a card) and have MythTV be able to record the shows he wants then just store them on a server. Then I need to build front ends for all his TV's to stream from the server.

I'm really new at this so if anyone can help with suggested hardware I would appreciate it. As for a price limit he's pretty open on going all out. Try to keep the TV Card under 350 if possible. TIA for any suggestions!

---

### Post by Das Hammer on 2009-07-02
Assuming you will be capturing HD video since you mentioned HDMI and/or component......

The only way to capture HD video (and meet your budget) is to use a Hauppauge HD-PVR. It's a USB box that has component input and runs about $200 to $220 US. 

There is support for it, but from what I understand, you have to use some packages other than the standard Mythbuntu release. It's been a while since I've looked into it, and at the time it was pretty new. It is supposed to be supported natively in MythTV 0.22, but the official version is not released yet.

Search on the forums and you're bound to run across threads regarding this hardware.

By the way, you'd also need an "IR Blaster" to change the channels on the Dish Notwork receiver.

Good luck.

---

### Post by Das Hammer on 2009-07-02
As for other hardware, I should mention that an nVidia 8400 GS video card will do you well. They are cheap and can take advantage of VDPAU which is hardware acceleration. 

VDPAU will officially be supported in MythTV 0.22, but you can use it right now in 0.21 with avenard's packages which have been backported.

The benefit: I'm watching an above average bitrate 1080i channel, deinterlacing it and sending it out to my 1080P tv, and mythfrontend.real is using about 10% of the CPU (that's 10% of one core).  It is lower with other channels.

---

### Post by bitphire on 2009-07-02
Thanks for the reply! The only reason I put that limit on there is that I read something about HDMI cards running in the thousands and boss said no to that idea :P I have been looking at that HD PVR. Anything better even it does cost a little bit more?

---

### Post by Das Hammer on 2009-07-02
> **bitphire said:**
> Thanks for the reply! The only reason I put that limit on there is that I read something about HDMI cards running in the thousands and boss said no to that idea :P I have been looking at that HD PVR. Anything better even it does cost a little bit more?

I don't know if there is anything better in it's class, probably not. The bigger question is: Is there anything else that would work with MythTV and do what this does? I'm pretty sure the answer to that is no.

I know that early on there were some bugs (like you could only capture 720p output), but I really don't know where it stands right now. I know people are using them, so obviously it works.

---

### Post by Jayy on 2009-07-03
> **Das Hammer said:**
> By the way, you'd also need an "IR Blaster" to change the channels on the Dish Notwork receiver.
The HD-PVR has a built in IR Blaster. :) Though I don't know if it's supported in Mythbuntu...

---

