---
title: "When is the best time to add components for new Mythbuntu box?"
date: 2007-12-20
forum: Mythbuntu
---

### Post by despidey on 2007-12-20
I'm a total noob but have had great luck w/ two installs of Ubuntu and one of Xbuntu. I'm going to use an older computer - P4 1.7  for a trial Mythbuntu box. After reading thru the documentation I know that I have to add cards - nVidia 6200, PVR-150, a new (used) hard drive and some RAM.  

Are there any size limitations for the hard drive?  I have an 800GB from a dead file server
Should I install the hardware before I load up Mythbuntu (machine is currently Win2K) or after?  
Any issues I should be aware of?

---

### Post by newlinux on 2007-12-20
> **despidey said:**
> I'm a total noob but have had great luck w/ two installs of Ubuntu and one of Xbuntu. I'm going to use an older computer - P4 1.7  for a trial Mythbuntu box. After reading thru the documentation I know that I have to add cards - nVidia 6200, PVR-150, a new (used) hard drive and some RAM.  

Are there any size limitations for the hard drive?  I have an 800GB from a dead file server
Should I install the hardware before I load up Mythbuntu (machine is currently Win2K) or after?  
Any issues I should be aware of?

Yes, you should install the hardware and make sure your BIOS recognizes before running mythbuntu.

any particular reason you already know you have to add a video card and RAM? How much Ram do your currently have and what is your current video card? 

A 800GB hard drive should be recognized fine in Linux AFAIK, but it's possible your BIOS might not recognize that size... usually a BIOS update will fix that...

---

