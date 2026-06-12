---
title: "MythTV makes my head hurt. Advice, please."
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by DirtDawg on 2007-12-20
My wife wanted TiVo for Christmas, but we don't feel good about paying for the hardware *and* a monthly subscription. So I suggested MythTV.  Even though I've been reading about MythTV for several hours, but I still have some very basic questions (I'm completely new at this).

1) Is MythTV a viable substitute for TiVo? My research so far makes me think, "yes."

2) I have the 845G Intel Chipset. Right now there's an onboard 64Meg Video card and an onboard sound card. I'm pretty sure I need to get a new video card, but I'm still a little foggy on what I need. The plan was to hook our cable line to the computer, then use RCA cables to route it to the television. Our TV is an old analog one. Our cable is just one of those fatty wires (looks like [this]("http://www1.istockphoto.com/file_thumbview_approve/203376/2/istockphoto_203376_glowing_cable_wire.jpg")) and no cable box, just the wire sticking out the wall. Is it possible to get a TiVo-like setup with this arrangement, or am I missing something?

3) As far as video cards are concerned, I think I need to get a card with an input for the cable wire and RCA outputs. Is this correct? I have also seen many people talk about a tuner card. Is this required also or is this only to receive broadcast television?

4) I am under the impression that installing a distro specifically geared toward MythTV (ie Mythbuntu) with its own partition might be easiest. Is this the case and, if so, any suggestions would be welcome.

Other than that, from what I can tell, I think my hardware is probably good to go. For now I really need some clearing up on these very basic issues. I don't even want to attempt such a complex procedure or spend the money required for a nice card without knowing exactly what I'm getting into. 

Thanks.

---

### Post by andrewc6l on 2007-12-20
1. Yes, it's a viable substitute. Depending on where you live, you might still have to pay for a subscription (TV schedule information) - but $20/year to schedulesdirect.com is better than TiVo prices.

2. The hardware requirements for MythTV are here:
[http://www.mythbuntu.org/requirements](http://www.mythbuntu.org/requirements)

My 1.2 GHz box with a cheapo nVidia 6200 is too slow to do HDTV without stuttering - depending on your machine, you might need a faster machine, then think about video cards. My video card also has an SVideo output, which is nice (but not so much mandatory these days as newer LCD TVs have video inputs). I would say try it with the video card you have, and then upgrade if you need to.

3.  You'll also need a tuner card. I'm using the PCHDTV 5500 ([http://pchdtv.com](http://pchdtv.com)), and it's pretty good for over-the-air signals. Cable / encrypted HD signals will probably have to go through a cable box before going to your tuner card.

4. I'd dedicate a machine to MythTV and install Mythbuntu to it. The box will need to be on all the time in order to record.

You'll also probably want a remote. I've just started using the StreamZap remote, so I can't say how good it is long-term. In general you want to avoid analog-only capture cards (at least in the US) because of the digital switch in Feburary 2009.

Warning: you end up watching more TV than you did before :-)

---

### Post by DirtDawg on 2007-12-21
Thanks for your input.

So, it sounds like I will need to buy a new video card (my computer has no output other than the monitor output) *and* a tuner card *and* a cable box? Ouch. Costs are adding up quick.

It even sounds like the best bet would investing in an entirely new box to run the system which is an entirely different animal altogether. 

Hmmmm, maybe my idea was not such a good one. I was hoping to buy a graphics card for $150 or so and that was it. I have already checked the rest of my hardware vs. requirements and I think I'm good.

---

### Post by andrewc6l on 2007-12-21
You'll only need a cable box if you use one currently. But yes, you'll want a video card that has svideo output (or some other way to connect your PC to the TV), and a tuner card (to connect your antenna/cable to the PC).

You could run with one PC if you wanted - it would be dedicated to MythTV (in other words, you wouldn't shut it down when you're not using it), but you can also do other things with it as well. However, most TV resolutions are pretty bad - so you'd probably also want a monitor for "real" work.

If you just want to start out, try getting a capture card and setting it up using your current monitor / PC. Then you can see if you want to go further.

---

### Post by DirtDawg on 2007-12-21
> **andrewc6l said:**
> You'll only need a cable box if you use one currently. But yes, you'll want a video card that has svideo output (or some other way to connect your PC to the TV), and a tuner card (to connect your antenna/cable to the PC).

You could run with one PC if you wanted - it would be dedicated to MythTV (in other words, you wouldn't shut it down when you're not using it), but you can also do other things with it as well. However, most TV resolutions are pretty bad - so you'd probably also want a monitor for "real" work.

If you just want to start out, try getting a capture card and setting it up using your current monitor / PC. Then you can see if you want to go further.

Thanks for clearing that up and the advice in general. :KS

---

