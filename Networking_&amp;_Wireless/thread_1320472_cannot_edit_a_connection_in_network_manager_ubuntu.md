---
title: "cannot edit a connection in network manager ubuntu 9.10"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by dalfish on 2009-11-09
I have recently upgraded to karmic from jaunty. The Huawei EC325 USB CDMA modem worked fine in jaunty. It is not working in karmic. after giving the root password .I edit the connection in the network manager to provide the  username and password for logging on to the internet. after that click the automatically connect box. This worked fine in jaunty . The same procedure i repeated in karmic. after giving the root password  it returns with a dialog box saying "ERROR intialising editor insufficent previlages " then it close down the network manager. I cannot connect to the internet in karmic. Please help




Regards




Dalfish

---

### Post by madmax75 on 2009-11-09
There has been a bug affecting apparently ALL Huawei broadband modems in 9.10.

The new kernel update 2.6.31-15-generic seems to fix this. This update is in Synaptic's Proposed updates, so you have to check the appropriate box in Synpatic settings.

I have a Huawei E169 modem and the updated kernel made it work. I was able to circumvent the problem temporarrily by using the instructions a fellow named dj-toonz provided on this forum, but this was only a temporary solution.

I advice you to get the new kernel for example using another computer and then tranferring it to your computer by using a USB memory stick, if you can't get to the net at all with your computer.

---

### Post by fparri on 2009-11-10
Could you please send me the deb files with the 2.6.31-15-generic kernel. A colleague of mine here at work needs them to use his Huawei 3G dongle. Otherwise, he's connectionless ;)
I'm on a Windows box here, so I can't get them off Synaptic :(

---

### Post by dalfish on 2009-11-22
_**OLD IS GOLD **_

Thank you for your reply . I am back to Ubuntu 9.04 good bye 9.10. I removed karmic now huawei works in my ubuntu 9.04 I am happy with it. I feel 9.o4 is far better to the 9.10. It has been found that 9.10 has a lot of bugs. 9.04 will be more stable than 9.10 unless ubuntu developers fix the bugs I have decided not to go after the new releases. I have installed VLC goldeneye and Firefox 3.54 that is the main differrence in ubuntu 9.10 These are in my 9.04 and i am happy with it. [B]My advise is to simply dont go for new releases. 
[/B]It will take alot of time to fix these enormous bugs. so waiting for it is of no use. if one hardware works in a version and it does work  in another version can be embarrasing. I know that it has to be like that when it comes to linux distributions. So stick to the previous one will be better as it save your valuable time.  Jaunty jacklope you are the best.  **Jaunty We love you**


dalfish

---

