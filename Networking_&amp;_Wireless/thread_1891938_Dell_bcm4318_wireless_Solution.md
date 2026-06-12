---
title: "Dell bcm4318 wireless Solution"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by drf_engineer on 2011-12-06
Issue: Ubuntu 11.10 Dell Wireless Card Issue & Resolution
 

 This is a summary of the issue I had with my Dell Wireless Card using Ubuntu 11.10 and how I resolved it. Hopefully will save you some time...  
 

 This applies to the bcm4318 card/chip-set.
 

 After installation of Ubuntu 11.10 from Windows XP the network connections drop - down stated that &#8220;Firmware was missing&#8221;. I installed the 'Synaptic Package Manager'. Following this, I installed the following to match the bcm4318 card,
 

 
[LIST]
[*]'firmware-b43-installer'
[*]'b43-fwcutter'
[/LIST]
 

 and rebooted...
 

 After rebooting I got the error about the 'wireless disabled by hardware switch'. I then pressed Fn+F2 (your keyboard may be different, whatever turns on your wireless via Fn on your keyboard), and within 30
 seconds my wireless was working.  
 

 This article is just to summarize how I got mine to work, since theirs a lot of people having issues with this chipset/card. If you think there could be improvements or additional information added to this, please leave it/comment.

Cheers,
drf_engineer

---

