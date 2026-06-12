---
title: "GMA 3100 tearing"
date: 2009-01-03
forum: Multimedia Software
---

### Post by sebrock on 2009-01-03
Since the upgrade to 8.10 from 8.04.1 I have tearing with basically everything, from desktop windows to video. As I use mythbuntu for my home theatre its basically impossible to watch anything.

I use the integrated Intel GMA 3100. Now I know this might not be the best out there but it suits my purpose just fine and it DID work perfectly in Hardy. I just hate it to see working packages get worse in later releases...

I've also read other people with similar issues. Now is there anyway to solve this or hope for an update?

regards Sebastian

---

### Post by densou on 2009-01-05
paste your xorg.conf & /var/log/Xorg.0.log

Need an update ? Add these lines to your /etc/apt/sources.list 
```
deb http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ubuntu intrepid main
```
(**stable** backports)

---

### Post by sebrock on 2009-01-05
I wiped the disk and put back my backup of 8.04.1 instead. I think I'll wait until 9.04. However as there are a lot of people with this issue (judging by previous discussions and google) this might come in handy for someone else...

you got Intel graphics yourself?

regards

---

### Post by KindredCharles on 2009-01-05
I believe the fix for this is to change your video output to x11


terminal -> gstreamer-properties -> video -> X windows system ( No Xv)

and I had to change it in vlc too.

---

