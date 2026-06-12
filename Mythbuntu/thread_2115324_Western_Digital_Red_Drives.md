---
title: "Western Digital Red Drives"
date: 2013-02-12
forum: Mythbuntu
---

### Post by daone on 2013-02-12
Hi,have been searching Google for a couple weeks and haven't found any specific information I have been looking for. 

I was hoping someone in the Ubuntu community could help me answer an hard drive upgrade question. I am curious if I should get a Western Digital Red or Green drive for my Mythtbuntu backend/frontend system?

I was thinking a WD Red Drive was the way to go as I leave the system on 24/7 usually. Specifically I wanted a new 3TB  [Red Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822236344").

I searched the forums and found this one article  posted last month about ssd and a red drive.[previous user post]("http://ubuntuforums.org/showthread.php?t=2096727&highlight=hard+drive")

I was also interested in changing my boot drive from a mechanical SATA drive to a 64 GB [SSD]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211718")

Mythbuntu System Info
Distro = Mythbuntu 12.04
CPU = Intel E8400
Motherboard = Foxconn P41A-G
Memory = Corsair 4GB DDR2
Video Card = Nvidia Geforce 210
Hard Drive OS Drive = Seagate 750GB ST3750640AS
Hard Drive #2 Media Drive = Seagate 1.5TB ST31500341AS
Hard Drive #3 Media Drive = Seagate 2TB ST2000DM001-9YN1
Power Supply = Seasonic 450 watt
Network Tuners = HDhomerun Prime
                 HDhomerun Dual Tuner Original
TV tuners = Hauppauge HD-PVR  USB
            Hauppauge PVR-250 PCI

I plan on upgrading the main OS drive with the Adata SSD and the Seagate 1.5 TB with a new Western Digital 3TB drive.

I'm just curious if a NAS drive will work just as well as a Green desktop drive when recording multiple HD streams at the same time?

Any reply or info I should consider would be appreciated.

---

### Post by tgalati4 on 2013-02-12
If you haven't found any info in 2 weeks of searching, then you are the source of the information.  Green drives are generally not recommended if you are going to set them up in a RAID configuration.  If they are standalone, then you should be OK.  As far as performance, your network router and cabling and number of services using the network will determine bandwidth, so NAS vs Desktop speed with far exceed what you can push through your local network.

Reading some of the reviews from the link you posted don't give me a lot of confidence of using a WD 3TB Red drive.

As far as recording multiple HD streams, that will definitely stress a drive.  The heads heat up after long (2 hr) writes and can delaminate, resulting in a dead drive.

I would research what drives are being used in TiVo units and cable boxes with DVR capabilities and try to source one of those.  I would also look into server-class drives.  They are more expensive, but you may save yourself some headaches in this application.

---

### Post by PhilWig on 2013-02-12
I’d have thought that the main benefit of an SSD would be faster boot-up.  As you leave your system on 24/7 that would not apply.

Red or Green?  My WD green 500Gb has been super for 4 years now with not a single glitch and not a single issue in SMART data so I'm a fan.  I use mythwelcome so it does not have the luxury of no power cycling.  However, with the bigger green disks WD seem a little coy about rotation speed so I went Seagate for my latest 2Tb drive.  No experience of red.

My approach is:
500Gb  holding root plus swap plus partition holding a backup of recordings

2Tb  with emergency root, emergency swap and /var/lib/mythtv (media)

Disk traffic is nicely balanced.

Each night I automatically do a database backup to the 2Tb and automatically take an incremental backup of a selection of recordings to the backup partition on the 500Gb.  That way I can recover from a single disk failure.  The backup code is published should you be interested - see Mythtv wiki autobackup.sh and autobackup.pl

Phil

---

### Post by BicyclerBoy on 2013-02-12
A small tweak for WD green drives is to increase the head park idle time from the default 8sec (could be 12sec?)
[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

A system SSD can make db access faster & compiling s/w is much faster..

---

### Post by daone on 2013-02-13
I thank everyone who has replied so far.

 My interest in WD red drives goes all the way back to July 2012 tgalati4. I've been a fan of "This Week In Computer Hardware"hosted by Ryan Shrout and Patrick Norton. Over at pcper.com, they wrote a good article about why people should use Red drives for RAID arrays and how this drives are more server reliable.[Full-Review]("http://www.pcper.com/reviews/Storage/Western-Digital-Red-3TB-SATA-SOHO-NAS-Drive-Full-Review").
[TWICH Ep #177 talking about them]("http://twit.tv/show/this-week-in-computer-hardware/177")

I was just making sure I did search the forums before posting my question to make sure I wasn't asking what somebody hasn't already asked?

I'm trying to take advice from the creator of [spinrite]("https://www.grc.com/sr/spinrite.htm"), Steve Gibson. Do not wait until a drive fails before you need to replace it. I know the Seagate 1.5TB in my system is on borrowed time and has had sector problems since I bought it.

My interest in these hard drive upgrades is to reduce noise at the very least as my mythbuntu system is in my living room.The drive noise can be distracting if not irritating when watching something or using other devices like a blue ray player or playing a game console on my plasma television. I sometimes just choose to shut the system down when I know its not needed for awhile to cut down on the noise.

I am aware of the bad reviews on Newegg on the Western Digital Red drive I linked to. But it's not really surprising as just about every hard drive for sale has bad reviews and reliability issues. And I would be fully aware the single drive I purchase may work perfectly, or be a dud out of the delivery package.I was just thinking Western Digital would be more reliable then a similar sized Seagate Drive.

I was hoping someone could post some experience they have had with these Red Drives and if they have used them in a mythtv system? Or if anybody could show me a link to user's experience with NAS and mythtv?

---

### Post by daone on 2013-02-16
Don't know if my last post scared everybody off, or gave the impression my questions were answered.

Anybody have experience with using Red Drives with Mythtv?

Anybody have experience with using NAS with Mythtv?

---

### Post by mroubas on 2013-02-16
I have 2 WD Red drives in my backend which has been running for ~1yr with no issues.

Take a look at MythTV's use of Storage Groups ([http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)). This would allow MythTV to distribute the use of HD's over as many as you have to improve performance and lifetime of the HD's. This also would prevent the need for setting up any kind of RAID storage to accomplish the same task (depending on exactly what RAID you're interested in setting up).

When I put my system together I used 2x 1TB Red drives instead of 1x 2TB drive for this reason. The downsides are that it costs more and takes up more space in your system. On the plus side you could evenly spread 2 or more HD recordings onto 2 or more separate HDs.

My setup looks like this: 1x SSD (OS, SW, etc.), 1x 2TB HD (longterm storage, movies, songs, etc.), 2x 1TB WD Red HD (live tv, recorded episodes)

All of this is housed in a fairly large PC case that will eventually get moved to a closet and only used as a media server. My next step is to add another hard drive to backup the SSD, 2TB long term storage, and other PCs on my network. At the moment I don't plan on backing up my WD Red drives and not worry about losing my recorded tv shows if/when that should happen. I would only lose all of my recordings in the unlikely event that they fail simultaneously.

---

### Post by gordintoronto on 2013-02-16
35% of the reviews on Newwegg gave the Red drive one or two stars. That would scare me off.

When I assembled my system 3 1/2 years ago, all the drives of 1 TB or larger were getting dreadful reviews. I went with a 640 GB Black drive, and it has performed flawlessly. Sample of 1: not significant.

---

### Post by daone on 2013-02-17
Well, price and reliability have been reasons I have held off purchasing a 3 TB drive.

I will consider what mroubas and gordintoronto have said. I would be purchasing a single hard drive as my system has a limit of 4 on-board serial ata ports. I can add a spare Adaptec SATA pci card I have.But I'm aware drives connected would not be full speed and would try to avoid doing that.

The drive would be used for non-critical data. I've always been aware my mythtv system can fail at any time and make peace that the recordings lost would be inconvenient, not devastating.

I have yet to purchase [spinrite]("http://www.grc.com/sr/spinrite.htm"). But I will add the additional cost and use it on what-ever new hard drive I purchase to get more confidence that the new drive will be healthy and reliable. I'd also like to use it on the drive I'm replacing to figure out how far degraded it is at the time of replacement?

---

### Post by Zorbitz on 2013-02-18
Well, the 3TB Red drive is the cheapest of the 3 models if you look at price / capacity.

I've been using four of them in a Synology NAS with no problems at all so far. Excellent performance. Among other things, it serves as storage for my media files (recordings, videos and music), and having fault tolerance for 1 disk (raid 5) is the main reason I did this.

Only been running for aprox 3 months, so too early to know long term stability of the drives though.

---

### Post by topcat5 on 2013-02-18
> **gordintoronto said:**
> 35% of the reviews on Newwegg gave the Red drive one or two stars. That would scare me off....

It's been my observation that reviews on Newegg tend to be overly negative.   Some of it seems to by people who push their system well beyond specs then complain when something fails.  

For a sanity check, see if the device is for sale on Amazon. Usually it is, and if so, compare it to those reviews.

---

### Post by daone on 2013-03-10
Thought I should post an update of what I went and did and my results.

I ended up purchasing the SSD from newegg.com. And I purchased a single 3TB red drive from B&H Photo Video Pro Audio as it was cheaper and decided to take a chance with them. [Link to Sight]("http://www.bhphotovideo.com/c/product/884038-REG/Western_Digital_wd30efrx_3_TB_WD_Red.html")

I so far have ended up installing the 3TB drive without issue and moved all files from my old Seagate 1.5TB drive onto it using ext4 file system. formatted capcity of new drive is 2.773 TB.

I so far as of yet have not installed the SSD, I will eventually. I ended up instead of doing and in place upgrade of mythbuntu 12.04 to 12.10 on my Seagate 750GB drive. I was trying to upgrade my mythbuntu install from using 3.2 kernel to 3.5 kernel and I didn't realize until the upgrade that I went overkill and upgraded everything to 12.10. It is functional but far from perfect. I'm taking the time to learn and know how to do a clean install of 12.04.2 with 3.5 kernel on the SSD.I will put the swap partition on my 2TB Seagate drive to avoid excessive wear and tear on the SSD.

I did purchase Spinrite and tried it. I learned the hard way it is really dependent  on the BIOS and really won't work if the BIOS doesn't detect the hard drive.I foolishly tried it on a USB thumb drive on and old PATA system with my SATA PCI card with an SATA drive connected through the PCI card. Unfortunately Spinrite would just hang on the system and not boot because it was waiting on the BIOS to tell it the drives attached and would detect nothing as it couldn't understand the PCI SATA controller. I tried spinrite on anouther system with USB 2.0, and learned the impossible slow scan rate it would take to scan a drive on USB 2.0 and learned you really need a direct connection to a motherboard SATA port to make a the scan for defects practical. I laughably tried to scan the new RED drive on USB 2.0 and it would have taken 400 hrs to scan 750GB of the drive my external SATA dock reported. All I used spinrite to tell me in 6 hrs was that the drive worked and was not giving any obvious problems.

Have been using the 3TB drive for a week with no problems and I'm happy I made the purchase so far.I will in the future purchase more as my storage needs grow.

---

### Post by grunge09 on 2013-03-10
I have Three Wd Green 2tb drives in Raid5 running on the onboard sata 2 controller (no raid card).  Been running for about 3 weeks with smart monitoring enabled and so far no problems.  

Raid5 runs on a dual core AMD 6000+ CPU w/ 2gb ram.  Running 12.10 Ubuntu Server w/ Samba linked to 3 pcs and a mythtv data store over the gigabit network and no problems so far.  

I have been able to pickup the WD20EARS drives off a popular auction site for $65.00 plus shipping, sometimes less.

---

