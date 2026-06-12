---
title: "Building new (right!) PVR help needed."
date: 2008-07-30
forum: Mythbuntu
---

### Post by oldsoundguy on 2008-07-30
Ok, here is the issue;

My brother wants me to build him a PVR ... out of an old People PC box.

It is an Intel in810 board and I have managed to get it upgraded a bit from it's truly old and slow 333/66 with 64mb ram and a 6gb hd and a  generic cdrom.
It now has:
Celeron 800
512 mb of PC 100 (fsb 100)
120 gb WD drive
Lite On dual layer DVD-RW with Light Scribe
Lite OnDVD-ROM
NVida G-Force FX5500 video (replacing the on board)
Creative Live! 5.1 audio (replacing the on board)
USB to RJ45LAN plug in LAN adapter so it can be networked(because there is only one PCI slot left and that has to be used for the tuner/capture card!)

The issue is:
What tuner/capture card?  Looking closely at the Fusion HDTV5 Gold as the answer as he has DIGITAL CABLE (his set is 720) and is not using any antenna.
Would this be a good choice, or should I continue my search?

Have my copy of Mythbuntu 8.04 ready to go (8.04.01 has problems with the download file somehow .. cd check shows errors .. several sources tried all with the same result!)

TIA

---

### Post by oldsoundguy on 2008-07-31
bump~

---

### Post by oldsoundguy on 2008-08-03
guess I need to bump this up again.

---

### Post by axelsvag on 2008-08-03
I know it is awful not to get any response. But I think you must say where you live and what you want to watch before anyone can give you any advice.

---

### Post by oldsoundguy on 2008-08-03
And just why is that?  I have been on these forums for quite a while and NEVER had that request!

Just put it this way .. I am in the US.  The unit is to be a PVR .. Personal Video Recorder (which is what PVR means).  And I mentioned that he is on cable and not off the air already.

---

### Post by shad0w_walker on 2008-08-03
Well that's a paranoid response if ever there was one. I don't recall him asking for your address, but a general region. Each country/area tends to have it's own weird way of doing things.

The what you want to watch no doubt has to do with you won't be able to directly tune to non free to air channels using a tuner card, so before you start getting all paranoid and whiney I suggest you screw your head on and realise that we are trying to help you, bitching is not the way to make us want to do so.

---

### Post by oldsoundguy on 2008-08-03
OK ...
 In the USA
 On digital cable and paying for it already.
 Want to record OFF of the cable (IE TIVO type) without adding the cost of 
a cable company hard drive recorder to that cable charge. (already has "On Demand".)
 It can be done
 All I asked was a recommendation for the video capture card (has to be PCI not PCIe) (I listed the computer equipment and most of this in the initial post.)

---

### Post by nickrout on 2008-08-03
If you have digital cable I am guessing you need a DVB-C card, but I would ask on the mythtv users mailing list. 

You should check out whether the cable delivers encrypted or unencrypted data, if it is encrypted you may be SOL.

And yes your whereabouts and the type of TV you are trying to capture is important. Different countries have different standards.

---

### Post by shad0w_walker on 2008-08-03
If you are on a subscription, odds are the major channels are all encrypted to atleast some degree, which means either, you might be able to find a card reader/decrypter that you install on your PVR to get the stream directly, or more likely you will have to take the output of the STB and pipe that into your TV card so that you have unencrypted streams, this would of course also require a IR blaster or other method of STB control.

---

### Post by oldsoundguy on 2008-08-03
All but the subscription channels and the HDTV channels are un-encrypted and QAM I believe .. on demand on the FREE movies also un-encrypted. 
Comcast cable.

---

### Post by wisenuts on 2008-08-03
Try linuxmce....its BAMF!:popcorn:

---

### Post by oldsoundguy on 2008-08-03
I am open on the software and will try several things as I want to set it up for him to be as easy to use and to be as stable as all possible.  My brother is wheelchair bound and is unable to repair things .. that is my jurisdiction .. but the question is not software, but hardware.

---

### Post by nickrout on 2008-08-03
I am unfamiliar with what hardware is good for digital cable in the US, which is why I suggested Mythtv-user mailing list.

---

### Post by oldsoundguy on 2008-08-03
and I do appreciate that.  But there HAS to be US users that have the knowledge other than going on a mailing list

The last time I went on a mailing list for information was with Handhelds.org and their mailing list became a spamming list!  Not saying this would happen with the Myth peeps, but I AM a tad gun shy over mailing lists because of that.

I am REALLY awaiting the shake out of Mediabuntu .. for my own usage as a media controller.  Rumors make me salivate!! LOL

But. I will continue to work on this for my brother.  It is not of dire need, except to get the stuff off the floor and out of here!!

---

### Post by nickrout on 2008-08-03
The mailing list is not spammy at all [1] although sometimes goes a little off topic. 

It is high volume though and you'll want to filter it to a folder in your email client. It is simply the best support for mythtv, far better than this forum.

Alternatively you could search through the archives:

[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

Lastly (but maybe not leastly) you could try a new thread on here with a more directed subject line - something like "Which tuner card for US digital cable?" - might get more answers.

[1] I saw one spam last week which provoked a long largely OT thread but it is a rare event.

---

### Post by fatlard on 2008-08-06
I will recommend a card for you.

How about a PVR 150?

It is an older card so you can find it on eBay.  This has a built in tuner to get all your analog channels from 2-125? but as for the digital channels I can offer no advice.

---

### Post by nickrout on 2008-08-06
> **fatlard said:**
> I will recommend a card for you.

How about a PVR 150?

It is an older card so you can find it on eBay.  This has a built in tuner to get all your analog channels from 2-125? but as for the digital channels I can offer no advice.

he said DIGITAL cable, not analogue.

---

### Post by dsbw on 2008-08-06
The KWorld ATSC 115 is cheap and now works without tweaking in Mythbuntu.

---

### Post by oldsoundguy on 2008-08-06
Thanks to a couple of you that actually responded .. this area of the Ubuntu forums seems to be off in the corner somewhere and very little traffic.

I picked up a DVico Fusion HDTV5 RT Gold after much searching.  THINK this will do for the unit as it does spec out quite nicely. The only issue will be IF Mythbuntu likes it!

---

