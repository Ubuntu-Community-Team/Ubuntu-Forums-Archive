---
title: "/usr/bin/mythpreviewgen - crashes almost daily"
date: 2014-10-03
forum: Mythbuntu
---

### Post by neutron68 on 2014-10-03
I've been seeing this crashing for 3-6 months.  
I kept expecting it would get fixed through the update repo, but no fix has come along.

DistroRelease: Ubuntu 12.04
Package: mythtv-backend 2:0.25.3+fixes.20130813.b5adf03-0ubuntu0mythbuntu2 [origin: LP-PPA-mythbuntu-0.25]
ProcVersionSignature: Ubuntu 3.13.0-36.63~precise1-generic 3.13.11.6
Uname: Linux 3.13.0-36-generic x86_64

I'm seeing someone reported this same bug back in 2012!
[https://bugs.launchpad.net/mythbuntu/+bug/1017234](https://bugs.launchpad.net/mythbuntu/+bug/1017234)

Can anyone advise how to troubleshoot and fix this?

Eric


[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20141002_185802_zpsrdfit0ks.jpg[/IMG]

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20141002_185911_zpsolxmfodc.jpg[/IMG]

[IMG]http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20141002_185927_zpsh0cnbafb.jpg[/IMG]

---

### Post by neutron68 on 2014-10-13
Has anyone else on the forum had this error occur?

If so, what have you done to remedy it?

Thanks,
Eric

---

### Post by khPWXxF on 2014-10-15
Yes - and it froze my mouse.
Google the message and empty /var/crash. My problem was related to xorg but it's a bit early to say whether it will come back. 
Phil

---

### Post by khPWXxF on 2014-10-15
Ps I wish I had checked creation time for the file against the logs.
Phil

---

### Post by tgm4883 on 2014-10-16
0.25 doesn't get any more fixes. The current release is 0.27, so you may have to upgrade to that and see if the issue persists.

---

### Post by neutron68 on 2014-10-18
Oh...no more fixes for mythtv 0.25?  I guess not every bug gets fixed in a particular release.

I'm in the process of updating to 0.27 now, to prepare for the change in Schedules Direct services.  
I'll report back if the mythpreviewgen issue gets fixed by 0.27.

---

### Post by neutron68 on 2014-10-21
After 2 full days of running myth 0.27, I have not seen a crash from /usr/bin/mythpreviewgen.

Abandoning 0.25 was a fix for this issue.

---

