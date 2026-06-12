---
title: "Hp Compaq nc4010 Wlan driver"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by Firsttwo on 2012-09-16
Hey Everybody :)

Has anyone working Driver for the Hp Compaq nc4010 Wlan chip netbook on Ubuntu 10.04.X ?

When you have an Driver please let me know!
And give maybe an manual and maybe the manual in german ?! :D

---

### Post by mörgæs on 2012-09-16
The hunt for drivers downloaded from somewhere is a bad habit from Windows. 

First I would recommend a fresh install of 12.04 using wired internet access. Post again if you still have trouble after that.

A quick googling seems to indicate that you have the Intel PRO/Wireless 2200BG card. Is that correct?

---

### Post by Firsttwo on 2012-09-16
The official hp support website says the an Broadcom Wlan chip is inside the netbook !
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=de&cc=de&prodNameId=471994&prodTypeId=321957&prodSeriesId=395732&swLang=18&taskId=135&swEnvOID=1093]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=de&cc=de&prodNameId=471994&prodTypeId=321957&prodSeriesId=395732&swLang=18&taskId=135&swEnvOID=1093")

I try the fresh install with 12.04 :)

Thanks !

---

### Post by mörgæs on 2012-09-17
When you have 12.04 running using wired internet access, please run the command

**sudo lshw > lshw.txt**

and post the contents of lshw.txt here (in code tags). The command might take a while to complete.

---

