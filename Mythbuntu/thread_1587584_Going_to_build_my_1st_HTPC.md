---
title: "Going to build my 1st HTPC"
date: 2010-10-03
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-10-03
It's been a few years since I built a system, and I'm a noob with HTPC, and I'm seriously considering putting one together &#8943; now that I've retired.

I'd like comments on my proposed approach, please&#8230;

Stand alone Personal Digital Video Recorder 
(no general purpose computing, games or over-clocking) 
to be used for mostly off-air recording and delayed viewing.

Monitor/video will be 47" LCD HDTD via HDMI, may use 2nd monitor to view system performance, *&c*.

Plan to use the Media Center certified remote control transmitter from Hauppauge

MythTV from mythbuntu 10.04 distro (will leave a partition for possible windows intallation), will be a combined front-end and back-end.

&#8943;Processing&#8943;
·AMD Athlon II X2 260 Regor 3.2GHz 2 x 1MB L2 Cache Socket AM3 65W Dual-Core Desktop Processor
·SILVERSTONE NT07-AM2 80mm CPU Cooler
·Foxconn A74ML-K 3.0 AM3 AMD 740G Micro ATX AMD Motherboard
·Crucial 2GB (2 x 1GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Dual Channel Kit 

&#8943;Physical&#8943;
·SeaSonic SS-300ET Bronze 300W ATX12V V2.3 80 PLUS BRONZE Certified Active PFC Power Supply
·SILVERSTONE Black Aluminum / 0.8mm SECC Grandia Series GD05B

&#8943;Video&#8943;
·EVGA 512-P3-1240-LR GeForce GT 240 512MB 128-bit DDR5 PCI Express 2.0 x16 HDCP Ready 
·Hauppauge WinTV-HVR-2250 Media Center Kit Dual TV Tuner

&#8943;Storage&#8943;
·Western Digital Caviar Blue WD3200AAKS 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive
·Western Digital Caviar Green WD20EARS 2TB 64MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive
·Sony Optiarc Black 18X DVD-ROM 48X CD-ROM IDE DVD-ROM Drive Model DDU1678A

&#8943;Network&#8943;
·Rosewill RNX-G300EX IEEE 802.11b/g PCI Wireless Card

POWER BUDGET
&#8943;[http://www.thermaltake.outervision.com/](http://www.thermaltake.outervision.com/)&#8943;

System Type: &#8213; Single Processor	
Motherboard: &#8213; Regular - Desktop	
CPU: &#8213; AMD Athlon II X2 260 3200 MHz Regor	
CPU Utilization (TDP): &#8213; 85% TDP	
RAM: &#8213; 2 Sticks DDR3 SDRAM	
Video Card: &#8213; NVIDIA GeForce GT 240	
Video Type: &#8213; Single Card	
Regular SATA: &#8213; 2 HDDs&#8943;320GB system, home(Ext3), swap; & 2TB video & back-up (XFS)	
DVD-ROM Drive: &#8213; 1 Drive&#8943;Sony Optiarc Black 18X DVD-ROM	
AdditionalPCI Card: &#8213; 1 Card&#8943;PCI Wireless Card	
PCI-e x1: &#8213; 1 Card&#8943;TV Tuner	
Fans Regular: &#8213; 1 Fan 80mm (cpu);  3 Fans 120mm(case)	
Keyboard & Mouse: &#8213; Yes	
System Load: &#8213; 90 %	
 
Recommended PSU Wattage: &#8213; 260 Watts	

P.S. Thanks thanks to LowSky for his great work and posts :)

---

### Post by LowSky on 2010-10-04
Thanks for the shotout, lol...

unless you get the older 2250 with a USB remote, that reciever will not work... sorry to tell you. grab a USB  Windows media center reciever off ebay for cheap

Otherwise the card is pretty good. See my tutorial to get it working.
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

---

