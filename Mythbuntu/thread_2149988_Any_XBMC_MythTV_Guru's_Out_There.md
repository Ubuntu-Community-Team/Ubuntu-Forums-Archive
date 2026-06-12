---
title: "Any XBMC MythTV Guru's Out There?"
date: 2013-05-30
forum: Mythbuntu
---

### Post by cbanakis on 2013-05-30
This is not specifically about Mythbuntu, but this seems like the best place to post.

I have been trying to get rid of Windows Media Center for years.  (Literally)
(My Media Centers, are the only Windows left in my life)

Everytime I find something I like, it has always been lacking in one way or another.

Finally, I found something that I like.  (XBMCbuntu)

The only thing it is lacking for me, is Live TV.

As far as I can tell, I can run the MythTV backend in order to get live TV in XBMC.
(theoretically anyway)

No matter what I read, or what I try, I can't seem to get this going.

TV tuners I have...
AVerMedia AVerTV Bravo Hybrid PCIe
Hauppauge WinTV HVR-1800 PCIe
Ceton InfiniTV 4 PCIe


The closest I have ever gotten to getting one of these to work is...
I managed to install the driver for the InfiniTV.  (Thats It)

When I go into the MythTV backend, it says "Failed To Open Card"

Every other attempt to get a driver installed, or get Myth to detect has done nothing.

I am seriously at the point where I want to just pay someone to come set it up.

Obviously, I would prefer to just get some help here, but if it comes down to it, and someone in the Chicagoland area is willing to come get this figured out, I am willing to pay.

Does anyone have any advise?

Or does anyone want a job?  LOL

Thanks for reading all this, and for any feedback you may have to offer.

At the moment, I am experimenting with XBMCbuntu 12.2
I have everything setup perfectly and everything works great. (Except for Live TV)

---

### Post by nickrout on 2013-05-30
Are you running one machine or two?

If one, install mythbuntu, get the tuner working then apt-get install xbmc

If two, ditto for the first stage and then get openelec - the PVR side of XBMC works like a charm on openelec.

However the xbmc frontend is IMHO inferior to the mythfrontend for recordings and live tv. I like XBMC as a media centre, but am still switching back to mythfrontend for TV.

---

### Post by klc5555 on 2013-05-31
> **nickrout said:**
> Are you running one machine or two?

However the xbmc frontend is IMHO inferior to the mythfrontend for recordings and live tv. I like XBMC as a media centre, but am still switching back to mythfrontend for TV.

