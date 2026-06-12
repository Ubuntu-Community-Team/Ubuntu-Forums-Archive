---
title: "Motorola DCH3416 + Comcast + Firewire... good to go?"
date: 2010-11-22
forum: Mythbuntu
---

### Post by volcs0 on 2010-11-22
Sorry if this is a newbie question. I searched "DCH3416" and the three threads that came up were old or not helpful.

I currently have Comast digital with a Motorola DCH3416 DVR. I pay about $17/month for the box over my regular cable bill.

I recently looked into getting a TiVo premiere to use with a cablecard but I  stopped short when TiVo changed their premiere TOS.

Anyway, I'm thinking instead about building a Mythbuntu box (or recomissioning of the machines I already have).

My reading suggests that there is nothing I can do with a cablecard that I might rent from Comcast for $1.50. On the other hand, it appears that the firewire port on my DCH3416 might be used for recording / control.

So, if I understand things right, I would use the DVR for channel tuning / video out and use the linux box for everything else.

Do I understand the setup and my options correctly?

Again, sorry for the newbie questions.... just getting started and I wanted to make sure I had the concepts right.

---

### Post by LowSky on 2010-11-23
downgrade to a regular cable box, and stop paying for the dvr service if yu plan to go this route.

there is a a casble card option but that tuner card is like $400 and only works on windows.

firewire can work but more than likely comcast will block the signals with drm. if you want to record things beyond basic cable you will also need a haupauge hd-pvr.

i use firewire for only switching channels... i then send the video to a hd-pvr so i can record any show i wish. so i can record more than one thing at a time i also have a digital tuner which can capture local channels that cable cant blovk like nbc and cbs.

---

### Post by volcs0 on 2010-11-23
> **LowSky said:**
> downgrade to a regular cable box, and stop paying for the dvr service if yu plan to go this route.

there is a a casble card option but that tuner card is like $400 and only works on windows.

firewire can work but more than likely comcast will block the signals with drm. if you want to record things beyond basic cable you will also need a haupauge hd-pvr.

i use firewire for only switching channels... i then send the video to a hd-pvr so i can record any show i wish. so i can record more than one thing at a time i also have a digital tuner which can capture local channels that cable cant blovk like nbc and cbs.

Thanks very much for the help.

But if I get rid of the DVR, how I will get the HD signal? Is there a non-DVR HD-cable box (with firefire) that I can get? 

How does the Haupauge DVR fit in the mix?  Is it just a hardware encoder for the HD signal? What's the benefit of this box over a PC card solution?

So, the eventual setup would need to be

Comcast digital cable box (not DVR) --> Haupauge DVR --> PC ---> TV (either direct or LAN)

Do I understand that right?

Thanks again for the help and advice.

Edit: After much agonizing with the Comcast rep, they told me I should just discontinue DVR service on the 3416 but keep the same box - save $8/month. I pressed about which box I could change to (i.e. without DVR) and they sent me to this page:
[http://bit.ly/dqBOp6](http://bit.ly/dqBOp6)

So, which box would be best for integration into a Mythbuntu setup?

---

### Post by LowSky on 2010-11-23
By current law cable companies have to provide firewire on all digital cable boxes. Every company should have HD capable set top boxes that are not DVR.

Haupauge HD PVR is the only fully supported option for Linux users to record cable TV. There are no internal options for this. You can try using just straight firewire but most companies block signal to channels beyond the locals.

Set up could look like this:

```

    _____FireWire_Connection_______
   |                               |
cable box --> Haupauge HD PVR --> PC (MythTV) --> TV
    |            |
    |            |
    |---OR-------|--> TV (direct feed)


```

---

### Post by volcs0 on 2010-11-24
> **LowSky said:**
> By current law cable companies have to provide firewire on all digital cable boxes. Every company should have HD capable set top boxes that are not DVR.

Thanks for your advice - this is very helpful.

So, if I was going to "downgrade" from my current Comcast PVD to only an HD-cable box, which one would you recommend? That will at least save me $8/month for their PVR service. Believe it or not, when I chatted with Comcast, they said I would just keep the box and they would "turn off" the PVR service. But I'd rather just exchange it, if a different box would be easier to integrate into a setup.

[http://bit.ly/dqBOp6](http://bit.ly/dqBOp6)


Thanks for the help.

---

### Post by LowSky on 2010-11-24
Sorry I don't have Comcast and connot comment on their set top boxes.
Your current box should be capable of doing what you wish. Why exchange it if it works.

If I had to reccomend on it would be the Motorola DCT6208 only because I know it works with a channel changing script
[http://www.mythtv.org/wiki/6200ch](http://www.mythtv.org/wiki/6200ch)

I found this list of working set top boxes and your is on the list as working
[http://www.mythtv.org/wiki/Firewire_Cable_Box_Compatibility]("http://www.mythtv.org/wiki/Firewire_Cable_Box_Compatibility")

---

### Post by volcs0 on 2010-11-24
> **LowSky said:**
> Sorry I don't have Comcast and connot comment on their set top boxes.
Your current box should be capable of doing what you wish. Why exchange it if it works.

Ah.... so that makes a lot of sense. This way, I could build the box and get everything working - without disrupting my wife's DVR capabilities. Already, I know this will be another example of me screwing things up by trying to "make things better." So, in this case, I could wait until everything is working fine before calling Comcast and having them suspend the DVR service on that box...

Thanks again.

---

### Post by Linux Lurker on 2010-12-04
My 2 cents.

I am in a similar situation as you.  I am FED UP with Comcast, but acceptable alternatives are scarce.  Anyway... I too have the Motorola DCH3412 set top box.

To answer one of your questions, I JUST got this working with MythTV via firewire.  Live TV is watchable and channels are changeable (kinda awkward for now).  I only had one firewire 6to6 cable around, so I didn't try the SECOND 1394 connector.  My hope is that the second connector corresponds to the second tuner inside the stb. Heading out now, to buy a 2nd cable to try it.  <See edit update below>

I understand you mentally wanting to "map out" your building a box and transitioning to MythTV.  Much of your situation is similar... including the wife that doesn't know "how freakin' cool this is going to be", when done. :-)

I too would like to get rid of the DCH3416 as it seems redundant when building a MythTV box.  However, your comment stating that Comcast would just "disable" the pvr feature is a decent compromise between having a stb that I KNOW works via firewire... and gambling on another model.  I can hide the unit close enough to the Myth backend to be out of site.

I recommend you install Myth and get it all configured and running properly.  I opted to use .24 and the newest fixes branch.  You will get it all sorted out.  My biggest issue so far was problems trying to connect to the backend.  You'll find that you can't do anything until you resolve that issue.  Dive in and get started! I damn near bought the Hauppauge 2250 from NewEgg before stumbling upon the idea of firewire "capture cards".  DO NOT BUY ANY HARDWARE until you get MythTV operational.  You WILL have different ideas as you go along.

I'll update this message after I get the 2nd firewire configured and hopefully working as 2 tuners.  If that's not possible, I see no reason to keep the box, over trading it for a smaller version without the pvr.
Good luck.

<Edit>:
Yeah, I knew that was too much to hope for.  The two firewire ports on the back of the DCH3412 do not correspond to each individual internal tuner. There is only one GUID that shows in MythTV.  Well, for now I'm going to tweak my setup with only this single input for now.  I'll post back here if I discover or learn of any other approaches to this that may be of interest.
LL

---

### Post by dkhokhlov on 2012-07-04
Is it possible to record a show over Firewire on DCX3416 and watch another show on TV  at the same time?

---

### Post by wildmanne39 on 2012-07-05
Old thread closed, please start a new one.
Thanks

---

