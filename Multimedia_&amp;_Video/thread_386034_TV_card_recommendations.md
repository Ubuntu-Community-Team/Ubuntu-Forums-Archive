---
title: "TV card recommendations??"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by shingalated on 2007-03-16
I'm looking to get a TV card for when I go to college.  The dorms are quite small and I was hoping to save some space with a computer for a TV instead of a big clunky TV.  Does anyone have any recommendations?  I want a cheap card that I can set up with as little extra configuration as possible.  What cards work for you?

---

### Post by barney_1 on 2007-03-16
I would recommend the Hauppauge PVR-150 card.  If you don't already have a remote some of the PVR-150 packages come with one. 

As for what will work, check out the hardware support list for ivtv:

[http://ivtvdriver.org/index.php/Supported_hardware](http://ivtvdriver.org/index.php/Supported_hardware)

---

### Post by shingalated on 2007-03-16
Thank you, I found a nice PVR-150 on newegg that has good reviews.  People say it works well with linux, and it is only $67.  I think I´m gonna give it a try.
Wish me luck!:popcorn:

---

### Post by dannyboy79 on 2007-03-16
hang on! do you already have a tv-out video card???? if not than you'll need that to otherwise get both with the PVR-350. or you can get a cheap nvidia with tv-out for around 64.99, this is the oner I have. 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106)

---

### Post by shingalated on 2007-03-16
> **dannyboy79 said:**
> hang on! do you already have a tv-out video card???? if not than you'll need that to otherwise get both with the PVR-350. or you can get a cheap nvidia with tv-out for around 64.99, this is the oner I have. 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1776106)

I DO have TV-Out, but I don't know if it works.  WHy would I need it though?  I am just watching it on my computer.  I do not plan on plugging a TV into my PC.  Just cable into the PC.

---

### Post by rsambuca on 2007-03-16
Most of the Hauppauge 150's that Newegg is selling now are actually the new 1600 in the old pvr150 box.  Normally that would be a good thing since the 1600 is a much better card, but for linux, there are no drivers yet.

---

### Post by shingalated on 2007-03-16
[http://www.newegg.com/Product/Product.asp?item=N82E16815116620](http://www.newegg.com/Product/Product.asp?item=N82E16815116620)
looks good, the reviews are all saying good things about it on linux.  It sounds like it works with the ivtv drivers installed.

---

### Post by dannyboy79 on 2007-03-16
you're right, I am sorry I forgot you stated that you didn't want to haul a computer to school. you'll be fine watching it from your computer. just be careful about the PVR-150, like rsambuca says, the newer ones have a newer 1600 which isn't supported.

---

### Post by barney_1 on 2007-03-16
> **rsambuca said:**
> Most of the Hauppauge 150's that Newegg is selling now are actually the new 1600 in the old pvr150 box.  Normally that would be a good thing since the 1600 is a much better card, but for linux, there are no drivers yet.

That's good to know.  Kind of crappy on Hauppauge's part though.  They must know that it's the most popular card used with MythTV and that has to be a huge boost to their sales don't you think?

Anyway, NewEgg is a great company IMHO.  I would give their customer service a call and ask them if the card is the 1600 or not.  Chances are they'll be able to tell you before you put in your order.

---

### Post by Ergo on 2007-03-16
Try pcHDTV card 3000 or 5000 series.  They can capture too.  They also come with their own software!

---

### Post by fenian on 2007-03-16
The easiest cards to get to work on linux are bttv based cards as they are supported 'out of the box' and require the least amount of effort to set up.These cards work quite well for watching live T.V. with the TVTime application.These cards will work with PVR applications such as mythtv though they will use your computers processor to encode the video.These cards are typically less expensive than cards with encoding chips such as the Hauppauge 150.Here are some links to bttv based cards that I believe are supported...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006](http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006](http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006](http://www.newegg.com/Product/Product.aspx?Item=N82E16815122006)

I have personally used the Hauppauge card I listed and it worke with TVTime and Mythtv with no additional setup(plug and play)

---

### Post by rsambuca on 2007-03-16
The IVTV firmware drivers are preinstalled into Feisty, so the Hauppauge cards will also work out of the box.  You also have the benefit of leaving your cpu free from the mpeg encoding.

---

### Post by fenian on 2007-03-16
You don't need tv encoding if you just want to watch live TV. Setting up Mythtv and other  apps to use ivtv (which you have to do as TVTime doesnt support ivtv) require a bit of effort,many people have had lots of problems getting mythtv to work.Also mpeg encoding requires a lot of free hardrive space which can also be a problem for some.For a college student who may be on a limited budget and primarily wants a card to watch live TV the bttv cards offer substantial savings.

---

### Post by shingalated on 2007-03-17
I am going to go with a cheap ivtv card.  The bttv cards are analog only, am I correct?  The US is switching to digital only soon, my cable company said next year they would stop broadcasting in analog.  I also would like the onboard encoder, my processor is only a celeron, so I don't think it is up to the task of decoding videos on top of all its other tasks.  Thanks everyone for your help, I'll give newegg a call and ask about the chipset in the PVR-150.

---

### Post by fenian on 2007-03-17
Ivtv card such as the Hauppauge 150 are also analog cards.In order to get digital you must have an ATSC or DVB card.Digital broadcasts are sent in Mpeg-2 and don't need hardware encoding.Many ATSC and DVB cards are supported by the v4l(video for linux) drivers that also support bttv cards.A list of ATSC cards supporte by v4l can be found [here]("http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards").In the USA there are some issues concerning digital broadcast and tuner cards you can read more about that [here]("http://www.eff.org/IP/broadcastflag/").

---

### Post by barney_1 on 2007-03-19
I have to side with rsambuca here.  If you're going to spend money on a card I feel it must be an encoder card.  Otherwise you're just wasting your CPU cycles when they could be used elsewhere.  Because I have an encoder card I can record a program and transcode a different recording simultaneously.  Wouldn't be the case if my CPU was doing the heavy lifting of encoding the video stream as it records it.

---

### Post by dannyboy79 on 2007-03-19
> **fenian said:**
> Ivtv card such as the Hauppauge 150 are also analog cards.In order to get digital you must have an ATSC or DVB card.Digital broadcasts are sent in Mpeg-2 and don't need hardware encoding.Many ATSC and DVB cards are supported by the v4l(video for linux) drivers that also support bttv cards.A list of ATSC cards supporte by v4l can be found [here]("http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards").In the USA there are some issues concerning digital broadcast and tuner cards you can read more about that [here]("http://www.eff.org/IP/broadcastflag/").

This is not only in the USA, quoted from an article here ([http://arstechnica.com/news.ars/post/20070314-dvb-broadcast-flag-will-require-government-support-but-may-not-get-it.html](http://arstechnica.com/news.ars/post/20070314-dvb-broadcast-flag-will-require-government-support-but-may-not-get-it.html))

"Although the US has settled on ATSC for terrestrial broadcasting, much of the world has chosen DVB, meaning that the new CPCM technology has the potential to impact viewers from Namibia to the Faroe Islands to the Czech Republic to the UK. But it won't have much of an effect unless consumer electronics manufacturers play along."

And even some more unsettling news quoted from here ([http://www.eff.org/IP/DVB/dvb_critique.php](http://www.eff.org/IP/DVB/dvb_critique.php))

Summary: 

DVB creates digital television specifications for use in Europe, Asia, Latin America and Australia 
A DVB project called Content Protection and Copy Management (CPCM) goes beyond the customary work of setting television standards to set out specifications for restricting how television programmes are used after reception 
CPCM represents a grave danger to nations that mandate it as part of their digital television strategies

---

### Post by fenian on 2007-03-20
> DVB creates digital television specifications for use in Europe, Asia, Latin America and Australia
A DVB project called Content Protection and Copy Management (CPCM) goes beyond the customary work of setting television standards to set out specifications for restricting how television programmes are used after reception
CPCM represents a grave danger to nations that mandate it as part of their digital television strategies

Thanks for the info on CPCM dannyboy.

>  you're going to spend money on a card I feel it must be an encoder card. Otherwise you're just wasting your CPU cycles when they could be used elsewhere. Because I have an encoder card I can record a program and transcode a different recording simultaneously. Wouldn't be the case if my CPU was doing the heavy lifting of encoding the video stream as it records it.

DVB and ATSC signals are already encoded (mpeg-2) when sent  they don't need to be encoded 
again by your cpu or your tuner.

---

### Post by newlinux on 2007-03-20
If you are worried only having digital cable access in the future, get a card that does ATSC/QAM/NTSC, like the pchdtv 5500 or 3000, or the Kworld ATSC 110 or one of the Fusion 5 cards. The downside will be that the analog signals will have to be encoded in software. If your CPU is hefty enough, this isn't a problem. What CPU are you running? I have 3 kworld atsc 110s that work great and were easy for me to setup. I also have the PVR-150 and it was easy as well. The Fusion 5 lite I bought worked out the box.

---

### Post by dannyboy79 on 2007-03-21
when you say that the Fusion 5 worked out of the box, do you just mean by installing the card, chosing the correct drivers from the repo, then doing something like:
cat /dev/video0 > video-file.mpg
your video stream is working? Also, what drivers did you chose? Have you tried MythTV? What tv programs do you use?

---

### Post by newlinux on 2007-03-21
I didnt install anything. After I just opened up tvtime and was able to watch analog stations. Didn't check for dvb stations as I was going to install mythtv to do that. It's driver support should be built in the the kernel. That's what my research told me, and it actually did work. Now, I don't know if something I installed before that did it, but I doubt it, as when I had that card I had barely gotten into doing this stuff...

Yes, I currently use mythtv, although not with the fusion (The fusion is now in an dual boot XP/Ubuntu box because at the time it was one of few cards that had software for tuning QAM stations in XP).  I currently have a 6 tuner setup consisting of two backends and three frontends - 3 Kworld ATSC 110s, 1 hauppage 150, 1 Avermedia A180, and one firewire cable box connection. I used to have a pchdtv 5500 working fine in myth, but i sold that card and bought a cheaper Kworld.

---

### Post by dannyboy79 on 2007-03-22
so do you use a remote with any of your tuner cards? if so, do you have a cable box or satallite box? if so, how do you control the cable stations or satallite stations using the tv tuner cards remote? Do you just hook the cable in to an "input" on the tv card or do you hook it to the "tuner" on the card. Are you using an ir blaster, a serial connector or what? I am asking beause I have Time Warner Cable, I forget the exact model of my cable box, but one of the main things I am looking to be able to do is have mythtv be a total DVR, schedule recording maybe even tell it to record from the internet (if that's how mythweb works, not sure)  if I know a show is on when I am at a friends house and I want to record it,  can it also record HBO (channel 311 in my town) , it's a premium station or other stations that aren't "normal" and can't get "tuned" by the built in tuner. 

I'll give some history which will explain why I am asking, I kind of hacked a thing together when I was using windows xp and I had a ATI AIW 9800 Pro. I first tried just attaching the coax cable from the wall straight into the tv card. I scanned for channels and it found the normal ones but not the premium stations or HBO. I am guessing it's a encrypted channel that the cable box knows how to decrypt. So, in order to use my card to digitally record shows that didn't come thru (this setup only worked manually-no scheduling, I had to be there to select record, and had to make sure the switch was at the correct A or B channel (i'll explain)) I thought I would split the cable coming out of the cable box. From the cable box, I plugged that cable into the "in" of a signal splitter. 1 of the out cables goes to my normal tv of course and the other out cable went into an "in" of a 2-way switch, Position A. Then I took a cable that just comes straight out of the wall (ie not thru a cable box) and put that into the "in" of the 2-way switch, position B.  The "out" of the 2-way switch went into the tv card. So basically when I wanted to use the ATI Tv program to schedule recordings, watch normal tv and what not, I would have the switch at position B and everything was good, but I could only watch and record what the tuner found, which like I said WASN'T HBO. (I love ROME, Sopranos, Big Love, etc etc). Then if I knew I wanted to record HBO or any other station that the tv card couldn't "tune" I would flip the switch to A and then turn the real cable box to the station I wanted to record. I would have to turn the ATI Tv program to channel 3 and I was all good that way. See how insane this was. I didn't really understand how else I could accompish what I wanted to accomplish.

So now you know what I would like to do with the PVR-350 and mythtv will this work or can I only record the stations that the tuner cards accepts? I don't know how this all works as I haven't tried to do it yet.

This all may seem hard to understand but it's really not, I don't think. I have attached a little diagram.

---

### Post by newlinux on 2007-03-22
I use the firewire connection to a motorola DCT-6200 to both record from and control, so I don't need an IR blaster to control it. See [https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire) for more info. Whether or not you can do it that way depends on the model of cable box you have, and what 5C settings the cable box has on the different stations. I'm lucky in that on my cable box only a couple channels have 5c settings that don't allow me to record from them. But I get all my HD channels (including the premium ones such as HBO) through the firewire connection. And I tune them as i would any other channel in myth, from any of my mythfrontends. No IR blaster or other video connection needed if the firewire works.

If you can't record the channels you want via fire wire then you will need to use a serial connection or IR blaster and use a tuner card input to record channels you can't tune without the box, and you won't be able to record true HD. Basically it would be like you would do with a VCR and recording stations you can only get via the cable box.

Your scenario is exactly what I use mythweb and the firewire connection for (scheduling when away from home and recording stations QAM enabled cards can't tune). If the firewire works, it doesn't get any easier...

Unfortunately, the stations you can get via QAM and firewire are completely different depending on where you live, who your provider is, and what "protections" they have setup. Even within the same provider different regions have different stations they can get via QAM and firewire.

---

### Post by newlinux on 2007-03-22
Oh, and to clarify about the remote... yes i use a remote to interface with mythtv via LIRC. Then mythtv controls all of the tuner cards and the firewire connection to the cable box. 

Via QAM and ATSC, I get 95% of all the programs I want to record (all my local HD channels). The Hauppage and firewire get me the remaining 5%  (ESPNHD, HBO and Showtime shows, movies, and analog stations my cable company doesn't send via QAM). The firewire also allows me to basically turn a non-DVR motorola box into a DVR, with timeshifting and recording through myth from any mythfrontend in the house. I couldn't be much  happier with this setup.

---

### Post by dannyboy79 on 2007-03-22
MAN, you're sooooooooo lucky!!!!!!! I don't really care about HD (YET) but I do want to be able to record HBO. can u please explain the QAM, the 5C and the ATSC stuff. 

Ok, I just went on a local forum Milwaukee, WI HDTV and everyone is talking about how they can HD channels thru a normal coax cable because they have RoadRunner and I guess the frequencies are similar?? I don't know but I did catch this:

A question though... why is ESPNHD considered premium and encrypted, when you are already purchasing the digital package, along with the extra HD stream? Am I destined to only be able to receive the broadcast networks via HD Tuner on the PC?[/QUOTE]
I don't have an answer as to why ESPNHD is encrypted. I guess the cable/media illuminati want to restrict access to "trusted" hardware, to thwart copying. The type of encryption the cable provider uses mandates that this "trusted" hardware be used throughout the entire electrical path the signal passes through - it's not allowed to decrypt the stream until it's inside the television set and unable to be copied. PCs don't abide by this requirement (yet). You will be able to watch the premiums on your PC some day soon - once you upgrade to a "trusted" PC and a HDCP-compliant monitor - but with your current PC you will be out of luck unless the government passes a law that mandates that cable providers not encrypt their premium content... or until someone manages to crack the encryption (called DTCP or 5C) - but decrypting the stream would be illegal under the DMCA. (is that enough acronyms for you? :) )

Even once the day comes that you can watch premiums on your PC, the cable provider will still dictate the terms of what you can do with what you record. Your PC capture hardware/software will record the stream in its encrypted state and require validation to be able to view the recordings. I'm not sure of all the specifics of how it will work, but, this is my impression.

Your quote, "Basically it would be like you would do with a VCR and recording stations you can only get via the cable box."

Would I still be able to somehow control when this happens???? Maybe pre schedule myth to do this if the actual scheduling thingy doesn't work??? I don't know how all this work?


So my question is, does this mean that I can or can't record HBO????? That's my main goal!!!!! How do I find out what stations have the 5C flag??? Also, I am waiting to here back from TWC (Time Warner Cable) to see if they provide any of these: Motorola DCT-62xx series and the Scientific Atlanta SA3250HD/SA4200HD. I guess if I really wanted to do this with Firewire, I would be upgrading to HD. WHat would happen if I don't have an HD tv???? 

Your quote, "Basically it would be like you would do with a VCR and recording stations you can only get via the cable box."

Would I still be able to somehow control when this happens???? Maybe pre schedule myth to do this if the actual scheduling thingy doesn't work??? I don't know how all this work?

Thanks for all your help. How much is a tv card that can get OTA channels???? and can mythtv control multiple cards in 1 box.

---

### Post by newlinux on 2007-03-22
Hmm, where to start... well 5c  (or DTCP) in relationship to the cable boxes is the protocol that controls what devices will be allowed to record the stream via the firewire (ieee1394). 5c (more specifically the CCI component of 5c) will have to  be set to 0 for a computer to record from the cable box. Most cable boxes provide a way of displaying which stations are 5c protected and which ones aren't, but the procedure for finding this out depends on your cable box. This is a very simplified explanation of DTCP - but you can look up the specs on the web...

you can look up the QAM and ATSC wikis for more info on them. Basically QAM64/256 are what cable companies use to transmit digital stations, and ATSC is the format digital stations are transmitted over the air.

Even if you don't use firewire you can still have myth control the cable box using an IR blaster and LIRC. Search these forums on LIRC and mythtv or search google (also go to the mythtv talk forums) as well... I haven't needed to do this so I don't have first hand experience with having myth use an external channel changer (IR blaster) but I know there is an option to provide a script for doing so in myth - a quick search yields [http://www.eggshellskull.com/lirc/blaster/index.php#step8](http://www.eggshellskull.com/lirc/blaster/index.php#step8). So yes, you can still have schedule recordings from your cable box without using firewire. You just wouldn't be able to record in HD, and probably not very easily in dolby digital as well. But if you're not concerned with those, then you don't need firewire.

Most places you won't get more HD than the local HD channels over QAM. If they allowed this, then few people would pay for cable boxes or services. You can already get the locals in HD over the air, so that is not as big of a concern. I think law requires cable companies to transmit the HD locals, but there are exceptions in some areas. So that is why it is doubtful ESPNHD would be transmitted via QAM.

I've seen Air2Pc cards on ebay (which receive OTA ATSC) for $20-50.  They don't do QAM. The kworld atsc 110 is going for $55 right now on newegg and it does ATSC and QAM and NTSC (software decoding). Keep in mind, HD channels require powerful hardware to decode (but non-hd channels digital or analog don't).

---

### Post by newlinux on 2007-03-22
This has gone way off topic, and if this conversation continues it should probably be in a different thread. BTW newegg has the atsc 110 OEM for 49.99 - I didn't scroll down far enough...

---

### Post by dannyboy79 on 2007-03-23
Well in my opinion all this is related to tv card recommendations but I can start a new thread if you think I should I have a few more questions.

1. I have the new Intel Core 2 DUo E4300 (stock hsf), ASRock775-dual VSTA, 1.5gb ram, GeForce 6200 and plenty of hard drive space. :-) Would this be enough to record HD content? I wouldn't be needing the computer to output to a tv, only record shows that i'll miss cause I am not home or what not. My goal would be to then transcode into something smaller like avi or whatever a good container that is compatible with lot's of players?

I found out all these below are available and I also found out that since I subscribe to only Roadrunner (this is the high speed internet service and I wouldn't need a TV package) I could get all the unencrypted HD channels just fine. Since both ATSC and Roadrunner use QAM modulation. It would be hard to filter just one but not the other. 
4-1 WTMJ (NBC-HD)
4-2 WTMJ-WX (Weather Plus)
6-1 WITI (FOX-HD)
10-1 WMVS (three hour delay of analog channel 10)
10-2 WMVT (three hour selay of analog channel 36)
10-3 PBS-Kids 
10-4 PBS Create
10-5 MPTV Extra
10-6 MPTV Extra
10-7 MPTV Extra
12-1 WISN (ABC-HD)
18-1 WVTV (WB-HD, soon to be CW-HD)
24-1 WCGV (UPN-HD, soon to be MyNetworkTV-HD)
24-2 The Tube Music Network - SD
30-1 WVCY (SD)
36-1 WMVT (PBS-HD)
55-1 WPXE (Ion/Pax)
55-2 WPXE-2
55-3 WPXE-3
55-4 WPXE-4
58-1 WDJT (CBS-HD)
58-2 WMKE (independent SD)
NBC HD: 103.2 
FOX HD: 103.3 
TMJ+: 103.4 
CBS HD: 109.1 
ABC HD: 109.2 
MPTV HD: 116.5
CW in Milwaukee is WVTV- 18 analog ( DT-61).

2. In order to get OTA HD channels that are freely broadcasted in my Area do I need an Antenna to get the OTA channels?? or do I just hook the roadrunner cable to the Kworld 110.

3. Your quote, "Keep in mind, HD channels require powerful hardware to decode (but non-hd channels digital or analog don't)." Doesn't the Kworld 110 Decode the signal? I don't really understand how this all works? Or doesn't the cable box decode the signal? or are you talking about when I get the HD channels from OTA using the Kworld 110?

4. How does either the Kworld 110 or my PVR-350 get stations that aren't found with it's own tuner then if I wanted to record HBO? Oh, I think I may understand now, so you're saying that MythTV's channel will stay at 3, then the channel change script actually changes the cable box's station, then it records it also. OR am I wrong on this and I will want to plug that cable from the cable set top box right into the plug on my PVR-350? 

I just did the zap2it thing and it's awesome, allt he channels are in there even HBO, so I hope that it doesn't have the 5C thing on it!!!! See I wonder how that ATI Media Center TV program worked because that only had a guide with a very small  amount of channels. 

5.  I just thought, I really don't even care if the remote doesn't work. I don't need a remote since I really don't watch tv in my room. I am only really using this for scheduling recordings, then I'll watch it from my living room using my xbox media center. Can Xbox media center play the stored files or will I have to transcode them first into something the Xbox media center can play OR I own another xbox that I could just install mythbox on it. isn't that a solely linux version built for the xbox to make it a frontend? NEVERMIND, i just found my answer, I already have XBMC and there exists a Python Script which is the MythTV frontend software ([http://sourceforge.net/projects/xbmcmythtv/)](http://sourceforge.net/projects/xbmcmythtv/)). AWESOME!!!!!!

Hopefully you can just answer these last questions and that'll be it. Thank you sooooo much!!!!!! I am pretty new to linux but do feel that I have picked up a lot of stuff very quickly within the 1 year and if you ever need any help with anything I would be happy to try and help. Thanks again and am looking forward to hearing back.

---

### Post by newlinux on 2007-03-23
> **dannyboy79 said:**
> Well in my opinion all this is related to tv card recommendations but I can start a new thread if you think I should I have a few more questions.

I was just saying this because a thread with a topic more related to mythtv or tuner card might be easier to find for other looking for the same information in a search. not a big deal.

> 
1. I have the new Intel Core 2 DUo E4300 (stock hsf), ASRock775-dual VSTA, 1.5gb ram, GeForce 6200 and plenty of hard drive space. :-) Would this be enough to record HD content? I wouldn't be needing the computer to output to a tv, only record shows that i'll miss cause I am not home or what not. My goal would be to then transcode into something smaller like avi or whatever a good container that is compatible with lot's of players?


Recording HD playback takes very little processor. HD is just"captured" straight into an mpeg-2 stream so no encoding of the stream is needed. A PIII could probably record an HD stream and for recording your vidoe card is irrelevant. Takes up about 10-15GB per hour to record HD. However, if you will be transcoding to other formats you need all the CPU you can get or  it will take forever. Dual cores are the way to go for this...  

> 
I found out all these below are available and I also found out that since I subscribe to only Roadrunner (this is the high speed internet service and I wouldn't need a TV package) I could get all the unencrypted HD channels just fine. Since both ATSC and Roadrunner use QAM modulation. It would be hard to filter just one but not the other. 
4-1 WTMJ (NBC-HD)
4-2 WTMJ-WX (Weather Plus)
6-1 WITI (FOX-HD)
10-1 WMVS (three hour delay of analog channel 10)
10-2 WMVT (three hour selay of analog channel 36)
10-3 PBS-Kids 
10-4 PBS Create
10-5 MPTV Extra
10-6 MPTV Extra
10-7 MPTV Extra
12-1 WISN (ABC-HD)
18-1 WVTV (WB-HD, soon to be CW-HD)
24-1 WCGV (UPN-HD, soon to be MyNetworkTV-HD)
24-2 The Tube Music Network - SD
30-1 WVCY (SD)
36-1 WMVT (PBS-HD)
55-1 WPXE (Ion/Pax)
55-2 WPXE-2
55-3 WPXE-3
55-4 WPXE-4
58-1 WDJT (CBS-HD)
58-2 WMKE (independent SD)
NBC HD: 103.2 
FOX HD: 103.3 
TMJ+: 103.4 
CBS HD: 109.1 
ABC HD: 109.2 
MPTV HD: 116.5
CW in Milwaukee is WVTV- 18 analog ( DT-61).



I'm not sure what you mean by ATSC using QAM modulation. They are separate methods as far as I know. They may map to the same stations if your cable provider uses PSIP, but in myth you can filter and map them to whatever stations you like.

> 
2. In order to get OTA HD channels that are freely broadcasted in my Area do I need an Antenna to get the OTA channels?? or do I just hook the roadrunner cable to the Kworld 110.


You need an antenna. A cheap indoor antenna may work for you (it does for me, but for some channels I have to kind of point it in a different direction).  You should go to [http://www.antennaweb.org](http://www.antennaweb.org) for more info. Keep in mind in my area it said I needed an outdoor antenna for many of the stations, but I don't. Although, those are the stations I have to move the antenna a bit around for. But I really only use ATSC as a backup when cable goes out or all my other tuners are being used.

> 
3. Your quote, "Keep in mind, HD channels require powerful hardware to decode (but non-hd channels digital or analog don't)." Doesn't the Kworld 110 Decode the signal? I don't really understand how this all works? Or doesn't the cable box decode the signal? or are you talking about when I get the HD channels from OTA using the Kworld 110?


Decoding happens when you display the video (watch it). The Kworld and other tuner cards that don't have decoders (such as the PVR-350 does) and only encode or "capture" the TV stream. Your CPU and video card do all the work in decoding (i.e. displaying) the stream. Cable boxes decode too, but if you are using your computer to watch the recording your CPU and video card will be decoding the signal to your TV, not your cable box. As far as I know, no hardware decoding HDTV cards out work in Linux yet (a tuner card with hardware decoding would take the load of your video card and CPU to display the signal to your TV).

> 
4. How does either the Kworld 110 or my PVR-350 get stations that aren't found with it's own tuner then if I wanted to record HBO? Oh, I think I may understand now, so you're saying that MythTV's channel will stay at 3, then the channel change script actually changes the cable box's station, then it records it also. OR am I wrong on this and I will want to plug that cable from the cable set top box right into the plug on my PVR-350? 


They have video inputs (composite and S-video) that you would plug the corresponding output from the cable box into. If properly setup, mythtv would change the channel on the cable box and record from the input of the Kworld 110 or the PVR-350, just like a VCR would. You don't need to worry about Myth being on "channel 3." Myth would actually display the channel the cable box is on - making it seem seemless to you - again, if properly setup. So your understanding of how this would work is basically correct. Just keep in mind that you can  view two things at once from one card. Not sure if this applies to you. But if you had two mythfrontends you couldn't view a live recording from your Kworld's video input from the cable box on one frontend and it's cable input from the wall (QAM or NTSC) on another mythfrontend at the same time, I think. Actually, maybe you can - this I'm not sure about. Seems the card would have to be able to capture two live streams at the same time, and I don't think most cards can do that (the PVR-500 can but only NTSC). But if you plan on watching everything recorded, this isn't even a concern. If my last caveat is confusing, you can probably ignore it :). Also, keep in mind that I don't do this type of "tuning"  (I use firewire) so I have no first hand experience in it and can be wrong.
> 

I just did the zap2it thing and it's awesome, allt he channels are in there even HBO, so I hope that it doesn't have the 5C thing on it!!!! See I wonder how that ATI Media Center TV program worked because that only had a guide with a very small  amount of channels. 


If you are going to us an IR Blaster or Serial cable to control the cable box and output the video through it's composite or S-video ports you don't need to worry about 5c. 5c would only stop you from recording via firewire. You can get all the channels via S-video and composite. Just wanted to be clear on this. But it is definitely easier if you can do via firewire. It literally took me less than 10 minutes to set up the firewire (took me a lot longer to go through each channel and see which ones were 5c protected) using the guide I referenced earlier.

> 
5.  I just thought, I really don't even care if the remote doesn't work. I don't need a remote since I really don't watch tv in my room. I am only really using this for scheduling recordings, then I'll watch it from my living room using my xbox media center. Can Xbox media center play the stored files or will I have to transcode them first into something the Xbox media center can play OR I own another xbox that I could just install mythbox on it. isn't that a solely linux version built for the xbox to make it a frontend? NEVERMIND, i just found my answer, I already have XBMC and there exists a Python Script which is the MythTV frontend software ([http://sourceforge.net/projects/xbmcmythtv/)](http://sourceforge.net/projects/xbmcmythtv/)). AWESOME!!!!!!

Hopefully you can just answer these last questions and that'll be it. Thank you sooooo much!!!!!! I am pretty new to linux but do feel that I have picked up a lot of stuff very quickly within the 1 year and if you ever need any help with anything I would be happy to try and help. Thanks again and am looking forward to hearing back.


No problem. I used linux (well, actually I used netBSD)  in its infancy about 15 years ago, but I just started using it again last June, and I know how you feel about learning a lot. 

I think Mythtv is just absolutely awesome. It takes a while to get setup the way you want, especially if you want the more advanced functionality. But once you get it set up it's worth it.

---

### Post by dannyboy79 on 2007-03-23
ok, that's great. you're quickness is just awesome. Last questions

Your quote, "I'm not sure what you mean by ATSC using QAM modulation. They are separate methods as far as I know. They may map to the same stations if your cable provider uses PSIP, but in myth you can filter and map them to whatever stations you like."

ATSC signals are designed to use the same 6 MHz bandwidth as NTSC television channels. Once the video and audio signals have been compressed and mutiplexed, the transport stream can be modulated in different ways depending on the method of transmission.
Terrestrial (local) broadcasters use 8-VSB modulation that can transfer at a maximum rate of 19.39 Mbit/s, sufficient to carry several video and audio programs and metadata. Cable television plants generally operate at a higher signal-to-noise ratio and can use 16-VSB or 256-QAM to achieve a throughput of 38.78 Mbit/s, using the same 6 MHz channel. 
I basically got the above facts from the various wikis that are tied together. I think what a guy was saying in a local forum was that he doesn't have any cable tv subscription but he owns an HDTV, he doesn't even have a cable box but since my local cable distributor sends similar frequencies for it's broadband internet as well as it's HD content he was able to watch digital TV and HD channels. I may totaly be misunderstanding him but I think that's what he is saying. This is not from an antenna, it's thru a cable.

1. Why would people need a "tv tuner" built into the capture device if they are already paying for a signal?? I mean, I guess I am having a tough time understanding what the tuner is for if there is an input also. The stations are already "tuned" aren't they. Or is this in the case when people don't have a cable box and then simply hook up a coax cable to an antenna to pick the signal from the air?? OR Could I just hook up my cable modem wire to my Kworld 110 and have it "tune" and get channels? Since all I really wanted a DVR for was to be able to record stuff I didn't need to get a tuning card, I only needed something that would capture the input via s-video or composite.

2. So what you are saying is that I could hook up an antenna to pick HD channels out of the air and just have mythtv record the stream, what does the file get recorded as, mpeg-2 since that's what the stream is? So the hard part is actually taking that stream and playing it as an HD signal, is that what you are saying? Im sorry if these are dumb questions, I just don't get it. So can I buy an antenna and hook that up to my PVR-350? Will I get anything?? I guess I am getting confussed on what OTA stands for, is it OVER THE AIR? Are digital as well as HD channels transmitted OTA for free?

Your quote, "Decoding happens when you display the video (watch it)." I don't know if this is actually what you meant to write. According to PVR-350 documentation: 
WinTV-PVR-350 uses a new integrated hardware MPEG-1/MPEG-2 encoder and decoder, the IVAC015,which compresses your videos 100:1 whithout slowing down your PC's processor and while providing great on-screen video quality. WinTV-PVR-350 can record full screen TV using 2 GB of hard disk space per hour. The integrated MPEG hardware decoder can take your recorded videos, and play them back onto a TV set. 

The Kworld doesn't have this, so MythTV would be recording the original stream and it can't encode it so it's going to be huge like you said 

BUT either way, after each of the recordings, I'll still be able to (watch it) as you say, correct? OH, I think I finally understand, this is in the case of actually watching it while it's happening and being to able to time-shift and whatnot, I get it now, I think? So just tell me what the main disdvantage of the Kworld and the PVR-350. Is it that using the PVR-350, the file is saved straight away very small whereas the Kworld would be recorded as a huge file and then I would have to use FFMPEG or mencoder or something to encode (or is it transcode) into something else.

Thanks again, and I am hopefully out of questions.  :-)
(PS. this one took me over 2 hours to write doing research in between.)

---

### Post by newlinux on 2007-03-23
> **dannyboy79 said:**
> ok, that's great. you're quickness is just awesome. Last questions

Your quote, "I'm not sure what you mean by ATSC using QAM modulation. They are separate methods as far as I know. They may map to the same stations if your cable provider uses PSIP, but in myth you can filter and map them to whatever stations you like."

ATSC signals are designed to use the same 6 MHz bandwidth as NTSC television channels. Once the video and audio signals have been compressed and mutiplexed, the transport stream can be modulated in different ways depending on the method of transmission.
Terrestrial (local) broadcasters use 8-VSB modulation that can transfer at a maximum rate of 19.39 Mbit/s, sufficient to carry several video and audio programs and metadata. Cable television plants generally operate at a higher signal-to-noise ratio and can use 16-VSB or 256-QAM to achieve a throughput of 38.78 Mbit/s, using the same 6 MHz channel. 
I basically got the above facts from the various wikis that are tied together. I think what a guy was saying in a local forum was that he doesn't have any cable tv subscription but he owns an HDTV, he doesn't even have a cable box but since my local cable distributor sends similar frequencies for it's broadband internet as well as it's HD content he was able to watch digital TV and HD channels. I may totaly be misunderstanding him but I think that's what he is saying. This is not from an antenna, it's thru a cable.


Okay, then that's not ATSC. It's QAM. There is no ATSC over QAM. ATSC is used to transmit over the air digitally. Cable companies use QAM. Yes, unless the cable companies put a particular filter on the line if you order high speed Internet you will also get access to all of their analog and unencrypted QAM stations. But they can turn them off at any time with a filter.

> 
1. Why would people need a "tv tuner" built into the capture device if they are already paying for a signal?? I mean, I guess I am having a tough time understanding what the tuner is for if there is an input also. The stations are already "tuned" aren't they. Or is this in the case when people don't have a cable box and then simply hook up a coax cable to an antenna to pick the signal from the air?? OR Could I just hook up my cable modem wire to my Kworld 110 and have it "tune" and get channels? Since all I really wanted a DVR for was to be able to record stuff I didn't need to get a tuning card, I only needed something that would capture the input via s-video or composite.


the way most cable companies signals work (with the exception of IPTV and SDV) is that all stations are sent over the line to everyone on the same node all the time. Your cable box "tunes" by extracting the signal for the station you want. High speed internet access is sent over the same line. So with any cable signal a tuner is needed. A TV, cable box, or tuner card with an analog tuner can tune the stations that come over the line that are analog (NTSC). A TV, cable box, or tuner card with a QAM tuner can tune all the QAM stations, but only the cable box has the proper decryption information to display the encrypted QAM stations. A TV or tuner card with an ATSC tuner can tune over the air digital stations (ATSC). Without a tuner you can't get anything. If your cable company has not placed a filter on your high speed line you can get every unencrypted QAM and analog station without paying for service with a QAM and NTSC tuner, respectively. You'd just split the line going to your cable modem and run one of them to a tuner. If you have a TV with a coaxial input you can try it now. If the station you want to record is already tuned by your some other device (such as a TV or a cable box) then you don't need usa a tuner. However, you do need something to capture the video (s-video or composite) AND the sound and combine them for recordings. Tuner cards with inputs have this functionality as well as the ability to tune.

> 
2. So what you are saying is that I could hook up an antenna to pick HD channels out of the air and just have mythtv record the stream, what does the file get recorded as, mpeg-2 since that's what the stream is? So the hard part is actually taking that stream and playing it as an HD signal, is that what you are saying?


Yes. The more processor intensive part is displaying HD signals. SDTV is not very processor intensive to display. A PIII 700Mhz could probably do it.
> 
 Im sorry if these are dumb questions, I just don't get it. So can I buy an antenna and hook that up to my PVR-350? Will I get anything?? I guess I am getting confussed on what OTA stands for, is it OVER THE AIR? Are digital as well as HD channels transmitted OTA for free?

If you buy an antenna and hook it up to the PVR-350 all you'll get is analog NTSC (non digital, non-HD stations) over the air. Think rabbit ears on old TVs. The PVR-350 can't tune or display HD in any way. It is an analog tuner. You would need an ATSC tuner (such as the Kworld) to get digital OTA (ATSC).

OTA is over the air. NTSC and ATSC are transmitted over the air (NTSC is also transmitted through cable lines). But only ATSC can transmit HDTV over the air. NTSC is dying as everything is going digital in a few years. Digital as well as analog stations are transmitted for free OTA, including local HD channels. ATSC tuners can get the digital stations (including HD) and NTSC tuners can get the analog stations (none of which are HD).

> 
Your quote, "Decoding happens when you display the video (watch it)." I don't know if this is actually what you meant to write. According to PVR-350 documentation: 
WinTV-PVR-350 uses a new integrated hardware MPEG-1/MPEG-2 encoder and decoder, the IVAC015,which compresses your videos 100:1 whithout slowing down your PC's processor and while providing great on-screen video quality. WinTV-PVR-350 can record full screen TV using 2 GB of hard disk space per hour. The integrated MPEG hardware decoder can take your recorded videos, and play them back onto a TV set. 
.

What I said is what I meant, and their documentation echos what I said. The PVR-350 is for NTSC signals, which need to be encoded and decoded. ATSC and QAM only need to be decoded (because they are already digital). NTSC signals are analog, and as you know because computers store in bits and bytes (digital) analog signals need to be ENCODED into a digital format. The compressing the documentation is talking about is taking the analog signal and converting it to digital. The documentation says "hardware decoder can take your recorded videos, and play them back onto a TV set." So as I said, decoding is the act of displaying the file (watching on a TV).  Analog signals don't take up as much as HDTV signals obviously. I was writing about HDTV and digital signals.  Don't confuse encoding and decoding. Encoding is capturing the stream and digitizing it, decoding is displaying the stream. I don't believe you can use the PVR-350 for decoding HDTV because it doesn't have an HDTV output (component, HDMI, VGA, or DVI). And I said no HDTV decoding tuners are currently supported in Linux. What is it that you don't understand or think I didn't meant to write?

[/quote]
> 
The Kworld doesn't have this, so MythTV would be recording the original stream and it can't encode it so it's going to be huge like you said 


I don't think you are getting this. Their is no encoding to do with a digital stream because it is already digital. The size of the file doesn't has little to do with hardware vs. software decoding. Simply, HDTV has tons more lines of resolution and thus it is a bigger file. The Kworld's NTSC files would be about the same as the PVR-350's NTSC files, about 2-5GB per hour. I wrote about the size of HDTV files of which there is no comparison to the PVR-350 because it can't tune, display, encode or decode HDTV. The Kworld does the same "compression" and encoding as the PVR-350. It just uses the CPU to do it, whereas the PVR-350 doesn't need the CPU to do it.

> 
BUT either way, after each of the recordings, I'll still be able to (watch it) as you say, correct? OH, I think I finally understand, this is in the case of actually watching it while it's happening and being to able to time-shift and whatnot, I get it now, I think? So just tell me what the main disdvantage of the Kworld and the PVR-350. Is it that using the PVR-350, the file is saved straight away very small whereas the Kworld would be recorded as a huge file and then I would have to use FFMPEG or mencoder or something to encode (or is it transcode) into something else.


The are 2 main differences between the cards. The biggest difference is the PVR-350 can't do HDTV. That is why it has smaller files. It is NTSC only, and HDTV is digital (QAM or ATSC). The Kworld can do NTSC/QAM/ATSC. The second difference is that the PVR-350 has hardware encoding and decoding of NTSC so it uses less processor to encode NTSC than the Kworld would (because the kworld doesn't give any help to the processor) and the PVR-350 has hardware decoding (display) of NTSC. If you have a dual core processor, or heck, even an old pentium 4, your processor is strong enough to encode and decode NTSC without hardware help, so this difference is negligible unless you are really looking to save CPU cycles.

Neither one requires transcoding of their files to be viewed. When viewing HDTV however you need a hefty processor or you need to use XvMC. This stuff is all explained in the Myth wiki. You should really read that in detail.
> 
Thanks again, and I am hopefully out of questions.  :-)
(PS. this one took me over 2 hours to write doing research in between.)

---

### Post by dannyboy79 on 2007-03-26
> **newlinux said:**
>  Okay, then that's not ATSC. It's QAM. There is no ATSC over QAM. ATSC is used to transmit over the air digitally.  
I believe ATSC is a standard, so that doesn't neccessarily mean that these are only HDTV signals sent OTA does it? ATSC is the standard in which the HDTV signals are sent thru the cable in the ground as well isn't it?. According to my Cable Companies FAQ:
ATSC stands for the Advanced Television Systems Committee. It was responsible for defining the 18 different formats of HDTV. It was formed to develop technical standards for advanced television systems, including high-definition television. The ATSC specifies MPEG2 for video compression and AC-3 (more commonly known as Dolby Digital) for audio compression.

Am I wrong in thinking that just because some1 says they are gettings ATSC channels, that doesn't mean that they are receiving them OTA because they could also be getting them thru the ground??? ATSC just basically means that they are either digital or HDTV signals, correct? 

> **newlinux said:**
> 
What I said is what I meant, and their documentation echos what I said. 
Yeah, sorry I misunderstood what all this really meant etc etc.

> **newlinux said:**
> I don't think you are getting this.
No I am not and I apologize as I see you're getting a little impatient with me.

> **newlinux said:**
> The are 2 main differences between the cards. The biggest difference is the PVR-350 can't do HDTV. That is why it has smaller files. It is NTSC only, and HDTV is digital (QAM or ATSC). The Kworld can do NTSC/QAM/ATSC. 
Sounds like it would be well worth it to buy the kworld and hook my coax cable into it and see what I get, I should be able to get my local HD channels because when I called to see what I had to do in order to get HD channels TWC  said all I needed to do was come in and get the SA3250HD STB or the SA4200HD STB and that was all. So obviously I am currently receiving the HD signals I just need something to tune them! Or I might buy the kworld and this antenna ([http://www.antennasdirect.com/DB2_Indoor_antenna.html](http://www.antennasdirect.com/DB2_Indoor_antenna.html)) if after hooking the kworld up to my coax cable nothing comes in because they filtered it so that onlt there cable box can transmit it?

I again thank you soooo much for all your great info!!!!!!

---

### Post by newlinux on 2007-03-26
I'm not getting impatient. Rereading my post, I can see how you infer this, but that was not my intention. I just thought you weren't getting some of the things I was explaining.

Technically, you are probably right, ATSC probably can be used through cables, but this does not happen in the US (I say in the US because many other countries do things differently, using DVB and other standards. Cable companies operate at a higher SNR (signal to noise ratio) and thus can use QAM-256 (which is currently not part of the ATSC standard) which provides roughly twice the throughput that ATSC does (currently---technologies are always improving). This is one reason cable companies use QAM. Local broadcasters don't need that much bandwidth (right now) so ATSC suits them fine.

In short, ATSC is the digital standard for OTA in the US. Cable companies use QAM-64/256 for their digital transmissions (in the US). If someone says they are using ATSC (and they know what they are talking about) then they are talking OTA channels in the US. 

Most likely you can get the locals HDs through QAM in your area. Some cable companies encrypt them (but I believe they are not supposed to so you could complain to your local broadcasters about this). One thing I know a lot of people have run into is that many cable company providers send both a digital SDTV version of the locals as well as HDTV versions of the locals over QAM (mine does this). So if you get a channel that looks like a local but not HDTV, keep searching.

Yep, your assumptions about what you can do with the Kworld are right. There are other options for HDTV tuner cards in linux. The link below gives a good list of cards that will work with myth, some easier to setup than others, with different costs. The Kworld is about as inexpensive as you can get that does QAM/ATSC and NTSc. IF you are only interested in QAM/ATSC the Avermedia A180 is pretty good and cheap to (I use that one as well). It doesn't do NTSC.  The setup for both cards is the same (they use the same chip). As a tip, the Dvico Fusion 5s (and I think the 3s as well) can tune both NTSC and QAM or ATSC in mythtv. Other cards you have to setup as a QAM/ATSC tuner or an NTSC tuner (if they can do all those formats). You can switch them at any time, but you have to redo their setup in myth. The Fusion you can switch simply by changing the station - no resetup required. This applies to the mythtv in the edgy repos. The Kworld ATSC can do this as well in myth with the SVN version (The beauty of open source. I asked about this in the myth forums, and the next day this feature was available in the SVN version).

[http://www.mythtv.org/wiki/index.php/Category:Video_capture_cards](http://www.mythtv.org/wiki/index.php/Category:Video_capture_cards)

That antenna looks pretty good. I use a cheap indoor Philips PHDTV1 that I got free with one of the tuner cards I bought. Not the best reception in my area (I have to move the antenna different ways for different channels), but since I only need it as a backup when cable goes out, this is not a problem. If I need to record different channels off it all the time, that would be a problem.

Happy tuning... :)

---

