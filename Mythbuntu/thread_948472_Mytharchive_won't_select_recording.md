---
title: "Mytharchive won't select recording"
date: 2008-10-15
forum: Mythbuntu
---

### Post by daengbo on 2008-10-15
I have an installation of Mythbuntu 8.04 x86_64 which I am in love with. I decided to burn some shows to DVD for backup, but when I try to create a DVD, I run into a problem.

I choose to create a DVD, then select the DVD type and everything appears fine. On the next page, I am asked to add files. If I select "Add Video" or "Add file," then I can select files and they appear on the second page when I'm finished browsing, but this doesn't happen with the "Add recording" selections. Although I select episodes, they don't appear on the archive page.

My temp directories are correct and the episodes can be played. Does anyone know what could be wrong?

Thanks

---

### Post by klc5555 on 2008-10-15
> **daengbo said:**
> I have an installation of Mythbuntu 8.04 x86_64 which I am in love with. I decided to burn some shows to DVD for backup, but when I try to create a DVD, I run into a problem.

I choose to create a DVD, then select the DVD type and everything appears fine. On the next page, I am asked to add files. If I select "Add Video" or "Add file," then I can select files and they appear on the second page when I'm finished browsing, but this doesn't happen with the "Add recording" selections. Although I select episodes, they don't appear on the archive page.

My temp directories are correct and the episodes can be played. Does anyone know what could be wrong?

Thanks

Sometimes owner/group/permission problems on the directory/directories you have your recordings in cause odd issues like this with mytharchive. 

Check the directory with ls -l to confirm that the owner and group of the directory with the recordings are both "mythtv" (and not, say, "root") and that the directory has its permissions set to 775 (some people prefer wide open at 777). 

Mytharchive also seems to run better (i.e. gets further before it dies) if the temp working directory is set as a subdirectory under the user's home directory rather than the default suggested path provided during your mytharchive setup.

Make sure also that the .ICEauthority file is deleted from your home directory. (Write yourself a script to do this --it recreates itself every time X starts.) And you should be good for archiving analog recordings (at least). Archiving digital may present other, unique problems. But one thing at a time. Mytharchive can be, from time to time, one of the most infuriating features of mythtv.

Cheers! :)

---

### Post by johnnysako on 2008-11-29
I have a fresh install of Mythbuntu 8.10 and am having the same problem as mentioned below.  I select a recording or file and still see "No Files Selected" on the archive page and thus can not archive any files to DVD.  I have checked that all files and permissions are correct and still am not having any luck.  Any help would be greatly appreciated.

-John

---

