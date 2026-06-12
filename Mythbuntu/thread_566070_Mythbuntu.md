---
title: "Mythbuntu"
date: 2007-10-03
forum: Mythbuntu
---

### Post by ender8282 on 2007-10-03
I am getting ready to make a media center PC.  I am going to use mythbuntu as my os.  That was the easy part.  Now I have to decide what hardware to use.  My question is for people who are already running mythbunth.  What hardware are you using and how well does it work.  What mobo, what graphics card, what video card?  I would like like this thread to turn into recommendations of what hardware to use and what hardware to stay away from.

---

### Post by maarten_84 on 2007-10-03
eh..., nvidia works great, (with nvidia driver that is)
and these saa7134 tv-cards worked right out of the box (not that there is anything good on tv nowadays)
and I will try to control it with my phone to be. tomorrow I will buy a walkman phone.

---

### Post by tgm4883 on 2007-10-03
Alot really depends on what you want to do.  Do you want to watch multiple shows at the same time?  High-Def?  Standard-Def?  Do you have Cable, Satellite, etc.?  Where do you live (country)?  Do you wish for this to be a very small box, or does size not matter?  Or do you wish for the backend to be in the other room and have a very very small frontend?  What type of TV do you plan to connect it to(ie, does the TV have DVI, VGA, Component, HDMI, SCART, Composite, etc)?  

I can give you a much better estimate if you tell us your needs.

---

### Post by ender8282 on 2007-10-03
The most important thing for me is for the machine to function as a DVR.  There are a few shows that I like to watch but am not home for.  I would like to run two tv cards so that I can record two shows at the same time.  Most of what I am looking to record will be SD but in time being able to record HD would be nice.  
I think that my preference would be to use component video out from the computer to my TV but this is a weak preference.  
Am I better doing an all in one video card plus a tv tuner card or am I better doing two TV tuner cards and a more basic video card?  Do most tuner cards work out of the box?  Are there any that don't work at all?  What are my best options for remotes?  Should I just use a wireless keyboard/mouse or is there something else that works well?

---

### Post by jabagawee on 2007-10-03
> **tgm4883 said:**
> Alot really depends on what you want to do.  Do you want to watch multiple shows at the same time?  High-Def?  Standard-Def?  Do you have Cable, Satellite, etc.?  Where do you live (country)?  Do you wish for this to be a very small box, or does size not matter?  Or do you wish for the backend to be in the other room and have a very very small frontend?  What type of TV do you plan to connect it to(ie, does the TV have DVI, VGA, Component, HDMI, SCART, Composite, etc)?  

I can give you a much better estimate if you tell us your needs.

My box will be a headless server. I want to record shows mainly, maybe even record two at once. If I want to watch a show in real-time, I'll use my TV. When the US moves to high-def, I'll want my box to be future-proofed for it later. However, I will be recording standard-def as of right now for the most part. I have cable television. For anything more specific, I have cable with Time Warner in Southern California. Size does not matter whatsoever to me; I will be fine with anything up to a midtower ATX. This machine will be my only backend. All of my other computers will have a frontend. My questions are as follows:

What TV tuner card is best for my box? Support for Linux is a must, of course. What GFX card should I use? Remember, I will be outputting to nothing, not even a monitor. Will IGP work for me? What video card will my frontends need? And also, how much HDD space will i need? I plan to use MythTV sparingly, to record anything that catches my fancy. I will be archiving these shows forever; I will probably never want to delete a recording to free up space.

---

### Post by ender8282 on 2007-10-04
> **jabagawee said:**
> 
...  how much HDD space will i need? I plan to use MythTV sparingly, to record anything that catches my fancy. I will be archiving these shows forever; I will probably never want to delete a recording to free up space.

The most common format that I have seen for shows is xvid.  With file sizes of 350MB for an hour long episode (no commercials) you get pretty good quality.  If you record 5 different shows for an entire season you will generate about 45ish GB of data.  I hope that this helps you estimate your disk usage.

---

### Post by laga on 2007-10-04
> **ender8282 said:**
> The most common format that I have seen for shows is xvid.