### Post by scudderwagg on 2010-10-04
I have a very similar setup with my system.  Slightly older and slower Athlon processor, a ZONTAC GT220 Video card, an HDHR and a firewire connection to a cablebox.  I used a Harmony 880 remote with MCE IR reciever and a slightly customized lirc setup.  I use it mostly for delayed viewing, watching movies (ripped from DVD) and playing music.  It works great, have it plugged through the Onokyo reciever for awesome sound.  The only hiccup is I had to fix ALSA to get the sound output over HDMI.  See [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Oh and I was a total linux noob before I setup up this system and while a few issues were challenging (HDMI sound), it was relatively easy overall.

Best of luck!

---

### Post by keepitsimpleengr on 2010-10-04
> **LowSky said:**
> Thanks for the shotout, lol...

unless you get the older 2250 with a USB remote, that reciever will not work... sorry to tell you. grab a USB  Windows media center reciever off ebay for cheap

Otherwise the card is pretty good. See my tutorial to get it working.
[http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212)

Thanks!  I already have it bookmarked, and it was the post that let me decide to proceed with the project. :)

---

### Post by keepitsimpleengr on 2010-10-04
> **scudderwagg said:**
> I have a very similar setup with my system.  Slightly older and slower Athlon processor, a ZONTAC GT220 Video card, an HDHR and a firewire connection to a cablebox.  I used a Harmony 880 remote with MCE IR reciever and a slightly customized lirc setup.  I use it mostly for delayed viewing, watching movies (ripped from DVD) and playing music.  It works great, have it plugged through the Onokyo reciever for awesome sound.  The only hiccup is I had to fix ALSA to get the sound output over HDMI.  See [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

Oh and I was a total linux noob before I setup up this system and while a few issues were challenging (HDMI sound), it was relatively easy overall.

Best of luck!

Thanks for the great pointer!  One of my concerns was HDMI to my grand old Yamaha receiver, so that concern is history.:guitar:

---

### Post by PhilWig on 2010-10-04
A few observations (or personal prejudices) from one who's by no means an expert but has got Mythbuntu 9.04 working and has domestic harmony depending on it staying that way!

1.  keeping PVR and other functions separate and having a dedicated system is very wise.  Auto switchon and closedown works too via Myth welcome.

2. you have no doubt seen adverse comments about AMD graphics and avoided that by including an Nvidia graphics card, but you might consider a mobo with onboard nvidia.  I've gone for the Asus M3N78-EM with 8300 which is great with HDMI standard definition, but I've not tried high def.  There will be updated mobos since I bought mine in summer 09 though.

3.  That PSU looks a bit low.  PSU problems can be terrible to diagnose and highly loaded PSUs have a short life.  I'd be inclined to go a bit higher.

4.  I confirm that my Hauppauge remote (as bought with the T500) has been a troublesome baby.  My son with the same card & remote reports problems with Windows 7 too.  That said, the T500 card itself is PCI, has a dual DVB-T tuner and is very stable.
I have instead a remote wireless keyboard (Keysonic ACK-540RF) which even works with the bios.  In time, I'll get round to trying the media centre remote which I have.

5.  Seems you are chucking in a lot of disk.  Disk traffic is very light compared with SATA transfer rates and you might consider just using one big disk for your 'live' system and maybe another for development purpose.

6.  Loading Windows after Linux can be troublesome as W will grab everything including MBR.  You might find it easier to load it first then load Ubuntu which will sort out dual-boot stuff automatically.  I did that but only now load W by accident!

7. You may find that the second screen is tricky to set up, much though performance monitoring might be desirable.  Window switching may be easier.

Hope that helps.
Phil

---

### Post by keepitsimpleengr on 2010-10-04
> **scudderwagg said:**
> I have a very similar setup with my system.  Slightly older and slower Athlon processor, a ZONTAC GT220 Video card, an HDHR and a firewire connection to a cablebox.  

I suspect my CPU choice is a little more than needed, but I spec'd it to power consumption wrt low profile CPU cooler, maximum performance and reasonable budget.

I started out with a Intel processor because that's what I'm used to, but switched over to AMD to get more bang for the buck when paired with a workable mainboard.

I probably don't need that much video card either, but the nvidia video adapters reportedly can do GPU HD Video Processing under Linux with proprietary drivers.

Thanks again for the feedback :popcorn:

---

### Post by scudderwagg on 2010-10-04
> **keepitsimpleengr said:**
> I suspect my CPU choice is a little more than needed, but I spec'd it to power consumption wrt low profile CPU cooler, maximum performance and reasonable budget.

I started out with a Intel processor because that's what I'm used to, but switched over to AMD to get more bang for the buck when paired with a workable mainboard.

I probably don't need that much video card either, but the nvidia video adapters reportedly can do GPU HD Video Processing under Linux with proprietary drivers.

I think you've made some good choices overall.  I think you get better value for your money with AMD.  I too focused on a power efficient CPU, which is why I ended up with a 2.6ghz Athlon II, which had about the best TDP at the time I was buying my hardware(two years ago).

As for the GPU, a GT2XX is a good value and will do VDPAU (which will keep your CPU happy) hdmi video and audio (with the appropriate tweaks).  My understanding is that anything more than a GT220 is unnecessary, so you could save some money there.

I'm no PSU expert, but I think your 300 watt PSU would be good.  I've got either a 350 or 300W and have had no issues.  Just be sure you're getting a reliable one. I've always checked newegg reviews and have yet to have a significant hardware problem (cross fingers, knock on wood).

---

### Post by keepitsimpleengr on 2010-10-04
> **PhilWig said:**
> has domestic harmony depending on it staying that way!I heard that with my bad ear!> 
…consider a mobo with onboard nvidia.  I've gone for the Asus M3N78-EM with 8300 which is great with HDMI standard definitionThe Asus mainboard is no longer available, and I couldn't find a mainboard with nvidia chips&#8213;which I also prefer.  My pick was for a AMD CPU.  The Foxconn had DDR3 for $50 and got good comments.> 
That PSU looks a bit low.  PSU problems can be terrible to diagnose and highly loaded PSUs have a short life.  I'd be inclined to go a bit higher.PSUs are the bane to system builders, I've got a box of dead ones so I don't forget.> 
I confirm that my Hauppauge remote (as bought with the T500) has been a troublesome baby.I've added a separate remote and receiver!> Disk traffic is very light compared with SATA transfer rates and you might consider just using one big disk for your 'live' system and maybe another for development purpose.The smaller "system" disk will have Ext3 for system, the swap and possible windows partition, the bigger one will have the XFS filesystem for the large video files.  This system will be all HD and will be able to record two videos at once.> Loading Windows after Linux can be troublesome as W will grab everything including MBR.You can take that to the bank!  I may (most likely) will not add Windows.  My ears are still ringing from the thumping I took from Vista.  However my main workstation boots Ubuntu 10.04 (fresh install), ubuntu 10.04 (distribution upgrade, the original was 7.04), Vista Ultimate 64, and Windows XP x64 so I know how to handle that&#8943;but it's great advice!> 
You may find that the second screen is tricky to set up, much though performance monitoring might be desirable.Dual screens are indeed tricky.  I found that out getting them set up on ubuntu 7.04.  The good news is that I have a working xorg.conf for nvidia card and it's a little easier now.> Hope that helps.PhilYes it did, thanks.  Rethinking something like this is always a great idea. :D

---

### Post by keepitsimpleengr on 2010-10-04
> **LowSky said:**
> 
unless you get the older 2250 with a USB remote, that reciever will not work... sorry to tell you. grab a USB  Windows media center reciever off ebay for cheap

I checked eBay and newegg.  Seemed to be a QA problem with the Media Center remote set ups, so I opted for an Adesso set from newegg.  Prices were comparable.

This keeps a single source, newegg, and the price (sans shipping and tax) less than $750.  A new TiVo® Premiere XL with wireless and three years subscription is $858.98 (sans tax) or $783.53 from Amazon. Three years schedule service for MythTV is $60, so for a few bucks more I'm getting at the least three times the recording capability. All being told ***very satisfactory***.

So here's the new bill of materials»

&#8943;Processing&#8943;
1·AMD Athlon II X2 260 Regor 3.2GHz 2 x 1MB L2 Cache Socket AM3 65W Dual-Core Desktop Processor
2·SILVERSTONE NT07-AM2 80mm CPU Cooler
3·Foxconn A74ML-K 3.0 AM3 AMD 740G Micro ATX AMD Motherboard
4·Crucial 2GB (2 x 1GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Dual Channel Kit 
&#8943;Physical&#8943;
5·SeaSonic SS-300ET Bronze 300W ATX12V V2.3 80 PLUS BRONZE Certified Active PFC Power Supply
6·SILVERSTONE Black Aluminum / 0.8mm SECC Grandia Series GD05B
7·Adesso ARC-1100 Vista Infrared Remote Control
&#8943;Video&#8943;
8·EVGA 512-P3-1240-LR GeForce GT 240 512MB 128-bit DDR5 PCI Express 2.0 x16 HDCP Ready 
9·Hauppauge WinTV-HVR-2250 Media Center Kit Dual TV Tuner
&#8943;Storage&#8943;
10·Western Digital Caviar Blue WD3200AAKS 320GB 7200 RPM 16MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive
11·Western Digital Caviar Green WD20EARS 2TB 64MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive
12·Sony Optiarc Black 18X DVD-ROM 48X CD-ROM IDE DVD-ROM Drive Model DDU1678A
&#8943;Network&#8943;
13·Rosewill RNX-G300EX IEEE 802.11b/g PCI Wireless Card

---

### Post by keepitsimpleengr on 2010-10-04
> **scudderwagg said:**
> &#8943;
As for the GPU, a GT2XX is a good value and will do VDPAU (which will keep your CPU happy) hdmi video and audio (with the appropriate tweaks).  My understanding is that anything more than a GT220 is unnecessary, so you could save some money there.
Strangely enough, my first choice was the 220, but the 240 was $10 cheaper.  Go figure&#8230; :confused:
(*Note there's a rebate on the 240*)

---

### Post by keepitsimpleengr on 2010-10-05
Order placed with newegg this a.m. :P

---

### Post by LowSky on 2010-10-05
Awesome keep us updated. If you need help let us know!

---

### Post by keepitsimpleengr on 2010-10-05
Wow, newegg has issued tracking #s for all items in 4 shipments, 2 from southern CA, the CPU from Edison, NJ and the remote from somewhere.

I may get to start on this this weekend instead of next week :cool:

---

### Post by uncle hammy on 2010-10-05
> **keepitsimpleengr said:**
> The smaller "system" disk will have Ext3 for system, the swap and possible windows partition, the bigger one will have the XFS filesystem for the large video files.
No need to get into XFS...use EXT4 for both (which a Mythbuntu install will do by default).  

My original MythTV setup (going back to 7.04) I set my recording drives up as XFS.  There used to be a "daily XFS defragment" option, but one day last year, I noticed (by accident) that my XFS systems were incredibly fragmented.  The option has been removed because of the migration to EXT4.

Long story short, I spent a day moving all my recordings from disk to disk so I could then convert the disks to EXT4.  I have had 0 negative impact from doing this...and I record up to 6 HD programs at once.

---

### Post by keepitsimpleengr on 2010-10-06
Before I start flipping magnetic domains…

There are both 64 & 32 bit MythTV versions.  What are the up & down sides of each, considering this will sit under my television in the den and used just for DVR and video watching? :neutral:

I expect I will default to 32 bit, but never really looked into it

Thanx

---

### Post by LowSky on 2010-10-06
> **keepitsimpleengr said:**
> Before I start flipping magnetic domains…

There are both 64 & 32 bit MythTV versions.  What are the up & down sides of each, considering this will sit under my television in the den and used just for DVR and video watching? :neutral:

I expect I will default to 32 bit, but never really looked into it

Thanx

64 bit will be somewhat faster for transcoding  or ripping video files

---

### Post by scudderwagg on 2010-10-07
> **keepitsimpleengr said:**
> Before I start flipping magnetic domains…

There are both 64 & 32 bit MythTV versions.  What are the up & down sides of each, considering this will sit under my television in the den and used just for DVR and video watching? :neutral:

I expect I will default to 32 bit, but never really looked into it

Thanx

I've been using the 64 bit version for about 2 years and it's worked quite well.  Only problem I have run into is I had a couple of video files in WMV format and it seems the 64 bit version doesn't have all the same codecs as the 32 bit so Myth wouldn't play some of those WMV.  I converted them to AVI and have had no other issues.

---

### Post by keepitsimpleengr on 2010-10-07
OK!  64 bits it is

Remote arrived yesterday, everything else except the CPU here today, I'm getting excited.:P

---

### Post by keepitsimpleengr on 2010-10-09
Hardware assembled and tested, Mythbuntu (64bit) installed and updated, HDMI attached to LCD television and works.

Trying to get an X session running over LAN so I can proceed sitting at my desk as opposed to crouched down in front of the TV.

Pictures at:
[http://picasaweb.google.com/keepitsimpleengineer/HTPVPix?authkey=Gv1sRgCJaAlNvPwpWTGA&feat=directlink](http://picasaweb.google.com/keepitsimpleengineer/HTPVPix?authkey=Gv1sRgCJaAlNvPwpWTGA&feat=directlink)

Didn't need the low profile CPU cooler.

Next step is to get the Hauppauge WinTV-HVR-2250 working...

Good way to spend a Saturday morning :D

---

### Post by keepitsimpleengr on 2010-10-10
Well everything except the audio :-({|=  seems to be working, that's next.  Watching the Cowboys play without audio was curiously refreshing.

Had fits with the remote, seemed the receiver wasn't working.  I plugged it into a Vista system, and it started working.  The MCE remote from Hauppauge doesn't work with the receiver, but the Adesso ARC-1100 works, and has a mouse function on a twiddle pad. (You twiddle it with your thumb)  Pretty cool. :cool:

LowSky&#8943;great tutorial on setting up WinTV-HVR-2250 capture cards.  Thanks! ([http://ubuntuforums.org/showpost.php?p=9219191&postcount=212](http://ubuntuforums.org/showpost.php?p=9219191&postcount=212))

---

### Post by winewood on 2010-10-12
HEY!  I hate being late to a party, but I was out of town.
 
Grats on getting the system to work.  I got my audio to work by un-muting a channel using the alsa gui for the SPIDIF, if its a channel mute/unmute issue, use VLC and play video that you recorded.  You can use alsagui and play with the settings until you find which one can work for you.  The VLC windowed lets you keep your Frontend settings while you goof around with the sound.
 
I too bought the 2250 and it works well.  I did find that adding more channels wasn't possible as I ran out of PCI slots to put  it in.  If you want to upgrade to a 3rd and 4th channel, I strongly recommend the Silicon HDHomerun.  You will laugh at how easy it is vs the Hauppauge install.   In 5 minutes I had it up and working and there seems to be no difference in their workings.
 
As for remotes, I found that the MCE was the easiest to install, and the remote "in didn't work for me for the 2250 in Ubuntu.  The solution was to buy a 2nd remote with a usb plugin reciever.  For $20 bucks I had a 2nd remote and both can use the reciever, and it plugs into the front of my box.  (The wife has her remote/ I have mine)
 
I forsee you wanting a new HD very quick if your are recording HiDef shows.  I went with a 2TB disk for about $150 and i haven't looked back. 
 
Cheers!

---

### Post by keepitsimpleengr on 2010-10-12
So now that's the H/W is working, I ran into a glitch in the setup. :(

New [thread]("http://ubuntuforums.org/showthread.php?p=9961916#post9961916") for this.

---

### Post by keepitsimpleengr on 2010-10-13
> **winewood said:**
> &#8943;I got my audio to work by un-muting a channel using the alsa gui for the SPIDIF, if its a channel mute/unmute issue,&#8943;

How exactly did you launch the "alsa gui"?

I'm having fits with the audio, see this [thread]("http://ubuntuforums.org/showthread.php?p=9961916#post9961916").

---

### Post by LowSky on 2010-10-14
> **keepitsimpleengr said:**
> How exactly did you launch the "alsa gui"?

I'm having fits with the audio, see this [thread]("http://ubuntuforums.org/showthread.php?p=9961916#post9961916").

just type alsamixer in an open terminal

---

### Post by rhossack on 2010-10-24
I really appreciate this thread ... going to help me with my HTPC project I started today.

Looking at both MythTV and Freevo and weighing my options.

I've been gathering parts for a year and think I have everything I need to get this going.

Only thing I have second thoughts on is the on-board ATI video

Case: Silverstone GD05
PS: COOLER MASTER Elite 460
MB GIGABYTE|GA-MA785GM-US2H RT
CPU AMD ATH II X2 240 AM3 2.8G
Memory: G.SKILL 2GB 
Keyboard/Mouse: Rocketfish Wireless Bluetooth RF-BTCMBO2
HD: WD Caviar Green WD5000AADS 500GB
TV Tuner: SILICONDUST HDHOMERUN Dual Digital

---

### Post by LowSky on 2010-10-24
dont worry about ati onboard. vdpau is a nice feature but you will be fine with that CPU doing the work. sure it will run a bit hotter but it will not be dratic drain on the system.

I used an ATI card for a little while and only switched when I baught a new card for gaming. It worked very well.

---

### Post by wsume99 on 2010-10-28
> **LowSky said:**
> dont worry about ati onboard. vdpau is a nice feature but you will be fine with that CPU doing the work. sure it will run a bit hotter but it will not be dratic drain on the system.
 
I used an ATI card for a little while and only switched when I baught a new card for gaming. It worked very well.I too have a 785G MB that I would like to use for a Myth HTPC. I was considering getting a LGA775 MB with nvidia 9300 on-board graphics because so many people seem to prefer nvidia graphics with Linux. How much processor is needed to account for the absence of vdpau? Will a Sempron 140 handle the load or does it need to be a dual core (i.e. Athlon) or better?

---

### Post by keepitsimpleengr on 2010-10-28
> **wsume99 said:**
> I too have a 785G MB that I would like to use for a Myth HTPC. I was considering getting a LGA775 MB with nvidia 9300 on-board graphics because so many people seem to prefer nvidia graphics with Linux. How much processor is needed to account for the absence of vdpau? Will a Sempron 140 handle the load or does it need to be a dual core (i.e. Athlon) or better?

Maybe this will help.  With Hauppauge 2250, nvidia 240GTX, AMD Athlon II X2 260 Regor 3.2GHz 2 x 1MB L2 Cache Socket AM3 65W Dual-Core Desktop Processor AMD Athlon II X2 260 Regor 3.2GHz 2 x 1MB L2 Cache Socket AM3 65W Dual-Core Desktop Processor and using VDPAU, I was recording two shows and watching a recorded one,  I got the system load shown [here]("http://ubuntuforums.org/showpost.php?p=10039776&postcount=6").  I am currently shaking out the bugs and glitches in threads' HTPC.  Very happy with the results. :guitar:

---

### Post by LowSky on 2010-10-28
> **wsume99 said:**
> I too have a 785G MB that I would like to use for a Myth HTPC. I was considering getting a LGA775 MB with nvidia 9300 on-board graphics because so many people seem to prefer nvidia graphics with Linux. How much processor is needed to account for the absence of vdpau? Will a Sempron 140 handle the load or does it need to be a dual core (i.e. Athlon) or better?

You will need a dual core at least. The faster the better, AMD Athlon x2 250  ($60US) would be a great choice.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903&cm_re=athlon_x2_250-_-19-103-903-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103903&cm_re=athlon_x2_250-_-19-103-903-_-Product)

Here is what I'm using, its probably overkill to say the least.
[LIST]
[*]**OS:** Ubuntu 10.10
[*]**Processor: **Phenom II x4 B50 (unlocked PII x2 550)
[*]**Motherboard**: MSI 790FX-GD70
[*]**RAM:** G.Skill 1600 DDR3 4GB (2GBx2)
[*]**Graphics:** Nvidia GTX 460
[*]**Hard Drives:** WD Black 2TB (Root, /home, and media storage), WD Black 1TB (media storage), Seagate 500GB (media storage), Samsung 750GB (media storage)
[*]**Keyboard/Mouse:** Rii Wireless Mini Keyboard/Mouse, Logitech Illuminated Keyboard, Logitech G500
[*]**Tuner:** Hauppauge HVR-2250
[*]**Capture device:** Hauppauge HD-PVR
[*]**Printer:** HP 1018 Laserjet
[*]**Monitor:** HannsG 19" Widescreen LCD
[*]**HDTV:** Vizio 37" HDTV
[/LIST]

---

### Post by wsume99 on 2010-10-28
I was actually thinking about getting the [COLOR=Blue][AMD Athlon II X4 610e Propus 2.4 GHz]("http://www.newegg.com/Product/Product.aspx?Item=19-103-899&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo")[/COLOR]

The quad core will give me the ability to do encodes and DVD rips faster.  I'm wondering if I can get a faster quad core with a 95W TDP for less $$$ then back down on the voltage and clock speed to get the same result for less.  Back to Google ...

---

### Post by LowSky on 2010-10-28
same result for less? confused

2 faster cores are better at day to day stuff than four slower cores
plus the 65 watt chip will run cooler

just more to think about

---

### Post by wsume99 on 2010-10-29
> **LowSky said:**
> same result for less? confused
What I (and countless others) am looking for is a chip that sips power and runs cool but has plenty of processing power so that it doesn't get bogged down when doing more CPU intensive work. The [[COLOR=#000000]AMD Athlon II X4 610e Propus 2.4 GHz[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=19-103-899&SortField=0&SummaryType=0&PageSize=10&SelectedRating=-1&VideoOnlyMark=False&IsFeedbackTab=true#scrollFullInfo") is a 45W quad core. However it carries a $138 pricetag. Obviously AMD recognizes that there are many users out there trying to achieve low power but retain some serious computing power thus they charge a premium for this chip. My comment about the same for less was considering the idea that I could purchase a less efficient CPU, like a 65W or 95W TDP, and undervolt and possibly underclock it to mimic an Ath II X4 610e. I found [this article]("http://www.tomshardware.com/reviews/undervolt-cpu-phenom,2348.html") on Tom's hardware where they examined the benefits of undervolting a CPU. What they found is that for AMD chips there was no reduction in idle power consumption because if you're using cool 'n quite then it is already throttled down quite a bit. However undervolting did make a significant difference in the full load power consumption with reductions approaching 20%. So perhaps I could purchase the [Athlon II X4 640 Propus 3.0GHz]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103871") with it's 95W TDP for $100 and save $38 vs. the 610e. Now if I undervolted the processor I might be able to reduce full load power consumption by almost 20% before running into stability issues. Perhaps further power reduction is possible if the clock speed is lowered from 3.0 GHz down to 2.8 GHz. So I might be able to turn a 95W chip into a 65W chip.
 
It's the same concept as buying a X2 or X3 processor and unlocking cores to make it a higher $$ processor. You're trying to get the best value possible.

---

