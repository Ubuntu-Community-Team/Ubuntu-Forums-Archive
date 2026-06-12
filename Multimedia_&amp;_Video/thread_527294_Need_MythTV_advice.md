---
title: "Need MythTV advice"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by seepage87 on 2007-08-16
Quick note:  I am reasonably familiar with linux.  I've been dual booting Kubuntu for a little over a year now and use it for all my non-work purposes.  I've also dabbled in some other distributions in the past.  I am, however, still a little bit of a noob, so be kind and thorough in your responses. 


My goal is to setup a MythTV backend and file/web/email server.



I understand having a box do both of these is not a problem as far as resources are concerned, and they'd both want to be on all the time, so this isn't a problem, right?  

=====Storage=====

Storage is a big issue for me since I need a great deal of it.  I currently have:
[LIST]
[*]2 Seagate SATA 250 Gb drives
[*]1 Seagate SATA 300 Gb drive
[*]3 Seagate ATA 250 Gb drives
[/LIST]

I only have about 200 Gbs left, and plans to fill them soon.  I have a lot to lose, so I want to set up a RAID system, though I understand you can't do that with ATA, only SATA and SCSI.  
[LIST]
[*]Is it reasonable to make a good sized RAID system with SATA or should I definitely get a motherboard that'll do SCSI?
[*]How does setting up a RAID system work when there's bunches of data on already?  Do you have to start with drive pairs completely empty then move it on, or can you add a mirror drive and it'll fill itself up to match its partner?
[/LIST]


I'm going to need lots of extra space as well if I'm going to be recording shows.  I really don't like to delete stuff, so it'll probably need to be a decent amount more.  
[LIST]
[*]Am I almost certainly going to have to switch over to SCSI?
[*]What target drive size am I going to have to consider?
[/LIST]

My drives are currently attached to my Windows box, so they're all NTFS, so if I use them I'd probably want to switch the file system.  
[LIST]
[*]Is there a reasonable way to do this, or is it just going to be a lot of moving all data off one drive, reformatting it, and moving it back on over and over?
[/LIST]



=====Logistics=====

I live in Baltimore and have Comcast digital cable (HD, etc).  I've read that digital cable can be encrypted so you can't watch it without the Comcast box.  
[LIST]
[*]Is this something I should worry about?
[*]Can my MythTV box double as my cable box or will I need to connect it to the box via e.g. firewire?
[/LIST]  

Do to my house's layout, I may need my backend downstairs and my frontend way upstairs talking to the backend via wireless.
[LIST]
[*]Will recorded HDTV will be fine cause it's highly compressed?
[*]Is it not feasible to watch live HDTV over a wireless network, or is this compressed enough too?
[/LIST] 



=====Hardware=====

Obviously I'm interested in saving as much money as possible, but I also recognize this is a fairly big project and will cost a good amount.  I'd rather it be done right then cheap and not work, so err on the side of better, not cheaper.

[LIST]
[*]I have a motherboard (some 5 year old gigbyte) and processor (athlon 1.8 GHz, I think), but I'm not sure how much room it has for SATA drives, and if I need to switch to SCSI then it won't work, I think.
[*]I'd want TV tuners with hardware compression, right? Hauppauge seems to be highly recommended.  I need 2 to record one show and watch another, yes?
[*]How much RAM will I need? 1 gig about?
[*]I'm concerned about heat with all those HDs in there, but it might need to be quiet as well.  Is there a good solution to this?
[*]Will any network card (e.g. motherboard integrated) be fine?
[*]If I have to switch motherboard AND processor, what processor speed should I be aiming for?
[*]Any recommendations on case size, brade, etc for quietness, heat control, and ease HD access?
[/LIST]



=====Software=====

