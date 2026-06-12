---
title: "dvdFab not recognizing DVD"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Automat2 on 2011-05-02
Since I upgraded to Ubuntu Natty, dvdFab has not recognized any DVD I insert into the drive.

The program loads through Wine with no problems, and the disk is mounted by Ubuntu, but no dvd drives are recognized by dvdFab.

I guess it will be a conflicting setting or something, but I would like to know if there is a solution, because my DVD player is knackered and only accepts DVD5's -not double layers any longer.

---

### Post by HolgerB on 2011-05-02
> **Automat2 said:**
> Since I upgraded to Ubuntu Natty, dvdFab has not recognized any DVD I insert into the drive.

The program loads through Wine with no problems, and the disk is mounted by Ubuntu, but no dvd drives are recognized by dvdFab.

I guess it will be a conflicting setting or something, but I would like to know if there is a solution, because my DVD player is knackered and only accepts DVD5's -not double layers any longer.

Did you checkout the WINE AppDB on dvdfab ?

I guess any Windows-based decrypting program might have issues under WINE because they access the DVD ROM at a low hardware level which WINE might not emulate.

---

### Post by ghostborg on 2011-05-02
I also could not get it working so I just ended up running Windows 7 in Virtualbox using shared folders.

Remember to checkbox Passthrough under Storage=>Hostdrive this allows the guest OS to pass ATAPI commands directly to the host-drive.

I then burn the disc using K3b.

---

### Post by Automat2 on 2011-05-03
> **ghostborg said:**
> I also could not get it working so I just ended up running Windows 7 in Virtualbox using shared folders.

Remember to checkbox Passthrough under Storage=>Hostdrive this allows the guest OS to pass ATAPI commands directly to the host-drive.

I then burn the disc using K3b.

I only have a native Ubuntu, and only use Wine to emulate this Windows software.

Thank you, anyway.

---

### Post by Automat2 on 2011-05-03
> **HolgerB said:**
> Did you checkout the WINE AppDB on dvdfab ?

I guess any Windows-based decrypting program might have issues under WINE because they access the DVD ROM at a low hardware level which WINE might not emulate.

Before I upgraded to Natty, DvdFab worked pretty well on Maverick. I has only been over the last two or three days, since the upgrade, that dvdFab has failed.

However, how do I checkout Wine AppDB on dvdfab? I have gone through the settings menu but I haven't found it.

---

### Post by BULLIT22 on 2011-05-03
Hey, 

I had this problem as well. Seems Wine is not seeing the D: drive. Here's a link to my post that may help you out. This fixed my issue with DVDfab not seeing DVD's that were inserted.

[http://ubuntuforums.org/showthread.php?t=1744494](http://ubuntuforums.org/showthread.php?t=1744494)

Hope that helps.

---

### Post by Automat2 on 2011-05-03
> **BULLIT22 said:**
> Hey, 

I had this problem as well. Seems Wine is not seeing the D: drive. Here's a link to my post that may help you out. This fixed my issue with DVDfab not seeing DVD's that were inserted.

[http://ubuntuforums.org/showthread.php?t=1744494](http://ubuntuforums.org/showthread.php?t=1744494)

Hope that helps.


Yes, it has helped. I had to do it twice, one for each drive I've got, but now it works fine.

Thanks a lot!

---

### Post by BULLIT22 on 2011-05-03
Nice, Glad it worked for you.

---

### Post by Automat2 on 2011-05-04
Now, the problem is that DVDfab does not work under Wine for Natty in the same way it used to do for Maverick.

---

### Post by BULLIT22 on 2011-05-04
Actually I'm not quite sure what the issue is. I have two PC's set up both with Maverick. One install saw the DVD's in DVDFab just fine and the other is the one I had issues with. Both PC's were set up the same software-wise.

---

