---
title: "HD Homerun and regular cable"
date: 2009-05-27
forum: Mythbuntu
---

### Post by scottac on 2009-05-27
Little bit of history before I ask my real question.  At one point I had a Windows MCE pc setup with a Haupauge HVR-1800.  I was able to tune all of the regular channels with this (not the qam-256) device. for example if I run a coaxial cable from the wall into the back of my HD TV I get all the standard cable channels (1-63) plus the qam-256 channels (72.1, 116.1, etc...). 

I just read this in the mythtv.org hdhomerun wiki:

       [B]"Since it tunes only digital signals (OTA HDTV as well as "Clear" QAM digital cable), 
       which are already  MPEG2 encoded, it has no MPEG encoding hardware)." [/B]

After reading this I am beginning to think that I am not going to be able to to tune the regular cable channels with the HDHomerun... I have been trying tirelessly trying to get these channels tuned to no avail and believe I have just now realized that I have wasted a lot of time.

can anyone confirm this for me.

thanks for any and all help here.

regards,
Fredo

---

### Post by cenwesi on 2009-05-27
Yes, it is digital not analog. Come June 17th or what ever the final deadline is we just have to wait and see how things play out. Either way i don't think you wasted your time. Eventually ALL the stations will go digital... I see comcast constantly moving and re-arranging all their analog channel to digital and that constantly screws up things...

---

### Post by LowSky on 2009-05-27
best option is to get an digital OTA antenna if you live close to a broadcasting area. the HDHomeRun is a digital only tuner it says so on Newegg and on their website, so you wont get any analog channels.

Secondly cable companies are going to require you use a digital cable box to get their cable channels, basically cutting out the Tivo and HTPC crowd, because these devices cut into their sales. and if my HDTV cable box is anything like yours you cannot use it with the tuner card to get your channels with it. Their is something called cablecard that is supposed to work with tuner cards but its extremely proprietary and requires the user to buy a OEM PC from a major vendor with e selected parts. HP/Dell make them, and they can cost a pretty penny.

right now, with a cable box I get about 300 channels, give or take, without it about 25. Its a crappy deal but the cable companies have control over the system. if you want this to change talk to your local politicians and ask them to support a bill requiring the cable companies to use more open systems.

---

### Post by scottac on 2009-05-27
> **LowSky said:**
> best option is to get an digital OTA antenna if you live close to a broadcasting area. the HDHomeRun is a digital only tuner it says so on Newegg and on their website, so you wont get any analog channels.

Yeah.  I figured this out right after I posted this.  Very disappointing.  However I am thinking that I might just buy a analog tuner card 

> **LowSky said:**
> Secondly cable companies are going to require you use a digital cable box to get their cable channels, basically cutting out the Tivo and HTPC crowd, because these devices cut into their sales. and if my HDTV cable box is anything like yours you cannot use it with the tuner card to get your channels with it. Their is something called cablecard that is supposed to work with tuner cards but its extremely proprietary and requires the user to buy a OEM PC from a major vendor with e selected parts. HP/Dell make them, and they can cost a pretty penny.

Really? I know you can set up mythtv with a set top box. What is the difference here?

---

### Post by LowSky on 2009-05-27
Just remember analog is going to be gone as of June 12 in the US, so no need to buy an analog card. Its up to the cable companies to iffer channels unencripted so we will se how they decide to do so. I have Cablevision and they decided that QAM is only going to be used for local channels, which sucks as before switching to digital I had like 70 channels on analog, so I know the pain.

Im not really up on the set top boxes being used with MythTV, as far as I know MythTV can only be connected to change the channel so it can be annoying to use for recording TV, but if you connect a settop box using coax to the TV or tuner you will ony get standard defintiton TV so it wont work with you HDHomerun.
You need component or HDMI cables for HDTV, and as far as I know no PC maker makes a HDMI input or Component input PCI card.

---

### Post by crez79 on 2009-05-27
Yes the HD Homerun does digital only. The switch to digital OTA on June 12th has nothing to do with cable at all. Although many cable companies are switching to digital signals, it has nothing to do with the June 12 deadline. It is a cram as much into the same bandwidth as possible to make more money situation that is pushing them. As long as the cable company doesn't encrypt the QAM, the HDHR can tune it. I am lucky and my cable company doesn't encrypt many channels, so my HDHR can tune it. I have an old hauppauge tuner that fills in the encrypted channels with the analog channels, so it works for me. 

I had a set top box connected via firewire for another clear QAM tuner and used firewire to change the channels for the stb to output to the hauppauge for the rest of the channels and it worked great. Not in HD for the encrypted channels, but was able to record everything I could watch on the stb. I got rid of the stb to knock fifty bucks off the cable bill and get rid of the premium channels that i rarely used. I find it better to rent any movies I want to watch or wait for them to be aired. 

Until cable cards are made less restrictive and on linux, there is no ideal solution...

---

### Post by LowSky on 2009-05-28
Cablecards less restrictive....hahahahahaha...ha!

Cable companies got so scared from the few people stealing cable, that they made the whole system a big pile of proprietary crap. Y HD channls look better OTA/QAM, then through their set top box.
Cable companies wont change their practices until they loose too many customers, and I really doubt it will happen, unless AT&T and Verizon's networks are that much better and cheaper.

---

### Post by crez79 on 2009-05-28
I am waiting for cable to go away and everything to be on demand like hulu, or from the websites of many networks. But if hulu's unwillingness to play well with others is any indication, it too is going to be a big pile of closed source drm'ed crap. They aren't making it very easy for law abiding citizens to enjoy their content without downloading it from the internet without commercials thereby not making them a dime. I would gladly pay an online provider what I pay for cable to just watch the shows I want even with commercials. Hopefully the internet pipes will enlarge a little bit more to deploy on demand on a large scale.

---

