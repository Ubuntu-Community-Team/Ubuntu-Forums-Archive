---
title: "Broadcom 4311 device not working after upgrade"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by dempewolff on 2013-01-10
Upgraded to 12.04 (from 10.xx I believe). Wireless driver not working properly. Checked the document which describes how to fix this on Natty. Tried the commands on 12.04. First I entered "sudo apt-get purge bcmwl-kernal-source broadcom-sta-common broadcom-sta-source" (which seemed to go okay), I entered "sudo apt-get install b43 fwcutter firmware-b43-installer" on the terminal, I got files not found (b43 and fwcutter). I was using the wired connection to get info. So... are there different commands I should be running for 12.04? Any help would be appreciated.

---

### Post by audiomick on 2013-01-13
> **dempewolff said:**
> ...I entered "sudo apt-get install b43 fwcutter ...I got files not found (b43 and fwcutter). 

There is a hyphen missing there, at least the way you wrote it here. The package is called
```
b43-fwcutter
```

Without the hyphen, apt-get thinks that "b43" and "fwcutter" are two separate packages.

---

### Post by dempewolff on 2013-01-13
Thanks Michael! that was it. I was too lazy to setup a wired connection so I fired up WinXP to get to the forum; I manually copied the command on paper (and incorrectly at that as you noticed) and then booted up Ubuntu.

Command executed without errors. I rebooted after disconnecting the wired connection. Still not working properly though. I'll check out open Linux forum link that you posted.

Thanks again, Peter

---

### Post by dempewolff on 2013-01-13
Fixed. Rebooted a second time. The wireless connections showed up in drop down menu this time. Bingo

---

### Post by audiomick on 2013-01-13
Great. Glad you got it fixed.

---

