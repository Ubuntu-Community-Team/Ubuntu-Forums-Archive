---
title: "Mythweb stops responding after the box has been running for several hours."
date: 2016-06-12
forum: Mythbuntu
---

### Post by tim129 on 2016-06-12
I'm running Mythbuntu 16.06 with 28 Mythtv backend. Mythweb works when I first start the box, but after several hours the response returns an error without information on some of the pages. I still get a response but it takes a minute or two for it to reply and then at the top of the page I usually see this error:

User Notice at /usr/share/mythtv/bindings/php/MythBackend.php, line 110:
!!NoTrans: Unexpected response to MYTH_PROTO_VERSION '88': !!

The page doesn't include the expected information. I don't get a list of recordings or the mythbackend status. My guess is the mysql access is getting snorked somewhere... maybe it's running out of memory having too many accesses??? I can log into the machine and run stuff fine on the machine except for mythweb. I think this issue may also be related to why if I have a recording start shortly after being rebooted it seems to work, but if its been 24 hours or a day or two the box is nothing is recorded but a 1 minute entry is in the database along with pointing to a file.

If you can offer help.... thank you in advance.

---