I have to agree with you here: the incorporated mythfrontend client in XBMC 12.0 and 12.1 (haven't tried 12.2) is really not ready for use yet. Crash-prone, hang-prone at startup  --even editing Live-tv  settings is frequently enough to hang XBMC. I've come to disable XBMC's "Livetv" on all my XBMC installations and gone back to the old method of running XBMC from the Mythfrontend menu just as a drop-in replacement for mythvideo and mythmusic, and as a superior replacement for the annoying Hulu Desktop.

---

### Post by uteck on 2013-05-31
You might want to try using LinHES as your MythTV backend, it might do the configuration for you.  [http://linhes.org/](http://linhes.org/)
It has been a few years since I used it, but at the time the installer was fairly automated, so hopefully it will figure out your tuner card for you.  Setting up the backend is the hardest part of useing MythTV, and LinHES has some good training wheels to get you going.

O_O it looks like LinHES has built XBMC in.  I might have to reconsider my frontends.

---

### Post by uteck on 2013-05-31
Wops, double post.

---

### Post by cbanakis on 2013-05-31
Thanks for the posts.

I have a central 26tb file server, and 3 media centers.  (Bedroom, Living Room, Theater)

I have 2 AVerMedia AVerTV Bravo Hybrid PCIe, 1 Hauppauge WinTV HVR-1800 PCIe, and 1 Ceton InfiniTV 4 PCIe.

I would prefer to have them all as stand alone units that provide their own tv signal.

That way I do not have to leave 1 powered on all the time.

The file server is always on as it is, but its basically just an NAS, so I can't install a TV tuner in it.

I really won't be using the TV interface for much.  (Just news, and sports)

I will record from time to time, but not often.

If the XBMC front end will work for that, thats fine.

The primary function is to stream videos and music from my server, which is why I went with XBMC as the main interface.

But at this point, the immediate problem I am having, is getting my TV tuners to work with _ANYTHING_ aside with Windows Media Center.

Tried Media Portal when I was still into Windows.
Then Mythbuntu
Then (insert a dozen random linux based HTPC platforms)
And now XBMCbuntu

This was all over the last 5 years.
And every time, I ended up putting Windows back.

Honestly, all the bells and whistles in XBMC are pretty amazing, but if Windows just worked consistently, I would be fine with that.

I'm pretty sure if I can just get my tuners to work in Myth, that should get me to the point where I can figure out the rest on my own.

How bad is the XBMC frontend to Myth?
Do you think it will be fine for my needs?

---

### Post by cbanakis on 2013-05-31
> **uteck said:**
> You might want to try using LinHES as your MythTV backend, it might do the configuration for you.  [http://linhes.org/](http://linhes.org/)
It has been a few years since I used it, but at the time the installer was fairly automated, so hopefully it will figure out your tuner card for you.  Setting up the backend is the hardest part of useing MythTV, and LinHES has some good training wheels to get you going.

O_O it looks like LinHES has built XBMC in.  I might have to reconsider my frontends.

I tried that before as an OS, but never just as a backend.

Is it better as far as detecting hardware goes?

---

### Post by klc5555 on 2013-05-31
Problem: the AverTV Bravo Hybrid PCIe is unsupported under Linux. [http://www.linuxtv.org/wiki/index.php/AVerMedia](http://www.linuxtv.org/wiki/index.php/AVerMedia)

The Hauppauge HVR1800 PCIe appears to be only partially supported --digital is supported, but analog support depends on which analog tuner is built into a particular card. [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) However, available documentation on this card seems to be about 3 years old. Things may have changed since then.

The Ceton card, at least is fully supported --installation documentation here: [http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)

---

### Post by cbanakis on 2013-05-31
I found this page [http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Bravo_Hybrid_PCI-E_%28H788%29](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Bravo_Hybrid_PCI-E_%28H788%29)
At first I thought this meant there was a way to get the AverTV card working, but after a closer look, it looks like someone just tried to get it working at one point in time.  :(

That sucks, because I have 2 of them, and they are low profile.

The Hauppauge is fine, because there are no analog channels available any more in my area anyway.
(But it will only fit in one of my machines, as it is not low-profile)

I could not get Myth to connect to the Ceton, but as far as I can tell, it should work.
However, I still have not had a cable card installed from the cable company.

I only want local Clear QAM channels, but I guess the Ceton cannot do that until it has been paired with a cable card?

But then you can take the cable card out afterwards, and it still works?

So I can order Cable TV, get the card activated, then cancel service, and I can get Clear QAM with the Ceton?

IDK, everything I read about the Ceton with Clear QAM seems a bit odd.

Can anyone recommend some cheap low-profile Clear QAM capable cards that will work with ease on Myth?

---

### Post by klc5555 on 2013-05-31
Probably the easiest QAM card of all to use in Linux is the PCHDTV HD-5500, which is half-height, but is PCI (not PCIe) [http://www.pchdtv.com/](http://www.pchdtv.com/)  Now down to $89 evidently. You'll have to research a bit to find good half-height PCIe candidates, and then check their documentation over at linuxtv.org and/or the mythtv wiki to see how well these candidates are actually supported in Linux (and Mythtv)

But be aware that clear QAM is on its way out in the U.S., since the FCC cleared the way in December 2012 for all Cable Cos. to begin to encrypt the basic tier channels.  Eventually you will need a cablecard or a set top box to receive anything at all over cable. Many areas have already implemented this. You might wish to research what is happening in your area with your particular cable provider. Over the Air digital is unaffected, of course, and all these tuners handle 8VSB without problem.

---

### Post by cbanakis on 2013-05-31
> **klc5555 said:**
> Probably the easiest QAM card of all to use in Linux is the PCHDTV HD-5500, which is half-height, but is PCI (not PCIe) [http://www.pchdtv.com/](http://www.pchdtv.com/)  Now down to $89 evidently. You'll have to research a bit to find good half-height PCIe candidates, and then check their documentation over at linuxtv.org and/or the mythtv wiki to see how well these candidates are actually supported in Linux (and Mythtv)

But be aware that clear QAM is on its way out in the U.S., since the FCC cleared the way in December 2012 for all Cable Cos. to begin to encrypt the basic tier channels.  Eventually you will need a cablecard or a set top box to receive anything at all over cable. Many areas have already implemented this. You might wish to research what is happening in your area with your particular cable provider. Over the Air digital is unaffected, of course, and all these tuners handle 8VSB without problem.

Ah, so bad news, and more bad news.

None of my systems have old fashioned PCI slots.  :(

And the QAM thing...  Thats news to me.  :(

Have you had any experience with the Ceton Card?

If I can get that going, it would be a great all around card during this transition.

I can use QAM, and if and when my provider starts encrypting local channels, I can pay for basic cable, and get everything backup and running without having to change any hardware/software.

Is it true that the Ceton card will not work at all unless it has been paired with a cable card at one point?

Basically, what I have gathered, is that the card is basically locked, and needs to be activated by being paired.
At which time, it no longer needs the cable card in order to get QAM.

---

### Post by klc5555 on 2013-05-31
Sorry --no experience at all with the Ceton card.  Nor with PCIe cards in general. Since just about any junk can run mythbackend well, all my backend machines are thrown together from 9 year old junked motherboards that still had 4 or 6 standard PCI slots. The hot modern hardware is best saved for frontend machines. 

Good luck.

---

### Post by nickrout on 2013-06-01
Honestly if you don't want to record, mythtv is not for you. 

However as you aren't telling us how you have set uo any of these cards, we can't tell you where you went wrong. Mythtv has a defined setup procedure which is pretty well documented, and lots of logging available in the backend. If you want help, you need to tell us what you are diing, where the error arises and what the log files say.

---

### Post by AgentZ86 on 2013-06-02
Not meaning to hijack this post but I'm failing to understand the use for mythTV and/or XBMC or even Windows Media Center for that matter

I have verizon fios and TV cards cannot record ANY HD recording that I can tell
Unless you get a very expensive card in which case why bother if you can get a DVR provided by fios for $16.95 per month
I know that sounds high but the cards for recording digital HD and not analogue are over $300-$600 bucks in which case it would take 17-35 months of DVR serve just to equate to the $300-$600 for the cost of the expensive HD recording card

Am I wrong. 
I wanted for years to do this and when I finally got a card. An Avermedia card and used it on Windows just to see how it work. I couldn't record any HD because the verbage they used to sell the card was completely bogus
It suggests that is records digial media and it does but it only had a composite input thus there is no way it could record digital in digital HD format but only record digital shows in analogue which is deceptive in their selling tactics.

Additionally it didn't have any schedule or anything because the only input I could use was a component or coax output and could only record the actual channel that was playing at the time. So no schedule or anything that I keep hearing about.

Not to say there isn't cards out there that can do it but they are expensive and I'm not sure I understand the benifit of doing this even though I would have prefered to not have a monthly DVR service bill

Please advise and sorry for the long post on this but I would like to do this too if I can understand how and why I would do it.
Thanks

---

### Post by klc5555 on 2013-06-02
The original poster was talking about recording clear QAM from cable. The higher-tiered digital/HD content channels were encrypted from the get-go after the digital migration in 2009. But until the end of last year, the Cable Cos. were required also to provide all the "local" channels --defined loosely as about any station that a local area was theoretically capable of picking up over-the-air, plus a few others-- in clear QAM: clearly available over the cable in SD and normally HD without the intermediation of any set-top box or DTA whatever. This clear QAM content is recordable in full-quality SD and HD, just as it comes into your house, by any digital tuner card out there, from the $30 cheapies on up.

The Cable Cos. still provide clear QAM in most areas --FIOS too. But since the end of last year they are no longer required to do it, and so have plans in place to encrypt all cable content including the basic-tier locals. Therefore, many of us have gone back to over-the-air to record our SD and HD content from the local stations and broadcast networks, and keep some cable capability with a set-top or DTA or two or three to get the content not available over-the-air. 

People who use XBMC as their primary or secondary media interface (coupled with PVR suites like Mythtv or others) are frequently doing so in order to integrate their own stored media content (DVD files, videos, digital music, etc.) with high-quality web-based content (TV/Movies from HULU, Crackle, the Networks' own sites, or many other places) with the TV content got from their PVR in a single, reasonably organized interface.

I personally find it a convenience to be able to record 7-10 shows simultaneously when I want to on the apparatus I've thrown together over the last few years, and then be able to watch them from from any TV/computer/or device in or within about 50 feet of my house at any time while every other member of my family is watching other content similarly recorded, on whatever other household TV, computer, or device they may find themselves in front of. But that's my reason for bothering with this --you'll need to find your own reason for doing so.

---

### Post by nickrout on 2013-06-02
I know very little about verizon fios (except what I can read on wikipedia) but I can say that Mythtv is useful for many people in many markets. We don't all have a**hole media companies who encrypt everything that isn't nailed down. I have about 20 channels in New Zealand on DVB-T and I can record all of them at once if I chose to do something that crazy.

But [http://en.wikipedia.org/wiki/Verizon_Fios#Television](http://en.wikipedia.org/wiki/Verizon_Fios#Television) tells me that you have "local HD" in ClearQAM which means you can record those with a relatively cheap card. 

The attraction of mythtv over your STB recorder is that if mythtv works with your TV source, then it is far superior to your STB. Ask yourself

1. How many channels can your STB record at once?

2. How many TVs can you watch it on at once (we have 5 off one mythtv backend)

3. How flexible is your scheduling, new show detection etc

4. Does your STB download fanart and other metadata for the TV it records, as well as your entire ripped (or downloaded) movie collection?

5. Can you add as much storage as you can afford to your STB?

6. Does your STB detect and skip commercial breaks?

We could go on.

---

### Post by AgentZ86 on 2013-06-03
I see thanks.

---

