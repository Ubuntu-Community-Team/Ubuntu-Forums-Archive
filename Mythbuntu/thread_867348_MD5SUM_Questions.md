---
title: "MD5SUM Questions"
date: 2008-07-22
forum: Mythbuntu
---

### Post by Ronno6 on 2008-07-22
I am trying to set up a machine with Mythbuntu 8.04.1  The computer is an Asus M2NPV-VM motherboard, AMD Athlon X2 4600 dual core, 2gigs of ram, using the MB video: nVidea 6300, no tuner card yet, but Hauppauge 150 on the way. IDE DVD recorder, SATA2 hard drives. 
Problem is this: I cannot download the Mythbuntu for tha AMD64 build and burn to CD or DVD and have checksums that match the ones (there are 2 different ones) from the web site. 
The downloaded MD5SUM, at [http://mythbuntu.org/download/?file=mythbuntu-8.04.1-desktop-amd64.iso.md5sum](http://mythbuntu.org/download/?file=mythbuntu-8.04.1-desktop-amd64.iso.md5sum)
differs from the downloaded Mythbuntu file. That sum can be found at : [http://us-ut.cdimages.mythbuntu.org/mythbuntu-8.04.1-desktop-amd64.iso.md5sum](http://us-ut.cdimages.mythbuntu.org/mythbuntu-8.04.1-desktop-amd64.iso.md5sum) which  I gather is from a mirror site. 
I have tried to burn the downloaded .iso to CD and DVD, using Nero, DVDFabPlatinum, and IsoBurn. I get coasters every time. Media is Verbatim DVD, Maxell CD. Different speeds, etc. Why are there different checksums? Ho do I get this to work? Thanks.

---

### Post by tgm4883 on 2008-07-22
I'm not entirely sure I follow.  This is the correct md5sum for the 8.04.1 desktop amd64 iso

```
612b093448908b813c09503866090004  mythbuntu-8.04.1-desktop-amd64.iso
```

are you saying that when you run this
```
md5sum -c mythbuntu-8.04.1-desktop-amd64.iso.md5sum
```

that it is coming back as failed?

Also, I just checked every mirror and they all have the above md5sum.  Are you seeing a different md5sum somewhere?  Could you link me to it?

---

### Post by nickrout on 2008-07-23
If you have an iso that is borked the best way to fix it is to get a torrent of the download and use a bittorrent client to download the file. It will detect that you have, say, 98% of the file (with the damage in the remaining 2% chunk). It will then download just the 2% you need.

---

### Post by Ronno6 on 2008-07-23
What I am saying is that the sums from the 2 links are not the same. Every time I've downloaded the "Direct Desktop Download" for the AMD64 build, the sum matches the one that ends in "004".The address for this sum indicates that it comes from a mirror site (I think), and does NOT require a program to open. It just appears on a white screen without downloading.
 However, when I obtain the MD5SUM by using "Direct Desktop md5sum Download" (from the Mythbuntu website) , the sum is different.That sum, which requires  winMD5SUM to open the dowwnloaded file, ends in "13c0"  I have never been able to download a version of the Mythbuntu installation program that has the checksum contained in the second link. AS i do not understand much of this, I wonder if the Download of the Mythbuntu AMD64 program is not good? 
Has anyone been able to download and install Mythbuntu 8.04.1 for AMD64? 
I have downloaded and successfully burned .iso files for the Alternate install and i386 versions of the program. The only one I can't seem to get is the one I really NEED !!

What happens when I attempt to rune the Live CD is that it loads to the end of the progress bar, the screen goes black, then I get a mouse pointer (arrow) that tesponds to mouse movement, but, nothing further happens. The load stops there. If i attempt to "Install" the same thing happens except that I get an "X" mouse pointer rather than the arrow. That's it.
Running the "Check CD for Errors" just starts the progress bar, then stops. I've left it that way for an hour, being patient, but nothing further happens. Is the burn suspect?

I am not familiar with bit torrents as of yet. Maybe time to learn.

---

### Post by tgm4883 on 2008-07-23
I still can't find the md5sum that ends in 13c0.  The correct one ends in 004.  I've clicked the link that you posted and it takes me to the correct md5sum.  If you are still clicking on the direct download md5sum link and it gives you the other md5sum, please right click on the background, then view page source, then post the page source here.  It should look something like this.

```
<html>
<head>
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-2602400-1";
urchinTracker();
location.href="http://cdimages.mythbuntu.org/mythbuntu-8.04.1-desktop-amd64.iso.md5sum";
</script>
</head>
<body>
</body>
</html>

```

Some mirrors may make you download the file, in which case just upload it as an attachment here.

---

### Post by Ronno6 on 2008-07-23
Here you go:

<html>
<head>
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-2602400-1";
urchinTracker();
location.href="http://osuosl.cdimages.mythbuntu.org/mythbuntu-8.04.1-desktop-amd64.iso.md5sum";
</script>
</head>
<body>
</body>
</html>

That address gives a download box. Opening the file gives the folowing checksum: 1b3c6ad89d26eea67f940478c17a13c0

---

### Post by tgm4883 on 2008-07-23
> **Ronno6 said:**
> Here you go:

<html>
<head>
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-2602400-1";
urchinTracker();
location.href="http://osuosl.cdimages.mythbuntu.org/mythbuntu-8.04.1-desktop-amd64.iso.md5sum";
</script>
</head>
<body>
</body>
</html>

That address gives a download box. Opening the file gives the folowing checksum: 1b3c6ad89d26eea67f940478c17a13c0

says 612b093448908b813c09503866090004  mythbuntu-8.04.1-desktop-amd64.iso for me.  

Are you sure you don't already have a mythbuntu-8.04.1-desktop-amd64.iso.md5sum file in your download directory and the one you just downloaded is now mythbuntu-8.04.1-desktop-amd64.iso.md5sum(1)  ?

---

### Post by foxbuntu on 2008-07-23
I too can confirm the md5sum is correct. This would tell me it is localized to your machine. Try downloading to a seperate location to ensure there are no odities from overwriting files and such.

---

### Post by Ronno6 on 2008-07-23
This all may be just me spinning my wheels. The downloaded file has the correct checksum (ending in 004).
The real problem is , I cannot obtain either of the sums I've seen as being the sum on my burned disk. I have, however, checked the disk on my machine with Ubuntu installed. It indicates all files as "OK". But, I cannot find a way to obtain the actual checksum of the disk itself. 
I have started a new thread pertaining to my inability to install Mythbuntu AMD64. We'll see what that brings. 
In the mean time, is there a way to obtain the actual MD5SUM of my burned CD?? I've tried winMD5SUM, but Windows keeps saying "Invalid CD Detected"

---

### Post by tgm4883 on 2008-07-23
See other thread here 
[http://ubuntuforums.org/showthread.php?t=867981](http://ubuntuforums.org/showthread.php?t=867981)

---

