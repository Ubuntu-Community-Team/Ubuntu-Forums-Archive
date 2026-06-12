---
title: "Recommend me a DVD ripper and a CD ripper"
date: 2009-12-25
forum: Multimedia Software
---

### Post by niw_uk1964 on 2009-12-25
As the title says. Something akin to Exact Audio Copy for CDs and DVD Shrink for DVDs would be good :-)

In edition to this I'd like something to encode CD's to mp3.

This is on Karmic with Gnome.

TIA.

---

### Post by lisati on 2009-12-25
For "shrinking" a DVD from 8.5 to 4.7 Gb there's DVD95 Converter. 
For ripping DVDs there's DVD rip

If you're using 9.10 check out the Software Center. on 9.04 and older, check out the Add/Remove probrams option

---

### Post by HappyFeet on 2009-12-25
RipperX is good for ripping cd's. For dvd's, there's acidrip, dvd::rip.

---

### Post by cascade9 on 2009-12-25
Rubyripper is the closest thing to EAC that I've found in linux.

---

### Post by davec64 on 2009-12-25
I use K9Copy for DVD ripping, works well for me!

---

### Post by josephpmh on 2009-12-25
I love the dd command

```
dd if=dev/cdrom of=/media/outputfile.iso
```This elegant command creates an iso of your cd.  You can than mount the iso file as a drive:

```
sudo mkdir /media/ouputmount
sudo mount /media/outputfule.iso /media/ouputmount -o loop
```I agree with lisati:  dvdrip worx just fine.  I also like soundkonverter for ripping cd's.

---

### Post by niw_uk1964 on 2009-12-25
Thanks for the recommendations peeps.

Now on a related line, can you recommend a media player that will stream (play) content across my network from a Windows server?

Rythmbox and Banshee don't seem to do it.

---

### Post by cascade9 on 2009-12-26
I'm not sure about Banshee, but I thought that Rhythmbox does stream to windows. 

You could try VLC.  

> **josephpmh said:**
> I love the dd command

```
dd if=dev/cdrom of=/media/outputfile.iso
```This elegant command creates an iso of your cd.  You can than mount the iso file as a drive:

```
sudo mkdir /media/ouputmount
sudo mount /media/outputfule.iso /media/ouputmount -o loop
```

I dont know why anyone would make a .iso of a CD these days, it would make far more sense to do a lossless (.flac or .wv) copy.....smaller, easier to handle, built in error checking.

---

### Post by bcn17 on 2009-12-26
For CD ripping-
the package 'abcde' works great! You can customize your ripping exactly to your liking including file trees, making multiple copies in different formats including flac, ogg, mp3, bitrate, etc. Just edit the .abcde.conf file to your liking. Google "andrews corner abcde" and you will find a nice example of a .abcde.conf file.

---