I like to sort my TV shows by show/season/episode.*, but I've had problems in the past with running out of space on a harddrive causing the file tree structure to be compromised.  E.g. I've got first 4 seasons of 24 on HD A, I run out of space at 3:00 so 4:00 needs to be on a different disk. 
[LIST]
[*]Can I mount both drives to, for example, TV so that my file trees stay good?
[*]Will I instead have to have a TV folder with softlinks to the appropriate folders mounted elseware (e.g. tv1 points folders for seasons 1-4 to TV's 24 folder, tv2 points folder for season 5 to TV's 24 folder)?  I there a way to automate this process (something like "if THISSHOWFOLDNAME == any TVSHOWFOLDERNAME, then point all THISSHOWFOLDNAME.Subfolders to TVSHOWFOLDERNAME) so that everything just works?
[*]Can I configure MythTV to save all recorded shows under that naming scheme?
[*]Can I get MythTV to automatically record on the next drive once one is full?
[/LIST]



=====The Rest=====

[LIST]
[*]Is there anything I haven't thought of that I need to know or consider?
[/LIST]

Thanks so much for all the help and suggestions.

---

### Post by greerd on 2007-08-17
seepage87,

I'm no expert, but have read a lot on mythtv, and have my own working system.

Storage:
Feisty sees both ata  and sata drives as sata, (less /etc/fstab to check) so RAID might work on all your drives. I use an eSATA drive that comes with eSATA PCI bridge (two ports) and find it works good for me. Also consider LVM for dynamically changing volume size. Mythtv 0.21 will have the ability to spread your recording out across different directories and HDD's.
There are a lot of myth users using a combination LVM/RAID setup.

You should seriously consider not using ntfs for your recordings. Deleting huge files is something that few fs do fast, xfs for example is a good choice. My system is also dual boot with winxp (ntfs) and ubuntu (ext3) on my ata drive and my eSATA drive devoted to myth is xfs. 

Logistics:
Mythtv and any TV cards in North America (?) do not or are not supported by cable companies so you will have to use your Comcast stb as a tuner and connect to myth via firewire. I know that Motorola DCT62xx and DCT64xx stb will work with myth.

I have read that one can stream HD contend using 802.11g fine IF it is one way traffic only. I have not tried it and would use wired lan or Ethernet over power (200mbs) 

Hareware:
Hauppauge pvr 350 has dual ntsc tuners with onboard mpeg decoders/encoders which (I've read) can be setup and used with myth and will run on a system much slower that yours.
eSATA could answer your other hardware questions.

Software:
I don't believe mythtv 0.20 will alow you to record anywhere except the one and only directory created during the setup. Version 0.21 will.

That's about all I can help you with, its all in the forums if you want to search.

---

### Post by newlinux on 2007-08-17
Wow that's a lot. I'll add my inputs about mythtv.

You *may* be able to get cable stations without using your set top box.

If you are looking into digital stations you need to check your area to see what is available. Cable providers encrypt different stations in different places, so you need to check locally. This goes for which stations are available via unencrypted QAM (I would only expect the major networks, including their HD stations) and which stations are 5c encrypted via firewire. In my area I can get the local HDTV stations and a few other stations via unencrypted QAM, and I can get most non premium stations via firewire. Others can't get any via firewire, and others get everything including HD premium channels via firewire. I also use a a hardware analog tuner to get all the analog stations. You can also record from the set top box via s-video and RCA audio connections, but of course you won't get HD this way, but you can record all your channels. A good place to find out about what stations are transmitted in unencrypted QAM in your area is to look for you local cable forum at avsforum.com. 

You can check on an individual channel basis which stations are available via firewire on your motorala DCT 62xx or 34xx by accessing the service menu: [http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled](http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled)


Streaming live or recorded HDTV (their won't be any difference in compression) across wireless g may (most likely will be) problematic unless you transcode the recording. It depends the on the strength and consistency of your connection, as well as how much other wireless traffic there is. My wireless G tops out at about 20Mbps in real use and it works okay sometimes (with some audio drops and studders) and other times it is unwatchable. 

The PVR-350 is a good analog tuner, but it is not a dual tuner. The PVR-500 is dual hardware *encoding *tuner, but lacks hardware* decoding *like the PVR-350, but unless you are only interested in viewing standard definition and are using a very underpowered system, a hardware decoder is unecessary. I personally use the PVR-150 for analog stations.

If you want to view digital stations (and all HDTV is transmitted digitally) then you don't need a hardware encoding tuner. All hardware encoders are for analog only, as digital doesn't need to be encoded, as it's already digitial. Digital tuners simply tune and capture the stream, which doesn't require much CPU at all. Now displaying HDTV is the most processor intensive thing you'll probably do (other than transcoding). An Athlon 1.8 will struggle with displaying HDTV, will definitely need to use XvMC hardware acceleration to even have a shot. Any dual core processor won't have any problems with decoding HD. IF you are going single core, try to aim for 3Ghz. But if you are buying a new CPU, there are plenty of inexpensive dual cores out there, so I'd definitely get one.

If you already have recorded shows, you would probably want to view them with mythvideo plugin instead of importing them into Myth's recordings. If you do this, you can have the recordings on multiple disks and setup the filestructure how you like using symlinks. Your new recordings, however, must all be stored in the same place in the current version of myth, but the screen you use to browse them can be configured to sort them in a few different ways. Then of course, you could use myth to "archive" them and put them in the same place as the recordings you already have are and view them through mythvideo. This is what I do for shows I have episodes of that I didn't record from myth.

---

### Post by newlinux on 2007-08-17
Oh, and one thing you need to consider is your video card. I recommend nvidia. It need not be the latest and greatest (as most of the features of the higher end cards aren't supported by the linux drivers). I do JD just fine with the a Geforce 6200, 6150, heck even my old MX 440 does HD fine with myth and linux. A lot of people use the 5200.

---

### Post by seepage87 on 2007-08-20
Ok, two more quick questions.  

If I have digital cable, are all the channels already digital, or will the cable company transmit some of them analog?

HDTV viewing will be the most processor intensive, so would a hardware decoding card make it more reasonable?

---

### Post by seepage87 on 2007-08-20
Hold on, I think my last question was kinda irrelevant.  This box will just be a backend, so it won't do any of the work when watching TV by my separate frontend, right?  It just serves up the file and my frontend worries about the decoding.  Then my backend won't need a big CPU at all, since I'll hardware encoders.  Is this accurate?  

My frontend is already pretty beefy, but I'm probably going to get a card with hardware decoding.  I've only seen cards with MPEG-2 hardware decoding though; will this still aid in decoding MPEG-4?  I think much of my stuff is encoded with MPEG-4, so this is important to know.

---

### Post by newlinux on 2007-08-20
> **seepage87 said:**
> Hold on, I think my last question was kinda irrelevant.  This box will just be a backend, so it won't do any of the work when watching TV by my separate frontend, right?  It just serves up the file and my frontend worries about the decoding.  Then my backend won't need a big CPU at all, since I'll hardware encoders.  Is this accurate?  

Yes. that is mostly accurate. However, hardware encoding is for analog signals. Digital signals don't need to be encoded, just captured. And encoding analog signals isn't really that intensive, but hardware encoders in my experience produce a better picture for analog recordings. I'm just saying this last part for clarification cause it sounds like you are mostly interested in digital signals. In any event, and athlon 1.8Ghz should have no problems capturing and serving to a frontend digital or analog streams.

> 
My frontend is already pretty beefy, but I'm probably going to get a card with hardware decoding.  I've only seen cards with MPEG-2 hardware decoding though; will this still aid in decoding MPEG-4?  I think much of my stuff is encoded with MPEG-4, so this is important to know.

Linux won't likely won't be able to take advantage of most of the hardware decoding features of the video card. That's why getting a really beefy one won't help you much with mythtv. As I wrote earlier, the drivers aren't there (yet) and XvMC is about all you'll be able to use for hardware decoding (and it is a little buggy). Right now it is only supported by nvidia cards. 

How beefy is your frontend? I can playback 720p with a P4 2.6Ghz Hyperthreading without a stutter with a Geforce Mx 440 (without XvMC) at about 70-80% processor use. Chances are, if you have any dual core processor and a nvidia video card you won't need software decoding to display up to 1080p. If you will be decoding HD H.264 files you might need to worry about beef a more, however I don't think you'll find linux drivers that will take advantage of any onboard MPEG-4 support.

---

### Post by newlinux on 2007-08-20
> **seepage87 said:**
> Ok, two more quick questions.  

If I have digital cable, are all the channels already digital, or will the cable company transmit some of them analog?


Sorry, I just passed over this question.

Most US cable companies still also transmit analog stations in as well as the digital stations (if they didn't, any non digital TV without a set top box or a converter would not be able to watch any cable). There are a couple of areas where they completely switched off the analog signal (and consequently pissed off a lot of people, requiring them to get set top boxes or converters at their own expense). However, in 2009 analog is completely going away.

My cable company transmits both. However, most of the digital stations are encrypted and require a set top box (which, as stated before, varies from location to location. I can get all my HD locals -- ABC, FOX, CBS, NBC, CW, PBS-- and a few other stations unencrypted via QAM without a set top box). The analog stations are not encrypted, and thus for a couple of stations I watch I use the analog tuner and/or my firewire connection to the cable box (which gives a better picture than my analog tuner because they are digital).

---

### Post by seepage87 on 2007-08-21
Thanks for all the help.

In case anyone is interested, I think I'm going with an 8 x SATA hardware RAID 5 solution using 5 500Gb HDs (which I can get for about $100 now).  It's a little pricy, but it will give me room for 3.5 TB down the road, so I think it'll last for a long time.  Still looking for the right controller though (any suggestions).

I looked into the Hauppauge cards, and many people suggested getting 2 pvr-150s instead of a 500, since the latter's video quality is lacking, as is support for the card, so I think I'm getting those.

Going to try out my frontend as it is.  It has a ATI graphics card which I understand isn't well supported anymore.  If it ends up not doing the trick I'll look into getting a nvidia card.  Maybe the 5200.  I'm happy so long as I can DVI connect it to my TV.

I'll keep my mobo and processor, use 512 ram (maybe 1 Gig).

I think the whole system will turn out well, though if anyone sees any red flags, please let me know.  Again, thanks for all the help.

---

### Post by newlinux on 2007-08-21
> **seepage87 said:**
> Thanks for all the help.

In case anyone is interested, I think I'm going with an 8 x SATA hardware RAID 5 solution using 5 500Gb HDs (which I can get for about $100 now).  It's a little pricy, but it will give me room for 3.5 TB down the road, so I think it'll last for a long time.  Still looking for the right controller though (any suggestions).

I looked into the Hauppauge cards, and many people suggested getting 2 pvr-150s instead of a 500, since the latter's video quality is lacking, as is support for the card, so I think I'm getting those.

Going to try out my frontend as it is.  It has a ATI graphics card which I understand isn't well supported anymore.  If it ends up not doing the trick I'll look into getting a nvidia card.  Maybe the 5200.  I'm happy so long as I can DVI connect it to my TV.

I'll keep my mobo and processor, use 512 ram (maybe 1 Gig).

I think the whole system will turn out well, though if anyone sees any red flags, please let me know.  Again, thanks for all the help.

My understanding is that physically the pvr-500 is two pvr-150s on one board, so it seems unlikely to me to have much worse quality. It even has 2 separate inputs, so it doesn't split the signal. According to [https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list) the pvr-500 is supported right out of the box (as is the pvr-150). So support shouldn't be an issue. The bigger problem will probably be the quality of analog cable transmission in your area.

Good luck. Don't see any red flags, but then, I don't know what your frontend hardware is. Also, are you planning to do any HDTV or digital capture?

---

### Post by seepage87 on 2007-08-21
I'm hoping to, but I have to check what comcast is like in my area (Baltimore).  I might just have to settle for the outputs from my cable box, though I think there's firewire jack on the new box I'm getting that I can use.  If there is, then can I get HDTV to record that way even if it was previously encrypted?

---

### Post by newlinux on 2007-08-21
The cable box decrypts the signal, so at that point, QAM encryption wouldn't be the determining factor. The 5c content protection setting determines whether or not you can capture from the firewire on a channel by channel basis. If it is turned off (5c = 0/CCI=0) then you can. You can check the content protection setting with the link I sent above (channel by channel) if you have on of those model cable boxes...

 I capture HDTV and SDTV digitally this way. The cable box gives me access to more channels via firewire than I can tune with a QAM tuner. But I use both, since most of what I record are the HD locals, which are sent unencrypted. 

If the content protection is set, you can still capture the station, but not via firewire. You'll can do it recording from the composite or S-video outputs, and have mythtv change the channel on the box for you. Which means good video quality, but not HD, and no dolby digital.

---

