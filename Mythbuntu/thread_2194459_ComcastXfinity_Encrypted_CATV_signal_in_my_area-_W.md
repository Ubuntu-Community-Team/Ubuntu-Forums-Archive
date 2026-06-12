---
title: "Comcast/Xfinity Encrypted CATV signal in my area- What to do now?"
date: 2013-12-18
forum: Mythbuntu
---

### Post by forums-etarq on 2013-12-18
Folks, I'm in a dilemma now. I've been running my mythbuntu system for almost 6 years now without any hassles at all.  I have a PVR-500 I've used for years. I recently added a Digital Tuner Card and that has been working for a few months.  Now I've discovered that Comcast/Xfinity is now encrypting the signal so the only channels I can get are the "Hey you need a new box from us" broadcast.

I have a set top box for my only other TV in the home.  I re-attached my feed directly to the tuner on the TV, which also used to get all my analog and digital CATV channels. When I had the TV itself do a channel re-scan it get the same 3 Xfinity channels stating I need to call them to get a $1.99/month adapter box now.

So now my mythTV box can't do anymore DVR services for me, which was it's main function.

What are other folks doing?  I Had them send me this "box" but I read on the web that this box has it's own remote so I won't be able to really change the channel with MythTV? I'm going to have to program my remote to change the channel on that box?

I'm a bit confused.  Are my two tuner cards I have now going to be useless?

Thank you for any advice!

---

### Post by TheFu on 2013-12-18
Yes, your existing tuner cards are worthless.
If you must have cable, then get an HDHR-Prime. It is a 3-tuner, Linux compatible, MythTV [http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime) compatible.  I don't know anything more on this specific device. Sorry.

I do have an HDHR3-US QAM/ATSC tuner and** LOVE IT!** That is why I can completely recommend the Prime.

IMHO, CableTV companies have been asking to be fired for years when they started encrypting channels that I was paying for.

There was a warning in October about the coming Dec 1 encryption. I was on Limited Basic until about 16 months ago, coming down off a $160/month Comcast bill habit. As of Oct 2012, my Comcast bill is $0 - though the corporation pays for the ISP connection. ;)

A few of us who have fired Comcast: [http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results](http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results) .  In my metro area, there are over 70 channels available with broadcast TV.  If you do this, then your existing tuners should work fine, assuming they have ATSC tuners.  About 1 hr to build and $20 will go a very long way to a fantastic DB4 antenna. If you are lazy, $60 will buy a commercial DB4e ... but be certain to check tvfool.com before you do this.  My B-i-L lives in the middle of nowhere - over 130 miles from any metro area with TV broadcasting, so paying COX is his only solution.

---

### Post by aelfric55 on 2013-12-18
> **forums-etarq said:**
> Folks, I'm in a dilemma now. I've been running my mythbuntu system for almost 6 years now without any hassles at all.  I have a PVR-500 I've used for years. I recently added a Digital Tuner Card and that has been working for a few months.  Now I've discovered that Comcast/Xfinity is now encrypting the signal so the only channels I can get are the "Hey you need a new box from us" broadcast.

I have a set top box for my only other TV in the home.  I re-attached my feed directly to the tuner on the TV, which also used to get all my analog and digital CATV channels. When I had the TV itself do a channel re-scan it get the same 3 Xfinity channels stating I need to call them to get a $1.99/month adapter box now.

So now my mythTV box can't do anymore DVR services for me, which was it's main function.

What are other folks doing?  I Had them send me this "box" but I read on the web that this box has it's own remote so I won't be able to really change the channel with MythTV? I'm going to have to program my remote to change the channel on that box?

I'm a bit confused.  Are my two tuner cards I have now going to be useless?

Thank you for any advice!

Use the box. I have three of them (Pace/Motorola DTAs) that I've used to record my encrypted Comcast digital starter channels since the digital switchover back in 2009. The DTA outputs analog on channel 3 or 4 over coax that can be input into your PVR-500. You configure  LIRC on your myth machine and use an IR blaster to allow your myth machine to change channels on the DTA and your myth machine is just as functional as it ever was. A bit tricky to set up the first time, particularly in the selection of your preferred IR blaster (I use an Iguanatech USB model), but easy when you get the hang of it.

