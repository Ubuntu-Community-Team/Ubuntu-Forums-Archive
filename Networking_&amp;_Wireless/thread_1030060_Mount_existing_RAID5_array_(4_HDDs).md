---
title: "Mount existing RAID5 array (4 HDDs)"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by adlabens on 2009-01-04
I built a RAID5 array in OpenSuSE 11.0, then realized that I didn't want to use OpenSuSE but instead prefer the Ubuntu distros.  The OS is on it's own HDD, and the RAID5 array is 4 separate drives.  I can simply swap out the OS HDD and change the operating system.  I have OpenSuSE on one HDD, and Ubuntu 8.10 on another.  I'm trying to mount the existing RAID5 array in Ubuntu Server 8.10 so that I can get access to my data without having to restore nearly 300 gB from our two desktops (thankfully, I've not yet erased them!).

I've tried using Webmin, but I'm getting error messages with everything that I try.  My OS drive is /dev/sda, and my four RAIDed drives are sdb, sdc, sdd, & sde.  My mount point is /NW-DATA.  I'm thinking it should be an easy task to simply mount the array, but it's turning into far too many hours of hacking.  This is our home server, so I'm not desperate for a business or a consulting client (I don't consult, just do this for myself).  But, I'm wanting to get completely away from Microsoft, and this is the first step - migrating our data off the WinXP Pro boxes.

Any help will be GREATLY appreciated.

Thanks,
David
San Antonio, TX

PS, I've re-posted this in the Server thread, hopefully to get a response.  You can find it [here]("http://ubuntuforums.org/showthread.php?p=6492459#post6492459").

---

