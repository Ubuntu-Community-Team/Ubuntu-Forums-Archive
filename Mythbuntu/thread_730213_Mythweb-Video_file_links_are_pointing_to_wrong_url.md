---
title: "Mythweb-Video file links are pointing to wrong url"
date: 2008-03-20
forum: Mythbuntu
---

### Post by jalmargyyk on 2008-03-20
When I try to click file for download, the link seems to be pointing to wrong url. 

For example, if I click link for video Test.iso, I get the following message:

The requested URL /mythweb/data/video//home/jallu/Elokuvat/Test.iso was not found on this server.

As far as I understand the url is parsed together incorrectly, since it should be pointing to /mythweb/data/video/Test.iso 

My symbolic link to video directory in mythweb/data is as follows:
video -> /home/jallu/Elokuvat/

I'm using Mythbuntu 8.04 Alpha 4 with the latest updates.

---

### Post by slyhne on 2008-05-20
Hi

I'm having the same problem...

If you found a solution I would be glad to hear about it.

Regards 

slyhne

---

### Post by jalmargyyk on 2008-05-21
Unfortunately I haven't found any solution to this yet. Probably a minor parsing issue in mythweb code, but nobody has corrected it yet.

---

### Post by impossibilechecisiaquesto on 2009-02-25
Change /var/lib/mythtv/videos to /var/lib/mythtv/video

---

