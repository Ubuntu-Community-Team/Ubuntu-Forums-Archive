---
title: "BEST TV Tuner for MythBuntu 10.10"
date: 2011-02-07
forum: Mythbuntu
---

### Post by illdecree on 2011-02-07
i know this has been asked many times before, but i cannot find anything recent. i'm building a new HTPC, and want the best tuner i can get for mythbuntu. i need dual tuners, and plan to pick up OTA or the few 'must broadcast' channels i get via my cable company. i haven't decided which source i'll use.

i really like the HVR-2250, but i wanted to make sure there wasn't any i've missed that might be better.
what's your best suggestions?

---

### Post by nickrout on 2011-02-07
Where in the world are you?

Are any of your channels encrypted?

---

### Post by illdecree on 2011-02-07
> **nickrout said:**
> Where in the world are you?

Are any of your channels encrypted?

i'm in the US (florida). i'm sure there are encrypted channels. as it stands right now, i don't pay for cable. i do however pick up a bunch of channels via my TV's built in analog/digital tuner, and would like to be able to DVR these channels

---

### Post by nickrout on 2011-02-07
> **illdecree said:**
> i'm in the US (florida). i'm sure there are encrypted channels. as it stands right now, i don't pay for cable. i do however pick up a bunch of channels via my TV's built in analog/digital tuner, and would like to be able to DVR these channels

I'll leave it to someone knowledgeable on the US market to answer, as the technology is different to my locality.

---

### Post by efball3 on 2011-02-08
I'm using the dvico Fusion hdtv7 dual express
[http://www.fusionhdtv.co.kr/ENG/products/HDTV7DualExpress.aspx](http://www.fusionhdtv.co.kr/ENG/products/HDTV7DualExpress.aspx)
It works well with Ubuntu 10.04 and Windows 7.

---

### Post by lviperz on 2011-02-08
I'm in the US and have run a mythtv box for a few years using the Hauppauge PVR-350 and 250. I recently upgraded my pc using mythbuntu 10.10 and wanted to do HD. I got a HVR-1600 and had a hell of a time setting it up. Then I bought a HD Homerun and setup was almost plun-n-play simple.
 
I recommend the HD Homerun dual tuner. You can use it for OTA and/or cable. Just make sure you get a good video card like an nvida that uses vdpau for playback and you should be fine.
 
With the HDHR you will be able to DVR any of the channels you currently get with your TV's tuner. And it sets up fairly easy, at least for me it did.

---

### Post by LowSky on 2011-02-08
Well the HVR-2250 is my prefered choice. The FusionHDTV7  is good but hard to find in the US. HDHomeRun is another excellent choice, but it is external and need a wired ethernet connection, so be mindful of that, but its one of the best.

---

### Post by schlidel on 2011-02-09
So are both the analog and digital tuners with the HVR-2250 working in Ubuntu 10.10? (clear QAM channels and analog cable ntsc?) Specifically, can MythTV utilize both hybrid tuners of the HVR-2250?

I want to install Myth TV after experimenting with a myriad of other media software. (MediaPortal, BeyondTV, SageTV, etc.)

I think I've exhausted the Windows solutions with the WAF variable being the most difficult to solve.

I've honed in on XBMC + Mythbox with Mythbuntu possibly being a solution, just trying to find out if I can proceed. Thanks.

---

### Post by agamotto on 2011-02-09
> **schlidel said:**
> 
So are both the analog and digital tuners with the HVR-2250 working in Ubuntu 10.10? (clear QAM channels and analog cable ntsc?) Specifically, can MythTV utilize both hybrid tuners of the HVR-2250?

No. It can do the digital signals, but not the analog ones, at least not from just installing.  There are kernel tweaks, etc... but I wouldn't bother with it until it is 'finished.'

> **schlidel said:**
> 
I've honed in on XBMC + Mythbox with Mythbuntu possibly being a solution, just trying to find out if I can proceed. Thanks.

I have been using a Hauppauge 1800 with my Mythbox for nearly four years now.  I have not had some of the problems that others have had using the digital portion of this card.  The analog portion is something I haven't bothered with, as I am not willing to experiment.  I am currently using 10.04.1 as I didn't find anything in 10.10 worth the time spent in installing.

I record OTA signals with the 1800 card.  I love the picture and quality of the OTA programming.  PBS looks fantastic!  I simply hooked up a decent antenna, scanned the Broadcast frequencies, and ta-da!  

I do not record cable with it, as Mediacom requires a 'box' to tune in digital channels, even if you have a digital tv...  You can plug a digital telly into the service, but the channels will be missing program info, correct channel assignment, etc...  which recently led to my decision to cut the cord.

In speaking to several people at Mediacom, I was told that when they drop analog signals this year, you will be required to have one of their 'boxes' to get accurate channel assignments, a program guide, the HD channels, or the program info that supposedly is in the channels.

I am happy to have cut the cord, saving $70 per month, and I am also surprised at how little I miss any of the channels.

---

### Post by wh7qq on 2011-02-10
I got sucked in by the networking capability of the HDHomeRun and that is a really nice feature but the tuner leaves much to be desired in the area of multipath rejection. The PBS station that my old Tivax DTV converter and my new Sony LCD TV handle with ease are screwed up by a reflected signal, probably off of a hillside behind my house.  I have to turn the antenna so it is way off axis for the main signal. Can't recommend it.

---

### Post by ranjank on 2011-02-11
I am also looking for a TV Tuner [HD] . I am from India and I am using TATA SKY DTH service . How is Technisat Sky Star HD2 ? Anyone used it in Ubuntu 10.10 ?

---

### Post by NoVista on 2011-02-16
For regular Ubuntu 10.10, I'm currently putting the pieces together for a new p67 mobo system once the fixed ones come out, so I have a bit of time, and I don't want to make an error on my choice of a TV Tuner card / Graphics card either.

So looks like an ATI card is NOT the card to get regarding the statement made by lviperz >>
 Just make sure you get a good video card like an nvida that uses vdpau for playback and you should be fine.

efball3 >>
Does the Fusion hdtv7 dual express tuner work on Ubuntu both analog and digital?

Or anyone else who can answer the above two questions, or have other options. I will be using VLC as the main player.

---

### Post by efball3 on 2011-02-16
> **NoVista said:**
> 
So looks like an ATI card is NOT the card to get regarding the statement made by lviperz >>
 Just make sure you get a good video card like an nvida that uses vdpau for playback and you should be fine.

efball3 >>
Does the Fusion hdtv7 dual express tuner work on Ubuntu both analog and digital?

Fusion hdtv7 is digital only under Linux, but that's not much of a limitation anymore. 

There are lots of discussions on Video cards, but most recommend Nvidia Geforce GT 430 or GT 220 (both are excellent for HD video).  I'm using a 9400 GT which works well enough.  I needed component video out, so it was the best choice for me.

---

### Post by nickrout on 2011-02-16
> **ranjank said:**
> I am also looking for a TV Tuner [HD] . I am from India and I am using TATA SKY DTH service . How is Technisat Sky Star HD2 ? Anyone used it in Ubuntu 10.10 ?

If your sky transmission is unencrypted, that card should work.

However most "Sky" branded stuff is encrypted and your only method is to use the STB and an HDPVR.

---

### Post by ranjank on 2011-02-17
> **nickrout said:**
> If your sky transmission is unencrypted, that card should work.

However most "Sky" branded stuff is encrypted and your only method is to use the STB and an HDPVR.

It is encrypted [NDS] . I am looking for the way to transfer recorded stuff to PC

---

### Post by nickrout on 2011-02-17
> **ranjank said:**
> It is encrypted [NDS] . I am looking for the way to transfer recorded stuff to PC

you have your answer :)