Doing this with Comcast DTAs (and settop boxes) has been around for a long time. The following how-to is ancient, but nothing about the process has changed much since 2008 or so: [http://regx.dgswa.com/html/node/134](http://regx.dgswa.com/html/node/134)

Of course, a DTA only gives you an analog-quality signal for your PVR-500 to use. Fine for most of my Comcast Digital Starter trash, which was only SD to start with. But for my local channels that Comcast used to consider "Limited Basic" and would give me in HD Qam, I put up an external antenna and still get them in HD that way now that Comcast encrypts them. For the remainder of the digital starter range, I use the 3 DTAs on 3 analog tuners with LIRC and 3 IR blasters.

---

### Post by VMC on 2013-12-19
> **TheFu said:**
> Yes, your existing tuner cards are worthless.
If you must have cable, then get an HDHR-Prime. It is a 3-tuner, Linux compatible, MythTV [http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](http://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime) compatible.  I don't know anything more on this specific device. Sorry.

I do have an HDHR3-US QAM/ATSC tuner and** LOVE IT!** That is why I can completely recommend the Prime.

IMHO, CableTV companies have been asking to be fired for years when they started encrypting channels that I was paying for.

There was a warning in October about the coming Dec 1 encryption. I was on Limited Basic until about 16 months ago, coming down off a $160/month Comcast bill habit. As of Oct 2012, my Comcast bill is $0 - though the corporation pays for the ISP connection. ;)

A few of us who have fired Comcast: [http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results](http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results) .  In my metro area, there are over 70 channels available with broadcast TV.  If you do this, then your existing tuners should work fine, assuming they have ATSC tuners.  About 1 hr to build and $20 will go a very long way to a fantastic DB4 antenna. If you are lazy, $60 will buy a commercial DB4e ... but be certain to check tvfool.com before you do this.  My B-i-L lives in the middle of nowhere - over 130 miles from any metro area with TV broadcasting, so paying COX is his only solution.
HRanything has always confused me. What if I don't have a home network or just have or use one computer. Why the internet connection, so other PC's on the network can watch tv? How about internet speed. Is that a consideration? I keep reading all the rave reviews regarding HR.

---

### Post by forums-etarq on 2013-12-19
Thanks everyone, this is great info!!  Part of me wants to ditch Comcast and try your antenna routes. I have the PVR-500 and a digital tuner (can't remember the model at the moment) but it worked great for shows, that are better than the set top box was getting me.  I believe that tuner should be able to get the over-the-air tower broadcasts, but as mentioned earlier if you are in the middle of nowhere, that is a challenge.  Well, I am in the middle of nowhere.  :(  My nearest broadcasting station is about 40 miles away.  I have a friend who said he has a LEAF antenna he's not using anymore so I'm going to borrow that and test it.  If I need to go bigger and higher, I do have a 50' mast on the back of the house that still has the old school antenna on it. LoL. I never bothered taking it down thinking I'd need it someday...I think that day may have come.

---

### Post by TheFu on 2013-12-19
The leaf is a toy. I doubt it will work from 40 miles away.  

You can built your own antenna for $20 - see previous link - $15 in copper, $3 in scews and washers, plus a 4+foot 2x4 board and $2 balun from Walmart/$1-store. Of course, the homebuilt version won't stand up to weather or wind if mounted outdoors. Mine is in an attic and got 1 station 52 miles away - in addition to 60+ other, closer stations.

Or you can spend $63 (did this last week) and get a commercial DB4e antenna through Amazon. Since it is commercial, it is designed for an outdoor installation - weather won't matter.  Claims to be good for 65+ miles. Installed it a few days ago - don't have any stations more than 52 miles away that can be received (same channel used as closer stations), but it did get 74 stations yesterday with a $24 pre-amp.  Read my updated article on that above.

I wouldn't bother with a mast install for just 40 miles, though higher is better. It is amazing what can be received from an attic by just pointing these DB4-style antennas in the right general direction.

**If you have an old TV antenna - try it first. RF hasn't changed and many Radio Shack antennas from 1970 work great!** There is nothing different about HiDef TV transmission to require a new antenna.  VHF and UHF are the same.

Before you do anything - visit tvfool.com and see where the transmitting towers are relative to your house. If they are all in the same basic direction - great!  If they are in different directions, grab a copy of the "radar map" and post to the tvfool forums asking for help. Those guys are good and helpful. Difficult situations can be solved.  I wanted to get stations in different directions - the guys helped me select a specific antenna with a narrow reception beam to prevent other stations that I didn't want interfering - plus I had another antenna pointed towards the 15+ metro area transmission towers to get 60+ stations. Anyway - all is well now for less than 1yr of CATV costs that I'll never have to spend again.

Is the PVR-500 ATSC?  The specs don't say anything about that. If not, it is worthless for OTA broadcasts. The only use for it is to connect to a cablebox and record analog, low-resolution, output - yuck.

So back to the HDHR choice. which do you want?
* For encrypted cable TV, get the HDHR-Prime and contact the cable company for a CableCARD-m (I think that is the version you want). The Prime has at least 3 tuners ... they had a 6 tuner model at one point. I dunno anymore about them.
* For ATSC OTA broadcasts, get the HDHR3 tuner. It has 2 tuners. If you need more tuners, get another HDHR3.  I think there is an HDHR4 being released in early 2014, but I wouldn't worry about that.  Even the older HDHR models work great and for some situations, they are better than the HDHR3 models.  I'm completely addicted to the HDHRs ... my recording OS actually runs inside a virtual machine on a computer doing 5 other things 24/7. It is not a dedicated machine just for TV. I don't think I could do that with a PCI tuner.

Of course, there are lots of tuners available besides the HD-Homerun models. Check the MythTV compatibility lists first, then decide if encrypted QAM with CableCARD is needed or not. The HDHR guys are known to be Linux friendly - have since the beginning - so I want to support them.  I've had a few Hauppauge devices over the years - even bought a new HiDef recorder (1512) a few months ago (not a TV recorder) - it does not support Linux and may never support it.

---

### Post by TheFu on 2013-12-19
> **VMC said:**
> HRanything has always confused me. What if I don't have a home network or just have or use one computer. Why the internet connection, so other PC's on the network can watch tv? How about internet speed. Is that a consideration? I keep reading all the rave reviews regarding HR.

HDHR devices are TV tuners (clear QAM/ATSC OR encrypted QAM) that have a coax connection for TV input (antenna or digital CATV) on 1 side and an ethernet network port on the other. A PC connects using nominal networking to the HDHR and performs the recording of "tuned" shows. The PC only needs enough power to receive the bytes from the HDHR device and write those to disk.  All video encoding happens on the HDHR.

Multiple HDHRs can be used with any number of computers or a single computer can use multiple HDHRs. Since they are "on the network", there really isn't any limit (except with Windows) to the number of tuners.  HDHRs have 2, 3, 6 tuners inside and these can be connected to different sources - 1 for OTA ATSC and another for ClearQAM and another (Prime) for encrypted QAM from the evil CATV empire. ;) The recording software will have different channel maps for each tuner and prioritize accordingly.  No PCI slot limitation. No USB port limitation. Offloaded video encoding.  What is NOT to like?

Internet speed has absolutely NOTHING to do with HDHR recordings. The internet is used only during channel setup (to make smarter guesses for which channels are available) and the recording software will want to grab program data over the internet for the next 14 days - channel guide stuff.

So - the HDHR is just like a PCI card TV recorder ... just the PCI interface is now a network interface and many different computers can access the tuner(s) through the network to record or watch live TV, not just the PC with the physical card inside. Flexibility.  Also, coax has signal loss for every foot of cable run. CAT5e network cable can go 500 ft (or is that meters?) without loosing any packets.  Antenna in the attic, HDHR right next to it (my attic has a power plug right there), and now instead of running coax 50ft to the computer, just run a slim, tiny CAT5e ethernet to the router. Much, much easier and it avoids signal loss from the coax.

The main key idea with any HDHR is never use wifi. Always use wired ethernet - ALWAYS.  That applies to the HDHR, the recording computer AND to any devices used for playback.  Streaming video demands a solid, constant, network connection and wifi is not that at all. You'll see.  Everyone tries to use wifi, then experiences the stuttering, dropped packets, dropped connections, then finds a way to use wired ethernet or even powerline networking. A consistent, stable network is mandatory for hidef video recording and playback.

If you don&#8217;t have a network ... uh .... why not?  This idea is so completely foreign to me that I cannot process it. ;)  $20 for a cheapo router, $10 for some ethernet cables, and "poof",  you have a network.  No need to spend more than $50 for a router for most people and $20 is fine for a 100% wired ethernet setup. Disable wifi to avoid all those security issues - there are a bunch. Sorry, I digress.

---

### Post by forums-etarq on 2013-12-19
I actually built one of those antennas a few years ago and it didn't work. I don't think I knew what I was doing. Now I have real reason to dive into this. Unfortunately it's winter now.  Attic is freezing and mast is obviously outside.  I'll see what I can do with IR blasters, etc for now once the box comes from Comcast which will be tomorrow.  I'll be back home in January and I'll play around with it then.

I checked out TVfool and put in my location and it looks like I have some options and the majority of the channels i want in Digital are all mostly coming from the same direction. I take that as a win.

I can't recall if the PVR-500 is ATSC or not.  It never got the "13.1" channels. Just the "regular" channels.

The HDHR seems pretty awesome.  Regardless I have a LOT of reading to do over the holidays. :)

Thank you, "TheFlu" your info has been very helpful!!

---

### Post by TheFu on 2013-12-19
Sorry - after I posted those 2 replies, I kept adding and updating for another 30 min. Might be worth a re-read.

I looked up the PVR-500 - it is NOT ATSC.  There aren't any "regular channels" since 2009 in the USA. That is when the 100% digital TV switch happened.

Mounting an DB4 antenna in the attic 2 days ago took me less than 15 minutes.  Just used a nail in a rafter and hung the antenna rear-reflector on that.  Another antenna is hanging from 2 nylon ropes ... also off nails in the rafters. Had to get the direction correct, but mounting in an attic doesn't need to be a big deal.  My house already had coax lines nearby in the attic too.

Of course, everyone's attic is different.

---

### Post by tgm4883 on 2013-12-19
> **TheFu said:**
> HDHR devices are TV tuners (clear QAM/ATSC OR encrypted QAM) that have a coax connection for TV input (antenna or digital CATV) on 1 side and an ethernet network port on the other. A PC connects using nominal networking to the HDHR and performs the recording of "tuned" shows. The PC only needs enough power to receive the bytes from the HDHR device and write those to disk.  All video encoding happens on the HDHR.

Multiple HDHRs can be used with any number of computers or a single computer can use multiple HDHRs. Since they are "on the network", there really isn't any limit (except with Windows) to the number of tuners.  HDHRs have 2, 3, 6 tuners inside and these can be connected to different sources - 1 for OTA ATSC and another for ClearQAM and another (Prime) for encrypted QAM from the evil CATV empire. ;) The recording software will have different channel maps for each tuner and prioritize accordingly.  No PCI slot limitation. No USB port limitation. Offloaded video encoding.  What is NOT to like?

Internet speed has absolutely NOTHING to do with HDHR recordings. The internet is used only during channel setup (to make smarter guesses for which channels are available) and the recording software will want to grab program data over the internet for the next 14 days - channel guide stuff.

So - the HDHR is just like a PCI card TV recorder ... just the PCI interface is now a network interface and many different computers can access the tuner(s) through the network to record or watch live TV, not just the PC with the physical card inside. Flexibility.  Also, coax has signal loss for every foot of cable run. CAT5e network cable can go 500 ft (or is that meters?) without loosing any packets.  Antenna in the attic, HDHR right next to it (my attic has a power plug right there), and now instead of running coax 50ft to the computer, just run a slim, tiny CAT5e ethernet to the router. Much, much easier and it avoids signal loss from the coax.

The main key idea with any HDHR is never use wifi. Always use wired ethernet - ALWAYS.  That applies to the HDHR, the recording computer AND to any devices used for playback.  Streaming video demands a solid, constant, network connection and wifi is not that at all. You'll see.  Everyone tries to use wifi, then experiences the stuttering, dropped packets, dropped connections, then finds a way to use wired ethernet or even powerline networking. A consistent, stable network is mandatory for hidef video recording and playback.

If you don’t have a network ... uh .... why not?  This idea is so completely foreign to me that I cannot process it. ;)  $20 for a cheapo router, $10 for some ethernet cables, and "poof",  you have a network.  No need to spend more than $50 for a router for most people and $20 is fine for a 100% wired ethernet setup. Disable wifi to avoid all those security issues - there are a bunch. Sorry, I digress.

