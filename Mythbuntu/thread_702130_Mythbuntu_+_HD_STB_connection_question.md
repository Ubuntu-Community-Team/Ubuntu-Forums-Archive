---
title: "Mythbuntu + HD STB connection question"
date: 2008-02-20
forum: Mythbuntu
---

### Post by 4dognight on 2008-02-20
OK, Im still a newb, when it comes to myhtbuntu. I have played around with my PVR350 and mythbuntu, and understand how it all connects and works. 
I just got a new HDTV and not sure how to hook this up to my cable HD STB and Mythbuntu. In order to get all the HD channels that cable offers, I still need their STB despite HD being 'free'. So, my question is, how do i hook it up to my Myth box? Obviously I dont have an HDMI input on my Myth box. My only options I see are Coax and Svideo inputs, on a HDTV Tuner card. So, do i set it to channel 3 on the HD Tuner card? Will that still be an HD signal coming from the coax coming out of the STB? Im confused. It seems like Im going to lose HD somehow connecting it up like this. And if the signal coming out of the STB is on channel 3, do I  even need a HD Tuner in my Myth box???

Thanks in advance.

---

### Post by foxbuntu on 2008-02-20
Your best option to use your Cable with Myth and get HD video is to buy an HDHomeRun. Then you can connect the Coax cable line from your cable company directly to the HDHR and it will record in QAM format (Digital cable). Otherwise you will need to use something like a HD cable card, Firewire from your STB or DVB-C card, however most of the later options are not supported in the US by cable companies and thus you would not be able to use them.

---

### Post by volkswagner on 2008-02-20
I agree.  There are several cards that offer QAM, including KWorld 110 & 115 p series.  Since they just capture MPG2 directly they should all be equal in quality.  Just make sure it is supported in Mythtv.  You should contact your cable co. and request a box with firewire enabled.  This may give you a few more channels.  You wont be able to capture premium channels.  All cable companies allow different channels, and block with 5c.

---

### Post by 4dognight on 2008-02-20
Hmm, this isn't what I wanted to hear.:(

I have tried plugging my coax directly into my hdtv and was able to pick up the QAM channels. So, this would be what I can expect with an HDTV tuner that I put in my Myth box? 

So this still leaves me unable to get all those other 'free'  HD channels that my cable company is 'giving' away. I will ask them about the firewire port. It sounds like even if that is enabled , I wont even get all the other channels.  If the firewire is enabled, will that mean it is a tru 1080i HD output?

Also, if I do just go with the Channel 3 option, what would the resolution be coming out of the STB coax? 

Something tells me Im stuck with renting that crappy DVR from my cable company for HD.  :cry:

---

### Post by volkswagner on 2008-02-20
What other free channels are you referring to?  I am still in the process of setting up my SA 3250HD box, so I an no expert.  I was however, successful in tuning all major networks, and many others ESPN, TNT, CSPAN, etc.  I feel confident I will be able basic channels.  If you capture with your PVR350, you will be at SD res.  I do not know of any solution that will capture HD via. component or S-Video.

---

### Post by 4dognight on 2008-02-20
All the other HD channels other than the local Networks are "free' according to Cox. You don't pay any HD fee. But they don't advertise that You have to use their STB to get those channels. So, I can have all the free HD programming I want. I just can't watch it without their STB  cause its encrypted!

Anyway, I just got back from Customer service. They never heard of Firewire. I pointed it out on their DVR STB(its labeld 1394). She said it would be disabled probably. I ordered a  HDSTB anyway, and will check when I get it delivered, as they dont even carry them, they have to be ordered.

There has to be a way to record these NON QAM HD Channels using their STB and Myth , right?

---

### Post by newlinux on 2008-02-20
The only way to record them in HDTV is if the firewire is enabled and the 5c encryption is turned off. Say hello to DRM and the future it brings.

---

### Post by 4dognight on 2008-02-20
Well that sucks.

So what I dont get is, why can I record HD on their dvr , but not my own? It cant be DRM, as I can record HD as long as its on their hardware and not my own.

I get this feeling that creating my own DVR has just lost its appeal. Now that Im stuck recording local networks in HD. I guess if I want to record those other channels I have to keep their DVR. So much for saving any $ by returning their DVR.:( 

I did some googling and read up on this FCC mandate forcing them to provide firewire. But then I read, that they encrypt everything. So even if I get firewire enabled, Im still screwed.  

I tried using the builtin tunerin my HDTV and could only get the local networks and some other crap stations in the clear. 

:mad:

---

### Post by newlinux on 2008-02-21
> **4dognight said:**
> Well that sucks.

So what I dont get is, why can I record HD on their dvr , but not my own? It cant be DRM, as I can record HD as long as its on their hardware and not my own.


That's pretty much the definition of DRM, only being able to transfer native recordings to proprietary, controlled, Digital Rights Managed hardware. It is DRM. If the device you wan't to watch your show on can't have its rights managed, then you can't use it with DRM'd things. Just like cable cards, blu-ray discs, even DVDs (but the DRM has been cracked for DVDs). If you had a D-VHS player, which is 5c compliant (DRM compliant) you could transfer your recordings via firewire from the cable box or DVR even on 5c encrypted channels, but a linux PC will never be 5c compliant.

---

### Post by 4dognight on 2008-02-21
From what I  am hearing then, there doesn't seem to be any point in using Myth for HD. Might as well just get a HDTivo or use the cable company's DVR.

---

### Post by newlinux on 2008-02-21
If a lot of your recording is beyond the HD locals, I agree with you. For me, 90% of what I record is on the HD locals, anothe 5% I can't get from firewire in HD from my cable box, and the rest I just have to live with in standard definition or watch it when it comes on. So it is worth it for me, especially considering I stream this content to 4 different locations in my house, which would be cost prohibitive if I were to buy and HDTivo or rent company DVRs for that many rooms, not too mention I use mythvideo quite a bit and many other features I won't get from those. And I use all the computers for other purposes as well...

As you can see, your cable company really isn't giving away those other free HD stations. They're trapping you more and more into their hardware for DVR functionality, or you have to buy one of those expensive Vista Cable Card HTPCs, with DRM all over the place (but you can record everything you want in HD), or a tivoHD or S3. And then the cable company will probably charge you a small fee for the cable card. But hey, they are better than satellite providers :)

But better you find this out now, than before you drop some money into it :)

---

### Post by 4dognight on 2008-02-21
Unfortunately , I lept before looking! I have already sunk a ton of time and $$ (including the  tax rebate! ) into this.

I would have to say that most of my recording is in the local networks also. But still sucks that Animal Planet will have to be SD ;-) I only have one HDTV so at least the other SDTV wont be missing anything.

---

