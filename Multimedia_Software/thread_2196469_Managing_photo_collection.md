---
title: "Managing photo collection"
date: 2013-12-29
forum: Multimedia Software
---

### Post by foxy123 on 2013-12-29
I wonder how people manage their extensive photo collections. With the emergence of all mobile devices and digital cameras a lot of people including myself amassed enormous photo (and video) collections. I am interested in what other people use to manage their photos, how they keep them and so on. I have been using Shotwell for some time and the programme creates a sub-folder for each day. As a result I have ended up with a 3-level structure year/month/day, which sometimes is a bit difficult to navigate. I keep all the photos on my NAS. I use Ubuntu One to transfer files from my mobile phone and a digital camera to my laptop and then import them to the NAS using Shotwell. One of the problems is that Shotwell works very slow with network drives. Also I have now a lot of duplicates due to re-import and so one. The issue is that I tagged my files on the NAS and Shotwell treats the same tagged and untagged files as different ones so it is difficult to find duplicates. I was thinking that probably I should keep all photos in one folder and just tag them, but I am not sure. Also I wonder what photo manager I should use for photos located on the network drive and what is the best way to upload them without messing things up.

---

### Post by sudodus on 2013-12-29
I use ***DigiKam*** to manage my photos. I think it is better than Shotwell and F-spot. I keep them in a multimedia partition, that I back up with a synchronizing method (using Unison and an external eSATA drive).

---

### Post by foxy123 on 2013-12-30
> **sudodus said:**
> I use ***DigiKam*** to manage my photos. I think it is better than Shotwell and F-spot. I keep them in a multimedia partition, that I back up with a synchronizing method (using Unison and an external eSATA drive).

Thanks. It takes ages for Digikam to start with the library located on a network drive :(

---

### Post by sudodus on 2013-12-30
Maybe it is slow only the first time, when it is creating metadata (thumbnail pictures etc).

---

### Post by foxy123 on 2013-12-30
> **sudodus said:**
> Maybe it is slow only the first time, when it is creating metadata (thumbnail pictures etc).

No, it is slow every time I launch it. It looks like scanning everything over again every time.

---

### Post by sudodus on 2013-12-30
Well, I use it with local data (the picture files are in a HDD in the local computer). Try another photo manager!

---

### Post by SeijiSensei on 2013-12-31
What kind of network drive?  Samba or NFS?  I suspect you'd see better performance if you use [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). Samba is a kludge to support Windows users.  If you have an all-*nix system, NFS is a much better choice.

If you want to enable Windows users to see the files, run both NFS and Samba on the server, and export the share using the appropriate protocol for the client platform.  My home file server is visible both ways.

---

### Post by Dragonbite on 2013-12-31
I used to have my wife's laptop and my laptop copy pictures imported into a partition on the desktop computer (as well as desktop-imported pictures defaulting to the same location).  Now I have them going to a network hard drive, in part because the desktop partition has run out of space.

Now I have my wife's Windows computer use FreeFileSync to watch and copy any pictures uploaded to her system from her camera.

On Linux we have liked using Shotwell, due to it's visual navigation of albums for different time periods (day, month, year, etc.).  Windows Live Photo on Windows 7 is alright, but not great. I would prefer Shotwell for Windows.

Recently I started uploading pictures to Google+ for sharing and if you let them adjust the size to 1024 or less on the longest side, it doesn't count towards your space quota.  This may be handy, as I have 100 GB of pictures and having shrunken images is better than nothing if something catastrophic were to happen.

---

### Post by foxy123 on 2014-01-01
I'm using NFS. I've got most of my photos for the last couple of years backed up on G+, but still I need to manage my entire library on the network. I'm OK with Shotwell but it's not cut out for managing photos on network drives. I think it's even started somewhere in its wiki. The NAS had it's own web based photo manager but it's not very sophisticated. So I'm still looking for better options.

---

### Post by SeijiSensei on 2014-01-02
On your NFS server, do you include "async" in the list of options for the share?  That can make a substantial difference in terms of performance.  You can lose data if the server goes down during file writing operations, but a decent machine connected to an uninterruptible power supply makes that highly unlikely.

On the client I recommend increasing the values for rsize and wsize by adding them to the defaults in /etc/fstab:

```
server:/share /mount/point nfs defaults,rsize=32768,wsize=32768 0 0
```

---

