---
title: "All of my F-spot images are corrupted"
date: 2013-01-20
forum: Multimedia Software
---

### Post by xeddog on 2013-01-20
I have been using F-spot and Shotwell to archive all of my digital photos for quite some time now.  Over a year for sure.  But all of a sudden all of my F-Spot jpgs are corrupted.  Does anyone know of a good (and free) utility that runs on linux that I can get to attempt to recover them?

Thanks,

Wayne

---

### Post by tgalati4 on 2013-01-20
Are you sure the images are corrupted?  Perhaps it is just the database and thumbnails that are messed up.  Can you navigate though the folders and bring up an image with Gnome image viewer (eog--eye of gnome)?

---

### Post by xeddog on 2013-01-21
When this first started I could still navigate to the folders and open the jpgs with just about any other application so I thought it was F-Spot that was hosed.  Now, nothing I have tried will open them.  Two different image viewers, gimp, libre office draw, phatch, and probably a couple of others.

xeddog

---

### Post by kurja on 2013-01-21
> **xeddog said:**
> When this first started I could still navigate to the folders and open the jpgs with just about any other application so I thought it was F-Spot that was hosed.  Now, nothing I have tried will open them.  Two different image viewers, gimp, libre office draw, phatch, and probably a couple of others.

xeddog

That really badly sounds like a hard drive failure =( You do have backups - I mean, you DO have backups, right?

You might try that hard drive with another computer and see if it's any different, if not, well... There are some means of attempting to recover data, I'll leave that for the more knowledgeable users to talk about... in the meantime, avoid using that drive, and whatever you do, think first. Twice. But if you do have up to date backups, then ofc the solution is obvious.

---

### Post by xeddog on 2013-01-21
I don't think this is a hardware failure but an F-Spot failure because there are jpgs in many other folders on that drive that don't have any problems.  It's just the f-spot folder.  But just in case I am preparing to remove all data from it anyway.  I have all of my images backed up on another drive but the photo manager for the "backup" is Shotwell and not F-Spot.  

This actually started a couple of weeks ago when I was trying to do an import of images from my phone.  Initially I thought it might have been my phone.  When I started F-Spot, selected the import function, pointed to the folder on my phone, and clicked start, F-Sport started importing, but the report when it finished said that about 50 images could not be imported. Tried it again with the same result.  At that time I could open all of the other jpgs wth F-Spot or any other application.  I copied the jpgs off my phone into a new folder and tried importing from there, but F-Spot still had the same result.  Since I thought F-Spot was to blame and possibly corrupted, I did a re-install of F-Spot using synaptic.  That is when things really started to turn to excrement. Since then things went downhill for F-Spot and now it has reached the point where nothing will open any of the jpgs in that folder. It looks like if I want to try and save that folder I need to find a repair utility.
 

xeddog

---

### Post by tgalati4 on 2013-01-21
```
sudo apt-get install testdisk
man photorec
```

This a tool designed just to do that.

I'm thinking that you had a drive crash/failure and it happened in sectors that were located in the F-Spot photo directory.  The data on the rest of the disk is OK, but those sectors are toast.

Did you install smartmontools?  Check the SMART parameters for bad sectors.  Most modern drives will store the last few errors.  They will be quite obvious.

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -a /dev/sdb

```

You have some long evenings ahead of you.

---

### Post by xeddog on 2013-02-02
tgalati4 - I tried the photorec program.  After running for a couple of hours it looks like all it did was put about 600,000 (yup, six hundred thousand) folders/files on the disk but I can't find where it saved even one photo.  I'll keep working on it though.

Thanks,

X

---

