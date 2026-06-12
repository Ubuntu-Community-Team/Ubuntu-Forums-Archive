---
title: "Ubuntu NAS for Mac Environment"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by jollyboy on 2011-02-03
Hello all,

I'm really new to the Ubuntu scene, so please pardon the ignorance as it chooses to show itself at key moments.

I am in a little bit of a pickle. I've been using Mozy to back up all my files from my Mac Mini which acts as a HTPC and all around file server (multiple USB hard drives attached). Its been working great, until a few days ago when Mozy sent me an email saying they are going to jack up the rates (aka. make a profit?) on their service. The problem with that is that I have 1.1TB backed up with them and the new rate is 125gb for $10 as opposed to $5 for Unlimited backup space. Massive dissapointment.

This has led me to decide on building a NAS that will work with my Mac lifestyle. ):P After some research and conversations I am thoroughly confused and annoyed as there is no one right way of doing this; probably due to my needs and plethora of options. 

That said, I want to list out my needs and concerns and maybe someone who is much more capable/knowledgeable that I will help.

[B]My current hardware:
[/B]
Mac Mini (latest one) 4gb ram - will be used heavily to access the NAS and play movies/photos/slideshows ... I have the latest version of Snow Leopard
Airport Extreme Base Station (yeah, the one that allows you to attach a HD to it)
Misc sized USB hard drives (I would consider buying new ones)
$500 budget

[B]Here it goes:
[/B]
1) I need to be able to see this drive on my desktop
2) I need to be able to use it as a backup solution for My Lightroom photos
3) I need to be able to download HD content (4-50gb files) from newsgroups to it (SABNZB) ... yeah, I'm that guy. Specifically I mean large MKV files, etc.
4) Optional iTunes Server use
5) I would like RAID 5 so that its redundant
6) Hardware RAID Controller or FakeRAID (motherboard) controller?
7) Would love to be able to buy a $200 machine from eBay and then pay for a hardware RAID controller? Does it work that way?
8) I need it to not have problems with drive formatting (ZFS, UFS, HFS+, etc)
9) If the computer breaks (motherboard, controllers, etc), I'd like to be able to quickly get it all back online
10) The ability to hot-swap drives if need be. For example, if I want to add another 2tb drive I should be able to put it in and it would automatically add itself to the RAID. This is a huge plus but not a deal-breaker. Its not too hard to restart and add one
11) Hardware vs software RAID? Benefits?
12) I'd like to be able to remote desktop in.
13) it should be fast
14) Anything else I am missing like, is FreeNAS more suited, etc etc

I know this is a lot of info to ask for, but these are the things I am struggling with.

.lau

---

### Post by jollyboy on 2011-02-03
bump?

---

### Post by dBuster on 2011-02-03
Why don't you check out the drives such as the Western Digital My Book World Edition II.  That is what I have and absolutely love it!  So nice to not have to worry about another pc setup to run as a file server and I have all the access I need.  Albeit I am running Ubuntu but it is MC and Windows friendly.

> Easy to set up, easy to find on your network.
Set up is a snap; in just a few minutes you're up and running. 

Windows Vista and Mac computers will automatically find your My Book drive in seconds. Our simple discovery software makes it easy to find the drive with Windows XP systems.

User serviceable.

Want to upgrade a drive? Simply open the case and replace the existing drive – no screwdriver needed.

Built-in media server.
Now you can easily back up data from all your networked computers with the included Stream music, photos and movies to any PC, Mac or DLNA certified multimedia device such as Playstation® 3, Xbox 360®, wireless digital picture frames, and connected audio receivers. DLNA 1.5 & UPnP certified. 

Centralize your music collection and play from Macs or Windows PCs using iTunes® software.

High-speed data transfer with Gigabit Ethernet.
Gigabit networking and transfer rates are five to six times faster than other standard 10/100 Ethernet network storage systems. This performance is comparable to USB 2.0 direct-attached storage.

Your results will vary based on the file size and format, settings, features, software and other factors.

Capacity gauge.
See at a glance how much space is available on your drive.

iTunes server support.
Centralize your music collection and stream to a Mac or Windows PC using iTunes software.

USB 2.0 utility port.
Turn any USB drive into an instant network drive or extra capacity for your World Edition II.

View your photo collection with your mobile device.
Use your iPad, iPhone, iPod touch, or Android smartphone to get quick access to all the photos stored on your My Book World Edition II network drive. Download the free WD Photos photo viewer app and show off your entire photo collection without taking up tons of space on your mobile device. 

Simple file recovery.
Restore lost, damaged or older files back to their original location with a couple of clicks. Backup files are stored in the same file structure that you originally saved them, so it's easy and intuitive to find files.

Works seamlessly with both Windows and Mac computers.

Access and save files seamlessly from both your Windows and your Mac computers.

Cooler, quieter, eco-friendlier.

Equipped with WD drives using WD GreenPower Technology, this system consumes significantly less power and delivers performance on par with power hungry externals using 7200 RPM hard drives.
Remote access.

Access your files anywhere, anytime using MioNet remote access technology from WD. MioNet remote access technology also makes it easy for you to securely share documents with customers and vendors.

[My Book World Edition II](http://www.wdc.com/en/products/products.aspx?id=290)

---

### Post by jollyboy on 2011-02-03
too expensive. I had my eyes on a a synology drive or drobo but by the time i load it up with drives i'll be close to $1500... which is quite a bit more than what I am willing to spend right now.

---

### Post by dBuster on 2011-02-03
> **jollyboy said:**
> too expensive. I had my eyes on a a synology drive or drobo but by the time i load it up with drives i'll be close to $1500... which is quite a bit more than what I am willing to spend right now.

Too expensive?!  I would say not compared to what you posted.

the 2TB as well as 4TB drives both are under $500!!!!!

I believe they are even under $450.00  

Plus the nice thing, this drive unit can take additional drives off of the USB port on the back so if you have already USB drives they can be added on no problem.

---

