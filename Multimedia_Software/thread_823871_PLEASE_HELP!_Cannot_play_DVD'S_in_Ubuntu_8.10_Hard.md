---
title: "PLEASE HELP! Cannot play DVD'S in Ubuntu 8.10 Hardy"
date: 2008-06-09
forum: Multimedia Software
---

### Post by philidox on 2008-06-09
An error occurred Could not open location; you might not have permission to open the file.

I keep getting the error above everytime I pop in a DVD.  It works just fine under Windows Xp and my older ubuntu distributions.  Please help.  I know I have the right dependencies because I installed the exact same ones from older ubuntu distributuions.

---

### Post by mc4man on 2008-06-09
Check that you have libdvdcss2 installed. If so run 
```
sudo lshw -C disk
``` and we'll ck. out the device and links

---

