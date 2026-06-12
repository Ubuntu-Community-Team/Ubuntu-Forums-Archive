---
title: "Dual HDTV Tuner Solution"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by baekster on 2007-05-12
I'm trying to make a mytbox with dual tuners.  I have analog cable signal for the building (0-55 unencrypted).  And I'm pretty sure we have over-the-air HD signal (center town in Philadelphia).  What I want is either a dual tv tuner or a pair of tuners.  They need to be able to capture both analog and digital signal and should work together well.  So I can either record two shows at once or watch 1 show and record another, no matter whether the shows are HDTV or standard def analog.

I read about pcHD-5500.  It seems like something I want (a pair of them), but what worries me is that mysterious audio jack that needs to be connected to the sound card's AUX.  Apparently it's for analog signals (someone said that in some forum).  Is that true?

I am also open to suggestions for other cards, especially dual-tuner card or USB cards, as long as it has  hardware-based encoding.

if someone have set up a similar box and can tell me their experiences, it would be AWESOME.  Please, someone help!

---

### Post by tgm4883 on 2007-05-12
I have the HD5500 and the audio jack is only if you are using it for analog channels.  HD channels are streamed in mpeg2 and the audio is already in the stream.  The only thing that I have connected to that card is the cable from the cable company.  It works great with a simple loading of 1 driver

---

### Post by baekster on 2007-05-13
> **tgm4883 said:**
> I have the HD5500 and the audio jack is only if you are using it for analog channels.  HD channels are streamed in mpeg2 and the audio is already in the stream.  The only thing that I have connected to that card is the cable from the cable company.  It works great with a simple loading of 1 driver

Well...yes, HD contains audio but I also need to record non-HD channels as well.  if you don't use the audio jack, does it mean that your analog recordings won't have audio?  If so, how does someone deal with having two pcHD5500 then?  Most people only have one audio card...  Have you tried recording analog channels without the audio jack?  If you haven't, do you mind trying it and tell me how it goes?  :)  I would really appreciate it.

---

### Post by tgm4883 on 2007-05-13
You won't have audio for the analog shows if you don't use the cable.  You need the cable because these tuners don't have a hardware encoder for the analog shows (HD doesn't need a hardware encoder)

What are the specs of the computer your using for this?

For my analog shows I use a PVR-150 which is a single tuner analog card with a hardware encoder.  There is a  dual tuner card called the PVR-500 that has two tuners on the same card, and also has a hardware encoder.  Neither of these do HD though.  I recommend getting one of these as software encoding is a: more trouble than its worth and b:  pretty cpu intensive

Go here and find out what HD channels you will get with an antenna.  You may not feel the need for two HD5500's.  Also, when you do install these cards, try plugging your cable into one of the cards.  I noticed that when I had just analog cable (through comcast, 1-70) that they did broadcast the HD channels too (only the ones that I would receive OTA).  If this is true in your case, it would give you a much better signal, and you wouldn't need an unsightly antenna

[http://www.antennaweb.org/aw/welcome.aspx](http://www.antennaweb.org/aw/welcome.aspx)

---

### Post by baekster on 2007-05-13
> **tgm4883 said:**
> You won't have audio for the analog shows if you don't use the cable.  You need the cable because these tuners don't have a hardware encoder for the analog shows (HD doesn't need a hardware encoder)

What are the specs of the computer your using for this?

For my analog shows I use a PVR-150 which is a single tuner analog card with a hardware encoder.  There is a  dual tuner card called the PVR-500 that has two tuners on the same card, and also has a hardware encoder.  Neither of these do HD though.  I recommend getting one of these as software encoding is a: more trouble than its worth and b:  pretty cpu intensive

