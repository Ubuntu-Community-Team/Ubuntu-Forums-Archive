---
title: "Extracting .INF from .EXE wireless card drivers"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by Papa.Smurf on 2009-05-28
Alright well i just got a Encore ENLWI-N wireless card which supposedly supported by ubuntu but unfortunately not out of the box :(

I have ndiswrapper installed but i need the .INF file from my drivers to configure my wireless, and thats where the problems start. iv tried archive manager and cabextreact (though im not positive i used it correctly) and neither was able to extract the .EXE

Help is greatly appreciated.

EDIT problem has been solved:

Here are the Ralink2860 linux drivers which are a breeze to use and the .INF and .SYS files from the windows drivers.

```
http://ubuntuforums.org/attachment.php?attachmentid=115538&d=1243562431
```

---

### Post by chili555 on 2009-05-28
Can you give me a link to the .exe? Hopefully, we can work out how to extract it.

---

### Post by Papa.Smurf on 2009-05-28
> **chili555 said:**
> Can you give me a link to the .exe? Hopefully, we can work out how to extract it.

Yup, was just about to edit OP and add it in there.

Drivers are [here]("http://www.encore-usa.com/product_download.php?region=us&bid=3"), Im using the WIN drivers.

I downloaded the Linux drivers but they seem way overcomplicated and it seems it would be easier to just try to extract the .EXE

---

### Post by t0mppa on 2009-05-28
Install 7z from the repositories (package named p7zip-full), it can do this. I had to use it to grab a .inf from a Dell support package myself. Cabextract and the others only work for files that are .exe, but self-extracting zip archives. 7z is the only one I found that can do others as well.

---

### Post by Papa.Smurf on 2009-05-28
I found the drivers, had a buddy help me out and he extracted them on his windows rig all is well now! :mrgreen:

I also found the Ralink 2860 drivers for linux which i heard also work great

Ill attack both of them in case someone has the same problem as mine.

---

