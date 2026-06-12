---
title: "Wireless internet card wont work"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Demonflame on 2009-06-06
I have a C-MOTEC CDU-680 wireless internet card(sort like like an Edge car, but it doesn't use 3G) that has install directions for Linux. When I follow said instructions I get to the last step and it fails, because of a segmentation error. Is this something fixable?
 
 
> Copy the Linux Folder from your device to your Desktop
Open terminal 
Run "cd Desktop/Linux"
Run "sudo ./connect"
Enter root password
Device will switch to modem mode and attempt to connect. 
Press Ctrl-C twice to disconnnect
FOR SIP/MIP Preferr(QCMIP=0 or 1) Carriers
SIP carrier case, you may need to modify following part at ¡°execute.sh¡± file.
Please replace Username and Password with your Service providers (SIP User ID and Password) 
"Phone = #777\nUsername = broadband\nPassword = broadband" >> cdu680config
Username= broadband -> see followings
Password= broadband -> see followings
ACS Alaska
Security (Simple IP, 1xEVDO) 
Login(User Name or Account Name): [EMAIL="MDN@acsalaska.net"]MDN@acsalaska.net[/EMAIL] (MDN: 10 digit Phone Mumber)
Password: MDN (MDN: 10 digit Phone Mumber)
 
 
Those are the directions. Everything will go just fine until I put in the password, then it says there is a segmentation error. What's more is I've had two different friends try this out. One uses Ubuntu, the other uses Kubuntu. They both get the same exact thing. I've had to re-install windows as I live in the middle of no where and missed going online.

---

### Post by Demonflame on 2009-06-06
Bump.

---

### Post by Demonflame on 2009-06-06
Hello?

---