[http://www.antennaweb.org/aw/welcome.aspx](http://www.antennaweb.org/aw/welcome.aspx)

Specs:  Don't have one yet.  It's actually something I wanted to ask about, too.  Currently I'm thinking AMD 64 X2 5800+, AMD 690G/SB600 based motherboard (it has built-in X1250 integrated card with HDMI/DVI output).  I think the built-in graphics is probably enough for displaying HD?  I was trying to decide whether to go with this and possibly another PCI-E dedicated card or buying an SLI-based motherboard+card.  I don't think we'll be doing any 3D gaming.

One thing that bothers me about the idea of having a separate analog recorder is that the chances are we'd want to record 2 HD shows at times.    Do you know of any HDTV capture cards that have hardware encoders for both analog and HD signals?

---

### Post by tgm4883 on 2007-05-13
So i guess your going with a microatx motherboard then, I don't know of any that do that (other than streaming from an STB)

The computer sounds fine, I have an X2 3800 and can watch an HD show while recording 2 others so those specs are fine.  One thing I would caution against is the ati graphics.   I have onboard 6100 and it works great.

---

### Post by baekster on 2007-05-13
> **tgm4883 said:**
> So i guess your going with a microatx motherboard then, I don't know of any that do that (other than streaming from an STB)

The computer sounds fine, I have an X2 3800 and can watch an HD show while recording 2 others so those specs are fine.  One thing I would caution against is the ati graphics.   I have onboard 6100 and it works great.

Is it really true that nVidia works better compared to ATI?  If you have some insight into this matter, let me know so I can buy the right parts.

Also do you use on-board audio?

BTW, thank you so much for all the help.  It's good to get some advice from people who've done it.

---

### Post by tgm4883 on 2007-05-13
nvidia tends to be more linux friendly so that is why it works better.  You can also turn on xvmc to help take the load off of the cpu.

I use onboard audio and it is great except for one thing.  It tends to be a little quiet on my tv (I use my tv speakers).  If I got a 5.1 receiver I would also get a different card so I could do optical out.  (My board doesn't have optical out)

---

### Post by baekster on 2007-05-13
> **tgm4883 said:**
> nvidia tends to be more linux friendly so that is why it works better.  You can also turn on xvmc to help take the load off of the cpu.

I use onboard audio and it is great except for one thing.  It tends to be a little quiet on my tv (I use my tv speakers).  If I got a 5.1 receiver I would also get a different card so I could do optical out.  (My board doesn't have optical out)

Is it true that built-in board will consume less energy (hence less heat)?  6100 is somewhat old model, isn't it?  Do you know if the support for 7050 is good?  And what's the deal with HDCP?  It sounds like some evil DRM thing that makes me cringe.

---

### Post by tgm4883 on 2007-05-13
> **baekster said:**
> Is it true that built-in board will consume less energy (hence less heat)?  6100 is somewhat old model, isn't it?  Do you know if the support for 7050 is good?  And what's the deal with HDCP?  It sounds like some evil DRM thing that makes me cringe.

It will produce less heat.  The 6100 is more than enough to help with the displaying the HD shows.  I think that there is support up to the 8800.  HDCP is High Definition Copy Protection and it requires an HDMI connection.  I'm not sure how it works with Linux, but basically the source (computer, HD-DVD player, Bluray player, etc) will ask the tv if it really is a tv and not some recorder to record teh signal (this is a huge simplification, but I think you get the point).  This only comes into play if the show your trying to watch is flagged to check for this.  If the tv doesn't respond (isn't HDCP capable) then the show will revert to only 540i (I think thats the resolution, don't quote me on that) .  But again, this only applies to shows that have this flag.  

In my opinion (and I would need to do a little more research on this) I would rather have the HDCP built in and not need it, then be restricted for not having it.  That said, I think that it's crap anyways but sometimes you have to play by others rules.  Go with the HDMI as the 1 cable of convenience is great and then you wont have to worry about not having the HDCP (assuming that Linux supports that).  You won't be able to get around the HDCP anyway if you went with something else such as component cable (they are capable of the same resolutions, but not HDCP)

:EDIT:

Wanted to add that the onboard 6100 works great for me.  I do no gaming on it as it is my backend/frontend mythtv box and nothing more.  The one you mentioned should be fine also.

---

### Post by superm1 on 2007-05-15
I should throw in a plug for these guys:

Silicon Dust HDHomeRun: [http://www.silicondust.com/](http://www.silicondust.com/)

It will handle two streams as once, either QAM or OTA.

---

### Post by baekster on 2007-05-16
:)  Unfortunately, HDHomeRun seems to be only digital capture card (the network aspect is interesting) however it doesn't capture analog signal if I understand this correctly.  If I'm wrong, let me know and I'll go ahead and buy it.  It still looks like I have to buy this plus a Hauppauge dual tuner...

---

### Post by superm1 on 2007-05-16
> **baekster said:**
> :)  Unfortunately, HDHomeRun seems to be only digital capture card (the network aspect is interesting) however it doesn't capture analog signal if I understand this correctly.  If I'm wrong, let me know and I'll go ahead and buy it.  It still looks like I have to buy this plus a Hauppauge dual tuner...

Unfortunately yes, digital only for the HDHomerun.

---

### Post by baekster on 2007-05-16
Ok, I think I decided on HDHomerun (2 digital tuners) + Hauppauge PVR-500 (2 analog tuners with hardware MPEG2 encoder).  Thanks to the people in the forum who helped me with the choices.  Maybe I'll post a site/wiki about my experiences.

---

### Post by baekster on 2007-06-25
I set up a rather expensive machine to do the job I set out to do:

OS + distro:
 Ubuntu Feisty (package kernel amd64 version).  I run openbox with custom script that starts mythfrontend, instead of Gnome in order to save memory.  (a mythbox doesn't really need a full blown desktop).  I tried Xubuntu-desktop but it doesn't seem to be as lean as I'd like.

PVR software:
 MythTV (package version)

Tuners:
 4-tuners (PVR-500 2 analog tuners+HDHOMERUN 2 digital tuners).

Processor:
 AMD X2 4200+ (62w)

Motherboard:
 MSI K9NBPM2-FID Socket AM2 NVIDIA Quadro NVS 210S Micro ATX (GEForce 6150)
 with DVI-D out (used DVI-to-HDMI cable), integrated audio

Memory:
 1 gig DDR2 667 dual channel RAM (Upgrading to 2 gig soon---to run mythplugins without swapping)

Hard Drive:
 500GB 7200 RPM SATA 3.0Gb (SAMSUNG SpinPoint T Series HD501LJ)

Case:
  Antec NSK2400 (very nice---quiet, cool, sleek, pretty cheap, standard M-ATX)

TV:
 Sharp Aquos Sharp LC-46D62U LCD TV (1080p, 46 inch)
============================================================================

Thoughts:
 1. I really like the Sharp LCD TV I bought (I recommend it to anyone who is thinking of buying one).  No overscan at 1920x1080 using DVI-HDMI using dot-to-dot mode.  PQ is just beautiful and 4ms response time is nice (though I don't really play video games).  Some units have banding isues but other vendors have light leakage around the edges.  Mine has no such issues even thought it was refurbished (lucky me).  Another thing I really like about the LCD TV is that it has "audio only" mode when I want to just play music through mythtv, but save the TV's display lifetime.
 2. MythTV operations (recording TV+viewing TV+comm flagging) doesn't take up that much CPU time, thanks to built-in MPEG2 encoder, XvMC enabled Nvidia card (using the restricted driver), etc. 
 3.  I never thought 1gig RAM isn't going to be enough.  With the on-board video stealing 128MB RAM, I see that the system starts swapping when I run MythWeb and start running some transcoding jobs in the back...which can sometimes result in slow-response time.  So I'm adding another 1gig soon.  They were cheap, but I think if I knew this issue, I would have bought 2 gig dual channel kit instead of 2 1-gig dual channel kit.  Lack of memory also could be an issue when MythTV fails to find a substitute of expiring Zap2It DataDirect service.  Then Web-Scraping for the program details and schedule can also add to the lack of memory issue (sigh--I worry about this so much that I can't even sleep at night...lol).

====================================================================
Please share your thoughts and setups for multiple tuners (especially mixing hdtv and sdtv).  When I was taking on this task, I wasn't really able to find such setup guide and considerations as easily as strictly SDTV or single HDTV or strictly digital, etc.

---

