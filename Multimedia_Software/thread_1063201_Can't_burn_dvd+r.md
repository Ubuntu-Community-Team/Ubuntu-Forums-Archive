---
title: "Can't burn dvd+r"
date: 2009-02-07
forum: Multimedia Software
---

### Post by PapaCookie on 2009-02-07
Anyone have any ideas why I wouldn't be able to burn to dvd+r media?  dvd-r works fine.  I have a Toshiba SD-R5272 drive.

[This technical note]("http://sdd.toshiba.com/techdocs/SD-R5272TechnicalNotes-RevB.pdf") from Toshiba's website states that it does support writing to DVD+R media.

Here's what dvd+rw-mediainfo reports:
> INQUIRY:                [TOSHIBA ][ODD-DVD SD-R5272][1031]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Bh, DVD+R
 Media ID:              CMC MAG/M01
GET [CURRENT] PERFORMANCE:
 Write Performance:     2.4x1385=3324KB/s@[0 -> 2295103]
 Speed Descriptor#0:    00/16777215 R@1.0x1385=1385KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#1:    00/16777215 R@1.0x1385=1385KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#2:    00/16777215 R@1.0x1385=1385KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           complete
 Number of Sessions:    1
 State of Last Session: complete
 Number of Tracks:      1
READ TRACK INFORMATION[#1]:
 Track State:           invisible
 Track Start Address:   0*2KB
 Free Blocks:           0*2KB
 Track Size:            0*2KB
READ CAPACITY:          0*2048=0

Here's what genisoimage returns:

> Executing 'genisoimage -dvd-video dvd/ | builtin_dd of=/dev/scd1 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.22% done, estimate finish Sat Feb  7 16:13:05 2009
  0.44% done, estimate finish Sat Feb  7 16:13:05 2009
  0.66% done, estimate finish Sat Feb  7 16:15:36 2009
/dev/scd1: "Current Write Speed" is 2.5x1352KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type

I have also tried burning with K3b.  When I click *Burn*, the burn dialog has the *Burn* button grayed out, and the *Burn Medium* selector says "Please insert an empty DVD+-R(W) medium...

---

### Post by mc4man on 2009-02-07
You may want to try different +r media. CMC media seems to be an issue with some drives in linux and is generally viewed as low to middle end quality wise.

Blank dvd media is produced by just a handful of manufactorers and rebranded. The  major producers, worst to best are Cmc, prodisc or ritek, mcc (verbatium), and taiyo yuden.
At this point the 'name' brands aren't using taiyo yuden due to price pressures so you'll either generally get cmc or ritek  (not really up on this anymore, cdfreaks is a good site for info

For retail purchases I'd probably go with verbatium, online from a trusted site, taiyo yuden is still superior

---

### Post by PapaCookie on 2009-02-08
That sucks that I have inferior media.  I will have to try verbatim.

Here's some more info in case the problem is not the media.  When I try to write using Nautilus CD/DVD Creator, I get the following message:

> Please put a disc, with at least 4.3 GiB free, into the drive.  The following disc types are supported:
DVD-R, DVD-RW

Since it says only DVD-R, DVD-RW are supported, I'm wondering if I'm missing some library.  Any thoughts on this?

---

### Post by mc4man on 2009-02-08
Firmware is updated on dvd drives to add new media id's, so your drive may benefit in that regard. I don't think that would prevent a burn, more often could effect the burn quality, and allowed speeds.

here's the page on your drive - supports dvd+r

[http://reviews.cnet.com/dvd-drives/toshiba-sd-r5272/4507-3212_7-30907616.html?tag=mncol;psum](http://reviews.cnet.com/dvd-drives/toshiba-sd-r5272/4507-3212_7-30907616.html?tag=mncol;psum)

If you run ```
sudo lshw -c disk
```
you'll usually see the firmware ver. displayed on the line 

version: xxxx..

I'm not any use on linux burning apps cause I don't use them (Imgburn in wine) and the few times I have, they've worked ok. (though they're like driving in the fog.

They can be a bit flaky, the error messages/logs are either of the generic, nonspecific type like above or repetitive and obscure.

Maybe search getdeb for the latest brasero and try (make sure it's for your release (hardy or intrepid

[http://www.getdeb.net/](http://www.getdeb.net/)

Edit; many manufacturer's aren't so hot at releasing new firmware updates, your official latest is Version 1031 (from 2004

It seems to be an 8x burner, I'd burn at 4x

These would be excellent media for your drive if retail stuff doesn't work (most retail is 16x, may or may not be a concern 

[http://www.supermediastore.com/verbatim-shiny-silver-8x-dvd-r-plus-47gb-media-50.html](http://www.supermediastore.com/verbatim-shiny-silver-8x-dvd-r-plus-47gb-media-50.html)

[http://www.supermediastore.com/taiyo-yuden-8x-dvd-plus-r-4-7gb-silver-inkjet-50-disc-spindle.html](http://www.supermediastore.com/taiyo-yuden-8x-dvd-plus-r-4-7gb-silver-inkjet-50-disc-spindle.html)

---

### Post by oblidor on 2009-02-08
> **PapaCookie said:**
> Anyone have any ideas why I wouldn't be able to burn to dvd+r media?  dvd-r works fine.  I have a Toshiba SD-R5272 drive.


Update the firmware of the dvd-recorder. I had similar problem, but a firmware upgrade fixed it as the recorded didn't have right info for the new discs.

Check Toshibas support pages for firmware upgrade.

HTH

---

### Post by oblidor on 2009-02-08
> **mc4man said:**
> Firmware is updated on dvd drives to add new media id's, so your drive may benefit in that regard. I don't think that would prevent a burn, more often could effect the burn quality, and allowed speeds.


I can confirm that it *will* prevent a burn. I scratched my head for some days a couple year ago as non of the new DVD marks I had bought would work. The error message was not clear, but through some Googling and luck I figured out that firmware upgrade was needed. The firware was upgraded from version C to Y so quite a big upgrade, but still it solved the problem.

---

### Post by zipperback on 2009-02-08
Try using a different brand of DVD+R media.

I use primarily Sony & Memorex and I've been very happy with them.

- zipperback
:popcorn:

---

### Post by PapaCookie on 2009-02-08
Thanks for all the help guys.  The Ubuntu community never lets me down.  

> If you run
Code:

sudo lshw -c disk

you'll usually see the firmware ver. displayed on the line

version: xxxx..

This command didn't work for me verbatim.  I had to change it to

```
sudo lshw -C disk
```

Note the capitol *C*.  This returned the following for my drive:

```
  *-cdrom:1
       description: DVD writer
       product: ODD-DVD SD-R5272
       vendor: TOSHIBA
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1031
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```

> your official latest is Version 1031 (from 2004

I guess I'm up to date already :(

> I use primarily Sony & Memorex and I've been very happy with them.

The DVD+R media that I've been trying is Memorex. :(  This is the only media that I've ever had trouble with.  I know for a fact that I have used Maxell DVD-R and Dynex DVD-R with no problems.  I'm not sure, but this might be the first time I've tried any DVD+R media...

It might be time for me to upgrade my burner.  I'd like to get a dual-layer burner anyway...

---

### Post by ttguy on 2009-12-29
> **PapaCookie said:**
> 
This returned the following for my drive:

```
  *-cdrom:1
       description: DVD writer
       product: ODD-DVD SD-R5272
       vendor: TOSHIBA
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1031
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```I guess I'm up to date already :(

It might be time for me to upgrade my burner.  I'd like to get a dual-layer burner anyway...

I have been getting the same errors as PapaCookie when using DVD+R.
(see attachment - brasero says "It is not possible to write with the current set of plugins."

I normally use DVD-R but I have a new portable DVD player that does not seem to like DVD-R so much so I want to try some DVD+R disks.

I know that back under Windows 2000 and using Nero my drive could burn DVD+R.

But now it errors.

sudo lshw -c disk reports

```


  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-4160B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A301
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
```Which - like PapaCookie's output -  does not mention dvd+r in the capabilities section. Does this mean that according to linux my drive does not have dvd+r capabilities?
[http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=11079](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=11079) says the drive does have dvd+r and as I say - I have burnt a dvd+r disk under Windows 2K.

So it would appear to me that linux is missing something here. It appears that linux can not make use of the dvd+r capabilities of some drives that have the capability under Windows! :(

"It is not possible to write with the current set of plugins"  - this sort of implies that I could get it to work with different plugins right?

---

