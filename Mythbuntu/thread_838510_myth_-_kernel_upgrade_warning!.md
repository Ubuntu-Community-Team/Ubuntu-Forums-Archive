---
title: "myth - kernel upgrade warning!"
date: 2008-06-23
forum: Mythbuntu
---

### Post by zzztownsend on 2008-06-23
Hi folks


Yesterday - just done the apt-get upgrade to latest kernel 2.6.24-18 & mythbuntu weekly builds

BAD IDEA!!

Made a proper hash of my system. mythbackend won't run. keeps deleting /etc/mythtv/mysql.txt. 'quit' from right click on desktop doesn't

checked repositories and another kernel release has come out today 2.6.24-19. Installed this and most of the problems are gone but very jerky live TV playback and can't schedule any recordings - these just get forgotten

Please don't take this as a grumble because the efforts that go into ubuntu/mythtv are impressive - just note that if you're a bit of a numptie like me then its probably best not to upgrade for a while!!!!!

Moderators - if its bad form to post a message like this then feel free to remove sorry - just trying to let folk know 

Cheers

Matt

---

### Post by danbodoh on 2008-06-23
Your problems are probably due to the weekly myth builds, rather than the kernel.  I'm running the -19 kernel with no problems.

Dan Bodoh

---

### Post by superm1 on 2008-06-23
I would recommend you take a look at /var/log/mythtv/mythbackend.log to figure out why the backend isn't running.  Most common cause is permissions.

---

### Post by superm1 on 2008-06-23
And also, I run -19 on 4 different boxes without any problem.  VERY highly doubtful anything introduced in stable kernel updates (that only bump ABI) will cause these behaviors.

---

### Post by dsegel on 2008-06-23
Some recent update hosed my system as well but a little investigation revealed the only real problem was that the /etc/mythtv/mysql.txt file has been reduced to 0 bytes. Replacing it with the version from /usr/share/mythtv/mysql.txt.dist and putting the password back in fixed things up.

I am running the weekly updates so something there may have caused this. This problem also caused mythfrontend (or backend, I can't remember which) to create an enormous log file that eventually filled up my root filesystem.

Anyway, after fixing the mysql.txt and deleting the log file everything is working fine again.

---

### Post by zzztownsend on 2008-06-24
thanks for your replys guys - sorry if I'm wrong about the kernel part. 

I had already found that the mysql.txt file had been reduced to 0 bytes and fixed this - also an enormous (6GB) log file which I deleted

backend is now runing but frontend is not OK

In liveTV video is now very choppy and OSD seems to 'ripple'. If I record and then watch the recording close to real time, video displays fine
Also when in 'schedule recordings' pressing record or pressing enter and setting to record causes screen to refresh but system does not remember to record. 

Will post a typicical frontend log

Any help appreciated

Thanks

Matt

---

### Post by chrisork on 2008-06-27
zzztownsend, I have exactly the same problems.

choppy live tv. recordings playing fine. 

did you solve the problem?

---

### Post by db260179 on 2008-06-27
You can try my custom ubuntu kernels. Amd64 only and generic (intel etc)

64bit kernels only. We are in the 21st century.

[http://gallery.mulberry.towerhamlets.sch.uk/kernelamd64.rar](http://gallery.mulberry.towerhamlets.sch.uk/kernelamd64.rar)

[http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar](http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar)

Hope it helps?




> **chrisork said:**
> zzztownsend, I have exactly the same problems.

choppy live tv. recordings playing fine. 

did you solve the problem?

---

### Post by chrisork on 2008-06-29
i've booted into the other, older kernels.

still the same issues. live tv not watchable, recordings normal.

:confused:

---

