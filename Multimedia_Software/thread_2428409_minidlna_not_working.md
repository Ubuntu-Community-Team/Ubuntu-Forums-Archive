---
title: "minidlna not working"
date: 2019-10-03
forum: Multimedia Software
---

### Post by MickSulley on 2019-10-03
I installed minidlna a couple of years ago and it worked, but haven't really used it for a long time (maybe updated server version between), now it doesn't work, my server is not in the source options on the TV.

I have tried suggestions from threads on this forum,
sudo service minidlna stop
sudo minidlnad -d -R
sudo service minidlna start

which all seem to execute OK, but still I see nothing on the TV, any suggestions?

---

### Post by SeijiSensei on 2019-10-04
No one here can provide support if you're really running 11.04.  It reached end of life many years ago now.

Do you have a minidlna.log? If so, does it show any errors?

I find that deleting /var/cache/minidlna/files.db before forcing minidlna to rebuild its database can sometimes help.

The server and the TV are both in the same IP subnet, right? Like both share the same wifi router.

---

### Post by MickSulley on 2019-10-04
Many thanks for your reply.  I removed minidlna and reinstalled and now it is working!

---

