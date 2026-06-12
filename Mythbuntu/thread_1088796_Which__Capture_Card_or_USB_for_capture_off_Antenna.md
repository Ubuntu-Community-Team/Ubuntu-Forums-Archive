---
title: "Which:  Capture Card or USB for capture off Antenna?"
date: 2009-03-06
forum: Mythbuntu
---

### Post by io5150 on 2009-03-06
Hello,

I am a bit confused at the moment concerning what I need to purchase to get me going in the right direction for a mythbox.

I live in W Texas (USA) We have done away with satellite to save some on our monthly budget - switched over to Netflix (with Roku).  We have a powered antenna and a digital converter box that gets really good reception in the living room.  I am using an older 36" Toshiba CRT TV.  No HD, but it still has a great picture.  I won't be getting an LCD or Plasma any time soon (unless someone wants to donate :))

I am attempting to put together a mythbox on a limited budget. I have two systems with which I can build the box.  Here are the quick specs on the two systems.  (Wifey gave a thumbs up to use whichever system will work best for the task at hand :D)

System 1 Dell Dimension 2400 - Currently XP Home - very underutilized, in small tower.  Wifey currently uses the machine to work with Quicken 2008 for former employer.  
[LIST]
[*]P4 - 2.66 GHz
[*]1.25 GB RAM
[*]Intel 82845G onboard graphics
[*]On-board 100MB NIC - Broadcom 440x
[*]On-board sound - AC 97
[*]3 PCI slots - No AGP slots
[*]2.0 USB
[*]250W power supply
[*]40G HD w/ 6GB backup drive (internal)
[*]CD-R drive (can add DVD)
[*]No SATA support
[/LIST]

System 2 - Home Brew in EMachines tower - Ubuntu 8.10
[LIST]
[*]MSI KM4M - V with Sempron 1.6GHz
[*]512 GB RAM
[*]NVidia GeForce2 MX/MX 400 AGP 4x (on-board is S3 UniChrome)
[*]On-board NIC or 2Wire USB adapter (currently working with ndiswrapper)
[*]On-board sound - AC 97
[*]3 PCI Slots
[*]1 4x/8x AGP slot
[*]2.0 USB
[*]350W power supply
[*]60GB HD
[*]SATA support, if needed
[*]DVD & CD-R drives (specialized to case)
[/LIST]
I have been attempting to get the S-Video out to work with my TV but have had trouble with it... could use some help in this.  I am assuming the best I can hope for is 800x600?  I was planning on using this box as I traded with other geeks for the parts (case, MB, CPU, PS, etc).  I was hoping to run it both as a backend and frontend ... but was unsure it was powerful enough.  It is somewhere between the minimum and suggested system requirements on the mythtv site.

Both machines can be rebuilt to meet needs.
I have (2) 20Gb hard drives that can be added in the mix as well.
I am also planning on dropping some cat5e to the living room from my study (where my 2Wire router is).  I have an old 100MB 4-port Linksys router to work with (currently configured as a switch to work with my 2Wire router).  I have Fiber 3Mb synchronous (AT&T) in my study.

OK ... now we have the hardware listed I an ready to ask for advice on where to go from here.  

