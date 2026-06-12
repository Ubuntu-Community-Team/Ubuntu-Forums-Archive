---
title: "video drivers needed!"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by rkakkar on 2006-12-01
hello all.. i have the gigabyte GA-8GEM800 motherboard using onboard graphics. although ubuntu has detected the card, i think that i am not getting any 3d acceleration out of it because my opengl screen savers are not smooth. i checked their driver page:

[http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800](http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800)

but there are no drivers for linux. can someone help me? since i want to play Quake 3 on ubuntu.

---

### Post by zgornel on 2006-12-01
> **rkakkar said:**
> hello all.. i have the gigabyte GA-8GEM800 motherboard using onboard graphics. although ubuntu has detected the card, i think that i am not getting any 3d acceleration out of it because my opengl screen savers are not smooth. i checked their driver page:

[http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800](http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ClassValue=Motherboard&ProductID=1835&ProductName=GA-8GEM800)

but there are no drivers for linux. can someone help me? since i want to play Quake 3 on ubuntu.
To check for direct rendering do *glxinfo |grep direct*. Also, run *glxgears -printfps* and post the number of frames reported. The video chipset might be a i830 which is not very powerful.

---

