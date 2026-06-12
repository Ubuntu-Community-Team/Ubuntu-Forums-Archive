---
title: "Need help ripping dvd to mpeg files"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by hurtstotalktoyou on 2008-02-24
Hi, all.

I've been using Ubuntu Studio 7.10 Gutsy Gibbon for a few months, now, but I've never tried anything like this:  I need to rip video from a store-bought DVD and re-author it into a custom bitrate, menu-free DVD.  Unfortunately, I can't even get past the first step in this process:  ripping the VOB data to the hard disk.

First I tried [k9copy](http://en.wikipedia.org/wiki/K9copy).  It seemed to install okay from Synaptic Package Manager, and it starts up fine, too.  However, as soon as I try to "open" anything, the program crashes with the following error message:  "The application k9copy (k9copy) crashed and caused the signal 11 (SIGSEGV)."  After unsuccessfully screwing around with the program settings, I gave up and moved on.

Next I tried dvd::rip.  This was a confusing program, and I still don't know exactly what I'm supposed to do, assuming I can get it to work at all.  The project "storage path"s were all set to /media/..., and thus had to be changed to /home/[user]/... before the project could be created.  I find that very strange, but whatever.  When I try to read the DVD table of contents, though, it gives me the following error:  *Job 'Read TOC (lsdvd)' failed with error message: Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.*  In other words, the DVD doesn't seem to be detected by the program.  So, as with k9copy, I gave up and moved on.

Next I tried [thoggen](http://en.wikipedia.org/wiki/Thoggen).  Unfortunately, when I start it up, I get the following error:  *Failed to retrieve DVD title details for some reason.  Maybe you do not have libdvdcss2 installed?*  So, I looked for libdvdcss2 in Synaptic Package Manager, but found nothing.  I'm wary to install anything that isn't supported by Synaptic, so, instead of searching around Google, I just moved on.

Although I'd like to use dedicated Linux software, I was at a loss, so the next program I tried was DVD Decrypter in Wine.  It installed properly, as far as I can tell, and seems to load just fine, but under "Source" it tells me that there are "No Devices Detected!"  I have no idea how to get it to recognize my DVD drives under Wine.

So there it is:  four swings; four misses.  Any suggestions would be much appreciated.

Thanks in advance!
--Ben

P.S.  It may also be relevant to note that I can't even get the DVD to play, either in totem or vlc, despite having installed ubuntu-restricted-extras.  What's with that?

---

### Post by VMan on 2008-02-24
It sounds like the DVD may be bad.  I got similar messages with a DVD that turned out to be related to it being dirty.  After cleaning it, it worked just fine.  As to what software you need, I'm at a loss to help you there.  You have tried all of the solutions I use.  I use K9Copy for some stuff, DVD::RIP for others, and avidemux (spelling?) for others.  The combination of these three has met all my needs so far.  I have a bunch of video tapes from vacations, school plays, and etc. that I need to to transfer over, but haven't gotten around to that yet.  I'm learning as I go, so hopefully there is someone just a bit more experienced than me out there that can help you better than I.:confused:

---

### Post by suibhne on 2008-02-25
the links here will help - try the bottom of the page

as for thoggen, i tested it out a while ago and it was far to slow for me anyway.


[https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs](https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs)

(BTW libdecss is fine)

---

### Post by papafreebird on 2008-02-25
I use [DVDFabhddecrypter](http://www.dvdfab.com/download/DVDFabHDDecrypter4065Beta_avangate-689.exe) in wine to rip my dvds to my hard drive so that I can back them up to a blank dvd (I have kids that scratch the heck out of the dvd's and I don't want to replace the originals).  The original dvddecrypter dosen;t work on newer dvd releases because it's development stoped a long time ago.  You will have to go into wine configuration and make sure that your dvd drive is detected.  Click on the drives tab, hit the show advanced button, make sure your DVD drive is listed as Type CD-ROM. If not change it. Click apply .  You should now be able to use [DVDFabhddecrypter](http://www.dvdfab.com/download/DVDFabHDDecrypter4065Beta_avangate-689.exe)

---