1. What I want the HTPC/Mythbox to do (if possible):
[LIST]
[*]Watch recorded TV programs that are captured from the local antenna (digital broadcasts) on ABC, CBS, NBC, FOX
[*]Play DVD, audio CDs, video from media and web browser stream
[*]Browse web (might not be possible if I can't get sharp enough resolution on my TV out to read web pages)
[/LIST]


2.  Capturing digital broadcasts
If I purchase something like the PVR-150 - isn't this an analog capture device?  Will I need a converter box to bring the signal from digital to analog as I do currently with my TV?  Are there PCI cards that will capture the digital signal directly - no need for converter box?  Is there a USB or Firewire solution that is compatible with Linux?  Maybe purchase a second antenna for the HTPC?

3.  Should I consider using both machines?
Use one for the backend (Dell utilizing both 60GB & 40GB drives).  Virtualize the XP Home with VirtualBox under Ubuntu and use it only for the Quicken when she needs to use it - which is rarely.  Use the MSI machine as a front end using a 20GB HD GeForce2 card - get the Video out working properly?  I can get an image on the TV but if I attempt to play any video only the audio comes through (blank video).  

4.  VGA to TV conversion?
Would I have better luck (and get better results) using some type of converter box for PC to TV connection?  For example
[http://www.svideo.com/vga2videosmall.html]("http://www.svideo.com/vga2videosmall.html")

5.  Parts needed?
Is there anything besides the Cat5 and a video capture device that I will need beyond what I already have?  Something that I am not aware of?  I am hoping that the problems I am having with the GeForce2 card is more a matter of configuration than the card being unusable for what I want to do.  BTW ... I do know I need some type of wireless mouse and keyboard combo, but I think I have that covered.

I would appreciate any and all advice on this issue.  Wifey would be happy to be able to record her shows again (CSIs, Criminal Minds, Numbers, Idol, etc) and watch them at her leisure.   

David

---

### Post by theophile on 2009-03-06
Since you'll be using an SD television, I'm not sure there's any advantage to using an ATSC tuner to record the digital broadcast. If you use the converter box in conjunction with an NTSC tuner, I *think* the final picture on the TV will be comparable. The biggest difference is the amount of space the recordings occupy. A 1 hour show recorded in HD is over 6 GB whereas an analog recording is usually 1 GB or less. You'd be able to keep a lot more recordings if you went the NTSC route.

If you want to future-proof your setup, you can just get a dual NTSC/ATSC tuner. That way, in addition to being able to try it both ways and see if you notice a difference in the picture quality, you'll have it in case you do get an HD set in the future.

The short answer is that the 150 will work just fine with your converter box.

---

### Post by io5150 on 2009-03-06
> **theophile said:**
> Since you'll be using an SD television, I'm not sure there's any advantage to using an ATSC tuner to record the digital broadcast. If you use the converter box in conjunction with an NTSC tuner, I *think* the final picture on the TV will be comparable. The biggest difference is the amount of space the recordings occupy. A 1 hour show recorded in HD is over 6 GB whereas an analog recording is usually 1 GB or less. You'd be able to keep a lot more recordings if you went the NTSC route.

I am assuming that the quality that I see on my TV (which is converted back to SD from digital) is good enough.  Considering my size limitations in HD space (60GB for the largest drive I have available for the project) HD recordings directly from the antenna would eat up the space PDQ.  *Note to self:  Larger Drive. *

> **theophile said:**
> If you want to future-proof your setup, you can just get a dual NTSC/ATSC tuner. That way, in addition to being able to try it both ways and see if you notice a difference in the picture quality, you'll have it in case you do get an HD set in the future.

I wish that were so.  Wifey lost her job last summer.  She's working again ... but overall income is down by 25%.  We've made drastic cuts in our budget (lost the cars, but kept the house).  We have kept internet and switched to Netflix for entertainment (killed dish - but missed the DVR severly - hence this project).  Don't see a HD in the near future at all and am trying to keep expenses down for this project.

> **theophile said:**
> The short answer is that the 150 will work just fine with your converter box.

I guess I am missing a piece of the puzzle.  How will the analog 150 select for channels if there is a converter box in between the antenna and pc?  Will it automatically scan & discriminate channels by just being connected to the converter box (like a passthrough)?  To view channels now I have to manual change the channels on the converter box.

Thanks,
David

---

### Post by newlinux on 2009-03-06
The PVR-150 can capture from the converter box "VCR Style" (via composite input or RF) just like your TV connects to the converter box. With an IR blaster you can have myth change the channels on the converter box for you - but you'd have to get an IR blaster and configure that (this assumes your converter box receives infrared signals from a remote control). I think some PVR-150s may come with one, but I'm not sure.

you would also need to set up the channels in myth yourself, scanning won't work. But this is as easy as adding the channels you want to be able to view and record from...

The other issue with recording direct ATSC streams via antenna is that your box will have to not only have the capability to store HD streams (enough hard drive space) it will also have to have enough power to decode HD streams (even if you will be displaying them in SD). I'm assuming your OTA digital broadcasts are of HD quality for your major local stations. Your P4 2.6 is borderline but should be able to do it (I had a P4 2.6 that could) but your sempron will probably struggle unless you can get XvMC working on that Geforce card. Of course, if you only care about recordings, you'd could transcode them to SD, but that might take a while.

As far as costs go, please note you can get dual NTSC/ATSC tuners for the same price or less than the PVR-150, depending on where you look. My kworld 110/115s cost aroun ~$45 - less than my PVR-150 cost. But they require software analog encoding. I doubt you can find those now, but there may be others. I haven't bought a tuner in over 2 years :).

---

### Post by Caps18 on 2009-03-06
> **io5150 said:**
> 
2.  Capturing digital broadcasts
If I purchase something like the PVR-150 - isn't this an analog capture device?  Will I need a converter box to bring the signal from digital to analog as I do currently with my TV?  Are there PCI cards that will capture the digital signal directly - no need for converter box?  Is there a USB or Firewire solution that is compatible with Linux?  Maybe purchase a second antenna for the HTPC?

[http://pchdtv.com/](http://pchdtv.com/)

The hd5500 is what I use to grab digital OTA.  I just have one antenna going into it.  MythTV takes care of setting up the channels and other converter box duties.  It might be one of the higher priced cards though.  It's still cheaper than satellite or cable in the long run.  And it will be functional if you decide to upgrade to HDTV in the future.

I use the MCE remote from Newegg and it works well.

---

### Post by rodercot on 2009-03-07
I use a PVR-1250. They are Cheap sub 50 in some places and it is natively supported in .021 and K 2.6.26.4 and up I think, check linuxtv to be sure.  The only thing I had to do was switch my audio output back to spdif from hdmi as for some reason I could get no sound via hdmi for OTA. But I have found a //dev/mixer Alsa error in my backend.log, that I have not been able to fix yet, which could be the solution. 

 I had tried a HVR-950Q with the FW from linuxtv's links it loads fine and works. I assumed it was not as it was not finding but two channel on a scan BUT this turned out to be that my city just sucks for OTA pick-ups. So the HVR-950Q would work as well.

 I have sense added a 4 band Channel Master antenna in the attic pointing at one of the local towers and I pick up about 6 channels, I am going to get the digiwave amplifier and another antenna pointing at the other tower to see if I can get the other 6 channels that are suppose to be here. For me in Ottawa there are two tower ofcourse one is northwest and the other is south east of me. The digiwave amplifier allow for two UHF antenna's and one VHF antenna up to 100 miles to the source or more. I cannot get any plattsburg or Watertown channels right now, but I think when I put the antenna's on the roof in the spring it will fix this and maybe switching to the 8 band antenna will help as well. It seems to be the rec antenna at most OTA site, I think it is model 4228 from channel master, digiwave also makes some really cool antenna's to check out.

 I am not completely up on this yet as I have just started playing around with it all a couple weeks back. So far it looks good tomorrow and Nascar will be the first full HD show I will watch so I will see how it looks and if it was a full waste of $$$.

 Dave

---

### Post by Caps18 on 2009-03-07
> **rodercot said:**
> So far it looks good tomorrow and Nascar will be the first full HD show I will watch so I will see how it looks and if it was a full waste of $$$.


It isn't a waste of money.  I just wish they didn't talk as much so I could turn up my 18" sub and wear earplugs to feel like I was there.

---

### Post by io5150 on 2009-03-21
Hello,

More questions.  

FYI ... I ended up getting a little VGA to TV converter box that works quite well.  Good enough on video, but not too good on text.

The main question I have concerns storage.  I have an external USB drive (250G, USB 2.0) that is being under utilized in terms of storage use (backup).  I could drop a 60G in my main system for backup purposes and switch the external over to the PVR.  I plan on coming straight off the antenna (which will be HD recording - unless the tuner card can convert the signal to SD on the fly - I won't waste time converting the videos because they will be kept only long enough to view then deleted).

Will the external drive be fast enough for my purposes?  I will definitely need the space.  

Thanks,
io

---

### Post by newlinux on 2009-03-21
I;ve done external drive HD Mpeg-2 recordings before without a problem. USB 2.0 should be fast enough.

---