Most of this is correct. I just wanted to chime in on a few things.

1) You keep suggesting that the HDHRs are doing video encoding and that is what makes them so great. The digital signal is encoded from the broadcast/cable company in a format already usable (usually mpeg2-ts), there is nothing for the HDHR to encode (although I believe there is going to be a mpeg4 version of the HDHR that will have to encode on the fly). This is the same for all digital tuners, all they do is tune the channel and transfer bits. Video encoding is legacy analog stuff for the most part.

2) You don't actually need a network to use the HDHR, you can use a crossover cable and connect directly to it. No network needed (although I've not actually tried it because, yea, who doesn't have a network these days).

That said, the HDHR is an amazing device and OP should definitely get one. I love my HDHR Prime.

---

### Post by TheFu on 2013-12-19
> **tgm4883 said:**
> Most of this is correct. I just wanted to chime in on a few things.

1) You keep suggesting that the HDHRs are doing video encoding and that is what makes them so great. The digital signal is encoded from the broadcast/cable company in a format already usable (usually mpeg2-ts), there is nothing for the HDHR to encode (although I believe there is going to be a mpeg4 version of the HDHR that will have to encode on the fly). This is the same for all digital tuners, all they do is tune the channel and transfer bits. Video encoding is legacy analog stuff for the most part.

