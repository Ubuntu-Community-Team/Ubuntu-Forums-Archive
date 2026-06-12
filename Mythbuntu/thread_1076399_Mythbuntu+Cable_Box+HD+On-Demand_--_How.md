---
title: "Mythbuntu+Cable Box+HD+On-Demand -- How?"
date: 2009-02-21
forum: Mythbuntu
---

### Post by nighthawk98tj on 2009-02-21
Hi there,

I have a pretty new Mythbuntu box I've been running for SD cable for a while now, but the box was built with the power to do HD in the future.  The time has come and I am upgrading to HD and I am trying to figure out the best way to get everything working.  Here's the setup:

I have a system with a PVR-150 in it already and an HDMI output to the TV.

I am getting a cable box from the cable company (Comcast).

The issues I am wrangling with are how I can do all of the following:

1.  Watch and record SD channels.
2.  Watch and record unencrypted HD channels.
3.  Watch encrypted HD channels.
4.  Retain the ability to use the video on demand from Comcast through the cable box.

Unfortunately, I cannot come up with a plan to make all four items work and run everything through the Myth box.  I'm really hoping someone might have a similar setup and they can help me out.

Thank you very much!!

---

### Post by blackoper on 2009-02-21
1. any number of analog tuners
2. any number of hd qam tuners
3. hdpvr (component video/optical audio out to hdpvr and change the box channel with firewire channel change script) and a patched fixes of mythtv or mythtv-svn
4. not possible. Get a logitech harmony remote and quick switch to direct cable box and tv access and do your vod that way then switch back to myth when done.

---

### Post by nighthawk98tj on 2009-02-21
Thank you for the response!

Here's what I am thinking:

Cable comes out of the wall and split two ways:  One to the PVR150 in the Myth box and one to the Comcast box.  The PVR150 connection will allow recording of analog stations only.

From the Comcast box, run a firewire cable to the Myth box for unencrypted HD channels and channel changing functionality on the cable box.  This would allow recording of unencrypted HD channels.

From the Comcast box, also run an S-video cable to the PVR150 for digital channels that have to be accessed via the box but are not output via firewire.  This would also allow recording of digital cable channels.

From the Comcast box, run an HDMI cable directly to the TV for access to on-demand and encrypted HD channels (live viewing only, no recording ability).  I would have to flop over to the direct connection to access this content.

Do you think this will all work?  Do you foresee any possible issues with what I've outlined above?

The Logitech remotes look nice... which do you recommend?  I have five remotes involved in this system as it stands now!

---

### Post by crez79 on 2009-02-22
I have my cable box hooked up via firewire for the unencrypted channels and via s-video for the rest of the channels. You could also have cable only to the card for analog but for me it wasn't worth the hassle to get it so that cable/s-video and firewire/s-video didn't try to tune at the same time. It was much easier to just de-conflict s-video and firewire.

The hdmi cable from the cable box to the tv should work but there would be no way for myth to know what is going on with that for conflicts. Myth may change the channel while you are watching something via hdmi or worse you could change the channel while myth is recording. 

If you don't want/need it in hd you can tune to a cablebox station so it tunes via s-video and use the cable box remote to change the channel directly so myth knows you are watching tv wit the cable box and will at least let you know if there is a problem. It is a little tricky doing this because there is always at least a 5-6 second delay from the output of the cable box through myth and to your screen.

Since video on demand us usually broadcast unencrypted you could find the feed via firewire and order it up with the cable box and watch it via firewire or QAM. The video on demand channels are usually clustered together but aren't always broadcasting so it would be hard to program them all in. It is possible to have all the possible VOD channels added into the channel list (without EPG of course) and randomly check them to see if anyone else in the neighbourhood is watching something on VOD. The downsides to this is you don't know when or what is on and they might rewind/pause/fastforward/stop the show at any time, but if you ordered it that wouldn't be a problem.

There aren't really any elegant ways to do this but it may be worth it to you. I hope this makes at least a little sense to someone other than me...:rolleyes:

---

### Post by nighthawk98tj on 2009-02-22
Thank you for the response!

My original plan was to use the Myth box sort of on the side of the rest of the system and just jump over to it to either setup something to record or to watch a recording.  However, your point about Myth changing channels on the cable box or inadvertently changing a cable box channel when Myth is recording is a good one.