---

### Post by NoVista on 2011-02-17
> **efball3 said:**
> There are lots of discussions on Video cards, but most recommend Nvidia Geforce GT 430 or GT 220

OK, I'll be going with something 'higher up the chain', gtx465 or higher, so I'll be good to go then.

As far as the TV card goes, looks like for me it's a showdown between the Fusion hdtv7 dual express tuner, or the HVR-2250.

LowSky >> you said the HVR-2250 was your preferred choice over the Fusion. Why was that? 
Do one of those cards work better/have more features for an Ubuntu user?

Ok, it's not like I haven't researched them, but not having one or the other installed to see the differences, I haven't a clue what they would be like in real world use.

---

### Post by nickrout on 2011-02-17
> **NoVista said:**
> OK, I'll be going with something 'higher up the chain', gtx465 or higher, so I'll be good to go then.

Not sure that will do any better for video than a 430, and probably use more power.

---

### Post by NoVista on 2011-02-17
I do some gaming, so I want something a bit more, on the graphics card.

---

### Post by rhpot1991 on 2011-02-17
> **illdecree said:**
> i really like the HVR-2250, but i wanted to make sure there wasn't any i've missed that might be better.
what's your best suggestions?

HDHomeRun: [http://www.amazon.com/gp/product/B0010Y414Q?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B0010Y414Q](http://www.amazon.com/gp/product/B0010Y414Q?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B0010Y414Q)


If you can wait till march the new version will be shipping then: [http://www.amazon.com/gp/product/B004HO58SO?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B004HO58SO](http://www.amazon.com/gp/product/B004HO58SO?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B004HO58SO)

---

### Post by nickrout on 2011-02-17
> **NoVista said:**
> I do some gaming, so I want something a bit more, on the graphics card.

That will explain why you want a better card :)

---

