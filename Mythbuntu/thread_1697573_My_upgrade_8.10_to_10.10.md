---
title: "My upgrade 8.10 to 10.10"
date: 2011-03-01
forum: Mythbuntu
---

### Post by gmurison on 2011-03-01
So since my mythbuntu FE/BE had been running flawlessly, I had let itself get outdated.  Another reason was that I was saving up for a new TV.  So I got the new TV and so I might as well upgrade to the latest mythbuntu.

After backing up the DB and some pertinent configs, I did a clean install, (I had to, I couldn't upgrade for some reason I was getting a ton of 404 errors) Next I used the instructions ([ http://mythbuntu.org/upgrading]("http://mythbuntu.org/upgrading")) to restore my old db.

I came across the "no current version" error when the schema was being upgraded. I logged in mysql and verified that DBSchemver from mythconverg.settings showed 1216. So I tried again, by dropping the db again and trying another restore.  This time it worked! I think I missed stopping the backend by mistake, but I am not sure.

My second issue was that the frontend was getting "no tuners, but no active recordings".  I went to information center/tuner status and both said unavailable (I have a PVR-500).  Thanks to volkswagner and ian dobson, your posts somewhere on this forum put me on the right path.

I hope this helps someone else with their upgrade pains.

---