The reason I was going to run the coax was in order to have everything that did not require the cable box record over coax, which would be most of the channels we use.  Then, Myth would only access the cable box and possibly change channels on me for either an HD unencrypted channel, coming in over Firewire, or for a digital channel, coming in over S-Video.  Therefore, as long as I was recording an analog station (which I understand most of them still are), Myth would not conflict at all with the cable box.  Does that seem to make sense?

---

### Post by crez79 on 2009-02-22
Makes sense to me but most tuners don't allow you to capture from s-video and cable at the same time, so you would be limited to one at a time.

Because I had an extra analog tuner I use it for dedicated s-video capture. I have analog cable hooked up to a second tuner but it never gets used because the dual tuner HDHomerun, and either firewire or svideo from the cable box gets me what I need now.

I definitely recommend changing the cablebox channel with firewire because it is much more reliable.

---

### Post by nighthawk98tj on 2009-02-22
Sounds good.

My thought was to setup the PVR150 as follows:

Coax Cable Video Source:  Setup with as many channels as possible (all analog channels).

S-Video Source from Cable Box:  Setup with ONLY the digital channels, or at least give the coax source priority for non-digital channels.

This way, the myth box would use the coax as its primary source for anything that it can (ie analog channels).  Then, secondarily it would have to use the S-Video or the Firewire for digital or HD, respectively, if something was setup to record on those channels.

This is the idea, I'm just hoping that I can get it to work this way.

Question:  Does your HDHomerun allow you to watch encrypted HD channels on Myth?  My understanding is that it does not.  How do you watch encrypted channels such as Discovery HD, A&E HD, TNTHD, etc.?

Thanks!

---

### Post by blackoper on 2009-02-22
if you put the svideo tuner and the firewire tuner in the same input group for example "cablebox". This would cause myth to only use one of those inputs at a time, basically the one with the higher recording priority. The problem you will run into with using the box outside of mythtv (for direct tuning for hdmi on your tv) is that anything you have scheduled will automatically change the channel on your cablebox and geing recording causing no end of you annoyance until you quit using VOD and direct tuning alltogether (Ask me how I know)

---

### Post by crez79 on 2009-02-22
The HDhomerun does not tune encrypted channels. For any that are encrypted including the non-local hd channels, I have to use the cable box through s-video. It is not hd, but for now its better than not being able to watch these channels. I am waiting for an inexpensive easy soultion, which cable cards could be if cablelabs would let it.

blackoper is spot on about the input groups.

---

### Post by blackoper on 2009-02-22
crez I'm already using the hdpvr for recording pretty much everything on the cablebox (custom compiled mythtv.21 fixes with hdpvr support). Beign able to finally use myth for everything was worth the $200 cost for it. I don't think there will be another option/cheaper option anytime soon that will allow for recording of component cable with digital sound.

---

### Post by nighthawk98tj on 2009-02-22
Thank you for the responses!

It sounds like what I should do is forgo the coax directly the PVR150 and take it right to the cable box, then from there, run firewire and s-video back to the myth box and but both in the same recording group.

Then, basically I should use the myth box as the primary TV watching device and I feel I need to use on-demand, I can switch the TV over to the direct input from the cable box.  Same deal if I want to watch something on an encrypted HD channel.  However, I will just have to keep in mind I could be interrupted if I switch over to do that.

What sounds nice is that if I am watching/recording something on an encrypted HD channel through S-video and I want to watch it in HD, I can just change the input on the TV and the output on the audio receiver.

How are you guys bringing the sound over to the myth box from the cable box?  Left/right RCA's to the back of your tuner card?

---

### Post by nighthawk98tj on 2009-02-22
Could one of you also explain how the HDPVR unit might fit in and solve this issues I'm toying with?  I'm not sure exactly how this unit fits in and what, if anything, it replaces in the system.

Thanks!

---

### Post by crez79 on 2009-02-22
While recording via s-video you should be able to watch it straight from the cable box on the tv.

Yes I use the red and white rca cable for sound.

The HDPVR is what I am waiting for. It connects to the computer with USB and it takes the component output from the cable box and converts it to AVCHD in full HD. It would replace the s-video and tuner needed now. The next version of myth is supposed to incorporate it natively. There is a way to use it now, but is too far over my head right now. It is a little pricey, but I don't think there are too many other choices right now.

---

### Post by nighthawk98tj on 2009-02-22
Good to know.  I will await the native support and upgrade then.  For now, I think this setup will work for me.

---

