---
title: "Ubuntu 12.04-Skype beta 2.2 camera issue"
date: 2012-06-17
forum: Multimedia Software
---

### Post by ddrasko on 2012-06-17
Hi guys,
I am pretty new with Linux (not total beginner but close). I installed Ubuntu 11.10 and just upgraded it to 12.04 last night. Same issue with SKYPE 2.2 beta-after few min (1-2 min usually), other person video becomes "mosaic" picture like in witness protection program :lolflag:
When other person restart his camera, video comes back. But if done to quickly, my Skype dies!?
Note that this is happening only between Ubuntu and Windows. If I talk with someone that using Skype on iPad (for instance), it's fine.
What could be an issue here and how to fix it? Since I see my picture/video, camera seems to be fine.
Thank you in advance.

ddrasko

---

### Post by Bobhuber on 2012-06-17
> **ddrasko said:**
> Hi guys,
I am pretty new with Linux (not total beginner but close). I installed Ubuntu 11.10 and just upgraded it to 12.04 last night. Same issue with SKYPE 2.2 beta-after few min (1-2 min usually), other person video becomes "mosaic" picture like in witness protection program :lolflag:
When other person restart his camera, video comes back. But if done to quickly, my Skype dies!?
Note that this is happening only between Ubuntu and Windows. If I talk with someone that using Skype on iPad (for instance), it's fine.
What could be an issue here and how to fix it? Since I see my picture/video, camera seems to be fine.
Thank you in advance.


ddrasko
You might try updating to Skype 4.0. It sounds more like a memory or hardware issue though.

---

### Post by ddrasko on 2012-06-17
I tried that. First I checked ubuntu software center and I couldn't find Skype 4.0 for linux.
Then I downloaded it from Skype website. BUT, I got some weird error so I could not install 4.0 on there.
Just to be on safe side, what would be procedure to upgrade to Skype 4.0? Should be simple as download and install, right?
I suspected also on some hardware issue, but since iPad connection is superb, I think that is not the case.
What you think about idea to put Windows version through WINE?
(I would rather keep linux tho)

Thanks

---

### Post by Bobhuber on 2012-06-17
> **ddrasko said:**
> I tried that. First I checked ubuntu software center and I couldn't find Skype 4.0 for linux.
Then I downloaded it from Skype website. BUT, I got some weird error so I could not install 4.0 on there.
Just to be on safe side, what would be procedure to upgrade to Skype 4.0? Should be simple as download and install, right?
I suspected also on some hardware issue, but since iPad connection is superb, I think that is not the case.
What you think about idea to put Windows version through WINE?
(I would rather keep linux tho)

Thanks
Nope Wine and skype is not a good idea. You need to use the downloaded version from Skype and remove your current version before you try installing Skype 4.0.
To uninstall your present version from a terminal :
sudo apt-get purge skype
 sudo apt-get purge skype-bin
 sudo apt-get autoremove

Install the gdebi package installer
sudo apt-get install gdebi

Right click on the downloaded  file and select gdebi package installer to install the new version of skype.

---

### Post by ddrasko on 2012-06-17
Thank you. I will try that and let you know what happens.

---

### Post by ddrasko on 2012-06-19
I upgraded Skype to 4.0 as you instructed. Made test call for like 15 min. Everything was fine. Fingers crossed.
Thanks!
Do you know will video conference calls be available soon for Skype linux?

---

