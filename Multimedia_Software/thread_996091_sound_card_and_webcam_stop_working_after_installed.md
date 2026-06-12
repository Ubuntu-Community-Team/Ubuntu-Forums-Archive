---
title: "sound card and webcam stop working after installed latest kernel update 2.6.24-22"
date: 2008-11-28
forum: Multimedia Software
---

### Post by unclesam.xu on 2008-11-28
Last night I applied kernel update to 2.6.24-22, after I restarted the computer, I found out that my sound card (VIA8233) and logitech webcam stop working. I have checked this forum, It looks like I am not alone. 

Now the work around is every time I turn on my computer, I have to choose the previous kernel 2.6.24-21 to start ubuntu 8.04 in order to have the sound and webcam working properly. So I can use gizmo and skype to comunicate with others.

That is why I am sure there is a kernel glitch in the new 2.6.24-22. 

Hope it will be fix soon.

that is why I always delay about 6 month to upgrade to the most updated version of operating system.

sigh

sam

---

### Post by markbuntu on 2008-11-28
If you have upgraded your alsa version or have switched to OSS, you will need to do that over again, same if you used a non-repository driver for your cam. The kernel build does not recognize non-suppoted changes you may have made to it, does not know what to do with them and so leaves them out of the build. 

It is very important to watch the terminal window when updating the kernel because it will give you messages about modules it is unable to install or resolve automatically.

---

### Post by unclesam.xu on 2008-11-30
I installed 7.04 then 7.10 then upgrade to 8.04. It always no problem with my audio card and webcam. it was both runs normal. I have run this computer from 7.04 till now 8.04 for a year and half without a problem . why upgrade to 2.6.24-22 kernel will have a problem?

---

### Post by markbuntu on 2008-11-30
If that is the case, you should file a bug report at launchpad.

---

### Post by unclesam.xu on 2008-11-30
Yeah, I am using the old kernel with no problem. I will report the bug

---