2) You don't actually need a network to use the HDHR, you can use a crossover cable and connect directly to it. No network needed (although I've not actually tried it because, yea, who doesn't have a network these days).

That said, the HDHR is an amazing device and OP should definitely get one. I love my HDHR Prime.

Thanks for the correction. Didn't know that.

Some considerations with mpeg4/AVC1 encoders ... I've had a direct-to-xvid video encoder for years. It made editing (removing commercials) harder and the xvid encodings were 1-pass, so they were huge compared to 2-pass encodings.  I suspect editing video stored inside MP4 containers will be harder to edit too, at least for most people, for a few years, until the tools catch up.  Does **comskip** and/or **ccextractor** support video inside mp4 containers?  Will the mythtv commercial skip tools work with mp4?

I record to MPEG2, remove commercials, and transcode to h.264/mkv containers for shows I want to keep.  For shows that we watch just once, the transcoding step is not performed, so standard mpeg2 files are watched. With HiDef, those can be huge; 25G for a long movie at 1080i, but since it gets removed relatively quickly, that doesn't matter too much.  After transcoding, most of these hidef shows are 1G or so. Movies are 2-3G after transcoding.

Of course, the devices used for playback will determine which end-formats any one will want. That is a completely different issue. With mpeg2 recordings, the choice of final format/container is open.

