---
title: "Network not working after upgrade to Karmic"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by MickSulley on 2010-01-22
Hi,

I had everything working on Jaunty, Places > Network was showing the other machines and I could transfer files.

I upgraded my desktop and did a fresh install on my laptop, both to Karmic, since then I can't get anything to work (file wise, everything else works).

From the desktop I see 
    MICK-DESKTOP
    Windows Network

From the Laptop I see
    Windows Network

Why can I not see the other machine from each one?  I have researched the problem and followed several guides, edited various files, still it does not work.

I believe that as I only need Ubuntu to Ubuntu I can just use NFS and don't need Samba which I believe should make it simpler.  I can ping both ways, seems like I am a bit of setup missing but I cannot find it.

Can anyone help, please??????
Mick

---

### Post by quixote on 2010-01-23
If you have no Windows machines, is there a reason why the system is expecting things to run on a Windows network?  You're right that you don't need samba.  I'm not sure what the problem is, but it must have something to do with Karmic being more stringent about naming other hosts.  Or some service not being started.  I'm not that up on Karmic :(.  Maybe somebody who is will see this and jump in :).

---

