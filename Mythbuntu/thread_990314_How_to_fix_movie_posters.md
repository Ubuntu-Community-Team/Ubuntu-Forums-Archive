---
title: "How to fix movie posters"
date: 2008-11-22
forum: Mythbuntu
---

### Post by whaase on 2008-11-22
I downloaded Mythbuntu 8.10 and installed it on my media machine. Everything worked perfect except the movie posters. After hours of trying to figure out why, I decided to check the logs LOL

From the default install, the following directory is not created that needs to be.

/home/mythtv/.mythtv/[COLOR="Red"]MythVideo[/COLOR]

Create the MythVideo directory, I did a chmod 777 to it. After that, posters are working perfect

---

