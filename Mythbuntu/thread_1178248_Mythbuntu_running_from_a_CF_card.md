---
title: "Mythbuntu running from a CF card?"
date: 2009-06-04
forum: Mythbuntu
---

### Post by Jonte76 on 2009-06-04
Hi there!

Is it possible to run mythbuntu from a CF card or a Microdrive?

I'm thinking of buildning a small MultiMediaPC/HTPC and use Mythbuntu for OS.
Media will be streamed from a WHS server (Windows Home Server).

I have been looking on a Zotac ION-ITX-A motherboard but i don't know if mythbuntu
is able to use hardware decoding on MKV files.

So i hope that someone can help me before i buy the Hardware.

/Jonte

---

### Post by ian dobson on 2009-06-04
Hi,

My frontend MythTV system boots from a 8Gb CF Card plugged into a normal SATA plug using a CF-SATA adapter. I've been running it like this for about 8months now and haven't had any problems.

Before this I ran the frontend on a IDE flash card for about 1 year also without any problems. I changed over as I wanted to stop using the IDE interface.

A small pic here:-
[http://home.teleport.ch/idobson/computers/img/CF-SATA.jpg](http://home.teleport.ch/idobson/computers/img/CF-SATA.jpg)

Sorry but I don't know about decoding MKV.

Regards
Ian Dobson

---

### Post by managementboy on 2009-06-04
> **Jonte76 said:**
> 

I have been looking on a Zotac ION-ITX-A motherboard but i don't know if mythbuntu
is able to use hardware decoding on MKV files.


I guess you mean if the Nvidia onboard can handle H.264? Check out [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html) for packages of MythTV 0.21 that can handle VDPAU or use the trunk builds from the weekly builds repo.

more on compatibility of Cards with VDPAU at [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by iponeverything on 2009-06-04
Micro drive should work fine.

CF is easily corrupted by high I/O.

One of our boxes runs from CF and I have restore the image every couple of months.

---

### Post by Jonte76 on 2009-06-04
> **managementboy said:**
> I guess you mean if the Nvidia onboard can handle H.264? Check out [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html) for packages of MythTV 0.21 that can handle VDPAU or use the trunk builds from the weekly builds repo.

more on compatibility of Cards with VDPAU at [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

Great!

The onboard Nvidia is a 9400M and should work with VDPAU.

---

### Post by Jonte76 on 2009-06-04
> **ian dobson said:**
> Hi,

My frontend MythTV system boots from a 8Gb CF Card plugged into a normal SATA plug using a CF-SATA adapter. I've been running it like this for about 8months now and haven't had any problems.

Before this I ran the frontend on a IDE flash card for about 1 year also without any problems. I changed over as I wanted to stop using the IDE interface.

A small pic here:-
[http://home.teleport.ch/idobson/computers/img/CF-SATA.jpg](http://home.teleport.ch/idobson/computers/img/CF-SATA.jpg)

Sorry but I don't know about decoding MKV.

Regards
Ian Dobson

Well i just have to look at eBay for a CF-SATA :p

How big/small CF do you recommend?
(I got one 2.5Gb Microdrive over from another project, is it to small?)

---

### Post by Jonte76 on 2009-06-04
> **iponeverything said:**
> Micro drive should work fine.

CF is easily corrupted by high I/O.

One of our boxes runs from CF and I have restore the image every couple of months.

Microdrive it is then!

Is 2.5GB to small?

---

### Post by ian dobson on 2009-06-04
Hi, 

My frontend uses about 2Gb so 2.5Gb is just enough.

If you use a CF card make sure you get an x300 card. The x133 card in the picture worked for me but it was abit slow. I use a second card (16Gb x133) for mytharchive temporary files had have never seen any corruption.

Maybe mount the card as ext2 the options noatime.

Regards
Ian Dobson

---

### Post by Jonte76 on 2009-06-04
> **ian dobson said:**
> Hi, 

My frontend uses about 2Gb so 2.5Gb is just enough.

If you use a CF card make sure you get an x300 card. The x133 card in the picture worked for me but it was abit slow. I use a second card (16Gb x133) for mytharchive temporary files had have never seen any corruption.

Maybe mount the card as ext2 the options noatime.

Regards
Ian Dobson

OK!

I have found a Microdrive that is 8GB :p will go with that.

Seagate ST1.2 8GB

**General Features: **
8 GB capacity 
Type II CF+ interface 
3600 RPM speed 
2 MB buffer 
33.3 MB/s data transfer rate 
8.3 ms average latency 

**Power Specifications:** 
+5V (3.3v, up to 350 mA)

---

### Post by iponeverything on 2009-06-04
> **ian dobson said:**
> Hi, 

My frontend uses about 2Gb so 2.5Gb is just enough.

If you use a CF card make sure you get an x300 card. The x133 card in the picture worked for me but it was abit slow. I use a second card (16Gb x133) for mytharchive temporary files had have never seen any corruption.

Maybe mount the card as ext2 the options noatime.

Regards
Ian Dobson

Thanks for the tip, I'll try it.

---

### Post by larsolav on 2009-06-05
Hi Jonte,
Let us know how that motherboard works out. I am also curious to know what other components you are going to use (including the enclosure etc). I am thinking about building a frontend for my bedroom and this nifty card seems like the perfect solution!

---

### Post by ian dobson on 2009-06-06
Hi,

For all you out there with worries about corruption, Ive just ran small test on my CF card and haven't been able to corrupt the file system. The test consisted of:-

1) Copying 4Gb data over a Gb lan to the CF card and at the same time.
2) Transcode a 4Gb MPEG2 file to a 2Gb DVD iso using the CF as temp/output directory for mytharchive.
3) When either of the processes are finished delete the files created and repeat.

I've run this for almost 12hours and see no corruption in the FS using fsck. All I see in fsck is quite abit of fragmentation (4.2% nicht zusammenhängend dateien).

Regards
Ian Dobson

---

### Post by roundhay on 2009-10-26
I have been trying to get Ubuntu server and Mythbuntu to boot from a Microdrive but have been unsuccessful. I have posted in the hardware forum but not had a reply and have come across this thread. My post in the hardware forum is

[http://ubuntuforums.org/showthread.php?t=1299706]("http://ubuntuforums.org/showthread.php?t=1299706") 

I have just reinstalled mythbuntu onto one of the drives and the boot process has gone past the grub stage and is now stuck at

[HTML]Boot from (hd0,0) ext3[/HTML]

Could the problem but that the drives are just to slow? 

Here is the general spec for the drives
[http://www.hitachigst.com/hdd/support/micro/micro3k4.htm]("http://www.hitachigst.com/hdd/support/micro/micro3k4.htm")

---

### Post by dacodo on 2009-10-27
I'm running my system off a 8GB SSD that I pulled out of my netbook. Stuck it in a USB adapter and it's working great. I also ran an on a SDHC for a while. Seemed to also run fine. 

This were OS only of course. Using an IDE drive for recordings.

---

### Post by roundhay on 2009-10-28
I timed the boot from the 4GB Microdrive and it took 90 minutes to get to the Mythbuntu desk top! This is obviuopsly took long.

Is this down to the Microdrive or could it be the CF to IDE adapter?

---

### Post by ian dobson on 2009-10-28
Hi,

Thats far too long, I'd imagin it should boot in less than 1 minute (My system boots from a CF card in about 45 seconds from Grub to Mythfrontend).

Do you see anything strange in your syslog?

Regards
Ian Dobson

---

### Post by roundhay on 2009-10-28
I've never had to use /check a syslog before, where is this located and what should I be looking for?

---

### Post by ian dobson on 2009-10-29
Hi,

Under linux most log files are in /var/log or subdirectories under /var/log.

The interesting log file would be kern.log or syslog. Just open either of these files with an editor that you know and look for any errors about sda or file system problems.

Also mybe go to the terminal prompt and do a 
hdparm -t /dev/sda

This will perform a read test of the drive and report how quickly data can be read from the drive cache.

If you can try going into the BIOS and changing the port mode for the port that the Microdrive is using (UDMA mode/AHCI). It could be that the CF adapter reports a higher transfer mode than the Microdrive can support.

Regards
Ian Dobson

---

