---
title: "GUI for burning Bluray data discs"
date: 2012-11-30
forum: Multimedia Software
---

### Post by Longboringrant on 2012-11-30
Does anyone know a good GUI software for burning Bluray data discs in Linux? I don't need to burn movies or anything like that, just backups/archives of data. I'm only interested in Bluray for the 25GB capacity.

I've done plenty of googling that points to Nero for Linux, but apparently it is now abandonware and is no longer being sold :(

I'd jump in and install K3B or something and try to find out for myself, but I don't yet have a Bluray burner or anything. I'll only buy one if this will be an easy, viable backup solution (on top of Back In Time to a separate hard drive)--if not I'll stick to dual layer DVDs.

Thanks!

---

### Post by bandelguy on 2012-12-02
> **Longboringrant said:**
> Does anyone know a good GUI software for burning Bluray data discs in Linux? I don't need to burn movies or anything like that, just backups/archives of data. I'm only interested in Bluray for the 25GB capacity.

I've done plenty of googling that points to Nero for Linux, but apparently it is now abandonware and is no longer being sold :(

I'd jump in and install K3B or something and try to find out for myself, but I don't yet have a Bluray burner or anything. I'll only buy one if this will be an easy, viable backup solution (on top of Back In Time to a separate hard drive)--if not I'll stick to dual layer DVDs.

Thanks!

i don't have a Bd drive, but k3b & nero4 linux have bluray support. Brasero doesn't even support udf format. Else try using Imgburn with WINE.

---

### Post by MakOwner on 2012-12-31
> **bandelguy said:**
> i don't have a Bd drive, but k3b & nero4 linux have bluray support. Brasero doesn't even support udf format. Else try using Imgburn with WINE.

I have been burning BD data discs for some data backups.
I have audio 4 hour voice quality recordings that I produce on week days in raw format, I convert them to mp3 and tag them, and then every other quarter or so, I'll burn them off onto BD discs.  At about 250-280M per file, I usually get a quarter onto a single disk.  Takes 4 BD discs to a quarter's worth of the raw files.  

Good luck with buring BD discs.  It's always a crapshoot if you ask me.
I installed the real cdrtools (some sort of holy war about cdrtools is going on - just mentioning this will probably bring on a ... discussion).  
It will handle creation of the images and burn the images to discs.
If you are looking for a GUI ...  Brasero recognizes the format in the frontend, and with cdrtools behind it should work, but it's been my experience it just shits itself.  I wait long enough between sessions of doing this that I have to relearn every time.  Installing cdrtools over the broken wodim stuff isn't a picnic either.

If you find a GUI that works reliably over cdrtools, PLEASE post here!

Edit:  
This is not my articel, but this is a good general guideline to follow - this seems to be where I end up every time I relearn this...

[http://www.troubleshooters.com/linux/blu-ray-backup.htm](http://www.troubleshooters.com/linux/blu-ray-backup.htm)

---

### Post by chupnik on 2013-05-24
Try [Silicon Empire]("http://getsilicon.org") - GPL multifunctional tool set for burning cd/dvd/blu-ray disks.

---

### Post by fedetxf on 2013-08-03
This way works. Already burned 3 out of 3 with no issues.
[https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning](https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning)

---

