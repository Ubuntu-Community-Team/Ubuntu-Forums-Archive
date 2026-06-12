---
title: "[SOLVED] probably a user issue"
date: 2008-05-08
forum: Mythbuntu
---

### Post by malaTG on 2008-05-08
Hi everyone,

I installed ubuntu 8.04 on my computer and I suspect that I have some problems regarding user privileges. 

I installed the mythbuntu control center on top of my ubuntu installation and everything seems to work aright except for mythfilldatabase. I live in Sweden and use xmltv to grab my TV information but it doesn't work... 

I suspect that it is because I don't run mythtv as the user mythtv but my regular user login name. Is there something I can change so that mythtv/xmltv etc. recognizes my normal user and runs mythfilldatabase etc? or do I have to create a mythtv user or something in order to get mythtv to wrok properly?

Hoping for help....

Marcus

---

### Post by Nikas on 2008-05-08
> **malaTG said:**
> Hi everyone,

I installed ubuntu 8.04 on my computer and I suspect that I have some problems regarding user privileges. 

I installed the mythbuntu control center on top of my ubuntu installation and everything seems to work aright except for mythfilldatabase. I live in Sweden and use xmltv to grab my TV information but it doesn't work... 

I suspect that it is because I don't run mythtv as the user mythtv but my regular user login name. Is there something I can change so that mythtv/xmltv etc. recognizes my normal user and runs mythfilldatabase etc? or do I have to create a mythtv user or something in order to get mythtv to wrok properly?

Hoping for help....

Marcus

Hej hej,

How do you configure xmltv and please specify "doesn't work" ;)

Herrå.

/Nicke

---

### Post by malaTG on 2008-05-08
Hi Nikas

Thank you for answering!

I havn't configured xmltv in any "special" way. I have gone through the settings for mythtvbackend and when I get to the "video sources" section I chhose xmltv sweden and do the setup however after that I can't run mythfilldatabase. It fails to get the data with error 256. As I mentioned earlier I think it has to do with the fact that I don't have a mythtv user and I that haven't checked the box in mythbuntu control center for automatic login because then I get the xfce desktop which I don't want.

Is there any configuration file i can give you in order to explain it better?

/Marcus

---

### Post by Lindsay.Mathieson on 2008-05-10
Hi Marcus,

can you run mythfilldatabase from a console login and post the output here?

---

### Post by malaTG on 2008-06-04
This issue has been resolved. The problem was that all my xml settings was under my "normal" user not under my mythtv user. I just made soft links and gave my mythtv user permissons

/Marcus

---

