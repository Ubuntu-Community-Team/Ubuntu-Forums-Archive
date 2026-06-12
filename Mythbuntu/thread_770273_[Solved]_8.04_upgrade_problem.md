---
title: "[Solved] 8.04 upgrade problem"
date: 2008-04-27
forum: Mythbuntu
---

### Post by jonals111 on 2008-04-27
I've been running mythbuntu 64 bit for a year now with no problems. Decided to upgrade yesterday to 8.04 using update manager, and during the file upgrade process it rebooted and now I cannot boot into x-windows or find my precious home directory. 

I have tried the livecd 64bit and 32bit iso versions of Mythbuntu and the computer reboots each time about 10 seconds into the boot (safe graphics mode). Also tried an ubuntu 64bit iso and the same problem occurs.

But 7.10 Mythbuntu boots fine off the cd and finds my home directory on the hard disk, all intact.

it's a while since I fiddled with linux. Is there a way to see what is the causing the problem? Anyone got any ideas of what the problem is? The machine is fairly standard spec:

amd 4600
abit an-m2 
nova-T
samsung 250gb spinpoint

Thanks
Jon

---

### Post by twright on 2008-04-27
if you type sudo init 1 into terminal and then select fix x that might sort it

---

### Post by jonals111 on 2008-04-27
'fix x' came back with unknown command. However, I tried underclocking the RAM and it now installs fine. Strange that the RAM is fine with 7.10 but not 8.04.

thanks

jon

---

### Post by venator260 on 2008-04-27
doing the Fix X after sudo init 1 worked for me. 

I'm using a Toshiba Portege M200 with a Nvida graphics card. Had the same problem after doing an upgrade from Gutsy>Hardy.

---

