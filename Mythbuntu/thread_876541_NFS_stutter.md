---
title: "NFS stutter"
date: 2008-07-31
forum: Mythbuntu
---

### Post by whosmatt on 2008-07-31
I'm trying to offload some video from my myth box's internal HDD to a Freenas server via NFS.  I have mounted a NFS share in /var/lib/mythtv/videos/Podcast and am playing back H.264 video from revision3.com.  the video plays great locally but stutters when played over NFS. this is a bit puzzling since the video is consuming only ~3Mbps over a 1000Mbps connection as measured by the Freenas gui.

Any NFS tuning variables that will help me out?  Here's my mount from /etc/fstab:

freenas.local:/mnt/BIGUN/mythtv/Podcast /var/lib/mythtv/videos/Podcast nfs suid,dev,exec 0  0

I just followed the syntax from other nfs mounts in fstab which i think were created by webmin but i don't remember.

thx
matt

---

### Post by ian dobson on 2008-08-01
Hi,

Have a look here [http://docs.hp.com/en/B1031-90061/ch05s04.html](http://docs.hp.com/en/B1031-90061/ch05s04.html), maybe there are afew tips you can try.

In my tests I actually got better performance using Samba/CIFS than NFS on exactly the same hardware (Frontend C2D 1.6GHz, Backend Quad C2D 2.4GHz over a 1Gb network).

Regards
Ian Dobson

---

