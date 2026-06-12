---
title: "Capture Card for HD Cable input"
date: 2009-12-17
forum: Mythbuntu
---

### Post by tylersontag on 2009-12-17
Hey all,

I have my eye on a pchdtv 5500 capture card but, knowing the constraint on interpreting HD signals on a cable line i had some apprehension.  I know i'll be able to get over-the-air signals (Fox, ABC, etc.) and i'll count out getting any premium channels (HBO... i don't even pay for it so i'd be surprised if i could!)  But i would like to get my standard cable channels in HD if possible (FX, Discovery, History...)  

I've read its kind of a toss up, just whether or not my cable company (Cox Communications in this case) wants to be d#%ks and and encrypt the signal. If they are though, i've heard some people have success with certain cards+windows of getting them to play.  Are there any linux compatible cards that might be a little better in this endeavor?

---

### Post by mitchell2345 on 2009-12-17
HD-PVR captures component HD signals out of your STB.  Its the only way to record HD encrypted signals.

~Mitchell

---

### Post by tylersontag on 2009-12-18
Hmm, but i still need a STB?  Is this like a firewire streaming solution, in  that its just going to record whatever my STB is streaming out?  Or would i still be able to control the incoming content (i.e change the channel, setup auto-recording, etc.) through my computer?

---

### Post by the_pod on 2009-12-18
If they're encrypted you'll need the STB.  I have comcast and get the networks (ABC, NBC, Fox, CBS) in HD over the cable line the same as I would OTA unencrypted.  All other HD channels are encrypted so I don't get them (no STB in my house and I don't pay for that service). 

I use a HVR-1600 and a 1250.  

FWIW.

---

### Post by klc5555 on 2009-12-18
> **tylersontag said:**
> Hmm, but i still need a STB?  Is this like a firewire streaming solution, in  that its just going to record whatever my STB is streaming out?  Or would i still be able to control the incoming content (i.e change the channel, setup auto-recording, etc.) through my computer?

For the encrypted channels, you record what the STB (or DTA) spews out. Usually analog to an analog tuner (like a Hauppauge 1600, 150, etc.). You need to have Mythtv change channels on the STB to make scheduled recordings practical. This involves Mythtv transmitting IR codes directly to your STB as though Myth were an IR remote control. The IR transmitter (IR blaster) that does this will generally hook either to the serial port or to a USB port and interface with Mythtv via the frequently infuriating LIRC software. 

Simultaneous recordings of encrypteds require 2 tuners and 2 STBs (or 3 and 3 ... etc.). 

Non-encrypteds are handled by Mythtv directly via any old clear-QAM tuners.

---

### Post by tylersontag on 2009-12-22
makes sense, but some of my reason for this build was to avoid the $10 a month for the DTA, add in the cost of those Haupauge systems (though cool they are) and i think i'll be going with the pcHD550 and settling for low rez (i don't have a vid card with HD-OUT anyways... i was gonna get one but i think i'll just put my foot down on this money-trap-media-center)

Look forward to getting it setup, hopefully i won't be back here with a head scratcher :-D

---

