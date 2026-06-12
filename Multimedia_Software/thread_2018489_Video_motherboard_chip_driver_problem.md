---
title: "Video motherboard chip driver problem"
date: 2012-07-06
forum: Multimedia Software
---

### Post by flandyman on 2012-07-06
Hi real new beginner here, apologies for this if already answered elsewhere, got tired of windows got new base unit so took the plunge and installed Ubuntu 12.4lts - so far so good, tried to set up screen res to previous settings and no way - only showed 'unknown' and then 1024 x 768 res. or 800 x600 - its an on motherboard video chip and shows as ATI RS780L Radeon HD3000 - there is ref to a driver in additional drivers that shows a ATI/AMD FGLRX driver but when I installed this and rebooted the screen shows a message that says it cant display at that res and I cant get into Unbuntu - ended up having to rebuild from scratch - any ideas as to a driver I can install to get the video working to full res and get the best out of it?

Thanks for any advice a simpleton can follow ;)

---

### Post by Vakman on 2012-07-21
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6)
That link will take you to how to install the drivers manually. If you have any questions, just let me know. The driver you will want to use is on this page here: [http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx](http://support.amd.com/us/kbarticles/Pages/catalyst126legacyproducts.aspx)

---

### Post by Yellow Pasque on 2012-07-21
^Catalyst 12.6 dropped support for RadeonHD 2000-4000 series cards, so that's a no go..

---

### Post by Vakman on 2012-07-21
> **Temüjin said:**
> ^Catalyst 12.6 dropped support for RadeonHD 2000-4000 series cards, so that's a no go..

I didn't know this but it seems this is as off 12.7 anyhow. What I am using works fine for me, it is the beta 12.6 driver.

---

