---
title: "Need help getting ltsp clients to boot"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Lifebandit on 2011-01-30
I have installed Ubuntu 10.10 and installed and configured the software from this page [http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166) to the "T" untill it got to the "Preparing the Client" section. All that information wanted me to go to the Rom-o-matic site to build the boot disk. But the site is down. So I looked around the net and found a generic Pxe boot disk img that had the drivers for my nic. I booted the client and it downloaded the file nbi.img from the ltsp server. When it got finished with the transfer, it said "Done" and then stops. The client does nothing after that. 


What am I doing wrong?

---

### Post by gottr on 2011-02-10
It sounds like your networking is ok.  I would imagine your image is not proper.  Why not create an image via the ltsp-build-client command via the server command line?

---

