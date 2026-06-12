---
title: "[SOLVED] XC5000 firmware and Pinnicle PCTV HD Card"
date: 2009-01-07
forum: Mythbuntu
---

### Post by RonPDX on 2009-01-07
Good evening everyone, 

I am trying to get my Pinnacle (801?) to work with Mythbuntu, from what it appears, I don't have the XC5000 firmware installed. I have managed to download the firmware and when I try to extract it to the drivers directory I get a permissions error, I have even tried extracting it to the desktop and dragging it over but I get the same error. 

Am I doing something wrong? Is there a command line that I can use to extract the firmware to the drivers folder? 

Thanks in advance, 

Ron

**Update**

I finally was able to extact the zip file, know my only problem is copying it to lib/firmware, the error I receive "Error moving file, you don't have permissions". Looking at the permissions, it is owned by root. Any ideas? Sudo command line perhaps?

Thanks again, 

Ron

---

### Post by crez79 on 2009-01-07
> **RonPDX said:**
> I finally was able to extact the zip file, know my only problem is copying it to lib/firmware, the error I receive "Error moving file, you don't have permissions". Looking at the permissions, it is owned by root. Any ideas? Sudo command line perhaps?

From the command line use

```
cd /directory/to/firmware/file
sudo cp firmware.file /lib/firmware
```

if you prefer using a gui,from the command line

```
sudo thunar
```

and that should open thunar with root privilages to allow you to copy into /lib/firmware.

---