### Post by despidey on 2007-12-20
[QUOTE=any particular reason you already know you have to add a video card and RAM? How much Ram do your currently have and what is your current video card? [/QUOTE]

I read the system requirements for and thought that was what is needed.  I currently have:
256MB RAM
nVidia GeForce 2MX video card
40 GB drive

We replaced a number of computers about 3 years ago (mostly 300-700Mhz Celerons) and they have been lying around waiting for something to happen.  This computer was the best of them and I thought it would be fun and instructive to make a trial run and build a Mythbuntu box for our bedroom TV. Once I get it all figured out then I intend to build a better one for the HDTV home theater setup in the living room. I'm a semi-retired 63 year old and since I discovered Ubuntu, which I think is awesome, I've made a list of projects for these computers. My first was to install Ubuntu on my old T-30 laptop - works great with no tweaks.  This is the next one.  Am I being too ambitious?

---

### Post by newlinux on 2007-12-20
> **despidey said:**
> ....  Am I being too ambitious?

Not at all. Myth will probably require some tweaks, but it will help you with your future build. I think your approach is a good one.

You know for a standard definition machine you might try setting it up as is before buying hardware (although if you record much, that hard drive will definitely be to small, so go ahead and install the hard drive). With only 1 tuner card, you'd have to do an awful lot of recording to fill up an 800 GB disk... but you may be interested in archiving dvds and music and pictures, so you can never really have too much). If you do buy the new hardware it will definitely work fine for a standard definition mythbox. But it might work okay without it. If the price of new components isn't much of a concern, go for it and install them first before installing mythbuntu - might make it easier.

Just for reference, I have a P4 2.6Ghz with a 440MX card that does HD. Granted, it does have 2GB of memory, but It doesn't need that much. I just had some extra RAM from other systems to put in it.

---

### Post by despidey on 2007-12-20
> **newlinux said:**
> Not at all. Myth will probably require some tweaks, but it will help you with your future build. I think your approach is a good one.

You know for a standard definition machine you might try setting it up as is before buying hardware (although if you record much, that hard drive will definitely be to small, so go ahead and install the hard drive). With only 1 tuner card, you'd have to do an awful lot of recording to fill up an 800 GB disk... but you may be interested in archiving dvds and music and pictures, so you can never really have too much). If you do buy the new hardware it will definitely work fine for a standard definition mythbox. But it might work okay without it. If the price of new components isn't much of a concern, go for it and install them first before installing mythbuntu - might make it easier.

Just for reference, I have a P4 2.6Ghz with a 440MX card that does HD. Granted, it does have 2GB of memory, but It doesn't need that much. I just had some extra RAM from other systems to put in it.

Is RAM more important than processor speed for Myth?  I still have two empty slots - I might be able to snatch RAM out of the other machines lying around.  I'll drop in the PVR-150.  I already have the 6200 but I could save it for the HDTV box.  I also have a couple of 350 Gig drives lying around - I probably should use one of them instead. If all goes well, then I'll probably get either a PVR-500 or two 150s for the HDTV box and use the 800Gig in there. But for now, I'm gonna set up the simple box.  

BTW, I think that this is an amazing community - incredibly helpful, friendly and responsive.  I'm looking forward to becoming an all Ubuntu all the time user.

---

### Post by newlinux on 2007-12-20
> **despidey said:**
> Is RAM more important than processor speed for Myth?  I still have two empty slots - I might be able to snatch RAM out of the other machines lying around.  I'll drop in the PVR-150.  I already have the 6200 but I could save it for the HDTV box.  I also have a couple of 350 Gig drives lying around - I probably should use one of them instead. If all goes well, then I'll probably get either a PVR-500 or two 150s for the HDTV box and use the 800Gig in there. But for now, I'm gonna set up the simple box.  

BTW, I think that this is an amazing community - incredibly helpful, friendly and responsive.  I'm looking forward to becoming an all Ubuntu all the time user.

No, I don't think RAM is more important. For what you are doing, I'd bet 512MB would be sufficient, and actually think 256 would work, but I'm not sure. The processor is definitely more important, though

The 6200 would work great for an HD box (I use a 6150 and a 6200 for my HD frontends connected to my main HDTVs - the P4/440MXis connected to a computer monitor and doubles as my regular desktop). It's good to have around if you can't get it working with the 2MX.

One thing to note is that you won't get HD from a PVR-150 or 500. Those are analog only tuner/capture cards. You'll need a digital card to record HD via cable or OTA.

I joined the ubuntu community a year and a half ago, and I feel the same way you do. Which is why I try to help people. I didn't know anything about myth when I started, and hadn't used Linux in over a decade. I had forgot most of what I knew. Now I pretty much use Linux  at home 100% of the time.

---

### Post by despidey on 2007-12-20
> **newlinux said:**
> No, I don't think RAM is more important. For what you are doing, I'd bet 512MB would be sufficient, and actually think 256 would work, but I'm not sure. The processor is definitely more important, though

The 6200 would work great for an HD box (I use a 6150 and a 6200 for my HD frontends connected to my main HDTVs - the P4/440MXis connected to a computer monitor and doubles as my regular desktop). It's good to have around if you can't get it working with the 2MX.

One thing to note is that you won't get HD from a PVR-150 or 500. Those are analog only tuner/capture cards. You'll need a digital card to record HD via cable or OTA.

I joined the ubuntu community a year and a half ago, and I feel the same way you do. Which is why I try to help people. I didn't know anything about myth when I started, and hadn't used Linux in over a decade. I had forgot most of what I knew. Now I pretty much use Linux  at home 100% of the time.

Do you suggest setting up a separate front end when I finally get around to doing the HDTV stuff and using my "regular" computer for the back end?    
Which TV card do you use for HDTV? 

Sorry for all the questions - this stuff is absolutely fascinating and I'm learning more about home theater computers in the last week than I did in the 3 years I've been messing with it.  UP with the penguin!

---

### Post by newlinux on 2007-12-20
You could do both really. You could have a master backend and a slave backend. But if you just want one of the machines to be a backend, make sure and put a large hard drive in it, and make sure it has enough slots fo the cards you want to use (or you could use a networked device like the HDHomerun. 

The decision should be based on your hardware (slots, hard drive space), how else you'll use the computers, how stable they are, etc. The advantage of using your HD frontend computer as a backend as well is that you can have faster commercial flagging (for commercial skip) and extend the hard drive space for your total set of recordings. The disadvantage is more backends to maintain.

I use 3 backends. 2 of them have tuner cards in them and record, and one is just a master backend that is used for commercial flagging and is also a web server, file server, etc. They are also all frontends as well. Then you just have the frontends point to the master backend. If one of the slave backends is down, It can record with the other one. I know I'm not helping much but it is hard to say. there are pluses and minuses and what you should do depends on your situtation. You also have to consider your network bandwidth and where you TV/cable connections will be.

Are you planning on getting your HDTV over the Air or from cable? I use the Kworld ATSC 110, Avermedia A180, and Dvico Fusion 5 lite. They all provide an equivalent stream, but the Kworld was the least expensive (I have 3 of those). The Dvico was the easiest to get working, but all of them are fairly easy to get working (setup in myth is different story, but should be equivalent for all of them).

---

### Post by despidey on 2007-12-21
> **newlinux said:**
> You could do both really. You could have a master backend and a slave backend. But if you just want one of the machines to be a backend, make sure and put a large hard drive in it, and make sure it has enough slots fo the cards you want to use (or you could use a networked device like the HDHomerun. 

The decision should be based on your hardware (slots, hard drive space), how else you'll use the computers, how stable they are, etc. The advantage of using your HD frontend computer as a backend as well is that you can have faster commercial flagging (for commercial skip) and extend the hard drive space for your total set of recordings. The disadvantage is more backends to maintain.

I use 3 backends. 2 of them have tuner cards in them and record, and one is just a master backend that is used for commercial flagging and is also a web server, file server, etc. They are also all frontends as well. Then you just have the frontends point to the master backend. If one of the slave backends is down, It can record with the other one. I know I'm not helping much but it is hard to say. there are pluses and minuses and what you should do depends on your situtation. You also have to consider your network bandwidth and where you TV/cable connections will be.

Are you planning on getting your HDTV over the Air or from cable? I use the Kworld ATSC 110, Avermedia A180, and Dvico Fusion 5 lite. They all provide an equivalent stream, but the Kworld was the least expensive (I have 3 of those). The Dvico was the easiest to get working, but all of them are fairly easy to get working (setup in myth is different story, but should be equivalent for all of them).

I will be getting my HDTV signal from cable. Meanwhile, I'll work on the analog box.  I already have the 6200 and PVR-150.  Baby steps feel right to me.

Good grief!!  there is still a lot I am clueless about.  :confused:   I guess I'll have to read up some more.   I'm not even sure of the answer to basic questions like, what's the difference between a front end and back end, can a front end be totally run with a remote or is a monitor, keyboard, mouse required, etc.  Can you point me to a good site for this info?  Thanks.

---

