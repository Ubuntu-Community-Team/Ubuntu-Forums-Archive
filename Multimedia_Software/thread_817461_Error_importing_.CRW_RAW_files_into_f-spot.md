---
title: "Error importing .CRW RAW files into f-spot"
date: 2008-06-03
forum: Multimedia Software
---

### Post by frogitts on 2008-06-03
When trying to import a .CRW (canon RAW image) into fspot, I get the error: "Error importing [file name] Invalid Cliff Header Block"

Unfortunately, I don't know what a Cliff Header Block is, so I can't fix it. Digikam and gthumb have no problems with these files. Is there something I can do to import these files, or at least some way around clicking "Skip" a few hundred times in order to import my remaining .jpg pictures into f-spot?

---

### Post by tirithen on 2008-12-11
I'm having this problem too, someone that has a solution? Can I skip the crw files ll together?

---

### Post by ahillsbe on 2009-02-26
I am having this problem also!

When I use the terminal with super user privileges, it returns this

```
Error importing /media/disk/DCIM/218CANON/CRW_3802.CRW
FSpot.ImageFormatException: Invalid Ciff Header Block
  at FSpot.Ciff.CiffFile.Load (System.IO.Stream stream) [0x00000] 
  at FSpot.Ciff.CiffFile.get_Root () [0x00000] 
  at FSpot.Ciff.CiffFile.get_Date () [0x00000] 
  at FileImportBackend.ChooseLocation (System.String path, System.Collections.Stack created_directories) [0x00000] 
  at FileImportBackend.Step (.StepStatusInfo& status_info) [0x00000] 
Syncing metadata to file...
old = "" new = "" heading = "ASCII"
value = 2009:02:10 01:34:41 len = 19
value = f-spot version 0.5.0.3 len = 22
value = 2009:02:25 22:52:46 len = 19
value = f-spot version 0.5.0.3 len = 22
value = 2009:02:25 22:52:46 len = 19
Saved 7919 bytes


```
I am using a Canon s3is with the chdk hack.

...Also, maybe unrelated...  the F-spot photo thumbnails no longer link to the image locations and cannot write imported pictures to /media/sdb2/My Documents/Pictures.  Hope someone can help...

---

### Post by anabelle on 2009-04-19
Same error Here, also using CHDK hack..

---

### Post by bristolbadger23 on 2009-05-26
Did anyone get a fix? I'm using CDHK, on a S5IS and ubuntu Intrepid

---

### Post by fyo on 2009-07-01
```
sudo apt-get install gimp-ufraw
```

That will at least allow you to open them in GIMP.

---

