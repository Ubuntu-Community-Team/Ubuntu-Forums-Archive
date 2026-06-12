---
title: "Video driver changes when I restart (Nvidia quadro nvs 440)"
date: 2010-07-08
forum: Multimedia Software
---

### Post by henrique1977 on 2010-07-08
I'm having an interesting problem: I go to hardware settings, and activate the proprietary Nvidia driver, (the current version), and then I restart, and it works perfect. I have 4 monitors and a Nvidia Quadro NVS440 which supports 4 monitors.  

Then, it works perfectly. However, if I restart, the 3rd and 4th monitors stop working, and I can see on the nvidia-settings that they're not available. 

After trying all different scenarios, different configurations of xorg, I figure out that, when I go to Hardware Drivers under admin/preference, it says that the Nvidia current version is active but not being used. 

If I then, choose to remove and then activate again, then it tells me to restart. After the restart, then I believe the Nvidia proprietary driver is activated, and all the monitors work again, until the next restart. 

Anybody could give me an insight on this? Is there a command to check which driver it's actually using?  

I'd apreciate any help. 


I'm now running the Nvidia driver version 235. (I've tried with the 195 or the others. The same phenomenon happens).

---

