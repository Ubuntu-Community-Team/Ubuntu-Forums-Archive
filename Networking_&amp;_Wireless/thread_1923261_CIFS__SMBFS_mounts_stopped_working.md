---
title: "CIFS / SMBFS mounts stopped working"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by gushy on 2012-02-10
For some reason I can no longer mount CIFS shares on my NAS (Netgear ReadyNAS) from my ubuntu box.

This used to work and only recently stopped.  I can still connect fine using smbclient but using mount with either CIFS or SMBFS fails.

The odd thing is that it never actually 'fails', if attempt to mount I never get an error code back, just nothing happens - currently my mount command has yet to return to the command line and it's been like that for over 12 hours!

I can't see anything in any logs that would point to an issue.

If I put in the wrong credentials I got a bad password response, so it's definitely making contact with the NAS/share.

I can connect to the shares from my windows pc still

Anyone got any ideas?

---

