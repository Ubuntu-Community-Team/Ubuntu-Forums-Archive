---
title: "File /tftpboot/mvp.bin not found"
date: 2009-12-03
forum: Mythbuntu
---

### Post by MountainX on 2009-12-03
I am using [this guide]("https://help.ubuntu.com/community/MythTV/MediaMVP_Frontend") to set up a MediaMVP frontend with Mythbuntu 9.10.
 
After completing all the basic installation steps, I attempted to boot up the MediaMVP. The boot process did not complete, so I checked the logs:
$ tail -n 25 /var/log/syslog
Dec  3 10:49:14 myMythBE atftpd[2306]: socket may listen on any address, including broadcast
Dec  3 10:49:14 myMythBE atftpd[2306]: Creating new socket: 192.168.2.107:43431
Dec  3 10:49:14 myMythBE atftpd[2306]: Serving mvp.bin to 192.168.2.103:3909
Dec  3 10:49:14 myMythBE atftpd[2306]: **File /tftpboot/mvp.bin not found**
Dec  3 10:49:14 myMythBE atftpd[2306]: Server thread exiting
Dec  3 10:49:54 myMythBE atftpd[2306]: socket may listen on any address, including broadcast
 
Indeed, there is no mention of /tftpboot/mvp.bin in the how-to. As a guess, I copied dongle.bin to mvp.bin. Now the MediaMVP will boot up, but it lacks the MythTV configuration.
 
Searching on Google gives: **No results found** for "File /tftpboot/mvp.bin not found".
Wow. No one else has run into this???
 
more info:
MediaMVP Model 86001 rev D3A.ot4503
# uname -a
Linux 192.168.2.103 2.4.31-v1.1-hcwmvp #1 Tue Feb 20 22:58:51 CST 2007 ppc unknown
 
 **Can anyone tell me where I went wrong?**

---