Remember that you'll also have to transcode your recordings to xvid then which can take some time on slow hardware. However, if you do indeed use your mythtv box "sparingly" then you shouldn't have a problem, I suppose.

---

### Post by tgm4883 on 2007-10-04
> **ender8282 said:**
> The most important thing for me is for the machine to function as a DVR.  There are a few shows that I like to watch but am not home for.  I would like to run two tv cards so that I can record two shows at the same time.  Most of what I am looking to record will be SD but in time being able to record HD would be nice.  
I think that my preference would be to use component video out from the computer to my TV but this is a weak preference.  
Am I better doing an all in one video card plus a tv tuner card or am I better doing two TV tuner cards and a more basic video card?  Do most tuner cards work out of the box?  Are there any that don't work at all?  What are my best options for remotes?  Should I just use a wireless keyboard/mouse or is there something else that works well?

Comfortable HD will require you to get something in the 3+ GHZ range.  Get a hard drive that is a couple hundred GB (mine is 500 GB).  RAM is a little different, 512MB should suffice.

You're better to get a seperate video card and tuners.  For your situation, I would grab a mid level card that does component out.(I know that the Gigabyte GeForce 7300GS comes with a Component Dongle)  And then either 2 PVR-150's, or 1 PVR-500 (Only the PVR-150 comes in low profile if thats what you want.).  As for HD, I would recommend the HDHomerun.  It has two HD tuners in it and is connected via ethernet (it's a seperate box), so it can be placed anywhere and not take up any extra slots.  I personally do not have one, but superm1 does and he would recommend it too.

You will probably get a remote in at least 1 of the PVR-150's (or PVR-500 (you can shop for it without one, and probably should).  IMHO, the Hauppauge remote is crap.   I instead use a Windows Media Center Remote, which I think is far superior.  You don't want to use a wireless keyboard/mouse.  It's highly impractical and a PITA to use. 


> **jabagawee said:**
> My box will be a headless server. I want to record shows mainly, maybe even record two at once. If I want to watch a show in real-time, I'll use my TV. When the US moves to high-def, I'll want my box to be future-proofed for it later. However, I will be recording standard-def as of right now for the most part. I have cable television. For anything more specific, I have cable with Time Warner in Southern California. Size does not matter whatsoever to me; I will be fine with anything up to a midtower ATX. This machine will be my only backend. All of my other computers will have a frontend. My questions are as follows:

What TV tuner card is best for my box? Support for Linux is a must, of course. What GFX card should I use? Remember, I will be outputting to nothing, not even a monitor. Will IGP work for me? What video card will my frontends need? And also, how much HDD space will i need? I plan to use MythTV sparingly, to record anything that catches my fancy. I will be archiving these shows forever; I will probably never want to delete a recording to free up space.

First things first.  You have fallen for a common misconception.  The US is not moving to High-Def.  The US is moving to Digital.  Digital does not automatically mean High-Def.  With that being said, it may be difficult to future proof your box, as you will probably be required to have a cablebox in order to receive all channels (except for local channels).  Last I checked, the date for this to be done is by 2012, and I wouldn't expect the cable companies to jump the gun on that one.

So to future proof yourself, I would recommend some regular cards now and in 5 years (or more) to upgrade your cards.  If you wanted High Def now, then when everything goes digital you may be able to  use your High Def cards.  I believe that the pcHDTV 5500 will be able to receive those digital channels.  I'm not sure about the HDHomerun, although I think that it probably would.

As for your video card, my slave backend is the same way, headless.  I bought some 16mb video card from goodwill for like $3 and that is what is in there.  Come to think of it, it might even be 8mb.

You never wanting to delete these recordings may be a problem.  Although sparingly, once you start recording a couple different shows and your HD will fill up rather quickly.  Transcoding is an option, but even then you're going to run into problems when you want to watch, record, and transcode at the same time.  Throw High-Def in there and you have a serious problem.  

A better solution to that would be to backup to DVDR.  Then you can get away with a smaller Hard Drive (I would still recommend > 100GB) and you will still have the shows archived, that or just plan for adding future storage later on.  Once .21 hits (and you want to upgrade), adding more storage should be a breeze.

---

### Post by jabagawee on 2007-10-04
Nooooo! I fell for a misconception. I thought that was something only for the not-as-n00b as me. That's what I get for my super-duper overinflated ego. But, ummm, I plan to make a RAID 5. 1TB+1TB+1TB. *If* my dad lets me. Which I will make him do. I plan not to delete recordings for a loooooooong time. Why the disk space? I'm going to use the thing as a file server for everything. Do you still suggest pcHDTV 5500 or something from Hauppauge.

---

### Post by tgm4883 on 2007-10-04
> **jabagawee said:**
> Nooooo! I fell for a misconception. I thought that was something only for the not-as-n00b as me. That's what I get for my super-duper overinflated ego. But, ummm, I plan to make a RAID 5. 1TB+1TB+1TB. *If* my dad lets me. Which I will make him do. I plan not to delete recordings for a loooooooong time. Why the disk space? I'm going to use the thing as a file server for everything. Do you still suggest pcHDTV 5500 or something from Hauppauge.

The digital cards that Hauppauge (AFAIK) aren't supported very well in linux yet.  The pcHDTV card was made for linux (Windows support is in the works.  Take that Windows).  I believe the HDHomerun is the same.  I have the pcHDTV 5500 and like it, but would get the HDHomerun if I did it again because it has 2 HD Tuners built in and would free up a pci slot for me.

I would still check with those 2 companies to make sure they will get the digital signal fine.  I would think that they would, but I haven't done any research specifically into that.

---

### Post by jabagawee on 2007-10-04
I guess I'll go with the HDHomeRun. Any ideas where to get it?

Also, I was wondering. Is there any system requirements for MythTV? I saw in another thread that some guy had problems with a single core 2.8GHz AMD thingy. I also plan to run Apache, Jabber,  FreeNX, FTP, BitTorrent, MediaTomb, and DAAP on it. I know I'll probably blow something up. But can someone tell me the requirements for something like this?

---

### Post by rusty0101 on 2007-10-05
9thtee.com, as well as several other retailers (I think you can find some through Amazon) and through ebay I'm sure. I bought two from 9th Tee, and am very happy with them. (I can record more simultanious digital tv than analog at the moment, though I get more analog channels.)

3 T of storage may sound like a lot, but in a RAID 5 configuration, a part of that storage will be set aside for parity to build a recovery system. My Mythbuntu server has been collecting recordings for a little over a month and I am already using more than half a T.

The process starts with I really only want to record a couple of shows that I can't see for one reason or another. Then you get this you know I really want to see that movie, but I don't have time right now, record it for some time next week (or month), and before you know it you're going through the program guide saying 'This one', and 'that one', 'and yeah that too' and a week or two later you start wondering where all the storage space went. And while you think editing out the comercials and transcoding down to xvid will help, it just never is enough.

Recording is generally not a processor intensive situation. Both the hdhomerun and the haupauge cards that have been recommended capture directly to mpeg-2 which means you won't see a significant processor hit for recording. Watching on the other hand can be very processor intensive. I don't know about DAAP or MediaTomb, but for the most part the resto fo the services you are looking at are far more likely to be network bandwidth bound than cpu bound. For the server I would recommend a 1.5 ghz 512 meg or better system. Supporting the RAID5 configuration you are looking at will probably dictate more about the server than anything else. Set this up in an office or basement or someplace that has good circulation to keep the HDs cool. You will want to use good quality co-ax to get the cable to the video capture cards in the box. As noted elsewhere the hdhomerun boxes can sit anywhere that is convienent for the signal. 

Build a decent front end system with a dual core 2.5 ghz processor or so to drive your display. (Acutally you could use an x-box if you would like, though I have not tried that myself.) If you are outputing to a ntsc tv (not digital, not hd component) you can probably use a much slower processor, though you won't have room for growth later on. I have not tried the via itx boards with a hardware mpeg decoder in the video chip, but it is an option as well. The 2.8ghz AMD xp+ chip is not enough in my configuration to handle decompressing HD content. It handles everything else though. A video card with a dedicated MPEG decoder on it that's supported would handle this as well.

---