Just more considerations.

---

### Post by VMC on 2013-12-19
Thanks to both TheFu & tgm4883 for the info. I just I got my wires crossed somewhere. I read somewhere (unknown) that HR needed a fast internet connection.
I do have internet ( I am here, yes), but disregarded HR because of my misinformation.

I was all along thinking of using a [COLOR=#444444][FONT=arial]Hauppauge product, but have a small case, so USB would be the only solution. Now HR has taken on a whole new meaning.
I **only** watch and record ATSC channels. Don't have any cable TV. Never did.  I have a Magnavox [/FONT][/COLOR][COLOR=#444444][FONT=arial]MDR-513 that I use to record TV. HR would solve all that.[/FONT][/COLOR]

---

### Post by tgm4883 on 2013-12-20
> **TheFu said:**
> Thanks for the correction. Didn't know that.

Some considerations with mpeg4/AVC1 encoders ... I've had a direct-to-xvid video encoder for years. It made editing (removing commercials) harder and the xvid encodings were 1-pass, so they were huge compared to 2-pass encodings.  I suspect editing video stored inside MP4 containers will be harder to edit too, at least for most people, for a few years, until the tools catch up.  Does **comskip** and/or **ccextractor** support video inside mp4 containers?  Will the mythtv commercial skip tools work with mp4?

I record to MPEG2, remove commercials, and transcode to h.264/mkv containers for shows I want to keep.  For shows that we watch just once, the transcoding step is not performed, so standard mpeg2 files are watched. With HiDef, those can be huge; 25G for a long movie at 1080i, but since it gets removed relatively quickly, that doesn't matter too much.  After transcoding, most of these hidef shows are 1G or so. Movies are 2-3G after transcoding.

Of course, the devices used for playback will determine which end-formats any one will want. That is a completely different issue. With mpeg2 recordings, the choice of final format/container is open.

Just more considerations.

The HDPVR records in mpeg4 format, and MythTV supports it. I had one awhile ago and it worked fine with commercial skipping, although I didn't do any editing or things like that. The file sizes are smaller because of the better encoding with h.264 (mpeg2 is a lossy codec), and in my experience most things support h.264 if they support mpeg2 these days.

---

### Post by TheFu on 2013-12-20
> **tgm4883 said:**
> The HDPVR records in mpeg4 format, and MythTV supports it. I had one awhile ago and it worked fine with commercial skipping, although I didn't do any editing or things like that. The file sizes are smaller because of the better encoding with h.264 (mpeg2 is a lossy codec), and in my experience most things support h.264 if they support mpeg2 these days.

All true.  however ... 

The Hauppauge 1512 records to AVC1 with a few different container choices. I find the .ts container to be the easiest to edit, but about 20% of the time, editing fails completely due to some "stream problem."  VLC can't playback these videos either. Fortunately, XMBC handles them fine and newer handbrake releases do too.

With the 1512, I have to set the bitrate for recording.  This results in huge files, since setting that level too low results in terrible fast-action scene recordings.  I re-encode the video to h.264/mkv with handbrakeCLI later at _constant quality_ settings.  This usually cuts the file size from 13G/hr to 1-2G/hr for 720p content. Well worth the effort to setup this automation on a fast Core i7.

I'd also point out that hidef AVC1 or h.264 playback can be a huge issue depending on your hardware.  I have 4 yr old Netbook that couldn't handle h.264 playback except in software. No GPU decoders possible, so any resolution over 600p stutters - - terribly.  We often forget that older GPUs with drivers didn't support h.264 accelerated playback. That is a fairly recent feature only really included the last 2-3 yrs.  I have a number of other older playback devices that don't support h.264 at all and since the OP has a PVR-500 card -  I think this is probably important to note.

For SD content, I think xvid is still a better encoding format, but for anything over 480p, then h.264 is probably the better standard.

Good info here. Thanks.

---

### Post by forums-etarq on 2014-01-18
Based in the information from you guys here, I've purchased an HDHomeRun Prime device that has three tuners from woot.com the other day. It was a new item.  It'll be here on in a few days. Going to pick up the TVCard from Comcast next week.

---

### Post by TheFu on 2014-01-18
> **forums-etarq said:**
> Based in the information from you guys here, I've purchased an HDHomeRun Prime device that has three tuners from woot.com the other day. It was a new item.  It'll be here on in a few days. Going to pick up the TVCard from Comcast next week.

I hope you mean the CableCARD - be certain to get a mutlit-tuner version.
Also, I don't have ANY experience with the HDHR-Prime and do not know if it works with MythTV.

---

### Post by forums-etarq on 2014-01-18
> **TheFu said:**
> I hope you mean the CableCARD - be certain to get a mutlit-tuner version.
Also, I don't have ANY experience with the HDHR-Prime and do not know if it works with MythTV.

You're right - I meant CableCARD. I talked to Comcast last week and I can get one at no cost.  It looks like the HDHomeRun Prime does work with MythTV as well as Windows7 and other devices.  I just miss DVR'ing my shows, and until summer I'm not messing around with antennas yet.

---

### Post by TheFu on 2014-01-18
It isn't "no cost", it is just the same as the box you were renting ... or less.   I think the CableCARDs are $1.95/month here - plus whatever the programming costs.

Got a 2nd HDHR3 a few weeks ago and connected it to my network (and the antenna). It is working great. Seems that having 4 tuners is enough - I see 3 of them working many times a week, usually around 8p.  I can't imagine having to watch commercials again.

---

### Post by forums-etarq on 2014-01-23
> **TheFu said:**
> It isn't "no cost", it is just the same as the box you were renting ... or less.   I think the CableCARDs are $1.95/month here - plus whatever the programming costs.

Got a 2nd HDHR3 a few weeks ago and connected it to my network (and the antenna). It is working great. Seems that having 4 tuners is enough - I see 3 of them working many times a week, usually around 8p.  I can't imagine having to watch commercials again.

My HDHomeRun Prime arrived today. I activated the CableCard over the phone with Comcast. The actual set up with MythTV was a snap. Maybe that is because I upgraded to .25 a while ago.  I've been watching on every device I can try.  The HDHomeRun also works with my Samsung SmartTV as well using the app from HDHomeRun.

Very thankful for you guys with the HDHomeRun suggestions. It even gets the HD Channels so I can return my "Digital Only" set top box that looked like crap.

---

### Post by TheFu on 2014-01-23
> **forums-etarq said:**
> Very thankful for you guys with the HDHomeRun suggestions. It even gets the HD Channels so I can return my "Digital Only" set top box that looked like crap.

The HDHomerun stuff is pretty amazing. Glad it is working.  

I don't plan to ever own a "smart TV" ... it is just another network device to be hacked or to be used to watch what we do in our "castles."

---

### Post by topcat5 on 2014-01-24
> **TheFu said:**
> ....

Or you can spend $63 (did this last week) and get a commercial DB4e antenna through Amazon. Since it is commercial, it is designed for an outdoor installation - weather won't matter.  Claims to be good for 65+ miles. Installed it a few days ago - don't have any stations more than 52 miles away that can be received (same channel used as closer stations), but it did get 74 stations yesterday with a $24 pre-amp.  Read my updated article on that above.

I wouldn't bother with a mast install for just 40 miles, though higher is better. It is amazing what can be received from an attic by just pointing these DB4-style antennas in the right general direction.

**If you have an old TV antenna - try it first. RF hasn't changed and many Radio Shack antennas from 1970 work great!** There is nothing different about HiDef TV transmission to require a new antenna.  VHF and UHF are the same......While the OP has decided to stick with cable, I'll offer this up when it comes to considering an antenna.  Recommendations for specific antennas and placement are not going to be useful to anyone else.   What works in one place are most likely not going to work elsewhere.   The DB4e, for example, does not pick up VHF and especially VHF-lo.  Many areas still have stations broadcasting over these frequencies.   The DB4 is a wide band suburban antenna, many people will need a narrow band fringe antenna.  The Leaf, as you correctly point out, is overhyped and over priced.  

What anyone should do who is considering an antenna (in the USA or Canada) is to first understand what stations you wish to receive.  TV Fool is a good source for this and it allows you to post an anonymous link to your report in case you need help in choosing an antenna. There are several sites where there are plenty of people who are more than willing to help with one of these reports.   Once you know the mix of stations, direction, and strength, then does it make sense to look for an antenna that will receive these stations.   Outdoor mounting is far superior to attic mounting, but it is generally more difficult to install.   Someone lucky enough to have a mast wired up however should continue to use it.   

While it is true that RF hasn't changed, what did change were the frequencies.  Most stations were moved from their old VHF-lo, VHF-hi, locations to UHF.  This means that many old antennas may work but are not optimal for the new frequency bands.   it's worthwhile to simply plug up a old installed antenna to see what it can pick up, but never go out and buy one.   It's best to pick an antenna that has been cut to the new bands as this will insure that maximum gain occurs over the right frequencies.

---

### Post by TheFu on 2014-01-24
> **topcat5 said:**
> Recommendations for specific antennas and placement are not going to be useful to anyone else.   What works in one place are most likely not going to work elsewhere.   

Exactly!@!!!@#!@#!@#!@#!@!@#   tvfool.com rocks! It does a good job of explaining the issues too. I've been helped on their forums too. Smart and helpful people there.

> **topcat5 said:**
> The DB4e, for example, does not pick up VHF and especially VHF-lo.  Many areas still have stations broadcasting over these frequencies.   The DB4 is a wide band suburban antenna, many people will need a narrow band fringe antenna.  The Leaf, as you correctly point out, is overhyped and over priced.  
The DB4e does pick up RF 10 and higher, but not RF8. The elements are just a little too small. However, my home built DB4 with longer whiskers, does receive RF8, but doesn't get some of the higher UHF stations as well as I'd like.  I also have a yagi, but have it pointed in a different direction to pick up a PBS station that is UHF (replacing the RF8 station) - the yagi also receives some interesting stations that are NOT available in my metro area.

Overall, we are seeing 65 channels, about 25 are interesting. 1 frequency has 20 subchannels (10 audio only), which is next to worthless due to the extreme compression involved.

> **topcat5 said:**
> 
While it is true that RF hasn't changed, what did change were the frequencies.  Most stations were moved from their old VHF-lo, VHF-hi, locations to UHF.  This means that many old antennas may work but are not optimal for the new frequency bands.   it's worthwhile to simply plug up a old installed antenna to see what it can pick up, but never go out and buy one.   It's best to pick an antenna that has been cut to the new bands as this will insure that maximum gain occurs over the right frequencies.

Where I've lived in the USA - 9 different states, even more cities - there were always UHF stations, so we always had UHF antennas. The new UHF frequencies are actually smaller in total band, so those older antennas were not as "tuned" for the fewer frequencies. Hi-UHF has been cut from RF69 to RF51. Stations have been moved. [https://en.wikipedia.org/wiki/Digital_television_transition_in_the_United_States#Low-power_stations](https://en.wikipedia.org/wiki/Digital_television_transition_in_the_United_States#Low-power_stations)  So getting a newer, tuned, antenna does make some sense.

Here's much of what I've done in my attic: [http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results](http://blog.jdpfu.com/2012/08/03/diy-hdtv-antenna-deployment-and-results) including a few photos of my antennas as built and installed.  

Weather does impact reception, but not in the way I thought.  Rain only matters if it is extremely heavy. Light rain doesn't seem to matter at all.
Oddly, cold seems to matter more.  Low power stations UHF that were always fringe for us are refusing to come in at all this morning - no signal at all reaching the antennas. It is below 0 degF outside and clear.  Other channels that are not fringe are very clear, as usual.  We aren't used to cold weather here, so it could be that the transmitter is off-line. This is NOT one of the major networks.  I miss the F24 French news channel.

A caution. Antennas become addictive.

---

### Post by topcat5 on 2014-01-25
> **TheFu said:**
> 

Overall, we are seeing 65 channels, about 25 are interesting. 1 frequency has 20 subchannels (10 audio only), which is next to worthless due to the extreme compression involved.LOL, when I saw this, I said to myself that you must live in ATL, and then I looked at your info and true enough, you do.   That station is infamous for its compression.  Great idea though.  I wish more broadcasters were that enthusiastic about OTA.  Generally these days they only care about reaping subscription fees from cable/satellite.   

I don't live in ATL or GA, but I'm familar with what they did at that station.   Generally stations are good with 1 HD and 2 SD channels.  There are some that push 3 SD stations and some, in rural areas that will push two HD & 1 SD.  (generally to provide CW).   Much of how well they can pull that off is in the multiplexer equipment they are using.  Advanced statistical mux can do some amazing things with constantly reassigning bandwidth.  On the other hand, most stations don't do well beyond the standard HD + 1 or 2 SD subchannels.   

BTW, metro ATL has 4 VHF stations including 2 low power stations transmitting on VHF-lo.   If you don't care about those 2 low stations, then a great antenna for that area is the Antennacraft HBU-22 or anything from the HBU series, or any from the Winegard 769x series.  These are great antennas for VHF & UHF, they are cut for 7-51, well built, and best of all, still made in the USA.   They are also better priced than the DBXe series which generally are over priced.   

Alternatively with the DB4e you can get an appropriate VHF only antenna, and combine it with the DB4e with a UVSJ.   That sometimes is the best way to go.

---

### Post by TheFu on 2014-01-25
As to prices - both our commercial antennas were in the $45 area - little more, little less, but that was the average. $10 in coax and $25 for a pre-amp is a great return on investment. Less than 1 month of my old CATV bill when getting billions of channels that we never watched.

The issue for me with the Antennacraft HBU-22 was size (70 inches!!!!), the Winegard is bigger. Won't fit in the attic in an easy to access location. I tested antennas in the place that was large enough to install larger antennas and there is something blocking reception.  The convenient places for attic installation have much better reception and both the relatively flat DB4 style DOES fit facing 1 direction and a 50-ish inch yagi barely fits in the other direction.  Regardless, I will need 2 antennas pointed in different directions.

I have a VHF antenna and the pre-amp has a port to accept it and will filter VHF from the other input. Just don't have the correct connector/balun to fit and haven't searched the correct places to find one.  My normal stores don't care these things and the TV/electronics folks are clueless. ;)

For our needs, I'm confident this solution was the best ... or at least good enough.  Woulda-coulda-mighta.  Might swap the 2 antennas around tomorrow ... always a tweak to be done. ;)

---

### Post by topcat5 on 2014-01-26
Of course as a MythTV user, you don't really need to combine antennas at all.   If you get a separate tuner, a HDHomerun Dual is good, then you can connect the 2nd antenna to it.   Then when you set it up in MythTV you only put the channels that you want to receive for that antenna.  It works great if you have to point two antennas in different directions.

---

### Post by TheFu on 2014-01-26
Things are never as easy as they could be.  

I have 2 HDHR3 devices. These have a single COAX input. I am unwilling to have 2 coax lines from the attic, so I combine the antennas there using a simple splitter/combiner, then connect the pre-amp, run 1 coax to where the other equipment is, pre-amp power and a splitter to 3 outputs (HDHR3-a, HDHR3-b, TV).

Thanks to digital signally, the ghosting we used to get with analog TV by doing this stuff, is gone. Sure, pure antenna folks will say that I'm not getting the best possible picture, but what difference does it make if it works?  Digital EC handles it.

There are times when all 4 tuners are recording from 1 antenna, so splitting each antenna to a single HDHR would be less than desirable.

But, you are correct - I could.

I would mark this **thread solved**, if I could. Unsubscribing on my end.

---

