---
title: "Mythbuntu beginner"
date: 2008-10-05
forum: Mythbuntu
---

### Post by patrick0605 on 2008-10-05
Ok, so I've been wanting to do this for a while now, and now that I have the funds to do so I'd like to plan this out so I can get it up and running somewhat soon.

I'm not sure exactly how I would go about this so I'm looking for the experts to help.

I'm going to use a shuttle PC as the server/recorder/backend, which will be connected to my STB via Firewire.

I want to use an Apple TV as the frontend, or at least I think that the apple TV would be the frontend.  

I just want to make sure that's how this works, am I headed in the proper direction?  

I'm sure there is a walk through on how to install both the backend and the frontend, can someone link me to that, please?


Mainly I'm just interested in how this all works, can I do what I have in mind?  Or is there a better way to make this work?

Thanks,

Patrick

---

### Post by patrick0605 on 2008-10-07
Bump...

Anyone?

---

### Post by anonymousdog on 2008-10-08
The shuttle should be fine for a dedicated backend.  Frontend functions on that backend would require more video, CPU and memory than a dedicated backend machine.  Commflagging, transcoding and similar user jobs will tax the resources on a dedicated backend more than anything else it does.

I'm not seeing many posts from folks successfully running Apple TV as a frontend (though it's definitely been done).  It just looks harder to install linux on the Apple TV than some other front end options.

Are you planning on viewing HD recordings on the frontend?

---

### Post by patrick0605 on 2008-10-08
Hmmm, after doing a bit of thinking, i'm going to skip the apple tv since the backend will be in the same room as my TV, a seperate front end doesn't make sense to me.  I'm going to put the money that I would have spent on the apple tv into a whole backend/frontend system.

So far I've got a Dual-Core Pentium (E2180) 1GB of ram, will probably add another 1GB later on, 500GB Seagate HDD.  I haven't decided which video card to go with, any suggestions?

Yes, HD will be viewed, but that wont be till around Christmas when I hopefully pic up an HDTV on the cheap.

---

### Post by Archmage on 2008-10-08
I think the more important questions at the start is what video-capture card you are using.

But did you check out the hardware suggestions for MythTV?

---

### Post by patrick0605 on 2008-10-08
> **Archmage said:**
> I think the more important questions at the start is what video-capture card you are using.

But did you check out the hardware suggestions for MythTV?


I'm not going to use a capture card, I'm going to be using a firewire connection.

---

### Post by newlinux on 2008-10-08
Have you confirmed you'll be able to get the stations you want via firewire?

I'd recommend any inexpensive nvidia card that has the output connection you want to use with your HDTV. If you aren't gaming, you don't need to pay much at all for a video card. Onboard nvidia works fine too (I use it on 2 of my frontends). All my current nvidia are 6 or 7 series, all doing HD resolutions.

---

### Post by patrick0605 on 2008-10-08
I have Brighthouse cable, which uses the Scientific Atlantic boxes, a bit of google searching and it appears that people have had sucess using the firewire ports to connect to a PC.

---

### Post by newlinux on 2008-10-08
yes, that is true, but what stations are available from region to region (even within the same provider) varies. So even if the firewire port is enabled, it doesn't mean that the 5c setting is disabled on all channels. 5c has to be disabled for a non DTCP compliant device (such as a PC) to be able to record video via firewire. 5c can be enabled channel by channel, even program by program.

---

### Post by patrick0605 on 2008-10-08
Hmm, wasn't aware of that.

Worse comes to worse, if it doesn't work and I have to buy a capture card then I will, but for now I'm going to go forward without it.

I decided to go ahead and pick a motherboard that has a built in video card (Geforce 7100), and it also has an HDMI plug as well.  I'm going to stick with the Intel e2180 CPU (dual core) and for now a 1GB stick of DDR2-800 ram.  I can always upgrade the CPU and add more ram later if the need arises.

Do you think that will be a strong enough system for a combined frontend/backend?

---

### Post by newlinux on 2008-10-08
> **patrick0605 said:**
> Hmm, wasn't aware of that.

Worse comes to worse, if it doesn't work and I have to buy a capture card then I will, but for now I'm going to go forward without it.

I decided to go ahead and pick a motherboard that has a built in video card (Geforce 7100), and it also has an HDMI plug as well.  I'm going to stick with the Intel e2180 CPU (dual core) and for now a 1GB stick of DDR2-800 ram.  I can always upgrade the CPU and add more ram later if the need arises.

Do you think that will be a strong enough system for a combined frontend/backend?

Just wanted you to not be dissapointed and know what might happen. I ended up capturing some channels via firewire and others via a capture card, as you mentioned.

Without a doubt it is strong enough. My fastest machines have a E2180 (with 1GB RAM) and X2 4600 (2GB RAM) both are HD capable frontend/backend systems. All my systems in my sig (except the celeron) are HD frontend/backend systems. I even used to have a P4 2.6 that could do HD and was a combined frontend backend, with a Geforce 440MX (but I would have to not have a lot of other things running).

---

### Post by patrick0605 on 2008-10-08
> **newlinux said:**
> Just wanted you to not be dissapointed and know what might happen. I ended up capturing some channels via firewire and others via a capture card, as you mentioned.

Without a doubt it is strong enough. My fastest machines have a E2180 (with 1GB RAM) and X2 4600 (2GB RAM) both are HD capable frontend/backend systems. All my systems in my sig (except the celeron) are HD frontend/backend systems. I even used to have a P4 2.6 that could do HD and was a combined frontend backend, with a Geforce 440MX (but I would have to not have a lot of other things running).

Thank you for your insight, it is much appreciated.

Since I'm the type of person that likes to research the crap out of everything, to the point where I've read the same article or how-to at least 3 times, what capture card do you recommend?  My guess is that the HD channels are also available OTA (sports and basic cable channels), so I probably wont have to pay for an HD box from my provider.

---

### Post by newlinux on 2008-10-09
For digital recording I recommend the cheapest supported card you can find. There is no difference in quality of signal from any of the cards from a digital standpoint, just a difference in the sensitivity of tuning (and that difference isn't great among the cards - in my experience it makes no difference).

You can probably get HD locals over clear QAM from your provider or you can get them OTA if you can pick them up from your house. I'm not sure what sports channels you are talking about getting, but all you get from OTA ATSC is are your local channels (FOX, CBS, NBC, ABC, CW, PBS affiates) and their subchannels digitally (and the major channels will be HD). You won't get most basic cable channels. IF your cable company is still transmitting analog you can get them with an analog tuner.

[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

Is a decent reference for digital cards and digital/analog hybrid cards. I use older cards that I've had for a couple of years because I've had no need to change them:

Kworld ATSC 110/115 (for QAM/OTA ATSC/NTSC)
Dvico Fusion 5 (for QAM/NTSC - but can do OTA ATSC)
Avermedia A180 (for QAM - but can do OTA ATSC)
PVR-150 (for NTSC and capture from cable boxes)
I used to have a pchdtv 5500, but I sold it and bought two more Kworlds.

---

