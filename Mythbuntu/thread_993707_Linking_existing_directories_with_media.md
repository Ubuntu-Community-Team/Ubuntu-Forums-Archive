---
title: "Linking existing directories with media"
date: 2008-11-26
forum: Mythbuntu
---

### Post by c$$lguy on 2008-11-26
I have front-end and back-end both on the same computer. My media files are all in my Home directory. Recently I got PS3 and use it as a UPnP client and MythTV as a multimedia server. I managed to change Video directory but I cannot do it for Pictures and Music. My music and pictures files are located in the my Home directory. How can I change MythTV settings to pick up this data? Can I link my home directory stuff to /var/lib/mythtv/...? I tried but it did not work.

---

### Post by dmfrey on 2008-11-26
I link my music, photos and videos...They are located on a nfs mount on my server.  I mount something like /opt/multimedia and then link, for instance, /opt/multimedia/music/library to /var/lib/mythtv/music/library.

There are no changes required in MythTV then as mythbuntu has these directories setup already.

---

