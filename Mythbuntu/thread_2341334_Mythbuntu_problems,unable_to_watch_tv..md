---
title: "Mythbuntu problems,unable to watch tv."
date: 2016-10-27
forum: Mythbuntu
---

### Post by isprins on 2016-10-27
Hi, every time i try to watch tv,i go to the "watch tv", it flashes "please wait" on the screen momentarily and then returns to the menu! 
All my logs can be found here:
[https://www.dropbox.com/sh/eh5o2wwm7ltoqwx/AAAm-QPKAwH8DxBO65YT8H7Ka?dl=0](https://www.dropbox.com/sh/eh5o2wwm7ltoqwx/AAAm-QPKAwH8DxBO65YT8H7Ka?dl=0)

I am aware that the CAM reader was not plugged in at the moment,but i
have also the same problem with the CAM interface present and the card
inserted in the CAM reader.

The files present are:
dmesg.log 

mythfrontend.log      
mythtv-setup.log
mythbackend.log
mythmetadatalookup.log 

syslog
I am running the latest version of mythbuntu

---

### Post by aelfric55 on 2016-10-27
The frontend log includes the message that the backend may be misconfigured. 

The backend log shows two errors that are possibly significant. The first is that "no recorders have been defined..." which implies the full backend setup may not have been properly completed. 

The second error is that when your live TV is started, the backend  attempts to write to a directory /home/[YOURUSER]/Mythtv/... which is not writeable for the backend. It produces a "permission denied" error in the log. Mythtv usually installs by default with recording directories under /var/lib/mythtv/[recordings, etc.]... with the ownership/group of this path set to mythtv:mythtv This avoids the weird permissions glitches that tend to pop up constantly when one tries setting up mythtv storage under /home/[YOURUSER]/...

---

### Post by isprins on 2016-10-27
Huhm, I will try a new clean install and leave the storage directories alone,I hope that works.
I also will follow this guide:
[https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit#heading=h.yco0jatmc7xq](https://docs.google.com/document/d/19knOlqz8cV5_8VQ1tCvEd8tjEk6U50KsSOJCROR60o4/edit#heading=h.yco0jatmc7xq)
The weird thing is that i am quite certain that i did set up the DVB-C card correctly, so i am puzzled.
I will also try to get Mythbuntu to auto mount my HDD, i am installing on a 250 GB SSD.

---

