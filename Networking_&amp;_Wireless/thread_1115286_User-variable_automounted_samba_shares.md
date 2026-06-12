---
title: "User-variable automounted samba shares?"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-04-03
I have an old PC in my living room running Ubuntu (server is running Ubuntu as well) which I want to use as a multi-user system with different automounted network shares for each user. Basically I have 2 users: dan and guest. I want dan to have access to the entire home folder on the samba server (I already added the entry in fstab to automount this folder). However, I want to make it so that when "guest" is logged in, this share does not appear as a mounted network drive. Basically I want to somehow hide this share from that user, but still have it automount when "dan" is logged in. Is there a way to make this kind of conditional mounting scheme? It might have something to do with user permissions but I'm not sure where to start on that one. Worst comes to worst I could probably just get rid of the automount for the share in question, but it would be nice to have the functionality. Thanks for any help!

-Dan

---

