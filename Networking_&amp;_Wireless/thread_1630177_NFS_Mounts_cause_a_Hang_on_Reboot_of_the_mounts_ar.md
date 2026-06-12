---
title: "NFS Mounts cause a Hang on Reboot of the mounts are lost"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by malocite on 2010-11-24
*edit* Ooops, that should say when the mounts are lost */edit*

Sorry, even I don't know what that title meant :)  

Basically, here's the issue.  I have multiple ubuntu machines and I connect to one through an NFS share.  I have done this for a few years without issue.  However, since re-installing ubuntu and upgrading to 10.4 I have a problem with my system hanging when the remote shares are lost.

Basically, I can power down the machine downstairs, and my main machine then has a fit.  I can not open any folders in ubuntu, nor can I shut down.  If I try and shut down the system hangs, last time it hung for 8 hours before I had to kill the power.  

These are the lines in my fstab

#Mount the Mythbox
192.168.9.101:/home/malocite    /home/malocite/Mythbox  nfs     rw,async,intr,rsize=8192,wsize=8192     0       0
192.168.9.101:/home/malocite/drive01    /home/malocite/Mythbox/drive01  nfs     rw,async,intr,rsize=8192,wsize=8192     0       0

I don't know what I've done wrong, or how I can prevent this from hanging.  I have googled the heck out of this as well and can't seem to find an answer either.  Can someone help me?

---

### Post by malocite on 2010-11-28
Bump

Ok, I see 62 people have looked at the question, but no one has had an answer yet, so I thought I would chime in with some new info.  

On a whim I had a though, it turned out that idea was wrong but when I did google something similar it gave me the idea to try and force umount the drive in the console.  Using both umount and umount -f give the same error.

umount2: Device or resource busy
umount.nfs: /home/malocite/Videos/drive01: device is busy

Now, the computer with that share is now turned off, and if I try and shutdown, or reboot this machine it will hang until being force powered off.

Any ideas?  I see someone had a similar question about a year ago but he never got an answer... hopefully I will be luckier.

--malocite

---

### Post by SeijiSensei on 2010-11-29
You can't unmount a share that the OS thinks is in use.  Try "cd /" before unmounting.  You should also look to see if some program is using /home/malocite/Videos/drive01 like perhaps Nautilus.  Run "lsof | grep Videos" to see what programs are using the share.

Also you don't want to turn off the server before the client has unmounted it.  That will lead to a variety of unpleasant problems.  Run umount on the client, then shut down (never just turn off) the server.

---

